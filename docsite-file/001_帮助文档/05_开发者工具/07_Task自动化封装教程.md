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

<div style="text-align:center"><h3>实例一、Cap3的封装--简单版封装<h3></div>

**1.添加task与task参数配置**

1.1. docker镜像管理，在系统中点击分析平台-->docker镜像管理-->添加
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>

　　在弹出框中填写名称，版本和创建日期。一个镜像可以给多个task使用。创建好镜像后，还需要将镜像上传到中央服务器中。

由于镜像biodenovo中已经安装了Cap3的cmd命令，因此这里我们可以不创建新的镜像。  

1.2. taskmodule管理，在系统中点击分析平台-->taskModule管理-->新增，创建Cap3的task。
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

**Prepare：** task运行时的前处理工作，不会并行计算。在hisat2的案例中可以用于建索引，因为无论运行多少样本，索引都只需要运行一次，所以可以把建索引的工作放在Prepare中。
　　**Run：**task正式运行。如果输入多个样本，并且设定好并行计算，则本步会将样本放在不同的服务器上运行，以提高计算速度。在hisat2的案例中可以用于具体样本的mapping，这样多个样本可以在多台不同的服务器上运行。
  
**Summary：** task结束后的收尾工作。如运行结束后汇总mapping率等工作。

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
	<span style="color:red">type="Input" 这个参数是一个输入文件类型</span>
 
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
　　单元skipResults表示如果在结果文件夹中发现已经存在了相关文件，则本cmd命令就不会执行，用来防止多次执行一个耗时很长的且已经成功运行的命令。`<skipResults>…</skipResults>`则中间可以存在多个`<resultFile …/>`片段，每个片段代表一个输出文件。只有**当所有输出文件都存在**时，才会跳过该cmd。
　 `<resultFile id="prefix" value="%s.out"/>`
　　id="prefix" 前端的prefix会用在这里作为输出文件的文件名一部分。
　　value ="%s.out" 会用prefxi替换 %s 作为输出结果。
　　譬如前端设定prefix=novelbio，则会检查输出文件"novelbio.out"是否存。由于以上xml中仅有一个`<resultFile …/>`片段，所以如果系统检查到"myresult.out"文件存在，即会跳过本cmd的执行。

<div style="text-align:center"><h3> ** 实例二、hisat2的封装--简单版封装**<h3></div>
**1.	添加task与task参数配置**
　　大部分的cmd封装中，**docker**镜像的添加和**taskModule**添加都大同小异，**taskModuleParam**大部分的参数也差不多。不过有部分参数比较特殊，如：hisat2要求输入双端测序的数据；可以调用系统内置的染色体文件；有boolean型参数是勾选框类型。因此我们重点看taskModuleParam中比较特别的设置。
　　**双端文件设定：**hisat2的配置有一个特点，即输入文件可以是双端测序的fastq文件也可以是单端测序的fastq文件。一般来说双端测序的Fastq文件会有两个，一个是left.fq，一个是right.fq。这两个文件两两配对，每一对的reads数也相同。所以我们在进行计算的时候都需要将左端fq和右端fq配对输入task进行分析。因此在参数设定中，我们也需要设定LeftInput和RightInput，并且把这两个文件关联起来，并需要与它们对应的Prefxi也要关联起来。
　　左端文件配置，注意选择文件类型为LEFT，关联字段名称right（right是右端文件配置的名称项），对应组名prefix--这个和Cap3类似。注意是否根据本字段进行切分设置为“true”。
<div style="text-align:center"><img data-src="9.png" width="600px" ></img>
</div>

　　右端文件配置，选择文件类型为RIGHT，关联字段名称left（left是左端文件配置的名称项），对应组名prefix。
<div style="text-align:center"><img data-src="10.png" width="500px" ></img>
</div>

　　分组信息设定，和Cap3的设置相同, 注意是否根据本字段进行切分设置为“true”。
<div style="text-align:center"><img data-src="11.png" width="500px" ></img>
</div>

