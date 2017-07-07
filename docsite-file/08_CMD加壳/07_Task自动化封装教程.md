###  **Task自动化封装教程**
**更新记录：**

| 日期        | 姓名   |  事宜  |
| --------   |:-----:  | :----:  |
| 2016-07-27    | 边联乐| 第一版编写完成    |
| 2016-08-05    | 宗杰| 修改Quick start，换成简单的CMD命令    |
|2017-7-6     |   边联乐  |    整理更新  |

&nbsp;
####  **一. Task封装简介**	
　　Task封装是一种快速将第三方软件封装为task，并在NovelBrain云平台上运行的解决方案，不但能够高度可定制化cmd命令，而且还可以将多个输入文件并行的分布在不同服务器上运行，以实现并行计算的目的。
　　NovelBrainTM的task运行基于虚拟机系统，我们选择了docker作为轻量级虚拟机系统，每个分析task都会在指定的docker Image中运行。以此保证了软件版本的稳定性和分析task的可回溯性。因此在上线自定义的task之前，需要上传自己的docker image，或者指定使用已有的docker image。
　　此外NovelBrainTM会根据task传入文件的分组信息(Prefix)的不同，将不同的文件分组在不同的docker虚拟机中运行，从而实现并行计算的目的。因此在编写自定义task的过程中，我们需要指定具体哪些参数/输入文件需要分组并进行并行计算。
　　本教程提供了从易到难的一系列教程，希望能快速帮助用户编写自己的application。

####  **二. 步骤介绍**	
Cmd封装分为三个步骤：
1. 添加task与task参数配置
我们需要创建一个task，上传相关的docker镜像（可选），并给task指定需要运行的镜像。同时还要配置task在前端所展示的参数。在本步中我们需要指定哪些参数可以进行切分（分组），从而实现并行计算。
2. 编写相关的xml文件并上传
我们需要将cmd所用到的一系列命令和参数编写成一个或多个xml文件，并且放在指定的stage中并上传。
3. 编写结果相关的xml并上传
NovelBrainTM提供了一个workflow引擎，即当我们拖拽好一个workflow后，系统就可以从头到尾的执行workflow中的task。这就要求我们必须事先知道某个task会产生哪些结果文件。在这里我们就需要编写结果相关的xml文件，用来告诉系统，本task会产生哪些结果信息。

####  **三. 实例详细解析**	

<div style="text-align:center"> ** 实例一、Cap3的封装--简单版封装</div>**
**1.添加task与task参数配置**
1.1. docker镜像管理，在系统中点击分析平台-->docker镜像管理-->添加
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>

　　在弹出框中填写名称，版本和创建日期。一个镜像可以给多个task使用。创建好镜像后，还需要将镜像上传到中央服务器中。
　　由于镜像biodenovo中已经安装了Cap3的cmd命令，因此这里我们可以不创建新的镜像。  

1.2. taskmodule管理，在系统中点击分析平台taskModule管理新增，创建Cap3的task。
<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>
主要填写四个内容：
　a) taskType--task的名字，这里我们填写Cap3。
　b) enable--是否启用task。0表示当前task不可选，1表示可选。这里我们填写1。
　c) tags--task的标签，在task选择页面的查询框内输入tag的内容，可以快速搜索到相应的task。这里我们可以留空，也可以填写cluster。
　d) dockerImage—选择运行该task所需要的docker镜像。


1.3.	taskModuleParam管理，在系统中点击分析平台-->taskModuleParam管理-->创建task的输入参数。
<div style="text-align:center"><img data-src="3.png" width="600px" ></img>
</div>
　　对于一个task来说需要设定一系列参数。主要有输入文件（InputFile），输入文件前缀（Prefix），输出文件前缀（OutPrefix，这个一般和输入文件前缀是同一个），普通参数等。
　　输入文件设定：
<div style="text-align:center"><img data-src="4.png" width="600px" ></img>
</div>

　　**输入前缀和输出前缀设定。**名称为prefix，后端会通过 id=prefix来获取具体的信息。参数类型是Prefix、OutPrefix。一般我们会通过OutPrefix来装配输出文件的文件名。

