# KCore

　　基因共表达网络（Gene Co-expression Network）是基于基因间表达数据的相似性而构建的网络图，图中的节点代表基因，连线代表基因间存在调控关系，具有相似表达谱的基因被连接起来形成网络。
　　节点的大小代表Degree，即网络中某一基因与周围基因的关系数量，degree越大，代表与它有相互作用关系的基因越多。k-core表示在一个子图中，1个点至少连接着k个点，用以评估基因在网络位置的中心程度。K-core值和degree值越大表示该点越处于网络图中的核心地位。若两个基因的k-core值相同，则说明二者之间具有一定的相似性及功能相关性。
**功能：**
　		计算基因的KCore值与Degree。
**使用软件**
　　**R：**R语言是一个用于统计计算和统计制图的优秀工具。基于R体系下的Bioconductor项目为用户提供了网络分析的整体解决方案。该task使用Bioconductor中的RBGL包进行网络分析。
**官网：**
　　**R :** https://www.r-project.org/
　　**Bioconductor: **http://www.bioconductor.org
 **应用范围**
对共表达基因集进行KCore值以及Degree的计算，用于后续网络图的绘制。
**** 
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
该Task的输入数据通常是CoExp的结果文件，如coExp.gene.txt。 
**inputFile：**CoExp的结果文件，如下表所示：

|AccID1  |  AccID2 |pearson|P-Value|FDR|style|
| -------- |  :----: | :----:  |  :----: | :----: | :----: |
| Cldn12 |Gdpd2 |-1 |2.01E-06|0.001281|Negative|
| Ifitm3   | S100a11   |1|4.44E-05|0.014132|Positive|
| Ifi35   | Id1   |1|1.58E-04|0.031341|Positive|
| Gbp3   |Hspb8  |-1|1.97E-04|0.031341|Negative|
| Cxcl1   | Tap1  |1|2.98E-04|0.03628|Positive|
**注意：**
1.输入表格中必须要有一行title信息，对于title名称无特殊 要求；
输入表格中两列基因名称信息是必须要有的。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
基因对应KCore值和Degree的结果列表（\*.xls）。
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

**containerNumber：**软件运行时使用的container数。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
\* .gxl：将输入文件转化为用于计算KCore值的输入文件格式，此为中间结果。
\* .kCore.xls：基因对应KCore值和Degree的结果列表，如下表所示：

|AccID  |  KCore |Degree|
| -------- |  :----: | :----:  |  :----: |
| ERCC6L |5 |5 |
| MCM7   | 6   |6|
| SETD8   |6  |6|
|hsa_circ_0068515   |6  |77|
| HJURP   | 6  |6|