　　最后展示拖拽界面如下所示：
<div style="text-align:center"><img data-src="12.png" width="500px" ></img>
</div>

　　**第三方文件的选择：**因为我们在实际hisat2分析过程中，有时候可能会使用数据库中不存在的染色体和gff文件，所以我们还需要添加选框让用户可以选自己的染色体文件和gff文件。
　　染色体文件输入配置，注意选择文件形式为SINGLE，意思一个task只能选一个染色体文件。是否根据本字段进行切分为false。
<div style="text-align:center"><img data-src="13.png" width="600px" ></img>
</div>
　　Gff文件输入配置，类似染色体文件输入配置。可输入文件类型选择GTF即可。
<div style="text-align:center"><img data-src="14.png" width="600px" ></img>
</div>
　　全部设定完毕后，拖拽页面现在变成这个样子，也就是我们最终的展示结果：
<div style="text-align:center"><img data-src="15.png" width="600px" ></img>
</div>
　　**单端输入文件的处理：**在实际项目中，如果输入的是单端测序而不是双端测序，那么只需要拖拽到左端，右端留空即可。如下图所示：
<div style="text-align:center"><img data-src="16.png" width="600px" ></img>
</div>
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

<div style="text-align:center"><img data-src="17.png" width="600px" ></img>
</div>

　　speciesVersion: 类似species的设置，注意顺序是2。
<div style="text-align:center"><img data-src="18.png" width="600px" ></img>
</div>
　　dbType: 类似species的设置，注意顺序是3。
<div style="text-align:center"><img data-src="19.png" width="600px" ></img>
</div>
　　最后展示如下：
<div style="text-align:center"><img data-src="20.png" width="400px" ></img>
</div>

　　那么我们接下来就可以在task的参数中选择物种版本和数据库了。在后端，也就是配置xml的时候，我们可以通过 id=species、id=speciesVersion、id=dbType来取到相关的值。然后这些值可以传给NovelBrainTM提供的groovy脚本，从而获得我们真正想要的信息，譬如物种所对应的染色体文件等。具体调用groovy脚本的方法我们会在后面详细介绍。
　　**选择框参数：** hisat2还有些特殊的参数配置，如dta。hisat2可以选择是否开启dta模式，开启dta模式需要在运行hisat2时添加 -dta参数。那么这个参数是一个boolean型参数，也就是true/false类型。所以我们在这里可以在前端添加一个选择框让用户来勾选是否开启dta模式。
<div style="text-align:center"><img data-src="21.png" width="400px" ></img>
</div>
展示如下：
<div style="text-align:left"><img data-src="22.png" width="120px" ></img>
</div>

其他参数类似Cap3，不再赘述。

**2.配置hisat2的运行xml文件**
hisat2在xml文件层面相对于Cap3比较大的区别有两个：
　　1).需要在mapping之前创建索引。
　　2).可以调用groovy脚本来获取数据库的染色体文件。
　　因此我们的思路即为获取数据库中的染色体文件，并对其建索引。
　　在Prepare中我们需要写两个xml文件，GetReferencePath.xml和index_make.xml。其中GetReferencePath.xml用来获取数据库中保存的染色体文件路径，index_make.xml用来给染色体建索引。
<div style="text-align:left"><img data-src="23.png" width="500px" ></img>

