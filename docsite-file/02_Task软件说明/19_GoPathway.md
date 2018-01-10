## GOPathway
　　该模块可以进行基因的注释分析，其中包括GO功能注释、KEGG pathway代谢通路注释以及COG注释，从而实现对海量基因进行快速有效的注释分析目的。
**功能：**
　(1) 基因的GO功能富集性分析。
　(2) 基因的KEGG pathway代谢通路富集性分析。
　(3) 基因的COG注释。
**使用软件：**
　1. **Blast2Go：**Blast2GO是一套集成的比较成熟的序列功能注释和分析平台， 可以整合NR， Swiss-prot 以及Interproscan的结果对序列进行Gene Ontology（GO）的功能分类。
官网：https://www.blast2go.com/
　2.** TopGO：**topGO是一个Bioconductor的包，用于GO term富集分析以及结果展示。Bioconductor是使用R统计编程语言开发的开放的开源项目，它提供了多种用于分析高通量数据的工具。
软件官网：https://bioconductor.org/packages/release/bioc/html/topGO.html
**应用范围：**
　　需要进行GO 和pathway富集分析或者COG注释的基因。其中GO分析可广泛应用于动植物中；Pathway分析则主要应用于动物，植物中较少应用，原因是植物的pathway在数据库中记录比较少，所以分析结果信息不太多；而通常情况下，在RNA-Seq的denovo组装项目分析中和微生物项目的分析中会使用到COG分析。 

  ***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于DifGene的显著性差异基因表格文件，也可以是外源基因表格文件。
　　**goAnnoFile：**已知的基因对应GO ID注释列表。　
　　**用途：**当所分析的物种，在后台数据库中的注释信息不全时，可以在此增加已知的基因对应GO ID注释列表，以增加基因的GO注释率（如果需要分析的物种已经存在于物种管理中，即可以在物种选择的下拉框中选择的，则可以输入该文件也可以不用输入该文件，如果物种管理中没有的物种，则必须要输入）。
　　**格式：**该输入文件一共有两列信息，第一列基因名称，第二列为基因的GO ID，两列之间用“tab”键隔开。如：
<div style="text-align:center"><img data-src="8.png" width="150px"></img></div>
　　注意，一个基因有多个GO ID时，需要用写成多行，即每一行只有一个基因名称和一个GO ID。
　　**querySeqCOG：**COG分析的时候需要提供分析基因的蛋白序列信息。如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。
　　**inputData：**基因列表，该输入文件的格式可以是以下三种类型 ：
　　(1).仅有基因名称一列信息，如：
<div style="text-align:center"><img data-src="9.png" width="90px"></img></div>
　　(2).含有基因名称和趋势序号的列表，即趋势分析的基因列表，如：
<div style="text-align:center"><img data-src="10.png" width="150px"></img></div>
　　注意：该趋势序号列必须在第三列，第二列信息可以是任意信息，也可以是空列。
  
　　(3).常用的显著性差异表达基因列表，如：
<div style="text-align:center"><img data-src="11.png" width="500px"></img></div>
　　注意：其中基因列和Log2FC列，这两列信息是必须要有的，其他列信息可有可无。
  
　　**background：**所分析物种的所有基因的列表（如果需要分析的物种已经存在于物种管理中，即可以在物种选择的下拉框中选择的，则可以不用输入该文件）。
　　**用途：**该参数文件用于在富集性分析过程中的fisher精确检验时做背景。
　　**格式：**该输入文件，仅需一列基因名称即可，如：
<div style="text-align:center"><img data-src="12.png" width="100px"></img></div>

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　基因GO功能注释结果列表（Excel格式）文件。GO分析所有结果存放在“GOAnalysis_result”文件夹中。根据GO结构的三大分类，将结果文件分为三类（BP、CC和MF），如果输入的基因文件为含有Log2FC的差异表达基因列表，那么输出结果中还会将这三大类文件，每一类都区分成两种，其中以_BP.xlsx、_CC.xlsx、_MF.xlsx结尾的是，区分上下调基因的GO富集分析结果；以_BP_All.xlsx、_BP_All.xlsx、_BP_All.xlsx结尾的是不区分上下调基因的GO富集分析结果。
　　基因Pathway结果列表（Excel格式）文件。Pathway分析的所有结果存放在“PathWayAnalysis_result”文件夹中，其中.Pathway-Analysis_All.xlsx是所有有pathway注释的基因注释结果列表，.Pathway-Analysis.xlsx是区分上下调基因的基因注释列表。　 
  
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考基因组的版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
　<label id='goAlgorithm'>GoAlgorithm：</label>是生成GO graph的算法，详情请查阅TopGO官方文档：
https://bioconductor.org/packages/release/bioc/vignettes/topGO/inst/doc/topGO.pdf

