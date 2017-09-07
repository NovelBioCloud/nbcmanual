# GOTree
　　功能层次网络构建是基于GO的层次结构，将所有差异基因同时参与的显著性GO及其相互从属关系构建功能网络，从全局角度，系统地概括功能间相互作用关系及所属分层关系。
　　GO与GO之间是存在层级从属以及树状结构的，即我们可以通过对于显著性GO-Term进行树状图构建，并解析他们之间的关联性可以对于GO分析结果进行总结，将一个几十甚至上百个条目组成的显著性GO分析结果进行总结，并剔除并不重要的GO条目。
　　软件官网：http://www.geneontology.org/
 
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　InFile (TABLE):输入GO-Term表格,格式xlsx。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='cutoff'>PvalueCutOff：</label>P-value的阈值。
　<label id='SelectGO'>SelectGO：</label>如果输入的GO条目是人为手动选择的文件，需要选中该选项。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1.GoTerm.txt：GO-Term条目列表。
<div style="text-align:center">
<img data-src="1.png" width="500px" ></img>
</div>
&nbsp;
2.GoTree.txt： 每一个GO-Term相互之间的层级从属关系列表。
　　GC content为计算碱基G和C的数量总和占总的碱基数量的百分比。红线是实际情况，蓝线是理论分布。GC content曲线为正态分布，均值不一定在50%，而是由平均GC含量推断。
<div style="text-align:center">
<img data-src="2.png" width="650px" ></img>
</div>