(1)．Prepare--GetReferencePath.xml
　　本步用来获取数据库中指定物种的染色体文件。我们在代码库中保存了一系列的groovy脚本，通过调用这些脚本就可以获得选定物种的染色体文件、Gff文件等信息。
```
<?xml version="1.0" encoding="UTF-8" ?>
<root>
	<name>species.groovy</name>
	<description>this is a script whi….n to get reference sequence file path.</description>  
  	<order>1</order>
  	<scriptType>groovy</scriptType>
  	<script>species.groovy</script>
  	<taskType>hisat2</taskType>
  	<stage>Prepare</stage>
  	<templet>
    		<script id="species" param="taxId"/>
    		<script id="speciesVersion" param="version"/>
    		<script id="dbType" param="gffDb"/>
		<script param="software" value="hisat2"/>
	</templet>
</root>
```
代码详细解析：调用groovy脚本的xml分为两部分。头部和中部，注意没有尾部。
头部最重要的是：
```
  <scriptType>groovy</scriptType>
  <script>species.groovy</script>
```
　　其中，`<scriptType>`设定为`groovy`，表示会调用系统的groovy脚本。`<script>`设定为`species.groovy`，表示具体调用的脚本名
　　**中部**是参数设置：
``` 
<templet>
    <script id="species" param="taxId"/>
    <script id="speciesVersion" param="version"/>
    <script id="dbType" param="gffDb"/>
<script param="software" value="hisat2"/>
  </templet>
```
　　以上是配置groovy脚本的输入参数，groovy脚本可以执行一系列命令
　　species.groovy的代码如下：
<div style="text-align:left"><img data-src="24.png" width="600px" ></img>
</div>

说明：
　　Groovy脚本的目的是调用NovelBrain内部的数据库获取一些相关文件，如染色体文件、gff文件、miRNA文件等。也可以调用NovelBrain的内部函数做一些工作。Groovy脚本需要输入一系列参数，同时会产生一系列结果参数，并将这些结果参数装入参数列表，并供给本stage的下一个xml文件使用。
　　头部${ }包围的为传入参数，如`taxId="${taxId}".toInteger();` 即为xml需要传入参数taxId。比如taskModuleParam中有参数species对应的taxId为9606，需要把9606这个值传给Groovy的taxId。则可以使用`<script id="species" param="taxId"/>`的方式传入。如果有一些特殊的标志性的参数在taskModuleParam中没有进行设置，例如，这种情况： 我们的物种数据库中已经保存了一个物种参考序列的多种不同软件的索引文件，如bwa、bowtie、hisat2等，那么，我们就需要根据不同的软件调用不同的索引文件。为了处理这种情况，我们可以通过`<script param="software" value="软件名称"/>` 的方式进行调用，比如本次就需要输入software为hisat2，即`<script param="software" value="hisat2"/>`的方式传入参数，告诉Groovy脚本，此时运行的是hisat2软件，需要调用hisat2相应的文件（即hisat2的索引文件）。
　　`//outkey@` 是一个标记，标记之后的参数会被临时性的加入到参数列表中，供本stage中其他的xml使用。譬如`//outkey@chrSeq`标记表示会在参数列表中加入参数名称为`chrSeq `的参数以及相应的值，那么本stage中的下一个xml就可以使用`<script id="chrSeq" />`来取到这个值。如果taskModuleParam中已经存在了`chrSeq`这个值，这时候默认Groovy脚本不会去覆盖taskModuleParam中的值。除非我们在头部设定`<isCoverParam>true</isCoverParam>`。
　　那么通过调用Groovy脚本，我们就可以在本stage接下来的xml中调取NovelBrainTM中的信息。
　　**注意：Groovy产生的结果参数（即使用`//outkey@` 标记的参数）是临时性的装入参数列表的，仅供当前Stage使用，如果下一个Stage需要使用参数，还需要在下一个Stage中再执行一次Groovy脚本。但是，如果是Groovy脚本对文件进行的操作，如修改文件内容，删除文件，移动文件等操作，那么这样的操作在其他Stage中也是有效的。**