　<label id='analysisType'>Analysis Type：</label>选择分析类型。
　　　　　　 　GOAnalysis:只做GO功能注释分析；
　　　　　　 　Pathway：只做Pathway代谢通路分析；
　　　　　　 　COG：只做原核蛋白同源性分析；
　　　　　 　　GOPATH：同时做GO功能注释和pathway代谢通路注释（推荐选择）；
　　　　　　　 ALL(NotRecommand)：同时做GO功能注释、pathway代谢通路注释、COG分析（不推荐选择）；

　<label id='cogType'>CogType：</label>COG_Prokaryotes 用于分析原核生物；
　　　　　 　 KOG_Eukaryotes  用于分析真核生物。
　<label id='acclDColNum'>GeneColNum：</label>输入文件中，基因名称所在的列数。
　<label id='valueColNum'>Log2FCColNum：</label>Log2FC，表示为以2为底，实验组和对照组信号值差异倍数的对数， 该参数表示在输入文件列表中，Log2FC所在列数。（通常Difgene中算法选择为DE，该列为5；算法选择为EB，该列为4）。需要注意的是，当输入文件是差异基因列表（即列表中含有Log2FC信息时）需要填写该参数。
　<label id='upValue'>CutOff>=：</label>Log2FC的最大阈值（根据ValueColNum 为fold change 或者logFC填写）。需要注意的是，当输入文件是差异基因列表（即列表中含有Log2FC信息时）需要填写该参数，基因的上调倍数值，例如，如果该参数设置为1表示，筛选上调基因的标准时：Log2FC>=1
　<label id='downValue'>CutOff<=：</label>Log2FC的最小阈值（根据ValueColNum 为fold change 或者logFC填写）。需要注意的是，当输入文件是差异基因列表（即列表中含有Log2FC信息时）需要填写该参数，基因的上下调倍数值，例如，如果该参数设置为-1表示，筛选下调基因的标准时：Log2FC<=-1）。
　<label id='goLevelNum'>GoLevelNum：</label>选择输出GO的层级数。每一个GO的分类，都是树形结构的，该参数表示基因的GO注释到树形结构中的第几层，可选择范围为【0~5】，默认为3。
　<label id='clusterGoPath'>ClusterGoPath：</label>当输入基因列表文件是带有趋势类型时，需要选中该选项。
　<label id='isCombine'>IsCombine：</label>当输入文件参数“**goAnnoFile**”有输入文件时，勾选该参数，表示，将“**goAnnoFile**”输入文件中的注释结果和使用平台数据库注释出的结果进行合并，如果不选中，则仅使用“**goAnnoFile**”输入文件做基因注释。
　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　基因GO/Pathway分析结果柱状图（png）文件。
（1）“GOAnalysis_result”：该文件夹中是的所有png文件详细说明如下：
　a) \*_All.png：是**所有**有GO注释的基因富集性分析柱状图；
　b) \*_Down.png：是所有下调有GO注释基因的富集性分析柱状图；
　c) \*_Up.png：是所有有GO注释的上调基因的富集性分析柱状图。
　以 \*_All.png为例，展示如下：
<div style="text-align:center">
<img data-src="4.png" width="500px" ></img>
</div>
  
  （2）“PathWayAnalysis_result”：该文件夹中的所有png文件详细说明如下：
