# CNVkit
　　拷贝数变异（Copy number variation，CNV）是由基因组发生重排而导致的，一般指长度为1kb以上的基因组大片段拷贝数的增加或减少，主要表现为亚显微水平的缺失或重复。CNV也是近来基因组学的研究热点，并且异常的DNA拷贝数变化（CNV）是许多人类疾病（如癌症、遗传性疾病、心血管疾病）的一种重要分子机制。作为疾病的一项生物标志，染色体水平的缺失、扩增等变化已成为许多疾病研究的热点。
　　**功能：**基于高通量测序技术的拷贝数变异检测。
　　**使用软件：**CNVkit，应用一个Python库和命令行软件工具包来推断基因拷贝数变异。它是一个基于基因组测序数据分析鉴定并展示拷贝数变异的有效手段。它也可以一定程度上分析外显子捕获测序，或者芯片靶向捕获测序的测序结果，而基于全基因组测序，它有更好的准确性，并且能够以全基因组作为范围寻找CNV。
　　软件官网：http://cnvkit.readthedocs.io/en/stable/index.html

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是Samtools进行去除Duplicate序列后的bam文件。
　　**InputBam (BAM)：**Samtools进行去除Duplicate序列后的bam文件。BAM就是SAM的二进制文件（B取自于binary）。一般情况下比对软件（如：bowtie/bowtie2 BWA）的结果文件都是Bam格式文件。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　　**TargetBed (BED)：**指定capture region的Bed 文件。如果需要在对指定区域进行变异检测，则使用该输入文件来指定区域范围，如果该参数无输入文件，则表示对全基因组进行变异检测。BED 文件格式详细信息请见说明文档：http://genome.ucsc.edu/FAQ/FAQformat.html#format1

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　拷贝数变异结果文件，结果都以bed文件格式存储。


***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**参考序列物种
　**版本：**物种的版本
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　**BedSpelit：**最小gap的碱基数，默认为5000。
　**Thread：**运行时，使用线程数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1) .antitargetcoverage.cnn/*.targetcoverage.cnn：
<div style="text-align:center"><img data-src="1.png" width="450px" ></img></div>
　chromosome:染色体名称。
　start:起始位置。
　end:终止位置。
　gene:Gene名称。
　depth:平均覆盖度深度。
　log2:平均覆盖度深度Log2值。
2) reference.cnn：Copy number refence profile，其中含有“chromosome”、“start”、“end”、“gene”、“log2”、“depth”信息以外，还有给定序列区域的GC含量、给定序列区域的RepeatMsker-masked比例和其他描述信息
3) .cnr：Bin-level log2 ratios 
4) .cns：Segmented log2 ratios
5) Genome.antitarget.bed/Genome.target.bed：bed文件格式，各列信息说明同，第一个文件格式说明，基因组位置从0开始计算。
　　详情请见官方：http://cnvkit.readthedocs.io/en/stable/fileformats.html

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**CNV：**拷贝数变异(Copy number variation, CNV)是由基因组发生重排而导致的, 一般指长度为1 kb 以上的基因组大片段的拷贝数增加或者减少, 主要表现为亚显微水平的缺失和重复。CNV 是基因组结构变异(Structural variation, SV) 的重要组成部分。CNV位点的突变率远高于SNP(Single nucleotide polymorphism), 是人类疾病的重要致病因素之一。
**参考文献：**
　1.Talevich, E., Shain, A.H., Botton, T., & Bastian, B.C. (2014). CNVkit: Genome-wide copy number detection and visualization from targeted sequencing. PLOS Computational Biology12(4):e1004873

