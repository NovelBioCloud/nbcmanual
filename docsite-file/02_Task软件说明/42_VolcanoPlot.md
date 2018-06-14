# VolcanoPlot
　　用于显示两组样品数据的显著性差异，RNA-Seq中，火山图显示了两个主要的指标：fold change和校正后的p value，利用T检验分析出两样本间显著差异表达的基因后，以log2(fold change)为横坐标，以T检验显著性检验p值的负对数-log10(p)为纵坐标。
**功能：**
　　根据差异基因列表绘制火山图。
**使用软件：**
　　R：是用于统计分析、绘图的语言，是一个用于统计计算和统计制图的优秀工具。该task使用R语言中的ggplot2绘图包进行各种图的绘制。软件官网：https://www.r-project.org/
**应用范围：**
　　对所有差异基因绘制火山图。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于DifGene计算出来的所有差异基因的列表，也可以是外源的差异基因列表。
　　**inputData：**所有差异基因列表，该输入文件的格式为：
  <div style="text-align:center"><img data-src="2.png" width="400px" ></img></div>
　　注意：
　　1.其中基因名称列、Log2FC和FDR（或者P-value），这三列是必须要有的，其他列信息可有可无。
　　2.要求列表中必须要有title行，title名称无特殊要求。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　绘制的火山图(png) 文件。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='logFC'>Log2FC所在列：</label>输入的差异基因列表中，Log2FC（即，以2为底，实验组和对照组信号值差异倍数Fold Change的对数）所在的列数。
<label id='logFcCutoff'>Log2FC阈值：</label>Log2FC的阈值设定。一般情况下设置为1，当Log2FC=1时，表示基因的差异倍数（Fold change）为2。绘制火山图时会根据该值和后面的参数P-value值，将基因分为是否为显著性差异基因，并在图中以不同的颜色表示（如：Log2FC>=1并且P-value<0.05，的基因为显著性差异基因，在图中用红色或蓝色点表示；红色表示显著性上调基因，蓝色表示显著性下调基因，灰色则表示为非显著性差异的基因）。
<label id='fdr'>PvalueFdr所在列：</label>输入的差异基因列表中，FDR或者P-value所在的列数。
<label id='pvalueFdr'>PvalueFdr：</label>选择使用P-value还是FDR进行差异阈值设定，用来结合上面的“Log2FC阈值”参数，判断基因是否为显著性差异基因。
<label id='pvalueCutoff'>PvalueFdr阈值：</label>差异的Pvalue或Fdr阈值设定，一般情况下设置为0.05，也可以根据显著性差异基因个数情况进行适当的调整。
<label id='xlimit'>X轴limit：</label>X轴最大显示数的绝对值。如当设置为4时，X轴的取值范围为-4~4。
<label id='Ylimit'>Y轴limit：</label>Ｙ轴最大显示数的绝对值。如当设置为10时，Y轴的取值范围为-10~10。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　Volcano.png：绘制的火山图。
　　结果得到两样本间的差异表达基因后，以log2（fold change）为横坐标，以T检验显著性检验P值的负对数-log10（P-value）为纵坐标，绘制火山图，在绘图过程中，根据一定的筛选条件（如大于2倍变化且P<0.05）,筛选出显著差异表达的基因，然后分别使用红色和蓝色表示出显著性上调（红色）基因和显著性下调（蓝色）基因，灰色表示非显著性基因。如下图所示：
<div style="text-align:center">
<img data-src="1.png" width="400px" ></img>
</div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**
　　用火山图推断差异基因的整体分布情况，从差异倍数（Fold change）和显著水平（P-value）两个水平进行评估。一般以log2（Fold change）为横坐标，以T检验显著性检验P值的负对数-log10（P-value）为纵坐标，利用一定的筛选条件（如大于2倍变化且P<0.05）,可以筛选出显著差异表达的基因，进行后续研究。
　　软件官网：http://chipster.csc.fi/manual/plot-volcano.html


