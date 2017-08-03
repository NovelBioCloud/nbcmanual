# OTUAnalysis
　　利用Qiime软件根据相似度将其聚类，用于物种分类的OTU(Operational Taxonomic Units)，统计各个样品每个OTU中的丰度信息，OTU的丰度来说明样品的物种丰富程度。
　　Qiime官网：http://qiime.org/
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　RemoveChimera产生的Allunique.fasta数据。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**OTUs_Similarity：**reads聚类的相似度，默认值为97%
　**Database：**选择数据库
　**Taxo_Similarity：**分类相似度
　**minOTUSize：**最少有OTU的丰度，默认值为2
　**containerNumber：**运行时，使用Container数

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　table.taxonomy.txt：OTU丰度信息和物种分类
<div style="text-align:center"><img data-src="1.png" width="600px"  ></img></div>
　taxonomy.html：物种分类图
<div style="text-align:center"><img data-src="2.png" width="500px"  ></img></div>

