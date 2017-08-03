# ReconstructTran
　　StringTie由约翰霍普金斯大学联合德州大学西南医学中心开发，能够组装转录本并预计表达水平。它应用网络流算法和可选的denovo组装，将复杂的数据集组装成转录本。StringTie能够拼接出更完整、更准确的基因，并且StringTie采用拼接和定量同步进行，相对于其他方法，其定量结果更加准确。
　　Cufflinks主要根据Tophat的比对结果，依托或不依托于参考基因组的GTF注释文件，计算出各基因的FPKM值，并给出trascripts.gtf注释结果（组装出转录组）。
　StringTie官网：https://ccb.jhu.edu/software/stringtie/index.shtml?t=manual
　Cufflinks官网：http://cole-trapnell-lab.github.io/cufflinks/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>

chrSeq：参考序列文件.fa
gtfFile(GTF)：参考序列.gtf文件
inputFILE(BAM)：需要分析的.bam文件
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**注释比对物种选择
　**物种版本：**基因组数据库版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　**软件名称：**选择使用软件StringTie或者Cufflinks
　**内存：**软件运行时设置使用内存数。
　**线程数：**软件运行时设置使用线程数。
　**minTranLength：**设置最小转录本长度，默认为200
　**minJunCoverage：**最少的junction reads数，默认值为1
　**minTranCoverage：**预测转录本最少的reads支持数，默认值为2.5
　**minAnchorLenForJun：**没有spliced reads到junctions，两边比对上的reads数总和，默认为: 10。
　**gapLength：**最小的locus gap 数.默认为: 50 (bp)。
转录本名称前缀：输出的转录本名称前缀，默认为: STRG。
　**FractionOfBundle：**最大的比率muliple-location-mapped reads 默认为: 0.95。
　**useRefAnnoAssembly：**组装过程中是否使用注释文件 (in GTF or GFF3 format)。
　**estimateRefTranAbundance：**是否只评估注释文件中有的转录本丰度。
　**reportGeneAbundance：**是否输出基因丰度。
　**reportBallgownTable：**是否输出用于Ballgown分析的输入文件。
　**是否获取表达值：**是否从stringtie结果中的gtf中，提取出基因表达量。
　**minTranLenInMerge：**用于stringtie merge模式，输入的最小转录本长度；默认为: 50。
　**minTranCovInMerge：**用于stringtie merge模式，输入的最小转录本覆盖度，默认为0。
　**minFPKMInMerge：**用于stringtie merge模式，输入的最小转录本的FPKM值，默认为: 0。
　**minTPMInMerge：**用于stringtie merge模式，输入的最小转录本的TPM值，默认为 0。
　**minIsoFraction：**最小isoform fraction 默认为: 0.01。
　**tranPrefixInMerge：**用于stringtie merge模式，merge后输出转录本名称前缀，默认为： MSTRG。
　**containerNumber：**运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
<div style="text-align:center">
<img data-src="1.png" width="600px" ></img>
</div>

　**seqname:** Denotes the chromosome, contig, or scaffold for this transcript. Here the assembled transcript is on chromosome X.
　**source:** The source of the GTF file. Since this example was produced by StringTie, this column simply shows 'StringTie'.
　**feature:** Feature type; e.g., exon, transcript, mRNA, 5'UTR).
　**start: **Start position of the feature (exon, transcript, etc), using a 1-based index.
　**end:** End position of the feature, using a 1-based index.
　**score: **A confidence score for the assembled transcript. Currently this field is not used, and StringTie reports a constant value of 1000 if the transcript has a connection to a read alignment bundle.
　**strand:** If the transcript resides on the forward strand, '+'. If the transcript resides on the reverse strand, '-'.
　**frame: **Frame or phase of CDS features. StringTie does not use this field and simply records a ".".
　**attributes:** A semicolon-separated list of tag-value pairs, providing additional information about each feature
