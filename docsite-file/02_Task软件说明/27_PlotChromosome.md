# PlotChromosome
　　绘制测序Reads在染色体区域上的分布图。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**PlotChromosome：**该软件由NovelBio研发团队编写java代码开发而成，用于绘制reads在染色体上的分布图。
**应用范围**
	&nbsp;&nbsp;&nbsp;&nbsp;绘制Reads在染色体上的分布图。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是Samtools排序后的Bam文件。
**InputBam：**排序后的bam文件。SAM的全称是sequence alignment/map format，而BAM就是SAM的二进制文件（B取自于binary）。SAM文件详细说明，请见官方文档：http://samtools.github.io/hts-specs/SAMv1.pdf。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;reads在染色体上的整体分布图（png）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。　 
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，通过该参数可选择特定数据库gtf文件。
**InvNum：**取样区段，默认以10bp取样。
**Normalized type：**取样后得到数据的标准化方式。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\* _chrome\_distribution\_*.png：**测序Reads在染色体上的分布图。每条染色体生成一张图。
<div style="text-align:center">
	<img data-src="1.png" width="600px" ></img>
</div>