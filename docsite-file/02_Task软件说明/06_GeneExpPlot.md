# GeneExpPlot
　　所有基因的FPKM的分布图以及盒形图对不同实验条件下的基因表达水平进行比较。对于同一实验条件下的重复样品，最终的RPKM为所有重复数据的平均值。
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**

**1.盒形图：**FPKM盒形图为不同实验条件下基因表达水平比对图，横坐标为样品名称，纵坐标为log10(FPKM),每个区域的盒形图对五个统计量，从上到下分别为最大值、上四分位数、中值、下四分位书、最小值。改图从表达量的总体的离散角度来衡量各样品之间的差异。
**2.密度分布图：**通过RPKM来量化基因的表达水平，RPKM能消除基因长度和测序量差异对计算基因表达的影响，计算得到的基因表达量可直接用于比较不同样品间的基因表达差异。横坐标表示样品表达量RPKM的对数值，纵坐标表示对应的密度值。
**3.相关性图：**相关分析是研究现象之间是否存在某种依存关系，并对具体有依存关系的现象探讨其相关方向以及相关程度，是研究随机变量之间的相关关系的一种统计方法。横坐标、纵坐标为样品名称，每一个方块为两个样品之间的皮尔森相关系数，颜色越深相关性越高。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　在inputFile处，输入基因表达量fpkm.exp.txt。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='isPlotBoxplot'>绘制盒形图：</label>是否绘制盒形图。
　<label id='isPlotDensityDistribution'>绘制密度分布图：</label>是否绘制密度分布图。
　<label id='isPlotSampleCorrPlot'>绘制样品相关性图：</label>是否绘制样品相关性图。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　RPKMBox.png ： 绘制的盒形图。
　density.png：绘制的PRKM密度图。
　Corr.png：绘制的样品相关性图。

　　　盒形图：
<div style="text-align:center">
<img data-src="2.png" width="300px" height="300px" ></img>
</div>
　　　PRKM密度图：

<div style="text-align:center">
<img data-src="1.png" width="300px" height="300px" ></img>
</div>
　　　样品相关性：

<div style="text-align:center">
<img data-src="3.png" width="300px" height="300px" ></img>
</div>
