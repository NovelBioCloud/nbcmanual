# PathActNet
　　信号通路调控网络构建（Pathway-Network）是根据所有差异基因同时参与的Pathway之间的相互调控关系构建信号通路调控网络，从系统的角度研究各个信号通路间的信号传导和调控过程，在多个显著性Pathway中发现受实验影响的核心Pathway,以及实验影响的信号通路之间的调控机理。
**功能：**
　　根据，KEGG数据库中信号通路上下游关系的信息，获取每个显著性信号通路之间的上下游关系。

**应用范围：**
　　通常应用于显著性富集的pathway。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于GOPathway的Pathway分析结果列表，也可以是外源Pathway列表文件。
　　　**InFile：**Pathway列表文件，该输入文件可以是以下两种类型，
　1.	输入文件只有三列，如：
<div style="text-align:center"><img data-src="3.png" width="550px" ></img></div>
　　注意：第三列“Style”，表示该条Pathway是上调基因富集（Up）、下调基因富集（Down）还是上下调基因都有富集（all）;该值也可以是趋势分析结果中，趋势基因所在的序列号如： 1、2等。表示，该GO Term是趋势基因富集的GO条目；特别注意的是，该列不能为空，也可以用“Na”，表示无任何意义。
　　2.	GOPathway的输出结果列表，通常情况下是.Pathway-Analysis.xlsx，文件格式如下：
<div style="text-align:center"><img data-src="4.png" width="550px" ></img></div>

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　PathActNet.xls：每一个Pathway-Term之间的信号上下游关系列表。如：
<div style="text-align:center"><img data-src="5.png" width="550px" ></img></div>

　　该列表可以作为Cytoscape的输入，用来绘制Pathway关系网络图。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='cutoff'>PvalueCutOff：</label>P-value的阈值，当输入文件列表为GOPathway的输出结果列表（* Pathway-Analysis.xlsx），即列表中含有富集分析的P-vaule值时，设置该阈值，task会自动筛选显著性富集的Pathway Term，对于筛选得到的显著性富集的Pathway Term进行PathActNet的分析。
　<label id='SelectPath'>SelectPath：</label>如果输入的Pathway Term是人为手动选择的文件时，需要选中该选项，表示不用进行Pvalue值的过滤，使用所有输入的Pathway Term进行PathActNet的分析。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　PathwayTerm.xls：Pathway Term条目列表。如：
<div style="text-align:center"><img data-src="6.png" width="500px" ></img></div>
　　其中，第一列表示Pathway ID；第二列表示Pathway Term;第三列“Style”，表示该条Pathway Term是上调基因富集（Up）、下调基因富集（Down）还是上下调基因都有富集（all）;该值也可以是趋势分析结果中，趋势基因所在的序列号（如： 1、2等），表示，该Pathway Term是趋势基因富集的Pathway条目。
  
 ***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明** 
**Pathway**
　　KEGG为计算机利用基因信息对更高层次和更复杂细胞活动和生物体行为作出计算推测。KEGG整合基因组、化学和系统功能信息的数据库，把从已经完整测序的基因组中得到的基因目录与更高级别的细胞、物种和生态系统水平的系统功能关联起来。KEGG的一个显著特点就是具有强大的图形功能，它利用图形而不是繁缛的文字来介绍众多的代谢途径以及各途径之间的关系，使研究的代谢途径直观全面。
　　软件官网：http://www.kegg.jp/kegg/pathway.html