(2).Prepare--index_make.xml
```
<?xml version="1.0" encoding="UTF-8" ?> 
<root>
<name>hisat index script</name>
<description>this is hisat index script.</description>
<order>2</order>
<scriptType>cmd</scriptType>
<taskType>hisat</taskType>
<stage>Prepare</stage>
<resource cpu="1" mem="10000" />
<templet>
    <script param="hisat2-build"/>
    <script id=" chrSeq" type="Input" />
    <script id=" chrSeq" type="Output" value="/index/%s"/>
</templet>
</root>
```
　　代码说明：
　　`<script id="chrSeq" type="Input" /> `
　　注意这里类型为<span style="color:red">Input</span>，调用了chrSeq，本参数既可通过选择species设定，也可以通过文件拖拽设定。如果两个存在，则以文件拖拽为准（因为默认<isCoverParam>true</isCoverParam>）。
`<script id=" chrSeq" type="Output" value="/index/%s"/>`
　　类型为<span style="color:red">Output </span>, value="/index/%s" 表示在结果路径中会创建一个名为index的文件夹并将建库后的结果文件放在该文件夹中，“%/s”是java format中的通配符。
　　<span style="color:red">注意：prepare中的xml命令是不能并行计算的。 </span>

(3).Run—hisatMapping.xml
```
<?xml version="1.0" encoding="UTF-8" ?>
<root>
  <name>hisat run script</name>
  <description>this is hisat run script.</description>
  <order>1</order>
  <scriptType>cmd</scriptType>
  <taskType>hisat</taskType>
  <stage>Run</stage>
  <resource cpu="3" mem="1000" />
  <templet>
  	<script param="hisat2"/>
		<script id="threadNum" param="-p"/>
		<script id="trim5" param="-5"/>
		<script id="trim3" param="-3"/>
		<script id="minIntronLen" param="--min-intronlen"/>
		<script id="maxIntronLen" param="--max-intronlen"/>
 	<script id=" chrSeq " type="OutInput" param="-x" value="/index/%s"/>
		<script id="leftInputData" type="Input" param="-1"/>
		<script id="rightInputData" type="Input" param="-2"/>
  	<script id="leftInputDataPrefix" type="Output" param="-S" value="%s.sam" isCopyToTmp="true"/>
  </templet>
  <skipResults>
  	<resultFile id="leftInputDataPrefix" value="%s.sam"/>
  </skipResults>
</root>
```
　　代码说明：
　　`<script id=" chrSeq " type="OutInput" param="-x" value="/index/%s"/>`
　　注意这里类型为”OutInput”，表示这里的输入文件是上一个阶段中的xml中生成的结果文件。
　　注意：`<script>`中id的值需要与taskModuleParam设置中的“名称”一列保持一致，param的值需要与所调用软件的参数名称一致。
　　<div style="text-align:center"><img data-src="25.png" width="650px" ></img>
</div>

&nbsp;
<div style="text-align:center"> <h3>**实例三、VarScan2的封装**<h3></div>
**1. 添加task与task参数配置**
　　Docker镜像的添加和taskModule的添加的方法可参考案例一Cap3的封装部分，taskModuleParam大部分的参数也与之前的两个案例差不多，该案例中比较特殊的参数设置为，该软件VarScan2中有两组样品比较的设置，如下图所示：
<div style="text-align:center"><img data-src="25_1.png" width="200px" ></img>
</div>
　　此时，就需要在taskModuleParam中配置参数类型的时候添加三个参数，分别为：”group1Array”，“group2Array”，“outFileArray”。
<div style="text-align:center"><img data-src="25_2.png" width="600px" ></img>
</div>
　　并且前两个参数的参数类型需要设置为“Compare”类型。
<div style="text-align:center"><img data-src="26.png" width="200px" ></img>
</div>

　　注意，这三个参数的“是否根据本字段进行切分”一列都需要设置为“true”，如下图所示：
<div style="text-align:center"><img data-src="27.png" width="600px" ></img>
</div>
<div style="text-align:center"><img data-src="28.png" width="600px" ></img>
</div>
<div style="text-align:center"><img data-src="29.png" width="600px" ></img>
</div>
**2. 配置VarScan2的运行xml文件**

