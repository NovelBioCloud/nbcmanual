# EnrichmentPlot
　　用于绘制GO或者Pathway的富集性散点图。
**功能：**
　根据GO功能或者Pathway代谢通路富集分析列表绘制富集性散点图。
**使用软件：**
　　**R：**R是用于统计分析、绘图的语言，是一个用于统计计算和统计制图的优秀工具。该task使用R语言中的ggplot2绘图包进行各种图的绘制。官网：https://www.r-project.org/
**应用范围:**
　　可应用于GO功能或者Pathway代谢通路富集分析列表。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于GO/Pathway分析产生的基因GO/Pathway富集性分析列表。
　**inputData：**基因GO/Pathway富集性分析列表，该输入文件的格式为：
<div style="text-align:center"><img data-src="2.png" width="500px"></img></div>

　　注意：其中GOID、GOTerm、DifGene、GeneInGO以及P-Value这几列是必须要有的，并且要求DifGene在第三列，GeneInGO在第五列，P-value值在第七列，第四列和第六列信息可以有数据信息也可以是空值，第七列之后的信息可有可无。
&nbsp;
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
绘制的富集性散点图。散点图是KEGG富集分析结果的图形化展示方式。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='title'>Title：</label>输入的数据类型，其选项有：
　　　　GO：输入的数据为GO功能注释列表
　　　　Pathway：输入的数据为Pathway注释列表

　<label id='sheet'>需要绘图的sheet位于：</label>需要绘制的sheet位于excel中的第几个sheet中。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　“\*. _GO/Pathway_Enrichment.png”：绘制的富集性气泡图。图中GO/KEGG富集程度通过Rich factor、P_value和富集到此通路上的基因个数来衡量。其中Rich factor指该GO/pathway中富集到的差异基因个数与注释基因个数的比值。Rich factor越大，表示富集的程度越大。我们挑选了富集最显著的20条GO/pathway条目在该图中进行展示，若富集的GO/pathway条目不足20条，则全部展示。以“*. _Pathway_Enrichment.png”为例，展示图如下所示：
<div style="text-align:center"><img data-src="1.png" width="400px" ></img>
</div>

