# miRNASeqAnalysis
　　通过与miRBase数据库、Rfam数据进行比对，快速鉴定不同组织、不同发育阶段、疾病状态下，已知microRNA的表达量，microRNA的种类分布。同时还可以进行通过Miranda、RNAhybrid进行Novel microRNA预测。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　inputFile选择的是FastQC Task的结果文件fq.gz，若是进行模式物种的Mapping，可以直接勾选Mapping To Species Specific Rfam进行Mapping。若是非模式物种，需要进行Novel miRNA预测，Blast到其他物种增加注释量，我们就需要在Blast处进行模式物种的选择，勾选 Prediect miRNA，Prediect miRNA即可开始分析。
　　输入文件格式：fastq或fastq.gz；输出文件格式：. txt、.xls、.fa。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择物种，跟miRBase数据库比对。
　<label id='speciesVersion'>版本：</label>参考序列版本。
　<label id='blastSpecies'>BlastSpecies：</label>可选择多个物种，在miRBase数据库比对，增加注释量。
　<label id='mappingToSpeciesRfam'>Mapping To Species Rfam：</label>跟本物种Rfam数据库比对。
　<label id='mappingAllToRfam'>Mapping All To Rfam：</label>跟整个Rfam数据库比对。
　<label id='mappingAllToGenome'>Mapping All To Genome：</label>在基因组数据库中比对。
　<label id='overlap'>cover exist result：</label>覆盖以前的结果。
　<label id='isparallel'>Isparallel：</label>并行，多个样品一起运行。
　<label id='predictMirna'>Prediect miRNA：</label>对Novel miRNA进行预测。
　<label id='thread'>thread：</label>计算运行时使用线程数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　miRNA.All.Counts.exp.txt：miRNA表达量统计。
<div style="text-align:center">
<img data-src="1.png" width="550px"  ></img>
</div>
　miRNAPre.All.Counts.exp.txt：miRNA前体表达量统计。
<div style="text-align:center">
<img data-src="2.png" width="550px" ></img>
</div>
　RfamClassAll.txt：miRNA数据比对到Rfam数据库的统计序列分类结果。
<div style="text-align:center">
<img data-src="3.png" width="400px" ></img>
</div>
　Genome.bam.mapping_statistics.xls：miRNA数据比对到基因组数据库的统计结果。
<div style="text-align:center">
<img data-src="4.png" width="500px" ></img>
</div>
　miRNA.bam.mapping_statistics.xls：miRNA数据比对该物种miRNA数据库的统计结果。
<div style="text-align:center">
<img data-src="5.png" width="500px"></img>
</div>
　rfam.bam.mapping_statistics.xls：miRNA数据比对到Rfam数据库的详细结果。
<div style="text-align:center">
<img data-src="6.png" width="500px" ></img>
</div>



