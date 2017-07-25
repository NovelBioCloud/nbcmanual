# GSEA
　　GSEA分析（Gene Set Enrichment Analysis），又称功能基因集富集分析，是目前非常常用的RNA表达分析手段。基因富集分析是分析基因表达信息的一种方法，富集是指将基因按照先验知识，也就是基因组注释信息进行分类。
　　2005年提出了基于基因集(gene set)定义的基因富集分析方法。首先要定义基因集，也就是基于我们的先验知识（基因组注释信息），将基因富集，可以想象成，用一堆代表基因功能的箱子（bin）把具有相同或相似功能的基因装起来，起到了降维的作用，当然，每个基因可能同时参与好几种功能。这样，得到这两组数据后，我们所分析的不是单个基因表达的差异，而是箱子与箱子之间的差异。由此，我们得到的数据更容易解释。
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　软件官网：http://software.broadinstitute.org/gsea/index.jsp
　软件下载地址：http://software.broadinstitute.org/gsea/downloads.jsp
　GASEA原理参考文献：
　　Gene set enrichment analysis: a knowledge-based approach for interpreting genome-wide expression profiles.Proc Natl Acad Sci U S A. 2005 Oct 25;102(43):15545-50. Epub 2005 Sep 30. 
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
　inFileName (TABLE)：表达值（需要提前进行GeneAnno操作，且为txt文件）
　GeneSet (TABLE)：GeneSet（格式同上文提到的gmx文件）


****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>

**GeneColNum：**输入gene所在列。
**DescriptionColNum：**Description所在列。
**PermutationType：**Phenotype labels:数据表达量表格的分组信息，包含总的分组名称数量，以及表达量报个每一列所属的分组。
　　　　　　　　　　Gene sets:基因集，包含挑选的基因，可以多个基因集在同一张表格中，tab分隔，输入文件为gmx时，每一列为一个Set，输入文件格式为gmt是，每一行为一个Set。
**MinSize：**最小基因数量。
**MaxSize：**最大基因数量。
**PlotTopSet：**画图的geneset数量。
**Collapse：**参数根据输入chip文件的格式选择或者不选，选择说明对chip文件进行处理（一般多为芯片的探针注释），不选代表不进行处理。

**文件对比：**加入对比两个组份。选择实验组与对照组比较。
　　　　　group1Array：选择对比组1；
　　　　　group2Array：选择对比组2；
　　　　　outFileArray：输出名称。
**containerNumber：**运行时，使用container数。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
　　运行后平台会自动生成Dataset，chipanno，groupset文件，并运行得到GSEA结果。
<div style="text-align:center"><img data-src="1.png" width="600px"></img>
</div>
<div style="text-align:center"><img data-src="2.png" width="600px"></img>
</div>
　　一般GSEA用于展示的结果主要包括，EnrichmentPlot，heatmap，以及分析结果的table。
Enrichment图如下：
<div style="text-align:center"><img data-src="3.png" width="600px"></img>
</div>
Heatmap图如下：
<div style="text-align:center"><img data-src="4.png" width="600px"></img>
</div>
