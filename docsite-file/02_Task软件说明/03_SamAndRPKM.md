# SamAndRPKM
　　RNA-Seq测序得到的reads进行表达定量统计软件。

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**

（1）**RPKM**（Reads Per Kilobase per Million）
　　RPKM是将map到基因的read数除以map到genome的所有read数(以million为单位)与RNA的长度(以KB为单位)。计算方法：RPKM=total exon reads/(mapped reads（millions）X exon length（KB）)。
　　total exon reads/mapped reads（millions）为所有read数中有百分之多少是map到这个基因，然后再除以基因长度，就可以某基因得到单位长度有百分之多少的total mapped read。
（2）**FPKM**（ Fregments Per Kilobase per Million）
　　FPKM与RPKM计算方法基本一致：FPKM=total exon reads/(mapped reads（millions）X exon length（KB）)。
　　FPKM与RPKM的区别为F是fragments，R是reads。如果pair-end测序，每个fragments有两个reads，FPKM只计算两个reads能比对到同一个转录本的fragments数量，而RPKM计算的是可以比对到转录本的reads数量，不管pair-end的两个reads是否能比对到同一个转录本上。如果是single-end测序，那么FPKM和RPKM计算的结果将是一致的。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　来源文件通常是RNASeq结果的Bam文件，选择默认的参数，即可输出基因的表达量表格。
　　输入文件：从实际文件或者规则文件中选择拖入bam文件，进行表达定量统计；组名为文件输出时名称，可以根据需求进行修改。
　　GTF文件：当数据库信息不全时或者非模式物种，上传该物种的GTF注释文件增加注释量。
　　输入文件格式：bam  输出文件格式：txt、xls、png。
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
　　　　　　　　　　1st Read is strand： 推荐Ion Proton 使用，read1在5"端上游，和前导链一致, read2在3"下游， 和前导链反向互补。 或者read2在上游, read1在下游反向互补。
　　　　　　　　　　2nd Read is strand：read1在5"端上游, 和前导链反向互补， read2在3"端下游，和前导链一致。
　<label id='tssUp'>Tss-UpStream：</label>转录组起始位点-上游，计算TSS区范围。
　<label id='tssDown'>Tss-DowmStream：</label>转录组起始位点-下游，计算TSS区范围。
　<label id='tesDown'>Tes-UpStream：</label>转录组结束位点-上游，计算TES区范围。
　<label id='tesDown'>Tes-DowmStream：</label>转录组结束位点-下游，计算TES区范围。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

**1.gene Expression**
　　基因表达水平的直接体现就是其转录本的丰度情况，转录本丰度程度越高，则基因表达水平越高。在RNA-seq分析中，我们可以通过定位到基因组区域或基因外显子区的测序序列（reads）的计数来估计基因的表达水平。Reads计数除了与基因的真实表达水平成正比外，还与基因的长度、测序深度成正相关。为了使不同基因、不同实验间估计的基因表达水平具有可比性，引入了RPKM的概念，RPKM是每百万reads中来自某一基因每千碱基长度的reads数目。RPKM同时考虑了测序深度和基因长度对reads计数的影响，是目前最为常用的基因表达水平估算方法。
　 Counts表达量：all.counts.exp.txt
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>


　 RPKM表达量：all.rpkm.exp.txt
<div style="text-align:center"><img data-src="2.png" width="500px"></img>
</div>
&nbsp;
**2.Gene Structre**
　　Gene_structure.txt是测序mapped reads在基因组上的分布情况。
<div style="text-align:center">
<img data-src="3.png" width="600px"  ></img>
</div>
<div style="text-align:center"><img data-src="4.png" width="550px" ></img>
</div>
**3.Sam Statistic**
　　测序mapped reads比对到基因组上的各个染色体的密度进行统计。
<div style="text-align:center">
<img data-src="5.png" width="550px" ></img>
</div>