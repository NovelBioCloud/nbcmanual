# PeakStatistics
　　Peak calling是一种用于鉴定ChIP-Seq或MeDIP-Seq所得到的比对读段富集在基因组哪些区域的计算方法。当免疫沉淀的蛋白质是一种转录因子时， DNA的富集区域就是这种转录因子的结合位点（TFBS）。该模块就是对Peak calling所富集的DNA区域在染色体结构上的分布进行统计。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;统计peak在参考基因组结构上的分布情况。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**PeakStatistics：**该软件由NovelBio编写java代码开发而成，用于统计peak在参考基因组结构上的分布。
**应用范围：**
	&nbsp;&nbsp;&nbsp;&nbsp;根据peak calling的结果列表，统计peak在基因组结构上的分布情况。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是Peakcalling的结果表格文件。
**inFileArray：**Peakcalling的结果表格文件，如：*_peaks.loc.xls
<div style="text-align:center">
	<img data-src="1.jpg" width="800px" ></img>
</div>
注意：
1.其中必须要有title行，对于title名称无特殊要求；
2.输入文件至少要有两列信息，即染色体信息与峰值（summit），其他信息可有可无。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;peak在参考基因组结构上的分布统计表（txt）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。
**转录起始位点-上游：**选定参考基因组转录起始范围上游。
**转录起始位点-下游：**选定参考基因组转录起始范围下游。
**转录终止位点-上游：**选定参考基因组转录终止范围上游。
**转录终止位点-下游：**选定参考基因组转录终止范围下游。
**染色体列号：**表格中染色体号对应列数。
**Peaksummit位点：**表格中Peaksummit对应列数。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\*peaks.gene_structure.txt：**得到peak区域在参考基因组上的结构分布。
<div style="text-align:center">
	<img data-src="2.jpg" width="600px" ></img>
</div>&nbsp;

