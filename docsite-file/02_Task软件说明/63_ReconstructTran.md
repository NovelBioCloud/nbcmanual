# ReconstructTran
　　目前，主要有两类方法可以用于构建转录组：
　　(1) 有参（cufflinks，准确性较高，分为两种方法一种是read比对（Tophat2）基因组，一种是read 聚类，然后在聚类区域预测），
　　(2) StringTie是借组基因组指导的软件，同时又有从头组装的思想，StringTie输入文件不仅仅是tophat的bam比对文件，还可以输入super read比对的结果（利用MaSuRCA将read按照kmer切割然后两端延伸，组装成的super read， 简称SR）然后利用String+SR 来代表操作是利用了read 和super read 两种数据。
**功能：**
　　重构已知转录本和组装新的转录本。
**使用软件：**
　　StringTie：StringTie由约翰霍普金斯大学联合德州大学西南医学中心开发，能够组装转录本并预计表达水平。它应用网络流算法和可选的denovo组装，将复杂的数据集组装成转录本。StringTie能够拼接出更完整、更准确的基因，并且StringTie采用拼接和定量同步进行，相对于其他方法，其定量结果更加准确。软件官网：https://ccb.jhu.edu/software/stringtie/index.shtml?t=manual
　　Cufflinks：主要根据Tophat的比对结果，依托或不依托于参考基因组的GTF注释文件，计算出各基因的FPKM值，并给出trascripts.gtf注释结果（组装出转录组）。软件官网：http://cole-trapnell-lab.github.io/cufflinks/

**应用范围:**
　　RNA-Seq理论上能够捕获细胞中基因表达所产生的所有转录本。通常情况下，有基因组参考的方法非常适用于高质量参考基因组的物种，而从头组装的方法则没有限制，可以用于任何物种，不论这些物种是否拥有参考基因组。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是RnaSeqMap中的比对结果bam文件。
　**chrSeq：**需要分析物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中则不需要输入该文件。
　  **gtfFile：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。
　  **inputFile：**比对结果bam文件，要求该bam文件是排序后的bam文件。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详见官网说明：http://samtools.github.io/hts-specs/SAMv1.pdf

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　重构转录本后的注释文件，以gtf格式存储。
  
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**选择参考基因组物种。
　**物种版本：**参考基因组的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**软件名称：**选择使用软件StringTie或者Cufflinks
　**内存：**软件运行时设置使用内存数。
　**线程数：**软件运行时设置使用线程数。
　**minTranLength：**设置最小转录本长度，默认为200
　**minJunCoverage：**一个junction的最少junction reads数（即，junction coverage），该值可以是小数，因为一些reads可能会比对到n个位置，那么一条reads在此处的junction coverage就是1/n，默认值为1。
　**minTranCoverage：**预测转录本最少的reads支持数，如果预测的一条transcript的reads支持数小于该值，则不输出该transcript，默认值为2.5。
　**minAnchorLenForJun：**当spliced reads的一端比对上的碱基数小于该设置值时，则不考虑该处的junction，默认为: 10。
　**gapLength：**最小的locus gap分割值，当比对上reads的距离小于该设定值时，则进行合并，默认为: 50 (bp)。
　**转录本名称前缀：**输出的转录本名称前缀，默认为: STRG。
　**FractionOfBundle：**设置出现在given locus处muliple-location-mapped reads的最大的比率 默认为: 0.95。
　**useRefAnnoAssembly：**组装过程中是否使用参考注释文件 (in GTF or GFF3 format)来指导转录本重构，输出结果中将包含表达的参考转录本和一些组装的新转录本。
　**estimateRefTranAbundance：**是否只评估比对到参考注释文件中的转录本（要求设置“-G”参数，推荐使用“-B/-b”参数）。
　**reportGeneAbundance：**是否输出基因丰度结果文件。
　**reportBallgownTable：**是否输出用于Ballgown分析的输入文件（_ctab）。
　**是否获取表达值：**是否从stringtie结果中的gtf中，提取出基因表达量。
　**minTranLenInMerge：**用于stringtie merge模式，输入的最小转录本长度；默认为: 50。
　**minTranCovInMerge：**用于stringtie merge模式，输入的最小转录本覆盖度，默认为0。
　**minFPKMInMerge：**用于stringtie merge模式，输入的最小转录本的FPKM值，默认为: 0。
　**minTPMInMerge：**用于stringtie merge模式，输入的最小转录本的TPM值，默认为 0。
　**minIsoFraction：**最小isoform fraction 默认为: 0.01。
　**tranPrefixInMerge：**用于stringtie merge模式，merge后输出转录本名称前缀，默认为： MSTRG。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
　1) transcripts.stringtie.gtf：Stringtie结果文件，如：
<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
</div>
各列信息解释如下：
<div style="text-align:center"><img data-src="3.png" width="550px" ></img></div>
　详细解释请见官方文档：http://ccb.jhu.edu/software/stringtie/index.shtml?t=manual

2) transcripts.gtf：cufflinks结果文件，如：
<div style="text-align:center"><img data-src="4.png" width="600px" ></img></div>
　　各列信息同上StringTie解释。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**可变剪接：**有些基因的前体mRNA（pre-mRNA）通过不同的剪接方式（选择不同的剪接位点）产生不同的mRNA剪接异构体，这一过程称为可变剪接（或者选择性剪切）（Alternative Splicing）。可变剪接是调节基因表达和产生蛋白质组多样性的重要机制，是导致真核生物基因和蛋白质数量较大差异的重要原因。可变剪接在产生受体多样性、控制调节生长发育等方面起决定性作用。尤其表现在神经系统和免疫系统，这与该类系统的功能多样性和反应敏感性是密切相关的。许多遗传疾病都与剪接繁盛异常紧密相关。
　　**GTF：**GTF全称为gene transfer format，主要是用来对基因进行注释，GTF详细解释，请见官方文档： http://mblab.wustl.edu/GTF2.html

参考文献：
Zhou, X. et al. Transcriptome analysis of alternative splicing events regulated by SRSF10 reveals position-dependent splicing modulation. Nucleic Acids Res(2014).