　　VarScan2在使用之前不用进行类似于hisat2建库的数据处理，所以，VarScan2的封装仅创建一个Run阶段即可。
　　由于VarScan2运行结束以后，需要对结果文件，进行提取somatic snp和somatic indel的处理工作，所以，VarScan2的Run阶段中包含有3个xml文件。
　(1) Run-- varScan2.xml
　　这个xml用来调用VarScan2命令。
```
<?xml version="1.0" encoding="UTF-8" ?>
<root>
  <name>VarScan2</name>
  <description>VarScan2</description>
  <order>1</order>
  <scriptType>cmd</scriptType>
  <taskType>VarScan2</taskType>
  <stage>Run</stage>
  <isSupportHdfs>true</isSupportHdfs>
  <resource cpu="4" mem="20000"/>
  <templet>
  	<script param="java"/>
		<script param="-jar"/>
		<script param="/bin/varscan.jar"/>
		<script param="somatic"/>
		<script id="group2Array" value=""/>
		<script id="InputData" type="Input" isCopyToTmp="false"/>
 	<script id="group1Array" value=""/>
		<script id="InputData" type="Input" isCopyToTmp="false"/>
		<script id="minCoverage" param="--min-coverage"/>
		<script id="minCovNor" param="--min-coverage-normal"/>
		<script id="minCovTum" param="--min-coverage-tumor"/>
		<script id="minCovFreq" param="--min-var-freq"/>
		<script id="minFreForHom" param="--min-freq-for-hom"/>
		<script id="pValue" param="--p-value"/>	
		<script id="pValueSom" param="--somatic-p-value"/>
		<script value="1" param="--output-vcf"/>
		<script id="outFileArray" type="Output" value="%s_snp.vcf" param="--output-snp"/>
  	<script id="outFileArray" type="Output" value="%s_indel.vcf" param="--output-indel"/>
  </templet>
  <skipResults>
  	<resultFile id="outFileArray" value="%s_snp.vcf"/>
  </skipResults>
</root>

```

详细代码解析：
　　`<isSupportHdfs>true</isSupportHdfs>`
　　该xml中有一个新的标签即<isSupportHdfst ／>，这个标签表示是否支持hdfs路径，默认为false。一般绝大部分情况下，都是不支持hdfs的，除了我们自己写的java处理程序和我们修改后的VarScan2软件是支持hdfs以外，VarScan2之所以支持是因为我们修改了该软件的输出方式，使之可以支持hdfs，也就是说，绝大部分情况下该标签使用默认即可。
　　`<script id=" group2Array" value=""/>`
　　这里的id=“group2Array”是一个标记位，故这里value的值应设置为空；
　　`<script id="InputData" type="Input" isCopyToTmp="false"/>`
　　这一句与前一语句结合使用，表示，此处的输入文件是“InputData”中，标记为” group1Array”列表中的。 
　　`<script id=" group1Array " value=""/>`
　　同上，这里的id=“group1Array”是一个标记为，value值应设置为空；
　　`<script id="InputData" type="Input" isCopyToTmp="false"/>`
　　这两句结合使用，表示，此处的输入文件是“InputData”中，标记为“group2Array”列表中的。也就是说，使用”group1Array”与”group2Array”将所有的“InputData”（即输入文件）分成了两组。这四行语句表示，ＣＭＤ命令的此处有两个输入文件，第一个输入文件是” group2Array”列表中的，第二个文件是”group1Array”列表中的。
　　另外，xml中的”outFileArray”可以理解为一个比较组(compare)的前缀，在该案例中“outFileArray”的参数类型设置为“OutPrefix”，即做为比较组结果文件的前缀。
　　其他的参数与案例一和案例二中的参数设置方法相同，此处不再赘述。

<div style="text-align:center"><h3> ** 实例四、Trinity的封装---复杂版** <h3></div>
**1.	添加task与task参数配置**
　　Trinity的cmd封装过程中的docker镜像的添加和taskModule添加都类似于上述实例，其中taskModuleParam中特殊的部分为下拉框的设置；另外一个是xml中的过滤器的使用方法。
　　首先，介绍taskModuleParam中下拉框的设置方法。
　　如要设置如下图所示的下拉框
<div style="text-align:left"><img data-src="30.png" width="150px" ></img>
</div>
具体实现方法为：
　a．	在“管理中心”中选择“数据字典”
<div style="text-align:left"><img data-src="31.png" width="150px" ></img>
</div>

