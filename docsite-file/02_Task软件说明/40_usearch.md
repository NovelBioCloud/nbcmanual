# usearch
　　usearch在序列搜索、聚类、去重、去嵌合体等序列操作中有非常重要的作用。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;用于搜索数据库中高可信度的非冗余序列。
**使用软件：**
　　**USEARCH：**Ultra-fast sequence analysis，是用于分析非冗余序列的工具，由Robert Edgar开发，目前已有4000多篇论文使用。USEARCH提供了查询和聚类的算法，运算速度远远高于BLAST。
**软件官网：**
&nbsp;&nbsp;&nbsp;&nbsp;http://www.drive5.com/usearch/
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;可对序列进行聚类、去冗余以及去除嵌合体等处理。

****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是需要去冗余或者聚类的序列文件，文件格式为fasta格式。
&nbsp;&nbsp;&nbsp;&nbsp;**InputFile：**需要聚类的序列文件，文件格式为fasta。

****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;聚类后文件（*.conSeq.fa），以Fasta文件格式存储。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='uIdentity'>Usearch identity：</label>序列一致性（两个序列之间的相似性）的阈值。
<label id='reverseMatch'>Reverse-complemented matching：</label>核酸序列聚类时是否采用反向互补配对（Reverse-complemented matching）的方式。
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)	**\*.conSeq.fa：**聚类得到的序列文件，以fasta格式存储。
2)	**\*.uc：**usearch的聚类格式（UC），是一个tab-separated text文件，uc文件详细说明请见UC output file http://www.drive5.com/usearch/manual/opt_uc.html
***

**参考文献：**
1.	Edgar RC.Search and clustering orders of magnitude faster than BLAST. Bioinformatics. 2010 Oct 1; 26(19):2460-1.
