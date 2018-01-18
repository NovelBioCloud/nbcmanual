# SamAndRPKM
　　将测序得到的reads比对到参考基因组序列上之后，得到bam文件，需要对bam文件进行统计计算，进而得到基因的表达量结果。
**功能：**
　(1) 表达量统计。
　(2) reads在基因组组件上的分布。
　(3) reads在每条染色体上的分布
 **使用软件：**
 由NovelBio编写的表达量统计软件，NovelBrain®云平台在此基础上添加了过滤序列的功能。
**应用范围：**
　　对完成参考序列比对的Reads进行计算分析，获得样品的基因表达量数据。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task数据来源文件通常是RnaSeqMap结果的Bam文件，选择默认的参数，即可输出基因的表达量表格。
　　**InputBam：**比对得到的bam文件。BAM就是SAM的二进制文件（B取自于binary）。一般情况下比对软件（如：bowtie/bowtie2 BWA）的结果文件都是Bam格式文件。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　　**gtfFile：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　基因表达量rpkm值列表和counts数列表（txt）。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　**物种：**选择参考基因组物种。
　**物种版本：**参考基因组的版本。
　**物种类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**OnlyUniqueMappedReads：**仅用UniqueMappedReads计算表达量。
　**isCallExp：**是否计算表达量（FPKM或RPKM）。
　**isSamStat：**是否进行mapping结果统计。
　**isCalGenStructure：**是否进行gene结构统计。
　**ncRNAStatistic：**是否进行ncRNA表达量的计算。
　**AdjustChrReads：**reads比对到参考序列多个位置，是否进行染色体定位的调整。例如1条reads同时比对到参考序列2个位置，每条reads表达量计为0.5。
　**Strand：**链特异性。Predict by software：软件自动检测。推荐使用。
　　　　　　　　　　Not consider strand：不考虑链特异信息。
　　　　　　　　　　1st Read is strand：当输入序列具有链特异性，且PE reads的左端与基因方向一致时，选择该选项。
　　　　　　　　　　2nd Read is strand：当输入序列具有链特异性，且PE reads的右端与基因方向一致时，选择该选项。
　**Tss-UpStream：**转录组起始位点-上游的距离，设置TSS区范围。
　**Tss-DowmStream：**转录组起始位点-下游的距离，设置TSS区范围。
　**Tes-UpStream：**转录组结束位点-上游的距离，设置TES区范围。
　**Tes-DowmStream：**转录组结束位点-下游的距离，设置TES区范围。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)	all.fpkm.exp.txt：所有基因表达量rpkm值列表。
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>
2)	all.counts.exp.txt：所有基因表达counts数列表，如：
<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>
3)\*.chr_distribution.png: 测序mapped reads比对到基因组上的各个染色体的密度进行统计。
<div style="text-align:center"><img data-src="3.png" width="500px" ></img>
</div>
4)\*.mapping_statistics.xls：比对统计列表。
<div style="text-align:center"><img data-src="4.png" width="300px" ></img>
</div>
5)\*.gene_structure.txt：reads在基因组组件上的分布，如：
<div style="text-align:center"><img data-src="5.png" width="500px" ></img>
</div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**

**RPKM:**Reads Per Kilobase per Million mapped reads的缩写，代表每百万reads中来自于某基因每千碱基长度的reads数。RPKM是将map到基因的read数除以map到基因组上的所有read数(以million为单位)与RNA的长度(以KB为单位)。计算公式为：PRKM=1E6C/NL/1E3
　其中RPKM为基因表达量，C为唯一比对到该基因上reads数，N为唯一比对到参考基因组上的总reads数，L为该基因编码区的碱基数。RPKM法能消除基因长度和测序量差异对计算基因表达的影响，计算得到的基因表达量可直接用于比较不同样品间的基因表达差异。如果一个基因存在多个转录本，则用该基因的最长转录本计算其测序覆盖度和表达量。
