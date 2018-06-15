# SPAdes
　　Pacific Biosciences第三代测序仪的出现，明显地提高了基因组测序的读长，促进了完整基因组的组装。只用PacBio的数据就能够产生高度准确且完整的组装结果。
**功能：**
	&nbsp;&nbsp;&nbsp;&nbsp;细菌基因组组装。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**SPAdes：**是美国加州大学圣地亚哥分校计算机科学家Pavel Pevzner领导的国际研究小组开发出的一种新算法，来对有机体单个细胞的基因组进行更加快速准确的测序。软件包含了前期对测序数据的错误纠正（Quake hammer）以及基于k-mer值的错配纠正（mismatch correction）。
**软件官网：**
http://spades.bioinf.spbau.ru/release3.1.1/manual.html#sec2.1
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;通常用于单细胞测序的细菌基因组组装，也可用于非单细胞测序数据。输入数据可以是Illumina、IonTorrent reads,或 PacBio、Sanger reads，也可以把一些 contigs 序列作为 long reads 进行输入。该软件可以同时接受多组 paired-end、mate-pairs 和 unpaired reads 数据的输入。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是测序reads序列文件。	
**PE Left：**Paired-End测序数据的左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz。
**PE Right：**Paired-End测序数据的右端reads序列。单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz。
**Mate Left：**使用Mate-pair方法进行测序得到的序列数据的左端reads序列。
**Mate Right：**使用Mate-pair方法进行测序得到的序列数据的右端reads序列。
**Pacbio：**使用第三代测序系统-PacBio测序得到的序列文件，文件格式为fastq。
**Sanger File：**Sanger测序（一代测序）得到的序列文件。
**trust Contigs File：**如果需要组装的物种有可信的contigs序列，可以在此输入该contigs序列文件。要求该contigs文件没有组装错误，且只可以包含极少的错配或Indels等错误信息。注意该处不适用于近源物种的contigs序列，即此处是需要输入本物种的contigs序列。
**untrust Contigs File：**如果需要组装的物种有可信度不是很高的contigs序列，可以在此输入该contigs序列文件。该contigs序列文件中可以有一些组装的错误，但注意，该处不适用于近源物种的contigs序列，即此处是需要输入本物种的contigs序列。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;组装后序列文件（scaffolds.fasta），以fasta文件格式存储。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

<label id='threadNum'>threadNum：</label>使用线程数。
<label id='maxMemory'>maxMemory(G)：</label>最大内存数。
<label id='dataType'>数据类型：</label>选择输入数据的类型，其选项有：
&nbsp;&nbsp;&nbsp;&nbsp;MDA: single-cell数据
&nbsp;&nbsp;&nbsp;&nbsp;metagenomic: 宏基因组数据
&nbsp;&nbsp;&nbsp;&nbsp;RNA-Seq：RNA-Seq数据
&nbsp;&nbsp;&nbsp;&nbsp;Plasmid：质粒数据
&nbsp;&nbsp;&nbsp;&nbsp;Ion Torrent：IonTorrent 测序数据
<label id='kMer'>k-mer size：</label>组装过程中使用的k-mer大小，可使用逗号将多个不同的k-mer值进行分隔。注意，所有的k-mer值必须是奇数，并小于128，而且要按照升序排列，如：21,33,51,75，如果设置了-sc，那么默认值为21,33,55。对于多单元数据集，系统根据最大read长度自动选择K-mer值，对于Illumina组装的长reads，k-mer的设置详细说明可参照：http://spades.bioinf.spbau.ru/release3.11.1/manual.html#sec3.4。
**containerNumber：**运行过程中使用的container数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)	**\* final_contigs.fasta：**组装完成的contigs。
2)	**\*. scaffolds.fasta：**组装完成的scaffolds。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 详细说明**
**Sanger：**Sanger法是根据核苷酸从某一固定的点开始，随机在某一个特定的碱基处终止，并且在每个碱基后面进行荧光标记，产生以A、T、C、G结束的四组不同长度的一系列核苷酸，然后在尿素变性的PAGE胶上电泳进行检测，从而获得可见DNA碱基序列的一种方法。
**Paired-End：**Paired-end 方法是指在构建待测DNA文库时，在两端的接头上都加上测序引物结合位点，在第一轮测序完成后，去除第一轮测序的模板链，对测序模块引导互补链在原位置再生和扩增，以达到第二轮测序所用的模板量，进行第二轮互补链的合成测序。
**Mate-pair：**文库制备旨在生成一些短的DNA片段，这些片段包含基因组中较大跨度（2-10kb）片段两端的序列，更具体地说：首先将基因组DNA随机打断到特定大小（2-10kb范围可选）；然后经过末端修复，生物素标记和环化等试验步骤以后，再把环化后的DNA分子打断成400-600bp的片段，并通过带有链亲和霉素的磁珠把那些带有生物素标记的片段捕获；这些捕获的片段再经末端修饰和加上特定接头后建成mate-pair文库，然后上机测序。
**PacBio 测序：**全称PacBio RS II单分子实时测序（single molecule, real-time,SMRT）。测序反应是在其SMRT cell中进行的，每个SMRT cell中有150,000个ZMW（纳米级的零模波导孔zero-mode waveguides），每个ZMW都能够包含一个DNA聚合酶及一条DNA样品链。SMRT cell能够平行进行大约75,000个单分子测序反应。
***

**参考文献：**
1.	Bankevich A, Nurk S, Antipov D, et al. SPAdes: a new genome assembly algorithm and its applications to single-cell sequencing[J]. Journal of Computational Biology, 2012, 19(5): 455-477.
