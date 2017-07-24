# KCore

　　基因共表达网络分析（Gene Co-expression Network Analysis）是基于基因间表达数据的相似性而构建的网络图，图中的节点代表基因，线代表基因存在的调控关系，具有相似表达谱的基因被连接起来形成网络。
　　节点的大小代表degree值，即网络中某一基因与周围基因的关系数量，degree越大，代表与它有相互作用关系的基因越多。k-core表示在一个子图中，所有的点至少连接着k个点，其用以评估基因在网络位置的中心程度，值越大表示degree越大且越中心。相同大小的k-core体现的是基因之间的相似性及功能相关性。

**** 
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　**inputFile：**一般为CoExp的输出结果，输入文件输入。或两列输入基因关系列文件：.txt。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

**containerNumber：**软件运行时，使用的container数。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　.kCore.xls：基因列、KCore值、Degree值。
<div style="text-align:center"><img data-src="1.png" width="300px"></img></div>