　　以上两个参数配置了输入文件以及其对应的组名。
　　第一个配置了输入参数，为MULTIPLEPREFIX，表示可以输入多个文件；可输入文件类型为FASTA，表示输入的文件类型。对应的组名为prefix，表示和第二个名称为prefix的参数绑定在一起。
　　第二个配置了prefix，类型为Prefix、OutPrefix，表示这个参数即用于输入的前缀，也用于输出文件的名字。譬如输入文件为 Trinity.fasta，prefix为novelbio，则输出即为 novelbio.out。
　　NovelBrainTM的一个特色在于可以并行计算，也就是如果输入多个文件，可以将多个文件分散在不同的虚拟机中一起运行，从而加快计算速度。那么在对文件分组的过程中，系统一般是通过对参数类型为Prefix的参数进行切分，也就是相同的Prefix归为一组，放在一个container中。而InputFile则通过与Prefix挂钩的方式来告知系统具体切分的文件。也就是说我们可以把Prefix看成是分组。那么在实际生产中，如果有多个文件挂钩同一个Prefix，譬如:Tumor组有1.bam,2.bam两个文件，Normal组有3.bam一个文件，那么最后1.bam,2.bam会放入一个虚拟机中计算，3.bam会单独放入一个虚拟机中计算。**为了让系统能正确的切分文件，我们要把需要切分的InputFile和Prefix的"是否根据本字段进行切分"设置为"true"，同时把InputFile的对应组名设置为Prefix的名称。**
　　这两个参数配置好后，在task选择文件部分就可以正确的选择文件了。如下图展示：

<div style="text-align:center"><img data-src="5.png" width="600px" ></img>
</div>

　　按照以上设置，上述Trinity1，Trinity2，Trinity3就会在三个不同的虚拟机中运行了。
　　**普通参数设定。**Cap3有一些特定的参数，如gapLength这种，我们还需要每个都设定。

<div style="text-align:center"><img data-src="6.png" width="600px" ></img>
</div>

　　注意每个都要填写TaskType为Cap3。名称gapLength就是后端会通过id=gapLength来获取具体的参数。显示名称是选择框的名字。是否根据本字段进行切分 为false，因为不需要按照这个切分。注意参数类型为Normal、PageParam。只有当设定为PageParam时，前端才会显示出这个参数。**而由于Normal为默认参数，所以我们在这里也可以只设置为PageParam。**
　　普通参数配置好后，在task选择页面就可以选择相应的参数了。示例如下：
<div style="text-align:center"><img data-src="7.png" width="300px" ></img>
</div>

**2.配置Cap3的运行xml文件**
　　前面是配置了Cap3的task，使用镜像以及输入参数，现在需要把这些参数组织起来，方便后端进行调用。
　　一个task由三个阶段组成，分别是Prepare、Run、Summary。
　　**Prepare：**task运行时的前处理工作，不会并行计算。在hisat2的案例中可以用于建索引，因为无论运行多少样本，索引都只需要运行一次，所以可以把建索引的工作放在Prepare中。
　　**Run：**task正式运行。如果输入多个样本，并且设定好并行计算，则本步会将样本放在不同的服务器上运行，以提高计算速度。在hisat2的案例中可以用于具体样本的mapping，这样多个样本可以在多台不同的服务器上运行。
　　**Summary：**task结束后的收尾工作。如运行结束后汇总mapping率等工作。
　　每个阶段有一个对应的文件夹，根据XML的功能将不同的XML放在不同的阶段中，即不同的文件夹中。如果不需要某个阶段，可以不建立该文件夹。
　　每个阶段中都可以顺序调用多个cmd/groovy命令，每个cmd/groovy命令用xml的形式配置，也就是说每个stage中可以放置多个xml文件。以聚类软件Cap3举例，该软件仅需要一个阶段，也就是Run。因此我们仅需要创建一个Run文件夹。

**2.1 在创建任务文件夹: Cap3。注意这里Cap3必须与task名字相同。**
**2.2 在任务文件夹Cap3中创建阶段文件夹Run。**
　　Cap3/Run
　　Cmd分为Prepare、Run、Summary三个阶段，一般我们只需要配置Run阶段即可。
**2.3 在阶段文件夹Run中编写调用Cap3命令的xml文件**，xml文件命名为
　　Cap3/Run/runCap3.xml
　　这里xml的文件名可以随便起，只需要后缀名为xml即可。
在xml文件中填写以下内容：
```
<?xml version="1.0" encoding="UTF-8" ?> 
<root> 
	<name>Cap3 run script</name> 
	<description>This is Cap3 run script.</description> 
	<order>1</order> 
	<scriptType>cmd</scriptType> 
	<taskType>Cap3</taskType> 
	<stage>Run</stage> 
	<resource cpu="3" mem="10000" /> 
	<templet> 
		<script param="cap3"/> 
		<script id="inputFile" type="Input" />
		<script id="gapLength" param="-f" />
		<script id="overlapLength" param="-o"/> 
		<script id="overlapIdentity" param="-p" /> 
		<script id="readSupNum" param="-z"/> 
		<script id="prefix" type="Output" param=">" value ="%s.out" />
	</templet> 
	<skipResults> 
		<resultFile id="prefix" value="%s.out"/> 
	</skipResults> 
</root>
```
　　最后，将任务文件夹“Cap3”放在服务器 task/scriptmodule 路径下即可。
　　此时，Cap3加壳的代码部分已经完成。

