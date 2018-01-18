# RemoveChimera
　　嵌合体序列是PCR扩增时，两条不同的序列产生杂交、扩增而形成的序列。16S测序数据在数据过滤以后，需要进行去除嵌合体序列的处理。嵌合体形成主要有两个方面的原因：1. 菌株分离不纯或者有污染，包含其它混杂序列；2. PCR过程有问题或者测序过程有问题等。
　**功能：**
　		检测并去除输入数据中的嵌合体序列。
  **使用软件：**
　　**QIIME2：**QIIME （Quantitative Insights Into Microbial Ecology）是一个专门针对于微生物群落的分析流程，主要用Python编写，也整合了很多其它的工具包，可以进行OTU分析和多样性分析等。拥有处理16s rRNA所需要的软件并呈现相应的处理结果。
	**软件官网：**http://qiime.org/

 **应用范围**
依据参考数据库去除嵌合体序列。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　该Task的输入数据是FastQC之后的结果文件。
　**InputFq：**输入过滤后的FASTQ文件。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件** 
　去除嵌合体之后的序列文件，以fasta文件格式存储。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**containerNumber:**运行时使用容器（Container）数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
**Final_Fasta：**每个样本去除嵌合体序列之后的结果fasta格式文件，其中的“All.fasta”是将所有输入样品的fasta结果合并成一个fasta文件。
<div style="text-align:center"><img data-src="1.png" width="800px"  ></img></div>
**详细解释**
1）**16S**
通常所说的16S是指16S rDNA（或16S rRNA），16S rRNA 基因是编码原核生物核糖体小亚基的基因，长度约1542bp，包括9个可变区和10个保守区，保守区序列反映了物种间的亲缘关系，而可变区序列则能反映物种间的差异。因16S rDNA分子大小适中，突变率小，故成为细菌系统发育和分类鉴定最常用的标签。
2）**16S测序**
是指选择16S rDNA某个或某几个变异区域，选择通用引物对环境样本（肠道、土壤、水体等）微生物进行PCR扩增，然后对PCR产物进行高通量测序，并将得到的测序数据与已有的16S rDNA数据库进行比对分析，从而对环境群落多样性进行研究，核心是物种分析，包括微生物的种类，不同种类间的相对丰度，不同分组间的物种差异以及系统进化等。
**参考文献：**
1.Caporaso, J. Gregory, Justin Kuczynski, Jesse Stombaugh, Kyle Bittinger, Frederic D. Bushman, Elizabeth K. Costello, Noah Fierer et al. “QIIME allows analysis of high-throughput community sequencing data.” Nature methods 7, no. 5 (2010): 335-336.
2.Schloss, Patrick D., Sarah L. Westcott, Thomas Ryabin, Justine R. Hall, Martin Hartmann, Emily B. Hollister, Ryan A. Lesniewski et al. “Introducing mothur: open-source, platform-independent, community-supported software for describing and comparing microbial communities.” Applied and environmental microbiology 75, no. 23 (2009): 7537-7541.
