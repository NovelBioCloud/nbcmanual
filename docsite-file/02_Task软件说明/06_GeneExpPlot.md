# GeneExpPlot
　　绘制所有基因的FPKM值的分布图以及盒形图，对不同实验条件下的基因表达水平进行比较。对于同一实验条件下的重复样品，最终的RPKM值为所有重复数据的平均值。
**功能：**
　　绘制基因表达量的盒形图、密度分布图、样品相关性图。
**使用软件：**
　　R：R是用于统计分析、绘图的语言，是一个用于统计计算和统计制图的优秀工具。该task使用R语言中的ggplot2绘图包进行各种图的绘制。
**官网：**https://www.r-project.org/
**应用范围：**
　　可以针对基因的表达量值绘制盒形图、密度分布图以及样品相关性图，注意，只能对输入样品个数大于1的数据绘制样品相关性图。
  
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于SamAndRPKM的基因表达值列表文件，也可以是外源基因表达列表文件。
**inputData：**基因表达值列表，该输入文件的格式为：
　　常用的表达基因列表，如：
<div style="text-align:center"><img data-src="4.png" width="500px"></img></div>　　注意：其中基因表达值要求必须位于第三列以及第三列之后列。
  
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　绘制出的盒形图（如果选中绘制）、密度分布图（如果选中绘制）、相关性图（如果选中绘制）的png文件。


***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='isPlotBoxplot'>绘制盒形图：</label>是否绘制盒形图，选中表示绘制盒形图，否则不绘制。
　<label id='isPlotDensityDistribution'>绘制密度分布图：</label>是否绘制密度分布图，选中表示绘制密度分布图，否则不绘制。
　<label id='isPlotSampleCorrPlot'>绘制样品相关性图：</label>是否绘制样品相关性图，选中表示绘制品相关性图，否则不绘制。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**

　 1)RPKMBox.png ：是基因表达量FPKM值的盒形图。是不同实验条件下基因表达水平比对图，横坐标为样品名称，纵坐标为log10(FPKM),每个区域的盒形图对五个统计量，从上到下分别为最大值、上四分位数、中值、下四分位数、最小值。该图从表达量的总体的离散程度来衡量各样品之间的差异。如：
 <div style="text-align:center">
<img data-src="2.png" width="300px" height="300px" ></img>
</div>
　2)density.png：为基因表达量RPKM值的密度分布图。通过RPKM值来量化基因的表达水平，RPKM能消除基因长度和测序数据量差异对计算基因表达的影响，计算得到的基因表达量可直接用于比较不同样品间的基因表达差异。横坐标表示样品表达量RPKM的对数值，纵坐标表示对应的密度值。如：
 <div style="text-align:center">
<img data-src="1.png" width="300px" height="300px" ></img>
</div>
　3)Corr.png：是样品相关性图。相关分析是研究现象之间是否存在某种依存关系，并对具体有依存关系的现象探讨其相关方向以及相关程度，是研究随机变量之间的相关关系的一种统计方法。横坐标、纵坐标为样品名称，每一个方块为两个样品之间的皮尔森相关系数的平方，颜色越深相关性越高。如：
<div style="text-align:center">
<img data-src="3.png" width="300px" height="300px" ></img>
</div>
　　　