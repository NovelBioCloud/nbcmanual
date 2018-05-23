# Ballgown

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;重构转录本以后需要统计基因以及转录本的表达量。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;计算基因和转录本的表达量。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**Ballgown：**Ballgown 发表在《Nature Biotechnology》，是进行差异表达分析的工具。它可以利用RNA-Seq的数据，预测基因和转录本的差异表达。
**软件官网：** 
https://www.bioconductor.org/packages/release/bioc/html/ballgown.html
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通常是先将RNA-Seq数据使用StringTie软件添加-B参数,输出的结果文件作为Ballgown的输入文件来做进一步处理。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;RNA-Seq数据使用StringTie添加-B参数直接生成Ballgown的输入文件，如果是Cufflinks的输出结果，需要使用Tablemaker生成Ballgown的输入文件。
**inputFile：**由于该软件的输入文件是文件夹路径，而目前我们这个模块还无法拖入文件夹，所以目前的处理方法是，在输入文件夹的同路径下配置一个prefix.flag文件，拖入该文件即可。 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;其输入文件夹中一种有5个文件，分别是：
e_data.ctab：外显子水平表达量；
i_data.ctab：内含子水平表达量；
t_data.ctab：转录本水平表达量；
e2t.ctab：外显子与转录本的对应关系；
i2t.ctab：内含子与转录本的对应关系。
***
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　	基因表达量和转录本表达量统计结果。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**containerNumber：**设置task运行时使用的container数。
***
 #### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
（1）\*.ballgown.Exp.txt：基因表达量统计结果列表；
（2）*.Data.ballgown.FPKM.txt：转录本表达量统计结果列表。
***
**参考文献**
1.	Frazee AC, et al. Ballgown bridges the gap between transcriptome assembly and expression analysis. Nat Biotechnol. 2015; 33:243–246. [PubMed: 25748911]


