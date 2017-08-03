# GetCircSeq

　　通过基因名称、序列位置等信息提取circRNA的序列软件。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件<span>**

　　输入.txt格式文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置<span>**
**物种：**选择参考序列物种。
**版本：**参考序列的版本。
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
**CircNameCol：**Circ名称Id列所在列数。
**ChrCol：**染色体所在列数。
**StartCol：**提取cicRNA起始位点的所在列数。
**EndCol：**提取cicRNA终止位点的所在列数。
**StrandCol：**链特异性正反链所在列数
**HostGeneCol：**HostGene所在列数
**containerNumber：**软件运行使用container数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明<span>**
　circRNA.fa：提取出的circRNA序列。
　type.xls：circRNA的长度、type等信息列表。
<div style="text-align:center"><img data-src="1.png" width="600px" ></img></div>