　b．	进入数据字典页面，如果数据字典中已经存在我们需要使用的项目内容，则可以省略此添加的步骤，直接选择使用即可，如数据字典中不存在，则需要在数据字典中添加新的项目内容。添加的步骤为：
　　(i) 选择“新增”，页面会在列表的第一行新添加一行，分别填写“编码”和“显示名称”这两列内容。“编码”相当于是字典项的参数，使用的时候通过“编码”获取字典项的具体内容； “显示名称”，目前的仅作为一个备注说明（或者中文解释）的功能，便于理解其代表的意义，此项内容可以为空，但是不建议为空。填写完毕后，点击“保存”。
<div style="text-align:center"><img data-src="32.png" width="500px" ></img>
</div>

　　(ii) 设置参数下拉选项：选中刚才新增的数据字典条目，如“SS_lib_type”， 在右侧会出现“数据字典项对应的值”的页面,点击“新增”，会在列表的第一列添加一个空行，依次填写填写“编码”---相当于下拉列表中值的参数；“显示名称”---下拉框中的参数选项，也就是说，“编码”填写后台参数名称，而，“显示名称”为前台显示参数名称，“顺序”为下拉框选项中参数显示的顺序，点击“保存”即可。
<div style="text-align:center"><img data-src="33.png" width="500px" ></img></div>

c. 	在taskModuleParam页面中，设置下拉框参数（如，“SS_lib_type”）的“控件类型”为“nbcCombobox”,然后将“datadict_getlsDataValues/编码”填入“请求值的URL”一列中，如上面步骤中添加的数据字典项的“编码”为“SS_lib_type””，所以此处完整的URL值为“datadict_getlsDataValues/SS_lib_type”，如下图所示：
<div style="text-align:center"><img data-src="34.png" width="550px" ></img>
</div>

　　Trinity的其他参数设置的方法类似于前面的案例，此处不再赘述。
**2.	配置Trinity的运行xml文件**

　　Trinity的封装在xml文件层面相对于之前的案例最大的区别在于xml中复杂属性<filters>[<filter>]过滤器的使用。
　　使用<filters>[filter]过滤器是用来指定本xml是否需要执行。
　　由于在Trinity运行前不需要对数据进行其他处理，所以，Trinity的封装仅创建一个Run阶段即可。
　　Run文件夹中有两个xml文件，分别为runTrinityPE.xml和runTrinityPE.xml。
<div style="text-align:center"><img data-src="35.png" width="550px" ></img>
</div>

(1).Run--runTrinityPE.xml
　　本步用来处理输入的文件类型是PE reads的fq数据。
```
<?xml version="1.0" encoding="UTF-8" ?> 
<root> 
	<name>Trinity run script</name> 
	<description>This is just a test run script.</description> 
	<order>1</order> 
	<scriptType>cmd</scriptType> 
	<taskType>Trinity</taskType> 
	<stage>Run</stage> 
	<resource cpu="@id(CPU)" mem="@id(max_memory)*1200" /> 
	<filters>
		<filter id="right" type="isEmpty" value="false" />
	</filters>
	<templet> 
		<script param="Trinity"/> 
		<script id="left" param="--left" type="Input" sepValue="," isCopyToTmp="true"/> 
		<script id="right" param="--right" type="Input" sepValue="," isCopyToTmp="true"/>
		<script id="prefix" type="Output" param="--output" value ="%s.trinity"/>
		<script id="seqType" param="--seqType"/> 
		<script id="max_memory" param="--max_memory" value="%sG"/> 
		<script id="SS_lib_type" param="--SS_lib_type"/> 
		<script id="CPU" param="--CPU"/> 
		<script id="min_contig_length" param="--min_contig_length"/> 
		<script param="--full_cleanup"/> 
	</templet> 
	<skipResults> 
		<resultFile id="prefix" value="%s.fasta"/> 
	</skipResults> 
</root>
```
代码详细解析：
	`<resource cpu="@id(CPU)" mem="@id(max_memory)*1200" /> `
