# GOTree
　　GOTree,即功能层次网络的构建是基于GO的层次结构，将所有差异基因同时参与的显著性GO依据其相互从属关系构建功能网络，从全局角度，系统地概括功能间相互作用关系及所属分层关系。
　　GO与GO之间存在层级从属关系，我们可以通过对显著性GO-Term进行树状图构建，来解析他们之间的关联性，并对GO分析结果进行总结，重点关注那些由几十甚至上百个条目组成的GO条目簇，剔除那些散在的并不重要的GO条目。
**功能：**
　　获取每个GO-Term相互之间的层级从属关系列表。
**应用范围**
　　通常应用于显著性富集的GO Term，根据GO数据库中的GO Term之间的关系数据记录，整理出输入的显著性富集GO Term的相互之间层级关系。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于GOPathway的GO分析结果列表，也可以是外源GO Term列表文件。
　**InFile：**GO Term列表文件，该输入文件可以是以下两种类型，
　1.输入文件只有三列，如：
<div style="text-align:center"><img data-src="4.png" width="500px" ></img>
</div>
　　注意：第三列“Style”，表示该条GO Term是上调基因富集（Up）、下调基因富集（Down）还是上下调基因都有富集（all）;该值也可以是趋势分析结果中，趋势基因所在的序列号（如： 1、2等），表示，该GO Term是趋势基因富集的GO条目。
  
　2.GOPathway的输出结果列表，通常情况下是GO-Analysis_BP.xlsx，文件格式如下： 
  <div style="text-align:center"><img data-src="5.png" width="500px" ></img>
</div>

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　\*_GoTree.xls：每一个GO-Term相互之间的层级从属关系列表。如：
<div style="text-align:center"><img data-src="4.png" width="500px"></img></div>　　该列表可以作为Cytoscape的输入，用来绘制GO关系网络图。
<hr/>**<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='cutoff'>PvalueCutOff：</label>P-value的阈值，当输入文件列表为GOPathway的输出结果列表（\*GO-Analysis_BP.xlsx），即列表中含有富集分析的P-vaule值时，设置该阈值，task会自动筛选显著性富集的GO Term，对于筛选得到的显著性富集的GO Term进行GOTree的分析。
　<label id='SelectGO'>SelectGO：</label>如果输入的GO Term是人为手动选择的文件时，需要选中该选项，表示不用进行Pvalue值的过滤，使用所有输入的GO Term进行GOTree的分析。
 ***
**<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
　　\*_GoTerm.xls：GO Term条目列表, 当输入文件是\*GO-Analysis_BP.xlsx时，会产生这个结果文件，用来生成最终的层级从属关系列表（即，*_GoTree.xls），当输入文件是手动筛选的GO Term时（即，输入文件格式为“输入文件”中描述的第一种格式），不会生成该结果文件。该文件格式为：
<div style="text-align:center"><img data-src="7.png" width="500px" ></img></div>
　　其中，第一列表示GO ID；第二列表示GO Term;第三列“Style”，表示该条GO Term是上调基因富集（Up）、下调基因富集（Down）还是上下调基因都有富集（all）;该值也可以是趋势分析结果中趋势基因所在的序列号（如：1、2等），表示，该GO Term是趋势基因富集的GO条目。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**
　　GO：Gene Ontology，简称GO，是一套国际标准化的基因功能描述的分类系统，从1988年开始，它的应用范围从刚开始的三个模式生物数据库的整合:FlyBase (果蝇数据库Drosophila),Saccharomyces Genome Database (酵母基因组数据库SGD)、Mouse Genome Database(小鼠基因组数据库MGD)，经过不断发展扩大，现已扩展到涵盖几乎所有物种基因组功能注释的数据库整合平台。
　　GO具有三大类：
　生物过程biological process：生物学过程系指由一个或多个分子功能有序组合而产生的系列事件；
　分子功能molecular function：描述基因产物个体的功能，如与碳水化合物结合、ATP水解酶活性等；
　细胞组分cellular component：基因产物位于何种细胞器或基因产物组中（如糙面内质网，核或核糖体，蛋白酶体等）。
　　官网 http://geneontology.org/
