# GSEA
　　GSEA分析（Gene Set Enrichment Analysis），基因集富集分析，是目前非常常用的RNA表达分析手段。
　　**功能：**GSEA能够对不同层次、不同来源的数据进行整合，并在没有先验经验的情况下也能在表达谱整体层次上对上万条基因进行富集分析，从而为构建个体在不同生长发育阶段或者不同生理病理状态下的特征性基因模块及分子调控网络，提供了重要的启示及指导。
　　**使用软件：**GSEA：是麻省理工学院和哈佛大学的broad institute研究团队开发的一个针对全基因组表达谱芯片数据进行的分析工具。软件官网：http://software.broadinstitute.org/gsea/index.jsp
　
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451"> 应用范围**
　　一般的差异分析往往侧重于比较两组间的基因表达差异，集中关注少数几个显著上调或者下调的基因，这容易遗漏部分差异表达不显著却具有重要生物学意义的基因，忽略一些基因的生物特性、基因调控网络之间的关系及基因功能和意义等有价值的信息。而GSEA不需要指定明确的差异基因阈值，算法会根据实际数据的整体趋势，为我们提供一种合理的解决方法，即使在没有先验经验的情况下也能在表达谱整体层次上对多个基因进行分析，从而从数理统计层面把表达谱数据与生物学意义很好地衔接起来。

 ***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是带有基因注释的基因表达值文件。
　　**inFileName：**基因表达文件，由于GSEA只支持ASCII格式的文本文件，所以此处需要将基因表达数据整理在一个文本文件中，并需要将表达值列表中添加基因描述信息，如：
 <div style="text-align:center"><img data-src="5.png" width="500px" ></img>
</div>
**注意：**
1.输入文件需要有title行，对于title名称无特殊要求；
2.输入文件中要有“Description”(基因描述)这一列信息。
　　**GeneSet：**功能基因集文件，是位于MsigDB数据库（Molecular Signatures Database，分子标签数据库，该数据库中定义了已知的功能基因集合
  http://software.broadinstitute.org/gsea/msigdb
  ）中的各个信息文件，可有.gmx和.gmt两种格式。当功能基因集文件较多时，使用.gmt格式更便于保存，但当功能基因集文件数<256时，应用.gmx格式更利于发挥EXCEL的编辑优势。通常在GSEA网站可直接下载.gmt格式的功能基因集文件，如：
<div style="text-align:center"><img data-src="6.png" width="150px" ></img>
</div>

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　一般GSEA用于展示的结果主要包括，EnrichmentPlot，heatmap，以及分析结果的列表文件。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>

**GeneColNum：**输入gene所在列。
**DescriptionColNum：**基因Description所在列。
**PermutationType：**输入数据类型
　　　　　　　　　　Phenotype labels:数据表达量表格的分组信息，包含总的分组名称数量，以及表达量表格每一列所属的分组。
　　　　　　　　　　Gene sets:基因集，包含挑选的基因，可以多个基因集在同一张表格中，tab分隔，输入文件为gmx时，每一列为一个Set，输入文件格式为gmt时，每一行为一个Set。
**MinSize：**定义选择标准，功能基因子集中所含基因数最小值，默认值为15。
**MaxSize：**定义选择标准，功能基因子集中所含基因数最大值，默认值为5000。
**PlotTopSet：**画图的geneset数量。
**Collapse：**参数根据输入chip文件的格式选择或者不选，选择说明对chip文件进行处理（一般多为芯片的探针注释），不选代表不进行处理。

**文件对比：**加入对比两个组份。选择实验组与对照组比较。
　　　　　group1Array：选择对比组1；
　　　　　group2Array：选择对比组2；
　　　　　outFileArray：输出名称。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
　　index.html：结果分析报告，报告中提供了相关的统计数据以及相关的超链接，通过超链接可以进一步得到更详细的分析结果。
　　点击结果报告中的“Snapshot of enrichment results”中的“Snapshot”超链接就可以打开Enrichment图，图上部的曲线表示动态ES（Enrichment Score，富集分数）值，最高点表示此通路的ES值。图的中间部分表示该通路中基因的排序位置，黑竖线表示在此通路中出现的基因，所有的富集分数一开始都是0。如：

<div style="text-align:center"><img data-src="3.png" width="500px"></img>
</div>
点击报告中“Heat map and gene list correlation profile for all feature in the dataset”中的“Heat map and gene list correlation”超链接就可以打开基因的heatmap图， 如：

<div style="text-align:center"><img data-src="4.png" width="500px"></img>
</div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　GSEA：Gene Set Enrichment Analysis，基因集富集分析，能够对不同层次、不同来源的数据进行整合，并在没有先验经验的情况下也能在表达谱整体层次上对上万条基因进行富集分析，从而为构建个体在不同生长发育阶段或者不同生理病理状态下的特征性基因模块及分子调控网络，提供了重要的启示及指导。基因功能富集分析作为一种革命性的生物芯片分析方法，它通过生物学与数学的整合而形成了目前解决基因芯片海量数据的最佳方法，使得我们能很方便、快捷地了解隐藏在海量芯片数据背后的生物学意义。其中肿瘤、糖尿病、中医症候、药物研发等领域都有广阔的应用。
　　GSEA的基本思想是使用预定义的基因集（通常来自功能注释或先前实验的结果），将基因按照在两类样本中的差异表达程度排序，然后检验预先设定的基因集合是否在这个排序表的顶端或者底端富集。基因集合富集分析检测的是基因集合而不是单个基因的表达变化，因此可以包含一些细微的表达变化，得到更为理想的结果。
　　ES：是GSEA分析的原始结果，它反映的是将全部数据排序后，在此序列的前部或者后部一个功能基因集富集的程度。ES值计算的基本原理是扫描排序序列，当出现一个功能基因集中的基因时，就增加ES值，反之，就减少ES值，所以在整个扫描过程中，ES是一个动态的值。最终ES值的确定是将数据排序序列所在位置定义为0，ES值定义为距离排序序列的最大偏差。当ES值为正，表示某一功能基因集富集在排序序列的前方，当ES值为负，表示某一功能基因集富集在排序序列的后方。
　　NES：是功能基因集富集分析结果的主要统计量。NES是建立在数据文件集所有随机组合得到的ES平均值的基础上，因此，数据随机组合方法，随机组合次数，或表达数据文件集大小的改变都会影响NES。GSEA定义NES公式为：
  **NES=某一功能基因集的ES/数据文件集所有随机组合得到的ES的平均值**

**参考文献：**
　1.	Subramanian A, Tamayo P, Mootha VK, Mukherjee S, Ebert BL, et al. Gene set enrichment analysis: a knowledge-based approach for interpreting genome-wide expression profiles. Proc Natl Acad Sci U S A. 2005;102:15545–15550. [PMC free article] [PubMed]
　2.	Ackermann M, Strimmer K. A general modular framework for gene set enrichment analysis. BMC Bioinformatics. 2009;10:47. [PMC free article] [PubMed]

　3.	Shi J, Walker MG. Gene set enrichment analysis (GSEA) for interpreting gene expression profiles. Current Bioinformatics. 2007;2:133–137.
