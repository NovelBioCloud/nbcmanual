# RnaSeqMap
 　　一个快速将RNA-Seq数据进行剪接mapping的程序。

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
### Tophat
　　Tophat是 一个快速将RNA-Seq数据进行剪接mapping的程序。该软件调用Bowtie 或Bowtie2来将reads比对到参考基因组上，分析比对结果来测量基因表达水平并确定基因中剪接变异。最初由马里兰大学生物信息学和计算生物学中心开发，翰霍普金斯大学生物信息学和计算生物学中心、华盛顿大学基因组    部门联合开发的结果。
　　软件官网：http://ccb.jhu.edu/software/tophat/index.shtml
### MapSplice
　　MapSplice是一款RNA-seq数据比对到参考基因组，快速检测剪接位点，不依赖于剪接位点特征或内含子长度。可支持paired-end reads 和single-end reads,可支持不同长度的reads，还可发现新的典型以及非典型剪接、新的插入和缺失、基因融合。MapSplice由肯塔基大学和北卡罗来纳大学的计算机系部门联合开发。
　　软件官网：http://www.netlab.uky.edu/p/bioinfo/MapSplice2
### HISAT2
　　一个快速和灵敏的RNA-seq reads剪切比对软件，利用大量小型FM索引覆盖整个基因组，能够将RNA-Seq数据与基因组进行快速比对。约翰霍普金斯大学计算生物学中心的Steven Salzberg开发。
　　软件官网：http://ccb.jhu.edu/software/tophat/index.shtml
### STAR
　　STAR不但可以进行比对，还可以输出可变剪切，转录本融合，以及控制输出格式为SAM或者BAM,并对输出的BAM可进行选择性排序输出。最主要在比对的过程中还提供了ENCODE的比对参数。
官网：https://github.com/alexdobin/STAR/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　**chromesome：**当平台数据库没有相应的基因组序列或者用户需要选用自己上传的基因组序列时，在此输入基因组序列。
　**gtfFile：**当数据库信息不全时或者非模式物种，我们可以在此输入上传该物种的GTF注释文件
　**leftInputData：**输入左端mapping文件
　**rightInputData：**输入右端mapping文件
　输入文件格式：fastq、fastq.gz   输出文件格式： .bam、.bed 、.txt

***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种
　<label id='speciesVersion'>物种版本：</label>参考序列的版本  
　<label id='dbType'>物种类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
　<label id='threadNum'>threadNum：</label>运行线程数。
　<label id='memory'>Memory：</label>运行过程中使用的最大内存。
　<label id='useGTF'>useGTF：</label>选择是否使用GTF文件。
　<label id='software'>softwareName：</label>选择使用软件。
　<label id='minintronLen'>minintronLen：</label>内含子区域最小长度。
　<label id='maxintronLen'>maxintronLen：</label>内含子区域最大长度。
　<label id='trim'>trim5：</label>5’端剪切掉多少碱基。
　<label id='trim3'>trim3：</label>3’端剪切掉多少碱基。
　<label id='alignNum'>AlignNum：</label>非unique mapping允许的最多比对位置。
　<label id='reportNovelSplicesite'>ReportNovelSplicesite：</label>选中的话，将剪切位点输出到一个文件中。
　<label id='dta'>Dta：</label>选中的话，为转录本重构提供比对方式。
　<label id='useBowtie1'>使用Bowtie1建库：</label>内部调用Bowtie1进行比对。

**高级选项：**
　<label id='mateInnerDist'>MateInnerDist：</label>两个reads之间的碱基数，默认为50bp。
　<label id='ReadMismatches'>ReadMismatches：</label>reads最小mismatch碱基数，默认值为2。
　<label id='MinAnchor'>MinAnchor：</label>junction reads一边最小的匹配碱基数，最小值为3，一般默认值为8。
　<label id='SpliceMismatches'>SpliceMismatches：</label>最大mismatch。默认值为0。
　<label id='estimatedDepth'>ReadGapLength：</label>reads比对时，gap的总碱基数超过该设定的参数值，则舍弃该reads，默认值为2。
　<label id='maxInsertLength'>MaxInsertLength：</label>junction reads最大插入长度，默认为3bp。
　<label id='maxDeleLength'>MaxDeletionLength：</label>junction reads最大缺失长度，默认为3bp。
　<label id='segLength'>SegmentLength：</label>比对时reads被切分的最小片段长度，默认为25bp。
　<label id='minMapLen'>minMapLen：</label>mapsplice的最小完全比对碱基数，默认值为50。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

1.Hisat程序运行之后，会产生一个输出文件bam和hisat.novel.seplicesite.txt，bam为比对比对结果，hisat.novel.seplicesite.txt为剪切位点结果。
<div style="text-align:center">
<img data-src="1.png" width="600px" height="200px" ></img>
</div>

2.MapSplice程序运行之后，mapsplice.bam为比对好的序列， junctions.txt为junction位点信息，deletions.txt和insertions.txt为插入、缺失位点信息。

<div style="text-align:center">
<img data-src="2.png" width="600px" height="200px" ></img>
</div>
3.Tophat程序运行之后，tophat_sorted.bam为排序好的比对序列

<div style="text-align:center">
<img data-src="3.png" width="600px" height="100px" ></img>
</div>
4.STAR结果
　Chimeric.out.junction：融合转录本
　Aligned.sortedByCoord.out.bam：比对输出
　Aligned.toTranscriptome.out.bam：转录本比对输出
　SJ.out.tab：可变剪切结果输出

