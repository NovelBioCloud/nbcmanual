# ReconstructTran
　　转录本重构就是用测序的数据组装出转录本序列。
　　目前，常见的两种组装方式：
　　（1）de-novo构建:de-novo组装是指在不依赖参考基因组的情况下，将有overlap的reads连接成一个更长的序列，经过不断的延伸，拼成一个个的contig及scaffold。常用工具包括velvet，trans-abyss，Trinity等。 
　　（2）有参考基因组重构:参考基因组重构，是指先将read贴回到基因组上，然后在基因组通过reads覆盖度，junction位点的信息等得到转录本，常用工具包括scripture、Cufflinks。
该模块中使用的软件---StringTie,则是借助基因组序列指导转录组序列组装，同时又结合使用denovo组装方法的软件。
**功能：**
　　重构已知转录本和组装新的转录本。
**使用软件：**
　　StringTie：StringTie由约翰霍普金斯大学联合德州大学西南医学中心开发，能够组装转录本并计算各转录本的表达水平。它应用最优化算法中研究比较多的网络流算法（网络流算法简介请见 https://www.cnblogs.com/ZJUT-jiangnan/p/3632525.html ），并结合denovo组装方法，将杂乱的测序reads组装成转录本。相对于其他方法，StringTie能够拼接出更完整、更准确的基因，并且StringTie采用拼接和定量同步进行，其定量结果也更加准确。
  **软件官网**：https://ccb.jhu.edu/software/stringtie/index.shtml?t=manual
　　Cufflinks：主要根据Tophat的比对结果，依托或不依托于参考基因组的GTF注释文件，计算出各基因的FPKM值，并给出trascripts.gtf注释结果,即组装的转录组结果文件。
  **软件官网**：http://cole-trapnell-lab.github.io/cufflinks/

**应用范围:**
　　RNA-Seq理论上能够捕获基因表达所产生的所有转录本。通常情况下，有基因组参考的方法非常适用于高质量参考基因组的物种，而从头组装的方法则没有限制，可以用于任何物种，不论这些物种是否拥有参考基因组。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是RnaSeqMap中的比对结果bam文件。
　**chrSeq：**需要分析物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中则不需要输入该文件。
　  **gtfFile：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。
　  **inputFile：**比对结果bam文件，要求该bam文件是排序后的bam文件。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　重构转录本后的注释文件，以gtf格式存储。
  
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>物种版本：</label>参考基因组的版本。
<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
<label id='software'>软件名称：</label>选择使用软件，该选项有两个：StringTie或者Cufflinks。
<label id='memory'>内存：</label>软件运行时设置使用内存容量。
<label id='threadNum'>线程数：</label>软件运行时设置使用线程数。
<label id='minTranLength'>minTranLength：</label>设置输出的重构转录本的最小长度，默认为200bp。
<label id='minJunCoverage'>minJunCoverage：</label>一个junction的最少junction reads数（即junction coverage），该值可以是小数，因为一些reads可能会比对到n个位置，那么一条reads在此处的junction coverage就是1/n。默认值为1。
<label id='minTranCoverage'>minTranCoverage：</label>预测转录本最少的reads支持数，如果预测的一条transcript的reads支持数小于该值，则不输出该transcript。默认值为2.5。
<label id='minAnchorLenForJun'>minAnchorLenForJun：</label>当spliced reads的一端比对上的碱基数小于该设置值时，则不考虑该处的junction，默认为: 10。
<label id='gapLength'>gapLength：</label>在一个处理单元（processing bundle）中，当两条比对上基因组的reads在参考序列上的位置之间的距离小于该设定值时，则进行合并。默认值为50 bp。
<label id='tranPrefix'>转录本名称前缀：</label>输出的转录本名称前缀，默认为: STRG。
<label id='fractionOfBundle'>FractionOfBundle：</label>设置出现在给定位点处（given locus）的多处比对reads（muliple-location-mapped reads,即比对到基因组上多个位置的reads,此概念是相对unique mapping reads而言）所占的最大的比率，默认值为0.95。
<label id='useRefAnnoAssembly'>useRefAnnoAssembly：</label>组装过程中是否使用参考注释文件 (in GTF or GFF3 format)来指导转录本重构，输出结果中将包含发生表达的参考转录本和组装的新转录本。
<label id='estimateRefTranAbundance'>estimateRefTranAbundance：</label>是否只评估比对到参考注释文件中的转录本，若选择“是”的话，要求设置“-G”参数，推荐使用“-B/-b”参数。
<label id='reportGeneAbundance'>reportGeneAbundance：</label>是否输出基因丰度结果文件。
<label id='reportBallgownTable'>reportBallgownTable：</label>是否输出用于Ballgown软件分析的输入文件（\*_ctab）。
<label id='getGeneExpression'>是否获取表达值：</label>是否从stringtie结果中的gtf文件中提取出基因表达量。
<label id='minTranLenInMerge'>minTranLenInMerge：</label>用于Stringtie软件的Transcript merge模式，指输入的转录本的最小长度，默认为50bp。
<label id='minTranCovInMerge'>minTranCovInMerge：</label>用于Stringtie软件的Transcript merge模式，指输入的转录本的最低覆盖度，默认为0。
<label id='minFPKMInMerge'>minFPKMInMerge：</label>用于Stringtie软件的Transcript merge模式，指输入的转录本的最小FPKM值，默认为0。
<label id='minTPMInMerge'>minTPMInMerge：</label>用于Stringtie软件的Transcript merge模式，指输入的转录本的最小TPM值，默认为 0。
<label id='minIsoFraction'>minIsoFraction：</label>转录本的最小丰度，默认为0.01。
<label id='tranPrefixInMerge'>tranPrefixInMerge：</label>用于Stringtie软件的Transcript merge模式，指合并后输出转录本的名称前缀，默认为MSTRG。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
　1) \* .transcripts.stringtie.gtf：Stringtie结果文件，如：
<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
</div>
各列信息解释如下：
<div style="text-align:center"><img data-src="3.png" width="550px" ></img></div>
　详细解释请见官方文档：http://ccb.jhu.edu/software/stringtie/index.shtml?t=manual

2) transcripts.gtf：cufflinks结果文件，如：
<div style="text-align:center"><img data-src="4.png" width="600px" ></img></div>
　　各列信息同上StringTie解释。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　**可变剪接：**有些基因的前体mRNA（pre-mRNA）通过不同的剪接方式（选择不同的剪接位点）产生不同的mRNA剪接异构体，这一过程称为可变剪接（或者选择性剪切）（Alternative Splicing）。可变剪接是调节基因表达和产生蛋白质组多样性的重要机制，是导致真核生物基因和蛋白质数量较大差异的重要原因。可变剪接在产生受体多样性、控制调节生长发育等方面起决定性作用，尤其表现在神经系统和免疫系统，这与该类系统的功能多样性和反应敏感性是密切相关的。许多遗传疾病都与剪接发生异常紧密相关。
　　**GTF：**GTF全称为gene transfer format，主要是用来对基因进行注释，GTF详细解释，请见官方文档： http://mblab.wustl.edu/GTF2.html

**参考文献**：
Zhou, X. et al. Transcriptome analysis of alternative splicing events regulated by SRSF10 reveals position-dependent splicing modulation. Nucleic Acids Res(2014).