**2.4 对xml文件的详细说明：**
　　NovelBrainTM系统通过Xml文件来设定cmd命令所需要的参数。我们接下来对Cap3的xml文件来进行说明。一个Xml一般分为三大块，分别是：
　　**头部**--cmd命令总体配置
　　**中部**--具体参数设定
　　**尾部**--task跳过设定
<div style="text-align:center"><img data-src="8.png" width="680px" ></img>
</div>

　　Xml的说明和根节点，第一行是Xml的版本和编码等说明，所有xml都一样。具体xml的正文会包含在`<root>…</root>`中
```
<?xml version="1.0" encoding="UTF-8" ?> 
<root>
…
</root>
```
**头部**
```
<name>Cap3 run script</name> 
	<description>This is Cap3 run script.</description> 
	<order>1</order> 
	<scriptType>cmd</scriptType> 
	<taskType>Cap3</taskType> 
	<stage>Run</stage> 
	<resource cpu="3" mem="10000" /> 
```
　　头部主要是对task的总体描述。其中`name`、`description`、`taskType`、`stage`都无关紧要。不会对程序有影响。`taskType`、`stage`这两个参数在未来会被废弃。
　　`order`：表示第几个运行的xml。一个stage中可以放多个xml，用这个来排序。由于cap3仅有一个xml，所以这里就设置为1即可。
　　`scriptType`：XML可以调用第三方的cmd命令以及groovy命令，此处，表示该xml中调用的是cmd命令。cmd命令包括bwa、hisat2等普通cmd命令，也包括表用perl程序，python程序、java程序和Rscript。groovy命令是java的脚本，groovy脚本可以调用NovelBio公司的库函数和数据库。
　　`resource`：本cmd所需要的资源，这里表示需要3个cpu的core，10000MB内存。
**中部**
```
	<templet> 
		<script param="cap3"/> 
		<script id="inputFile" type="Input" />
		<script id="gapLength" param="-f" />
		<script id="overlapLength" param="-o"/> 
		<script id="overlapIdentity" param="-p" /> 
		<script id="readSupNum" param="-z"/> 
		<script id="prefix" type="Output" param=">" value ="%s.out" />
	</templet> 
```
　　中部是cmd命令的配置，在`<templet></templet>`中放置一系列的`<script … />`，每个`<script … />`即为一个命令片段。通过以上配置可以装配出cap3的实际命令。
在这里我们可以将本命令划分为以下几个片段：
　cap3 -- 命令名字
　Trinity.fa -- 输入文件
　-f 20 参数f
　-o 100 参数o
　-p 90 参数p
　-z 3 参数z
　> myresult.out 输出路径
代码详细解释：
　　每一个命令单元可以由一个<script />单元组成。如：
`<script param="cap3"/>`
　　输入的第一个参数cap3，如调用的软件名称。
`<script id="inputFile" type="Input" />`
　<span style="color:red"> 　type="Input" 这个参数是一个输入文件类型</span>
　　id="inputFile" 参数的具体值来自于前端的inputFile输入项
`<script id="gapLength" param="-f" />`
　　param="-f" 该参数的 key，即调用软件的参数
　　id="gapLength" 该参数具体的值来自于前端的gapLength输入项
`<script id="prefix" type="Output" param=">" value ="%s.out" />`
<span style="color:red"> 　type="Output" 这个参数是一个输出文件 </span>
　　param=">" 这是通过标准输出流输出的参数
　　id="prefix" 前端的prefix输入项的值，会用在这里作为输出文件的文件名一部分
		value ="%s.out" 会用prefxi替换 %s 作为输出结果。
		譬如前端设定prefix= myresult，则该段参数单元为 "> myresult.out"
　　<span style="color:red">以上代码片段会顺序组合，最后拼装成一个完整的命令。 </span>
　　如上述这段代码，拼装成的cap3的命令为：cap3 Trinity.fa -f 20 -o 100 -p 90 -z 3 > myresult.out。
**尾部**
```	
<skipResults> 
		<resultFile id="prefix" value="%s.out"/> 
	</skipResults>
```
　　单元skipResults表示如果在结果文件夹中发现已经存在了相关文件，则本cmd命令就不会执行，用来防止多次执行一个耗时很长的且已经成功运行的命令。`<skipResults>…</skipResults>`则中间可以存在多个`<resultFile …/>`片段，每个片段代表一个输出文件。只有当所有输出文件都存在时，才会跳过该cmd。
　 `<resultFile id="prefix" value="%s.out"/>`
　　id="prefix" 前端的prefix会用在这里作为输出文件的文件名一部分。
　　value ="%s.out" 会用prefxi替换 %s 作为输出结果。
　　譬如前端设定prefix=novelbio，则会检查输出文件"novelbio.out"是否存。由于以上xml中仅有一个`<resultFile …/>`片段，所以如果系统检查到"myresult.out"文件存在，即会跳过本cmd的执行。