　a)\* Path-Analysis-Enrichment.All.png是**所有**有pathway注释的基因的pathway富集性分析柱状图；
　b)\*.Path-Analysis-Enrichment.Down.png是所有有pathway注释的**下调**基因的pathway富集性分析柱状图；
　c)\*.Path-Analysis-Enrichment.Up.png是所有有pathway注释的**上调**基因的pathway富集性分析柱状图;
　d)\*.Path-Analysis-Log10P.All.png是将**所有**基因的pathway Term根据-Log10(P-value)进行从大到小排序后绘制的分布图；
　e)\*.Path-Analysis-Log10P.Down.png是将所有**下调**基因的pathway Term根据-Log10(P-value)进行从大到小排序后绘制的分布图；
　f)\*.Path-Analysis-Log10P.Up.png是将所有**上调**pathway Term根据-Log10(P-value)进行从大到小排序后绘制的分布图。

以\* Path-Analysis-Enrichment.All.png为例，展示如下：<div style="text-align:center">
<img data-src="6.png" width="300px" ></img>
</div>
　以\*.Path-Analysis-Log10P.All.png为例，展示如下：
<div style="text-align:center"><img data-src="13.png" width="300px" ></img>
</div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**
1）GoAnalysis
　　Gene Ontology，简称GO，是一套国际标准化的基因功能描述的分类系统，从1988年开始，它的应用范围从刚开始的三个模式生物数据库的整合:FlyBase (果蝇数据库Drosophila),Saccharomyces Genome Database (酵母基因组数据库SGD)、Mouse Genome Database(小鼠基因组数据库MGD)，经过不断发展扩大，现已扩展到涵盖几乎所有物种基因组功能注释的数据库整合平台。
GO具有三大类：
　生物过程biological process：生物学过程系指由一个或多个分子功能有序组合而产生的系列事件；
　分子功能molecular function：描述基因产物个体的功能，如与碳水化合物结合、ATP水解酶活性等；
　细胞组分cellular component：基因产物位于何种细胞器或基因产物组中（如糙面内质网，核或核糖体，蛋白酶体等）。 
　　官网 http://geneontology.org/
2）Pathway
　　KEGG为计算机利用基因信息对复杂的细胞活动和生物体行为作出计算推测。KEGG整合基因组、化学和系统功能信息的数据库，把从已经完整测序的基因组中得到的基因目录与更高级别的细胞、物种和生态系统水平的系统功能关联起来。KEGG的一个显著特点就是具有强大的图形功能，它利用图形而不是繁缛的文字来介绍众多的代谢途径以及各途径之间的关系，使研究的代谢途径直观全面。
　　官网http://www.kegg.jp/kegg/pathway.html
3）COG
　　COG（Clusters of Orthologous Groups of proteins）是NCBI开发的用于同源蛋白注释的数据库。构成每个COG的蛋白都是被假定为来自于一个祖先蛋白，并且因此或者是orthologs或者是paralogs。Orthologs是指来自于不同物种的由垂直家系（物种形成）进化而来的蛋白，并且典型的保留与原始蛋白有相同的功能。Paralogs是那些在一定物种中的来源于基因复制的蛋白，可能会进化出新的与原来有关的功能。COG数据库根据蛋白质序列的相似性，将蛋白质序列分成不同的类。每个类赋予一个COG编号，代表着一种同源蛋白。同时，将所有的同源蛋白再分成25个大类。此外，COG数据库包含COG和KOG共2个数据库。前者对原核生物的同源蛋白进行聚类，适合原核生物的COG注释，目前COG有4873个分类；后者对真核生物的同源蛋白进行聚类，适合真核生物的COG注释，目前KOG有4852个分类。COG分析对于预测单个蛋白质的功能和整个新基因组中的蛋白质的功能非常有用。COG注释的作用主要有：1. 通过已知蛋白对未知序列进行功能注释； 2. 通过查看指定的COG编号对应的protein数目，存在及缺失，从而能推导特定的代谢途径。
　　官网 http://www.ncbi.nlm.nih.gov/COG/
　　下载COG库和COGNITOR程序：ftp://ncbi.nlm.nih.gov/pub/COG
4）GO_Path
　　GO_Path是一个有向无环图（DAG）型的本体，GO中使用了is_a和part_of和regulates三种关系。is_a从属关系，Part_of表示靶标的小球是部分包含于的关系，regulate表示调控的关系。如图，线粒体是一种细胞器(organelle)，细胞器膜(organelle membrane)是细胞器的一部分。
 
<div style="text-align:center">
<img data-src="1.png" width="500px"  ></img></div>
