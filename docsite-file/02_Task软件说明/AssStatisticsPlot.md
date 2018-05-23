# AssStatisticsPlot

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;目前可变剪接可以分为8种类型，根据不同类型的统计结果，使用图形化展示不同类型可变剪接的分布情况。
**功能：**
　&nbsp;&nbsp;根据可变剪接不同类型的统计结果，绘制不同类型可变剪接分布的柱状图。
**使用软件：**
　　**R：**R是用于统计分析、绘图的语言，是一个用于统计计算和统计制图的优秀工具。该task使用R语言中的ggplot2绘图包进行各种图的绘制。
官网：https://www.r-project.org/

**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;可以为可变剪接类型的统计结果，绘制柱状图。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该task的输入数据通常是来源于RNAalterSplice的结果统计列表文件，也可以是外源可变剪接不同类型的统计列表文件。
**inputData：**可变剪接不同类型的统计列表，该输入文件的格式为：
<div style="text-align:center">
	<img data-src="1.png" width="200px" ></img>
</div>
注意：
1.	要求输入的表格要有一行title，对于每列的title名称，无特殊要求； 
2.	表格至少要有两列信息，第一列为可变剪切的类型，第二列为不同类型对应的可变剪接数量。
***
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　绘制出的柱状图（png）文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**containerNumber：**设置运行过程中使用到的最多container数。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\*_statistics.ASS.png：**绘制出的柱状图（png）文件。如：
<div style="text-align:center">
<img data-src="2.png" width="300px" ></img>
</div>
***