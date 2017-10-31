# ReadsDisPlot
　　测序得到的reads比对到参考基因组序列上，将比对结果进行结构区域的分布统计后，使用该task可以绘制出reads 在基因组基因结构上的分布图，从图中可以方便的看出reads富集在那些基因结构中，以及在不同结构中的富集比例情况。
**功能：**
　　根据比对的结果的统计文件，绘制出reads 在基因组基因结构上的分布图，从图中可以直观的看出reads在基因组结构区域的分布情况，该结果也可以作为判断测序reads是否合格的一个参考。
**使用软件：**
　　**R：**是用于统计分析、绘图的语言，是一个用于统计计算和统计制图的优秀工具。该task使用R语言中的ggplot2绘图包进行各种图的绘制。软件官网：https://www.r-project.org/

**应用范围**
　　对reads在染色体上分布统计后得到的统计结果（即，对reads比对到参考基因组上之后得到的Bam文件进行统计后得到统计结果）绘图。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于SamAndRPKM的reads在基因组结构上分布的统计结果文件，也可以是外源的reads在基因组结构上分布的统计结果文件。
　　**inputData：**reads在基因组结构上分布的统计结果文件，该输入文件的格式为：
<div style="text-align:center"><img data-src="2.png" width="500px" ></img></div>


　　注意：在绘图的结果文件中，我们不显示第4行和第10行的数据信息。
  
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　绘制reads 在基因组基因结构上的分布图(png文件)。



****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　　<label id='containerNumber'>containerNumber：</label>container的运行个数，此处为空时，表示为默认值，默认值为4个。
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　geneStructure.png 绘制的结果图，X轴表示基因结构，Y轴表示分布在每个基因结构上的reads数/10000，如：

<div style="text-align:center">
<img data-src="1.png" width="320px" ></img>
</div>