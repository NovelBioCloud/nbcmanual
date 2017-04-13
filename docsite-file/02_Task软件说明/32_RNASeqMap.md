# RNASeqMap
　　一个快速将RNA-Seq数据进行剪接mapping的程序。
　　输入文件格式：fastq、fastq.gz；输出文件格式： bam、bed 、txt。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　**chromesome：**当平台数据库没有相应的基因组序列或者用户需要选用自己上传的基因组序列时，在此输入基因组序列。
　**gtfFile：**当数据库信息不全时或者非模式物种，我们可以在此输入上传该物种的GTF注释文件。
　**leftInputData：**输入左端mapping文件。
　**rightInputData：**输入右端mapping文件。
 　输入文件格式：fastq、fastq.gz   输出文件格式：bam、bed 、txt。

****
### １.Tophat 
　　Tophat是一个快速将RNA-Seq数据进行剪接mapping的程序。该软件调用Bowtie 或Bowtie2来将reads比对到参考基因组上，分析比对结果来测量基因表达水平并确定基因中剪接变异。Tophat最初由马里兰大学生物信息学和计算生物学中心开发，翰霍普金斯大学生物信息学和计算生物学中心、华盛顿大学基因组部门联合开发的结果。
软件官网：http://ccb.jhu.edu/software/tophat/index.shtml
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>Species：</label>选择参考基因组物种。
　<label id='speciesVersion'>Version：</label>参考序列的版本。
　<label id='useGTF'>UseGTF：</label>选择是否使用GTF文件。
　<label id='library'>Library：</label>测序文库类型。
　　　　　　SingleEnd：单端测序；
　　　　　　PairEnd：双端测序； 　　　　　　　
　　　　　　MatePair：2~10k建库测序；
　　　　　　MatePairLong：20kb建库测序。
　<label id='algorithm'>Algorithm：</label>选择比对软件。
　<label id='intronLenMin'>IntronLenMin：</label>内含子区最小长度。
　<label id='intronLenMax'>IntronLenMax：</label>内含子区最小长度。
　<label id='thread'>Thread：</label>使用线程数。
　<label id='memory'>Memory：</label>运行过程中使用的最大内存。
　<label id='sensitive'>Sensitive：</label>敏感度。

| 名称        | 参数   |  
| --------   | :-----:  |
| very-fast        | Same as: -D 5 -R 1 -N 0 -L 22 -i S,0,2.50   | 
| fast     | Same as: -D 10 -R 2 -N 0 -L 22 -i S,0,2.50 | 
| sensitive        |   Same as: -D 15 -R 2 -L 22 -i S,1,1.15 (default in --end-to-endmode)   | 
| very-sensitive        |   Same as: -D 20 -R 3 -N 0 -L 20 -i S,1,0.50   | 
**Strand type：**链特异性信息。
　　　　　　Predict By Software:软件自动匹配，推荐使用；
　　　　　　consider strand:不考虑链特异信息；
　　　　　　1st Read is strand:推荐Ion Proton 使用，read1在5"端上游, 和前导链一致, read2在3"下游, 和前导链反向互补. 或者read2在上游, read1在下游反向互补；
　　　　　　2nd Read is strand:read1在5"端上游, 和前导链反向互补, read2在3"端下游, 和前导链一致。

****
### 2.MapSplice
　　MapSplice是一款RNA-seq数据比对到参考基因组，快速检测剪接位点，不依赖于剪接位点特征或内含子长度。可支持paired-end reads 和single-end reads,可支持不同长度的reads，还可发现新的典型以及非典型剪接、新的插入和缺失、基因融合。
　　MapSplice由肯塔基大学和北卡罗来纳大学的计算机系部门联合开发，Kai Wang等人于2010年发表Nucleic Acids Research上的具有高度特异性和敏感性的转录组测序比对算法。软件官网：http://www.netlab.uky.edu/p/bioinfo/MapSplice2
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**Species：**选择参考基因组物种。
**Version：**参考序列的版本。
**Library：**文库的类型。
**Algorithm：**选择比对软件。
**intronLenMin：**内含子区域最小长度。
**intronLenMax：**内含子区域最大长度。
**thread：**运行线程数。
**Memory：**运行过程中使用的最大内存。

****
### ３．hisat2
　　一个快速和灵敏的RNA-seq reads剪切比对软件，利用大量小型FM索引覆盖整个基因组，能够将RNA-Seq数据与基因组进行快速比对。约翰霍普金斯大学计算生物学中心的Steven Salzberg开发。
　　软件官网：http://ccb.jhu.edu/software/tophat/index.shtml
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**Species：**选择参考基因组物种。
　**Version：**参考序列的版本。
　**use GTF：**使用GTF文件。
　**Library：**文库的类型。
　**Algorithm：**选择比对软件。
　**intronLenMin：**内含子区域最小长度。
　**intronLenMax：**内含子区域最大长度。
　**Thread：**计算使用线程数。
　**Memory: **运行过程中使用的最大内存。
　**AlignNum：**非unique mapping允许的最多比对位置。
　**sensitive：**

| 名称        | 参数   |  
| --------   | :-----:  |
| very-fast        | Same as: -D 5 -R 1 -N 0 -L 22 -i S,0,2.50   | 
| fast     | Same as: -D 10 -R 2 -N 0 -L 22 -i S,0,2.50 | 
| sensitive        |   Same as: -D 15 -R 2 -L 22 -i S,1,1.15 (default in --end-to-endmode)   | 
| very-sensitive        |   Same as: -D 20 -R 3 -N 0 -L 20 -i S,1,0.50   | 
**Strand type：**链特异性信息。
　　　　　　Predict By Software:软件自动匹配，推荐使用；
　　　　　　consider strand:不考虑链特异信息；
　　　　　　1st Read is strand:推荐Ion Proton 使用，read1在5"端上游, 和前导链一致, read2在3"下游, 和前导链反向互补. 或者read2在上游, read1在下游反向互补；
　　　　　　2nd Read is strand:read1在5"端上游, 和前导链反向互补, read2在3"端下游, 和前导链一致。
**trim5：**5’端剪切掉多少碱基。
**trim3：**3’端剪切掉多少碱基。
**Dta：**转录本重构时定制参数，可以减少转录本重构使用计算内存。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　Hisat程序运行之后，会产生一个输出文件bam和hisat.novel.seplicesite.txt，bam为比对比对结果，hisat.novel.seplicesite.txt为剪切位点结果。
<div style="text-align:center">
<img data-src="1.png" width="750px"  ></img>
</div>
　　MapSplice程序运行之后，mapsplice.bam为比对好的序列， junctions.txt为junction位点信息，deletions.txt和insertions.txt为插入、确实位点信息。
<div style="text-align:center">
<img data-src="2.png" width="750px" ></img>
</div>
　　Tophat程序运行之后，tophat_sorted.bam为排序好的比对序列。
<div style="text-align:center">
<img data-src="3.png" width="750px" ></img>
</div>
