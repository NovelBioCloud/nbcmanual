## **Degree**
　　Degree表示基因的核心度。在基因代谢通路中，一个基因往往参与多个信号通路，并且上下游的基因在不同的信号通路中也各不相同，degree表示每一个基因与其他基因的互作程度，Degree越高，说明这个基因在信号通路中越处于核心地位，也越为重要。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;根据基因与基因之间的关系列表统计每个基因的degree值。
**使用软件：**
由NovelBio编写的计算基因degree的软件。
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通常是先对差异表达基因进行基因互作网络（Gene-Act-Net）分析，得到基因之间的相互关系，然后基于这个基因之间的关系列表，进行基因degree的计算。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是差异表达基因进行基因网络分析得到的基因之间的相互关系列表。
**inFileName：**差异表达基因进行基因网络分析得到的基因之间的相互关系列表，如。
<div style="text-align:center">
	<img data-src="11.png" width="500px" ></img>
</div>
注意：
1.	要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
2.	输入表格中，必须要有如表中所示的前两列信息，即第一列基因名称和第二列基因名称，其他信息可有可无。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　	基因的degree结果(txt)文件。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择基因的物种，用于在结果表格中添加基因的description信息。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**degree.gene.xls：**基因的degree结果列表，如：
<div style="text-align:center">
	<img data-src="2.png" width="600px" ></img>
</div>
各列说明如下：
<div style="text-align:center">
	<img data-src="3.png" width="300px" ></img>
</div>
***
