# SamAndRPKM
　　将测序得到的reads比对到参考基因组序列上之后，得到bam文件，需要对bam文件进行统计计算，进而得到基因的表达量结果。
**功能：**
　(1) 表达量统计。
　(2) reads在基因组组件上的分布。
　(3) reads在每条染色体上的分布
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

　<label id='species'>Species：</label>选择参考基因组物种。
　<label id='speciesVersion'>Version：</label>参考序列的版本。
　<label id='dbType'>Gtf：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
　<label id='useGTF'>UseGTF：</label>如果为非模式物种可以上传该物种的GTF注释文件。
　<label id='isUseUMReadsExp'>OnlyUniqueMappedReads：</label>仅用UniqueMappedReads计算表达量。
　<label id='expressCount'>isCallExp：</label>计算表达量，是否计算FPKM或RPKM。
　<label id='samStatistics'>isSamStat：</label>是否进行mapping结果统计。
　<label id='geneStructure'>isCalGenStructure：</label>是否gene结构统计。
　<label id='nCRNAStatist'>ncRNAStatistic：</label>是否ncRNA进行统计。
　<label id='correct'>AdjustChrReads：</label>reads比对到参考序列多个位置，是否进行染色体定位的调整。例如1条reads同时比对到参考序列2个位置，每条reads表达量计为0.5。
　<label id='strandType'>Strand：</label>链特异性：Predict by software 软件自动匹配。推荐使用。
　　　　　　　　　　Not consider strand 不考虑链特异信息。
　　　　　　　　　　1st Read is strand：read1在5"端上游，和前导链一致, read2在3"下游， 和前导链反向互补。 或者read2在上游, read1在下游反向互补，推荐Ion Proton 使用，。
　　　　　　　　　　2nd Read is strand：read1在5"端上游, 和前导链反向互补， read2在3"端下游，和前导链一致。
　<label id='tssUp'>Tss-UpStream：</label>转录组起始位点-上游，计算TSS区范围。
　<label id='tssDown'>Tss-DowmStream：</label>转录组起始位点-下游，计算TSS区范围。
　<label id='tesDown'>Tes-UpStream：</label>转录组结束位点-上游，计算TES区范围。
　<label id='tesDown'>Tes-DowmStream：</label>转录组结束位点-下游，计算TES区范围。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)	all.fpkm.exp.txt：所有基因表达量rpkm值列表。
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>
2)	all.counts.exp.txt：所有基因表达counts数列表。
<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>
3) chr_distribution.png: 测序mapped reads比对到基因组上的各个染色体的密度进行统计。
<div style="text-align:center"><img data-src="3.png" width="500px" ></img>
</div>
4) mapping_statistics.xls：比对统计列表。
<div style="text-align:center"><img data-src="4.png" width="300px" ></img>
</div>
5)gene_structure.txt：reads在基因组组件上的分布，如：
<div style="text-align:center"><img data-src="5.png" width="500px" ></img>
</div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**

（1）**RPKM**（Reads Per Kilobase per Million）
　　RPKM是将map到基因的read数除以map到genome的所有read数(以million为单位)与RNA的长度(以KB为单位)。计算方法：RPKM=total exon reads/(mapped reads（millions）X exon length（KB）)。
　　total exon reads/mapped reads（millions）为所有read数中有百分之多少是map到这个基因，然后再除以基因长度，就可以某基因得到单位长度有百分之多少的total mapped read。
（2）**FPKM**（ Fregments Per Kilobase per Million）
　　FPKM与RPKM计算方法基本一致：FPKM=total exon reads/(mapped reads（millions）X exon length（KB）)。
　　FPKM与RPKM的区别为F是fragments，R是reads。如果pair-end测序，每个fragments有两个reads，FPKM只计算两个reads能比对到同一个转录本的fragments数量，而RPKM计算的是可以比对到转录本的reads数量，不管pair-end的两个reads是否能比对到同一个转录本上。如果是single-end测序，那么FPKM和RPKM计算的结果将是一致的。
