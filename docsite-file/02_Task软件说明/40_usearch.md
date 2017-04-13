# usearch
　　usearch 算法搜索数据库来查找高可信度的hits。
　　相关网站：http://www.drive5.com/usearch/
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　InputFile输入组装的fasta文件，输出文件：.conSeq.fa。
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='uIdentity'>Usearch identity：</label>序列一致性（两个序列之间的相似性）的阈值。
　<label id='reverseMatch'>Reverse-complemented matching：</label>核酸序列聚类时是否采用Reverse-complemented matching的方式。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1. conSeq.fa：聚类后的一致性序列。
2. uc：usearch的聚类格式（UC），是一个tab-separated text文件，uc文件详细说明请见UC output file（http://www.drive5.com/usearch/manual/opt_uc.html）。
<div style="text-align:center">
<img data-src="1.png" width="800px" ></img>
</div>
