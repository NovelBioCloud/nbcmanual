# QUAST
　　QUAST为组装后序列信息统计软件。（如：组装序列条数、最长序列长度、N50等）。
　　软件官网：http://quast.bioinf.spbau.ru/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
inputFaFile：输入组装完成的序列，格式为contigs.fasta。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
Min Contig:组装时最小contig值，默认500bp。
threadNum:运行时使用线程数。
containerNumber:运行时使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
组装统计结果：
<div style="text-align:center"><img data-src="1.png" width="400px" ></img></div>
contigNx长度统计结果，例如contigN50。
<div style="text-align:center"><img data-src="2.png" width="400px" ></img></div>
contig叠加长度统计：将contig从长到短排列，依次叠加长度统计。
<div style="text-align:center"><img data-src="3.png" width="400px" ></img></div>

GC含量曲线图
<div style="text-align:center"><img data-src="4.png" width="400px" ></img></div>

GC含量柱形图
<div style="text-align:center"><img data-src="5.png" width="400px" ></img></div>
scaffold覆盖度曲线图
<div style="text-align:center"><img data-src="6.png" width="400px" ></img></div>
scaffold覆盖度柱形图
<div style="text-align:center"><img data-src="7.png" width="400px" ></img></div>
