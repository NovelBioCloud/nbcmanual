# Lnclocation

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;提取lncRNA在基因组上的位置信息，其信息包括与lncRNA相关的mRNA、上下游基因、以及与上下游基因的距离等。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;获取lncRNA在基因组上的位置信息。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;由NovelBio编写的提取LncRNA在基因组上位置信息的软件。
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通常是差异LncRNA列表。
***

#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是差异表达的LncRNA列表。
　　**inFileName：**差异表达的LncRNA列表，或者仅有一列lncRNA名称的列表，如。
<div style="text-align:center">
	<img data-src="1.png" width="100px" ></img>
</div>
注意：
1.	要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
2.	输入表格中，必须要有如表中所示的第一列信息，其他信息可有可无。
***

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　	lncRNA位置信息结果列表（txt）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择基因的物种；
**版本：**选择基因的物种版本；
**数据库类型：**选择分析使用的基因组注释文件，同一版本的基因组数据，在不同数据库汇总记录的信息不同；
**上下游基因的距离：**lncRNA在基因组上距离上下游编码基因的距离；
**查询方式：** 查找信息的方式，其值有：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ByName：根据lncRNA名称；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ByLoc：根据lncRNA位置。
**LncID列号：**当“查询方式”选择为“ByName”时，显示该参数，在此处设置lncRNA名称在输入列表文件中所在的列数；
**染色体列号：**当“查询方式”选择为“ByLoc”时，显示该参数，在此处设置染色体号在输入列表文件中所在的列数；
**开始列号：**当“查询方式”选择为“ByLoc”时，显示该参数，在此处设置lncRNA起始位置在输入列表文件中所在的列数；

**结束列号：**当“查询方式”选择为“ByLoc”时，显示该参数，在此处设置lncRNA终止位置在输入列表文件中所在的列数；
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　	**\*.txt：**lncRNA位置信息结果列表，如：
 <div style="text-align:center">
	<img data-src="2.png" width="800px" ></img>
</div>
各列详细信息说明如下：
<div style="text-align:center">
	<img data-src="3.png" width="500px" ></img>
</div>
***






