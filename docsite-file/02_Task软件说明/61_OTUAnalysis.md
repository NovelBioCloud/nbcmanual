# OTUAnalysis
　　在97%相似度下利用Qiime软件将其聚类为用于物种分类的OTU(Operational Taxonomic Units)，统计各个样品每个OTU
中的丰度信息，OTU的丰度初步说明了样品的物种丰富程度。
Qiime官网：http://qiime.org/
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　RemoveChimera产生的Allunique.fasta数据。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
OTUs_Similarity：reads聚类的相似度，默认值为97%
Database：数据库
Taxo_Similarity：分类相似度
minOTUSize：最少有OTU的丰度，默认值为2
containerNumber：运行时，使用Container数

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**