# CASH

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;随着二代测序读长和覆盖度的增加，可变剪接（Alternative Splicing，AS）的识别率和准确度也在不断提升，越来越多的疾病以及生物学现象被发现是由转录本剪接形式的不同所造成。目前可变剪接已经成为转录组测序研究的一个重点。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;检测可变剪接和差异可变剪接。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**CASH：**CASH（Comprehensive AS Hunting）是由烈冰生物信息研发团队自主研发的差异可变剪接软件。CASH于2014年发表在《Nucleic Acids Reseach》杂志上，现已升级到1.2版本，新版本修复了bug并优化了转录本重建过程，可支持NCBI上Gff3文件下载。
**软件官网：** http://soft.novelbio.com/cash/index.html
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;对RNA-Seq比对后的结果文件进行可变剪接的检测， 该模块可以准确地检测出8种可变剪接类型。
***

#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是RnaSeqMap得到的比对结果bam文件。
**inFileArray：**比对结果bam文件，要求该bam是排序后的bam文件。BAM是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
**gtfFile：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中，则不需要输入该文件。
***

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　	可变剪接结果列表(txt)文件。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**物种版本：**选择参考基因组的版本。
**dbType：**同一版本的基因组数据，在不同数据库中记录的信息不同，通过该参数可选择不同数据库gtf文件。
**MergePvalue:**对junction reads的P-value与mapping reads的P-value进行合并的方式，其选项值有：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Arithmetic：算术平均值方式；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Geometric：几何平均值方式。
**isCombine：**是否合并bam文件。当选中时，如果样本组内有重复，软件会将组内的重复样本合并成一个bam文件；不选中时，如果样本组内有重复，则当正常的生物学重复处理。默认为false。
**isDisplayAllEvent：**是否输出每个基因的所有可变剪接形式。如果不选，一个基因只记录一条可变剪接形式。
**StrandSpecific：**设置链特异性，选项值有：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NONE：非链特异性建库测序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;FirstStrand：链特异性建库，PE reads的第一条read 代表测序片段的方向；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SecondStrand：链特异性建库，PE reads的第二条read 代表测序片段的方向。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;默认为NONE。
**SpliceCons：**是否基于RNA-Seq数据和参考注释文件构建可变剪接模型，引导检测样本中的novel 可变剪接。勾选表示根据RNA-Seq数据和gtf/gff文件构建可变剪接模型，此时软件运行时间比较长；不勾选表示仅根据gtf/gff文件推测可变剪接的模型。默认为勾选。
**文件对比：**设置比对组。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CaseGroup：选择Case组；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ControlGroup：选择Control组；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OutPrefix：设置输出文件前缀。
**打开高级选项：**
**JuncAllSample：**当所有样本中的junction reads数量小于该值时，不进行AS的预测，默认值为25；
**JuncOneGroup：**当一组样本中的junction reads数量小于该值时，不进行AS的预测，默认值为10；
**minAnchorLen：**当统计junction reads时，比对到两端exon上的序列的最小长度，默认为5bp;
**minIntronLen：**内含子最小长度，当RNA-Seq reads 之间的gap值大于该设定值时，认为该处可能是个内含子，默认值为25bp；
**minJuncReadsForNew：**在重构的剪接位点处， junction reads的最小长度，默认为10bp；
**runSepChr：**对于一些特殊的物种（如：Hordeum vulgare），基因组很大时，‘htsjdk(v2.9.0)’无法给该基因组序列创建索引，此时，不勾选该参数，表示不给基因组创建索引，选中则表示创建索引。当不选中该参数时，软件在运行过程中会占用较大的内存，运行时间比较长。默认是选中。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　	1) * .alldiff.statistics.txt：八种可变剪接数量统计表，如：
<div style="text-align:center">
	<img data-src="1.png" width="600px" ></img>
</div>
其中，八种可变剪接分别为：
<div style="text-align:center">
	<img data-src="2.png" width="400px" ></img>
</div>
	2) *. alldiff.txt：差异可变剪接详细信息，如：
<div style="text-align:center">
	<img data-src="3.png" width="800px" ></img>
</div> 
详细信息解释如下
<div style="text-align:center">
	<img data-src="4.png" width="500px" ></img>
</div>
***
**详细解释:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;可变剪接：有些基因的前体mRNA（pre-mRNA）通过不同的剪接方式（选择不同的剪接位点）产生不同的mRNA剪接异构体，这一过程称为可变剪接或者选择性剪切（Alternative Splicing，AS）。可变剪接是调节基因表达和产生蛋白质组多样性的重要机制，是导致真核生物基因和蛋白质数量较大差异的重要原因。可变剪接在产生受体多样性、控制调节生长发育等方面起决定性作用，尤其表现在神经系统和免疫系统，这与该类系统的功能多样性和反应敏感性是密切相关的。许多遗传疾病都与剪接发生异常紧密相关。
***
**参考文献：**
1.	Zhou X, Wu W, Li H, Cheng Y, Wei N, Zong J, Feng X, Xie Z, Chen D, and Manley JL et al. 2014. Transcriptome analysis of alternative splicing events regulated by SRSF10 reveals position-dependent splicing modulation. Nucleic Acids Res 42: 4019-4030.
2.	Wu W, Zong J, Wei N, Cheng J, Zhou X, Cheng Y, Chen D, Guo Q, Zhang B, Feng Y. CASH: a constructing comprehensive splice site method for detecting alternative splicing events. Briefings in Bioinformatics. Apr 2017. doi: 10.1093/bib/bbx034.

