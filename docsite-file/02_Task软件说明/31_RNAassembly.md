# RNAassembly
　　能够拼接出更完整、更准确的组装转录本并定量预计基因表达水平的软件。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　输入文件：leftInputData和rightputData分别输入组装的左端和右端序列，组名输入输出时显示组名。如果在已有基因组基础上做组装，可以在genomeFile输入参考基因组序列，在genomeSortBam处输入测序序列在参考基因组上的sortBam文件。
　　输入文件：fq；输出文件：.fa、.xls。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='strandType'>Strand type：</label>链特异性信息。
　　　　　　Predict By Software：软件自动匹配，推荐使用；
　　　　　　consider strand：不考虑链特异信息；
　　　　　　1st Read is strand：推荐Ion Proton 使用，read1在5"端上游, 和前导链一致, read2在3"下游, 和前导链反向互补. 或者read2在上游, read1在下游反向互补；
　　　　　　2nd Read is strand：read1在5"端上游, 和前导链反向互补, read2在3"端下游, 和前导链一致。
　<label id='threadNum'>线程数：</label>计算使用线程数。
　<label id='insertSize'>Insert大小：</label>测序文库插入片段长度。
　<label id='withOverlap'>High gene density with UTR overlap：</label>基因密度大的时候选择。
　<label id='memory'>内存：</label>Trinity运行过程中使用的最大内存。
　<label id='standReads'>标准化的Reads：</label>是否标准化reads。
　<label id='genomicSplicing'>基因组拼接：</label>已有基因组序列，是否采用基因引导的方式。
　<label id='intronMaxLen'>最长内含子的长度：</label>设置最长内含子的长度500000（bp）。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　 trinity.fasta：组装序列文件。
<div style="text-align:center">
<img data-src="1.png" width="500px" ></img>
</div>
　trinity.fasta.stat.xls：组装指标。
<div style="text-align:center">
<img data-src="2.png" width="300px" ></img>
</div>