　　运行该xml时，docker 镜像分配的cpu个数以及内存大小，内存单位为MB，这里可以使用`@id(***)`来指定获取某个param的值，如`@id(CPU)`，表示获取CPU的值，另外此处也可以写入一些计算公式，如`@id(max_memory)*1200`，表示获取参数max_memory的值后再乘以1200后的值赋值给mem。
```
    <filters>
		<filter id="right" type="isEmpty" value="false" />
	</filters>
```
　　当参数“right”的值为空的时候，根据value的值为true或者false来判断是否执行该xml，如value="false"，表示不执行该xml，即，当没有右端输入文件的时候，不执行该xml。如下图所示，当数据的FASTQ文件仅有左端文件的时候，不执行该xml文件，也就是说，当有右端输入文件的时候，执行该xml文件，即该xml处理输入文件是双端fq的数据。输入文件如下图所示：

<div style="text-align:center"><img data-src="36.png" width="550px" ></img>
</div>
(2) Run--runTrinitySE.xml
```
<?xml version="1.0" encoding="UTF-8" ?> 
<root> 
	<name>Trinity run script</name> 
	<description>This is just a test run script.</description> 
	<order>1</order> 
	<scriptType>cmd</scriptType> 
	<taskType>Trinity</taskType> 
	<stage>Run</stage> 
	<resource cpu="@id(CPU)" mem="@id(max_memory)*1200" /> 
	<filters>
		<filter id="right" type="isEmpty" value="true" />
	</filters>
	<templet> 
		<script param="Trinity"/> 
		<script id="left" param="--single" type="Input" sepValue="," isCopyToTmp="true"/> 
		<script id="prefix" type="Output" param="--output" value ="%s.trinity"/>
		<script id="seqType" param="--seqType"/> 
		<script id="max_memory" param="--max_memory" value="%sG"/> 
		<script id="SS_lib_type" param="--SS_lib_type"/> 
		<script id="CPU" param="--CPU"/> 
		<script id="min_contig_length" param="--min_contig_length"/> 
		<script param="--full_cleanup"/> 
	</templet> 
	<skipResults> 
	<resultFile id="prefix" value="%s.fasta"/> 
	</skipResults> 
</root>
```
代码详细解析：

```
<filters>
	<filter id="right" type="isEmpty" value="true" />
</filters>
```
　　该语句表示，当参数right的值为空的时候，执行该xml。也就是说，当右端没有输入文件的时候，执行该xml文件。也就是说，当仅有左端文件，右端文件没有输入的时候，执行该xml文件，输入文件如下图所示：
  
<main style="text-align:center"><img data-src="1.png" width="500px" style='margin:auto' /></main>

**注意事项：**
　　1.param=""字段中不能出现空格。
　　2.跳过机制如果写入多行，代表同时存在文件才跳过，目前不支持“或”条件。
　　3.id="prefix"后的value最多只能出现一次通配符%s，出现多个会报错，所以无法出现使用“%s/%s.txt”这种代码使带prefix名字的结果文件生成在以prefix命名的文件夹中。
　　4.在输入文件是最好添加isCopyToTmp="true"，把文件复制到tmp下再读入，防止出现读写冲突时服务器卡住的情况。
　　5.输出后续使用的文件字段直接用Output，不需要使用OutInput，需要添加。isCopyToTmp="true"，生成tmp文件，全部跑完后再复制出来，防止直接生成的结果文件因为报错或中断导致不完整，从而跳过整个步骤。
　　6.compare中的group1Array与group2Array在taskModuleParam中“顺序”一列的值需要设置为相同的数值，否则会报错，outFileArray的类型不是compare，需要设置为outprefix。
　　7.grep输入文件要求为标准流输入，及在输入文件的param中设置为"<"，而且需要用html的转义字符进行描述。
　　8.param中不要出现单引号，双引号。





