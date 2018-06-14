# RNAalterSplice
　　随着二代测序的读长和覆盖度的增加，可变剪接的识别率和准确度也不断的提升，越来越多的疾病以及生物学现象被发现是由转录本剪接形式的不同所造成。目前可变剪接已经成为转录组测序研究的一个重点。
**功能：**
　　检测可变剪接和差异可变剪接。
**使用软件：**
 　ASD：Alternative Splicing Detector，是烈冰生物信息研发团队自主研发的差异可变剪接算法。ASD于2014年发表在国际期刊《Nucleic Acids Reseach》杂志上，现已升级到1.2版本，新版本修复了bug并优化了转录本重建过程，可支持NCBI上Gff3文件下载。
　　软件官网：http://erp.novelbio.com/ASD/
**应用范围：**
　　对RNA-seq比对后的结果文件进行可变剪接的检测，该模块可以准确地检测出8种可变剪接类型。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是RnaSeqMap中的比对结果bam文件。
　　**inFileArray：**比对结果bam文件，要求是排序后的bam文件。而BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　　**gtfFile：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　可变剪接结果列表(txt)文件。



***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置</span>**
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>版本：</label>参考基因组的版本。
<label id='dbType'>dbType：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
<label id='displayEvent'>Display All Splicing Event：</label>每个基因输出所有的可变剪接事件，如果不选，一个基因只记录一条可变剪接事件。
<label id='considerRepeat'>Consider Repeat：</label>分析过程中是否考虑生物学重复。
<label id='reconstructIso'>reconstructlso：</label>分析过程中是否进行转录本重构。
<label id='isUseUMReadsExp'>仅用UniqueMappedReads算表达：</label>是否只用unique reads（即只比对到基因组上一个位置的reads）计算表达。
<label id='SS_lib_type'>链特异性：</label>测序数据的链特异性设置，其选项有以下四个：
　　　　　Predict by software 软件自动匹配。推荐使用。
　　　　　Not consider strand 不考虑链特异信息。
　　　　　1st Read is strand： 当输入序列具有链特异性且PE reads 的左端与基因方向一致时，选择该选项。
　　　　　2nd Read is strand：当输入序列具有链特异性且PE reads 的右端与基因方向一致时，选择该选项。
**文件对比：**加入对比两个组份。
　　　　　　group1Array：选择对比组1；
　　　　　　group2Array：选择对比组2；
　　　　　　outFileArray：输出文件名称。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明</span>**
（1）\* .alldiff.statistics.txt：八种可变剪接数量统计表，如：
<div style="text-align:center"><img data-src="3.png" width="400px" ></img></div>
其中，八种可变剪接分别为：
<div style="text-align:center"><img data-src="4.png" width="400px" ></img></div>


（2） \*. alldiff.txt：差异可变剪接详细信息，如：
<div style="text-align:center"><img data-src="2.png" width="700px" ></img></div>
详细信息解释如下:
<div style="text-align:center"><img data-src="5.png" width="400px" ></img></div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　**可变剪接：**有些基因的前体mRNA（pre-mRNA）通过不同的剪接方式（选择不同的剪接位点）产生不同的mRNA剪接异构体，这一过程称为可变剪接（或者选择性剪切）（Alternative Splicing）。可变剪接是调节基因表达和产生蛋白质组多样性的重要机制，是导致真核生物基因和蛋白质数量较大差异的重要原因。可变剪接在产生受体多样性、控制调节生长发育等方面起决定性作用，尤其表现在神经系统和免疫系统，这与该类系统的功能多样性和反应敏感性是密切相关的。许多遗传疾病都与剪接发生异常紧密相关。

参考文献：
Zhou, X. et al. Transcriptome analysis of alternative splicing events regulated by SRSF10 reveals position-dependent splicing modulation. Nucleic Acids Res(2014).





