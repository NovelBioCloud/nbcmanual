# OTUAnalysis
　　一般情况下，如果序列之间，比如不同的16S rRNA序列的相似性高于97%就可以把它定义为一个OTU(Operational Taxonomic Units)，每个OTU对应于一种不同的16S rRNA序列，也就是每个OTU对应于一种类型的微生物。通过OTU分析，就可以知道样品中微生物多样性和不同微生物的丰度。同时通过OTU的稀有度分析，还可以看出来测序量是否足够反应样本中的大部分微生物种。
  **功能：**
　		利用Qiime软件根据序列相似度将其聚类，用于物种分类，统计各个样品每个OTU中的丰度信息，OTU的种类多少说明样品的物种丰富程度。
  **使用软件：**
　　QIIME2：QIIME （Quantitative Insights Into Microbial Ecology）是一个专门针对于微生物群落的分析流程，主要用Python编写，也整合了很多其它的工具包，可以进行OTU分析和多样性分析等。QIIME拥有处理16s rRNA测序数据所需要的软件，并呈现出相应的处理结果。
  **Qiime官网：**http://qiime.org/
  **应用范围：**
　　要了解一个样品测序结果的菌种、菌属等数目信息，就需要根据指定的相似度，对所有序列进行归类，通过归类操作，将序列按照彼此的相似性归为许多小组，一个小组就是一个OTU。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
该Task的输入数据是RemoveChimera的结果fasta文件。
**InputFasta：**过滤嵌合体后的FASTA文件。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
OTU丰度信息和物种分类信息（txt）文件。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**OTUs_Similarity：**reads聚类的相似度，默认值为97%
　**Database：**选择比对数据库，其选项有：SILVA_128_97_otus，SILVA_128_99_otus和Default数据库，其中\*\_97_\*，和\*\_99_\*表示相似度为97%和相似度为99%的reference
　**Taxo_Similarity：**分类相似度
　**minOTUSize：**最少有OTU的丰度，默认值为2
　

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
　1）table.taxonomy.txt：OTU丰度信息和物种分类
<div style="text-align:center"><img data-src="1.png" width="600px"  ></img></div>
　2）taxonomy.html：物种分类图
<div style="text-align:center"><img data-src="2.png" width="500px"  ></img></div>
***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
**OTU**                
　　OTU即Operational Taxonomic Units的缩写，分类操作单元，是在系统发生学或群体遗传学研究中，为了便于进行分析，人为给某一个分类单元（品系，属，种、分组等）设置的同一标志。理论上一个OTU代表一个微生物物种。通过测序获得的大量reads，首先需要对这些reads进行归类（cluster），通常在97%的相似水平划分为不同的OTU，将OTU代表序列与相应的微生物数据库比对（Silva、RDP、Greengene等），得到每个样本所含的物种信息，从而进行后续生物信息统计分析。
**Q值**
　　Q值用来评估测序的碱基质量，Q值与测序错误E值之间关系为如果一个碱基的Q值为20，那表示这个碱基测错的可能性为1%。实际操作中常用Q20/Q30作为标准，一般要求Q20大于90%即可。
**参考文献：**
1.Caporaso, J. Gregory, Justin Kuczynski, Jesse Stombaugh, Kyle Bittinger, Frederic D. Bushman, Elizabeth K. Costello, Noah Fierer et al. “QIIME allows analysis of high-throughput community sequencing data.” Nature methods 7, no. 5 (2010): 335-336.
2.Schloss, Patrick D., Sarah L. Westcott, Thomas Ryabin, Justine R. Hall, Martin Hartmann, Emily B. Hollister, Ryan A. Lesniewski et al. “Introducing mothur: open-source, platform-independent, community-supported software for describing and comparing microbial communities.” Applied and environmental microbiology 75, no. 23 (2009): 7537-7541.