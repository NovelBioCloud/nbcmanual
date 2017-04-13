## GOPathway
　　集成进行GO分析，KEGG pathway分析、COG分析、GO_Path分析的一套分析系统。

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
1）GoAnalysis
　　Gene Ontology，简称GO，是一套国际标准化的基因功能描述的分类系统，由1988年，它的应用范围从刚开始的三个模式生物数据库的整合:FlyBase (果蝇数据库Drosophila),Saccharomyces Genome Database (酵母基因组数据库SGD)、Mouse Genome Database(小鼠基因组数据库MGD)。经过GO不断发展扩大，现已扩展到几户所有的物种基因组的功能注释的数据库。
GO具有三大类：
　生物过程biological process：生物学过程系指由一个或多个分子功能有序组合而产生的系列事件。
　分子功能molecular function：描述基因产物个体的功能，如与碳水化合物结合、ATP水解酶活性等；
　细胞组分cellular component：基因产物位于何种细胞器或基因产物组中（如糙面内质网，核或核糖体，蛋白酶体等）。 
　　官网 http://geneontology.org/
2）Pathway
　　KEGG为计算机利用基因信息对更高层次和更复杂细胞活动和生物体行为作出计算推测。KEGG整合基因组、化学和系统功能信息的数据库，把从已经完整测序的基因组中得到的基因目录与更高级别的细胞、物种和生态系统水平的系统功能关联起来。KEGG的一个显著特点就是具有强大的图形功能，它利用图形而不是繁缛的文字来介绍众多的代谢途径以及各途径之间的关系，使研究的代谢途径直观全面。
　　官网http://www.kegg.jp/kegg/pathway.html
3）COG
　　COG（Clusters of Orthologous Groups of proteins）是NCBI的数据库，COG分为两类，一类是原核生物的一般称为COG数据库，另一类是真核生物的一般称为KOG数据库，目前COG有4873个分类，KOG有4852个分类。对于预测单个蛋白质的功能和整个新基因组中的蛋白质的功能非常有用。COG库提供了对COG分类数据的检索和查询，基于Web的COGNITOR服务，系统进化模式的查询服务等。
　　COG注释作用：1. 通过已知蛋白对未知序列进行功能注释； 2. 通过查看指定的COG编号对应的protein数目，存在及缺失，从而能推导特定的代谢途径； 3. 每个COG编号是一类蛋白，将query序列和比对上的COG编号的proteins进行多序列比对，能确定保守位点，分析其进化关系。
　　官网 http://www.ncbi.nlm.nih.gov/COG/
　　下载COG库和COGNITOR程序：ftp://ncbi.nlm.nih.gov/pub/COG
4）GO_Path
　　GO_Path是一个有向无环图（DAG）型的本体，GO中使用了is_a和part_of和regulates三种关系。is_a从属关系，Part_of表示靶标的小球是部分包含于的关系，regulate表示调控的关系。如图，线粒体是一种细胞器(organelle)，细胞器膜(organelle membrane)是细胞器的一部分。
 
<div style="text-align:center">
<img data-src="1.png" width="500px"  ></img></div>


***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　Task的输入文件可来源于DifGene Task显著性差异基因表格，也可为外源基因表格，注意选取基因对应的上下调倍数值，若为非模式物种还要选取进行物种Blast，以增加注释量。
　　**goAnnoFile:** 后台数据库注释不全的时，可以增加一些注释列表（模式物种不需要填写）。
　　**querySeqCOG: **COG分析的时候需要提供分析基因的蛋白序列信息 （模式物种不需要填写） 。
　　**inputData: **趋势总表GENETABLE（必填）。
　　**background: **分析物种的所有基因的列表（模式物种不需要填写）。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>可选多个blast物种。
<label id='speciesVersion'>版本：</label>参考序列的版本。
<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
<label id='blast'>Blast：</label>与非模式物种比对，增加注释量。
<label id='blastSpecies'>BlastSpecies：</label>可选多个blast物种。
<label id='goAlgorithm'>GoAlgorithm：</label>生成GO graph的方法。Novelgo：常规超几何分布，烈冰研发算法。
<div style="text-align:center">
<img data-src="2.png" width="350px" ></img>
</div>

<label id='analysisType'>Analysis Type：</label>选择分析类型。
　　　　　　 　GOAnalysis:只做GO分析；
　　　　　　 　Pathway：只做Pathway分析；
　　　　　　 　COG：原核蛋白同源性分析，只输出Pathway结果；
　　　　　 　　GOPATH：GO、pathway（推荐选择）；
　　　　　　　 ALL(NotRecommand)：所有都输出 GO、Pathway、COG（不推荐选择）。

<label id='cogType'>CogType：</label>COG_Prokaryotes 原核生物；
　　　　　  KOG_Eukaryotes  真核生物。
<label id='acclDColNum'>GeneColNum：</label>基因识别列。
<label id='valueColNum'>Log2FCColNum：</label>趋势分析/差异基因所在列。（通常Difgene中算法选择为DE，该列为5；算法选择为EB，该列为4）。
<label id='upValue'>CutOff>=：</label>上调基因差异倍数（根据ValueColNum 为fold change 或者logFC填写）。
<label id='downValue'>CutOff<=：</label>下调基因差异倍数（根据ValueColNum 为fold change 或者logFC填写）。
<label id='goLevelNum'>GoLevelNum：</label>选择输出GO的层级数。
<label id='clusterGoPath'>ClusterGoPath：</label>趋势类型GO类型。
<label id='isCombine'>IsCombine：</label>输入平台中未注释的文件。
　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**　　GO分析结果:**
　　GO是Gene ontology的缩写，GO数据库分别从功能、参与的生物途径及细胞中的定位对基因产物进行了标准化描述，即对基因产物进行简单注释，通过GO富集分析可以粗略了解差异基因富集在哪些生物学功能、途径或者细胞定位。GO分析还可看enrichment score，数值越大表示某个GO term越容易受到实验因素的影响。
<div style="text-align:center">
<img data-src="3.png" width="500px" ></img>
</div>
<div style="text-align:center">
<img data-src="4.png" width="500px" ></img>
</div>
**　　Pathway分析结果:**
　　Pathway指代谢通路，对差异基因进行pathway分析，可以了解实验条件下显著改变的代谢通路，在机制研究中显得尤为重要。对差异表达基因进行Pathway功能分析，并计算Pvalue进行显著性判断，Pvalue越小，表明该pathway变化越显著，并可对每条Pathway通路图进行展示，同时在相应的位置标注差异表达基因。
<div style="text-align:center">
<img data-src="5.png" width="550px"  ></img>
</div>
<div style="text-align:center">
<img data-src="6.png" width="550px" ></img>
</div>