<div style="text-align:center"> ** 实例二、hisat2的封装--简单版封装</div>**
**1.	添加task与task参数配置**
　　大部分的cmd封装中，**docker**镜像的添加和**taskModule**添加都大同小异，**taskModuleParam**大部分的参数也差不多。不过有部分参数比较特殊，如：hisat2要求输入双端测序的数据；可以调用系统内置的染色体文件；有boolean型参数是勾选框类型。因此我们重点看taskModuleParam中比较特别的设置。
　　**双端文件设定：**hisat2的配置有一个特点，即输入文件可以是双端测序的fastq文件也可以是单端测序的fastq文件。一般来说双端测序的Fastq文件会有两个，一个是left.fq，一个是right.fq。这两个文件两两配对，每一对的reads数也相同。所以我们在进行计算的时候都需要将左端fq和右端fq配对输入task进行分析。因此在参数设定中，我们也需要设定LeftInput和RightInput，并且把这两个文件关联起来，并需要与它们对应的Prefxi也要关联起来。
　　左端文件配置，注意选择文件类型为LEFT，关联字段名称right（right是右端文件配置的名称项），对应组名prefix--这个和Cap3类似。注意是否根据本字段进行切分设置为“true”。


　　右端文件配置，选择文件类型为RIGHT，关联字段名称left（left是左端文件配置的名称项），对应组名prefix。

　　分组信息设定，和Cap3的设置相同, 注意是否根据本字段进行切分设置为“true”。


　　最后展示拖拽界面如下所示：


　　**第三方文件的选择：**因为我们在实际hisat2分析过程中，有时候可能会使用数据库中不存在的染色体和gff文件，所以我们还需要添加选框让用户可以选自己的染色体文件和gff文件。
　　染色体文件输入配置，注意选择文件形式为SINGLE，意思一个task只能选一个染色体文件。是否根据本字段进行切分为false。

　　Gff文件输入配置，类似染色体文件输入配置。可输入文件类型选择GTF即可。

　　全部设定完毕后，拖拽页面现在变成这个样子，也就是我们最终的展示结果：

　　**单端输入文件的处理：**在实际项目中，如果输入的是单端测序而不是双端测序，那么只需要拖拽到左端，右端留空即可。如下图所示：

　　**数据库信息的调用：**NovelBrainTM内置了大量物种信息，我们可以调用NovelBrainTM数据库，通过数据库获取指定物种的染色体信息等，而不是费时费力的去上传相关的染色体文件。因此我们需要在taskModuleParam中配置物种下拉框，同时第二部分xml文件中也需要调用NovelBrainTM提供的groovy脚本。
　　为了能够调用NovelBrainTM的物种数据库，我们需要在taskModuleParam中添加以下几个参数：
　　**species:** 物种下拉框（必选），添加后在前端页面可以展示一个下拉框来选择NovelBrainTM数据库中包含的物种。
　　**speciesVersion: **版本下拉框（依赖species）。我们知道一个物种譬如human，会有多个版本的数据库，如hg18、hg19、GRCh38等，添加这个后，在前端页面可以展示一个下拉框来选择指定物种的某个版本。
　　**dbType:** gff数据库下拉框（依赖speciesVersion）。给定物种和版本后，不同的组织会对这个基因组进行不同的注释，从而提供不同的gff注释文件。如hg19的gff版本就有NCBI、UCSC、Ensembl等不同的版本。这个参数就是用来选择不同的gff文件。添加这个后，在前端页面可以展示一个下拉框来选择指定物种版本的某个gff文件。
　　注意：
　　1. 以上三个参数是依次依赖的，就是说dbType依赖speciesVersion的存在，speciesVersion依赖species的存在。
　　2. 我们并不需要把三个参数都列出来，还是要看需求。如果task仅需要染色体文件，不需要用到gff，或者gff文件我们不用让客户选择，走默认即可。那么我们就可以不用添加dbType参数。
　　以下是具体参数的配置：
　　species: 注意参数类型为PageParam，名称必须是species。显示名称可以随便起，这里是起名Species。顺序为1，表示参数第一个就显示species下拉框。



