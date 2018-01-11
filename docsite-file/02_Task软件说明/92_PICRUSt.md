# PICRUSt
　　目前，对菌群16S rRNA基因进行高通量测序，是微生物研究中最基础和常用的方法，通过该方法可以揭示菌群的具体物种组成，然后通过使用PICRUSt可以把菌群的组成和其菌群行使的具体功能联系起来。
  **功能**
　　根据16S rRNA高通量测序结果预测微生物群落的基因，并结合KEGG、COG、Pfam功能进行分析。
**使用软件**
　　PICRUSt：PICRUSt全称为“Phylogenetic Investigation of Communities byReconstruction of Unobserved States”，可以通过16S rRNA基因序列，预测对应的细菌和古菌的代谢功能谱。
	**软件官网：**http://picrust.github.io/picrust/
**应用范围**
　　PICRUSt对于菌群研究贡献极大。首先，PICRUSt能从菌群组成数据解读潜在的功能，充分发挥了16S rRNA基因测序简单、快速的优势；其次，PICRUSt对菌群功能的预测，可以帮助指导后续宏基因组Denovo鸟枪法测序的实验设计，更合理地筛选用于后续研究的样本。　
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是OTUAnalysis的结果文件Forpicrust.biom。
**InputBiom：**输入BIOM格式的OTU文件。*.biom文件为QIIME软件分析过程中生成的OTU table文件， 即OTU丰度以及注释的矩阵文件。
文件详细说明请见官方文档：http://qiime.org/scripts/make_otu_table.html
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　功能注释后的功能列表文件（txt）。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**Prediction_Type：**选择功能分析类型，可以多选，其选项有以下三种：
　　“ko”：KEGG 代谢途径分析；
　　“COG”：同源蛋白注释的数据库；
　　“Rfam”：鉴定non-coding RNAs的数据库，常用于注释新的核酸序列或者基因组序列。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**

COG_categorize_by_function.L2.txt:COG功能预测结果。
KO_categorize_by_function.L3.txt:KO功能预测结果。
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**
1）KEGG：
　　KEGG为计算机利用基因信息对更高层次和更复杂细胞活动和生物体行为作出计算推测。KEGG整合基因组、化学和系统功能信息的数据库，把从已经完整测序的基因组中得到的基因目录与更高级别的细胞、物种和生态系统水平的系统功能关联起来。KEGG的一个显著特点就是具有强大的图形功能，它利用图形而不是繁缛的文字来介绍众多的代谢途径以及各途径之间的关系，使研究的代谢途径直观全面。
　　官网http://www.kegg.jp/kegg/pathway.html
2）COG：
　　COG（Clusters of Orthologous Groups of proteins）是NCBI开发的用于同源蛋白注释的数据库。构成每个COG的蛋白都是被假定为来自于一个祖先蛋白，并且因此或者是orthologs或者是paralogs。Orthologs是指来自于不同物种的由垂直家系（物种形成）进化而来的蛋白，并且典型地保留与原始蛋白相同的功能。Paralogs是那些在一定物种中的来源于基因复制的蛋白，可能会进化出新的与原来有关的功能。COG数据库根据蛋白质序列的相似性，将蛋白质序列分成不同的类。每个类赋予一个COG编号，代表着一种同源蛋白。同时，将所有的同源蛋白再分成25个大类。此外，COG数据库包含COG和KOG共2个数据库。前者对原核生物的同源蛋白进行聚类，适合原核生物的COG注释，目前COG有4873个分类；后者对真核生物的同源蛋白进行聚类，适合真核生物的COG注释，目前KOG有4852个分类。COG分析对于预测单个蛋白质的功能和整个新基因组中的蛋白质的功能非常有用。COG注释的作用主要有：1. 通过已知蛋白对未知序列进行功能注释； 2. 通过查看指定的COG编号对应的protein数目，存在及缺失，从而能推导特定的代谢途径。　
　　官网 http://www.ncbi.nlm.nih.gov/COG/

**参考文献：**
1.Langille MGI, Zaneveld J, Caporaso JG, McDonald D, Knights D, et al. (2013)Predictive functional profiling of microbial communities using 16S rRNA markergene sequences.NatureBiotechnology31: 814-+.
2.Wu J, Peters BA, DominianniC, Zhang Y, Pei Z, et al. (2016) Cigarette smoking and the oral microbiome in alarge study of American adults.ISME J10.1038/ismej.2016.37.

