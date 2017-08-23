# DnaSeqMap
　　一组集成了Bwa_aln、Bwa_mem、Bowtie2、hisat的DNA比对软件的平台。
 ***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
Software：
Bwa_aln、Bwa_mem
　　BWA包括三个算法构成：BWA-backtrack (通常称BWA aln）,BWA-sw 和BWA-mem。BWA_aln第一种适合illumina的100bp以下的序列，BWA_mem适合70bp-1Mbp的序列，比较快且准确。
Bowtie2
　　Bowtie2是一个快速、节省内存的将短序列比对到基因组上的工具。对于50bp-1000bp 的序列比对到相对较大的基因组上很有优势。
hisat
　　 一个快速和灵敏的RNA-seq reads剪切比对软件，利用大量小型FM索引覆盖整个基因组，能够将RNA-Seq数据与基因组进行快速比对。
 ***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
**左端序列文件(FASTQ)右端序列文件(FASTQ)：**输入比对文件。
**chrSeq：**参考序列文件。
**gtfFile：**参考序列gtf文件。
 
  
 ***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>物种版本：</label>参考序列的版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
　<label id='software'>softwarName：</label>选择比对软件。
　<label id='threadNum'>线程数：</label>运行时使用线程数。
　<label id='memory'>内存：</label>运行时使用内存。
　<label id='isLocal'>is local：</label> 默认为End-to-end模式
　<label id='sensitive'>Sensitive：</label>
　　　--very-fast	Same as: -D 5 -R 1 -N 0 -L 22 -i S,0,2.50
　　　--fast	Same as: -D 10 -R 2 -N 0 -L 22 -i S,0,2.50
　　　--sensitive	Same as: -D 15 -R 2 -L 22 -i S,1,1.15 (default in --end-to-endmode)
　　　--very-sensitive	Same as: -D 20 -R 3 -N 0 -L 20 -i S,1,0.50
　<label id='mismatch'>mismatch：</label>不匹配碱基个数
　<label id='gapLength'>gapLength：</label>gap长度。
　<label id='trim5'>trim5：</label>5’端剪切掉多少碱基。
　<label id='trim3'>trim3：</label>3’端剪切掉多少碱基。

**高级选项：**
　<label id='maxDiffInSeed'>maxDiffInseed：</label>bwa_aln 最大seed差异数，默认值为2。
　<label id='excludeIndelInEnd'>excludeIndelInEnd：</label>bwa_aln reas末端index大于此值时，被过滤掉。默认值为5。
　<label id='skipFirstIntReads'>skipFirstIntReads：</label>比对时reads的前几个bp不参与比对
　<label id='minFragLength'>minFragLengt：</label>最小fragment长度，默认值为0。
　<label id='maxFragLength'>maxFragLeng：</label>最大fragment长度，默认值为500。
　<label id='maxMismatchesInSeed'>maxMismatchesInSeed：</label>seed中最大的mismatches数
　<label id='seedLength'>seedLength：</label>seed长度
　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　mapping_statistics.xls：比对的统计文件
<div style="text-align:center"><img data-src="1.png" width="450px" ></img>
</div>
　chr_distribution.png：比对的reads分布
<div style="text-align:center"><img data-src="2.png" width="600px"></img>
</div>