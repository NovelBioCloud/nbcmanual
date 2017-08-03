# RNAalterSplice
　　烈冰生物信息研发团队利用RNA-seq技术，并结合自主研发的差异可变剪接软件。差异可变剪接ASD软件文章发表于2014年《Nucleic Acids Reseach》杂志上，现已升级到1.2版本，新版本修复bug并优化转录本重建过程，可支持NCBI上Gff3文件下载。
　　官网：http://erp.novelbio.com/ASD/
<div style="text-align:center"><img data-src="1.png" width="700px" ></img>ASD软件图示</div>



***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件</span>**

　**inFileArray (BAM)：**输入排序好的Bam文件.sorted.bam。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置</span>**
　**物种：**参考序列物种
　**版本：**基因组数据库版本。
　**dbType：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　**Display All Splicing Event：**否记录所有的可变剪接事件，如果不选，一个基因只记录一条可变剪接事件。
　**Consider Repeat：**是否考虑生物学重复。
　**reconstructlso：**否进行转录本重构。
　**仅用UniqueMappedReads算表达：**否只用unique reads计算表达。
　**链特异性：**是数据是否是链特异性建库。
　　　　　Predict by software 软件自动匹配。推荐使用。
　　　　　Not consider strand 不考虑链特异信息。
　　　　　1st Read is strand： 推荐Ion Proton 使用，read1在5"端上游，和前导链一致, read2在3"下游， 和前导链反向互补。 或者read2在上游, read1在下游反向互补。
　　　　　2nd Read is strand：read1在5"端上游, 和前导链反向互补， read2在3"端下游，和前导链一致。
　**文件对比：**加入对比两个组份。
　　　　　　group1Array：选择对比组1；
　　　　　　group2Array：选择对比组2；
　　　　　　outFileArray：输出名称。
　**containerNumber：**运行时所使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明</span>**

（1）alldiff.statistics.txt：可变剪接的统计信息
（2）alldiff.txt：差异可变剪接的信息
<div style="text-align:center"><img data-src="2.png" width="700px" ></img></div>
　AccID：可能发生可变剪接的转录本在NCBI的ID。
　Location：可能发生可变剪接的染色体区域。
　ExonNumber：发生差异可变剪接的外显子。
　Inclusive::Exclusive：没有发生junction和发生junction的外显子覆盖度。
　Exp：没发生差异可变剪接和发生差异可变剪接的外显子覆盖度。
　Pvalue-Arithmetic：发生可变剪接的可能性（算数平均数），P值越低越显著。
　Pvalue-Geometric：发生可变剪接的可能性（几何平均数），P值越低越显著。
　FDR：多重假设检验误判率。FDR越小，误判率越低。
　Splicing Type：可变剪接的类型。
　Symbol：基因名称。
　KeggID：基因在Kegg中的注释编号。
　Description：基因的描述。
