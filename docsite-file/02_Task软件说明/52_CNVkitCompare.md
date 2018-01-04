# CNVkitCompare
　　拷贝数变异（Copy number variation，CNV）是由基因组发生重排而导致的，一般指长度为1kb以上的基因组大片段拷贝数的增加或减少，主要表现为亚显微水平的缺失或重复。CNV是近年来基因组学的研究热点，是许多人类疾病（如癌症、遗传性疾病、心血管疾病等）发生发展的重要分子机制之一。作为疾病的一项生物标志，染色体水平的缺失、扩增等变化已成为许多疾病研究的热点。
**功能：**
　　基于高通量测序技术的拷贝数变异检测，对不同样本的CNV差异进行比较。
**使用软件：**
　　CNVkit: 应用一个Python库和命令行软件工具包来推断基因拷贝数变异。它是一个基于基因组测序数据分析鉴定并展示拷贝数变异的有效手段。它也可以一定程度上分析外显子捕获测序，或者芯片靶向捕获测序的测序结果，而基于全基因组测序，它有更好的准确性，并且能够以全基因组作为范围寻找CNV。

　　**软件官网**：http://cnvkit.readthedocs.io/en/stable/index.html
**应用范围：**
　　检测拷贝数变异，应用于“normal”VS “tumor”的样本，比较两组样本的CNV差异。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是使用Samtools软件去除重复序列后的bam文件。
　　**InputBam：**InputBam：使用Samtools软件去除重复序列后的bam文件。BAM就是SAM的二进制文件（B取自于binary）。一般情况下比对软件（如：bowtie/bowtie2 BWA）的结果文件都是Bam格式文件。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：  http://samtools.github.io/hts-specs/SAMv1.pdf

　　**TargetBed：**指定基因组区域或者基因组捕获区域（capture region）的Bed 文件。
 用途：如果需要在对指定区域进行变异检测，则使用该输入文件来指定区域范围，如果该参数无输入文件，则表示对全基因组进行变异检测。
 格式：BED 文件格式详细信息请见说明文档：     http://genome.ucsc.edu/FAQ/FAQformat.html#format1   
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　拷贝数变异结果文件，结果都以bed文件格式存储。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**参考序列物种。
　**版本：**物种的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　**BedSpelit：**可获取（捕获）序列区域之间的最小gap长度，如：对于外显子捕获测序来说，指的是两个外显子之间的最小距离，默认为5000。
　**Thread：**运行时使用线程数。
　**文件对比：**增加对比组，group1Array、group2Array分别为两个对比组，outFileArray为输出文件名。group1Array为“tumor”样本，group2Array为“normal”样本，可以在如下参数处修改组名：
　　　　　group1Array：选择对比组1，选择“tumor”样本；
　　　　　group2Array：选择对比组2，选择“normal”样本；
　　　　　outFileArray：输出文件名称前缀。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　(1).antitargetcoverage.cnn/*.targetcoverage.cnn：antitarget/target的bin 水平（即，指定长度区域）的覆盖度，结果以bed文件格式存储，bed格式文件说明请见官方文档：，如：
<div style="text-align:center"><img data-src="1.png" width="450px"  ></img>
</div>
各列解释为：
　　　chromosome：染色体名称
　　　start：起始位置
　　　end：终止位置
　　　gene：Gene名称
　　　depth：平均覆盖度深度
　　　log2：平均覆盖度深度Log2值

　(2).reference.cnn：参考基因组序列统计信息其中除了含有“chromosome”、“start”、“end”、“gene”、“log2”、“depth”信息以外，还有给定序列区域的GC含量、给定序列区域的使用RepeatMsker软件标识出的重复区域的比例和其他描述信息。
　(3).cnr：Bin-level log2 ratios,即指定长度区域覆盖度的log2值比率信息。
　(4).cns：Segmented log2 ratios,即片段覆盖度的log2值比率信息。

　各个结果文件详情请见官方文档：
　　http://cnvkit.readthedocs.io/en/stable/fileformats.html

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　CNV：拷贝数变异(Copy number variation, CNV)是由基因组发生重排而导致的, 一般指长度为1 kb 以上的基因组大片段的拷贝数增加或者减少, 主要表现为亚显微水平的缺失和重复。CNV 是基因组结构变异(Structural variation, SV) 的重要组成部分。CNV位点的突变率远高于SNP(Single nucleotide polymorphism), 是人类疾病的重要致病因素之一。
**参考文献：**
　　Talevich, E., Shain, A.H., Botton, T., & Bastian, B.C. (2014). CNVkit: Genome-wide copy number detection and visualization from targeted sequencing. PLOS Computational Biology12(4):e1004873


