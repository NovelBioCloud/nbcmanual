# ClusterPlot　
　　为了全面的直观的展示样品之间的关系及差异情况，将表达基因做聚类分析。用挑选的差异基因的表达情况来计算样品直接的相关性。一般来说，同一类样品能通过聚类出现在同一个簇（cluster）中，聚在同一个簇的基因可能具有类似的生物学功能。
　　在RNA-seq中热图的作用为：
　　1）直观呈现多样本多个基因的全局表达量变化；
　　2）呈现多样本或多基因表达量的聚类关系。
**功能：**
　　该模块功能为根据基因表达值绘制基因聚类图。
**使用软件：**
　　R：是用于统计分析、绘图的语言，是一个用于统计计算和统计制图的优秀工具。该task使用R语言中的gplots包中的heatmap.2函数。
  软件官网：
  https://www.rdocumentation.org/packages/gplots/versions/3.0.1/topics/heatmap.2
**应用范围：**
　　可应用于基因表达值列表。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于DifGene产生的差异表达基因列表。
**inputData**：差异表达基因列表，通常情况下，是对差异表达基因绘制聚类图，该输入文件可仅含有基因名称一列信息，其他信息可有可无，如：
<div style="text-align:center"><img data-src="2.png" width="100px"></img></div>
注意：
1.要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
输入表格中，第一列为基因名称列是必须要有的，其他列信息可有可无。
**RPKMFile**：输入所有基因的RPKM值。
**用途：**用于从中提取聚类基因的基因表达RPKM值。
**格式：**格式如下表格所示：
<div style="text-align:center"><img data-src="3.png" width="600px"></img></div>


注意：
1.要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
2.输入表格中，第一列为基因名称，从第二列开始的之后列都是基因在不同样本中的表达值。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　绘制的基因表达聚类图。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='isFilterByPre'>Filter by Present：</label>是否过滤掉基因缺少值的在所有样品的比例大于present设置比例的基因。结合下面的“**present**”参数使用。
　<label id='present'>present：</label>百分比值，作为基因在样品中缺少值的百分比阈值。结合上面的“**Filter by Present**”参数使用。
　<label id='isFilterBySD'>Filter by SD：</label>是否过滤掉基因标准方差值小于SD所设置的数值的基因。结合下面的“SD”参数使用。
　<label id='sd'>SD：</label>基因在所有样本中的表达值的标准方差阈值，SD值表示同一基因在不同生物学重复样本间表达水平的差异，结合上面的“**Filter by SD**”参数使用。
　<label id='isFilterByAbs'>Filter by Abs：</label>是否过滤掉表达样本个数少于sample count所设置数值，而表达绝对值大于Abs Value所设置数值的基因，结合下面的“**sample count**”和“**Abs Value**”这两个参数使用。
　<label id='number'>sample count：</label>某基因发生表达的样本个数阈值，结合上面的“**Filter by Abs**”和下面的 “**Abs Value**”参数使用。
　<label id='absValue'>Abs Value：</label>基因表达绝对值。结合上面的“**Filter by Abs**”和“**sample count**”参数使用。
　<label id='isLogTran'>Log Transform Data：</label>输入的基因表达值是否取log转换后，再进入下一步的聚类分析。
　<label id='normalizeGene'>Normalize Genes：</label>是否标准化基因，将每一行的所有数值都乘以一个标度因子S，使每一行的数值的平方和为1.0。
　<label id='normalizeArray'>Normalize Arrays：</label>是否标准化基因，将每一行的所有数值都乘以一个标度因子S，使每一行的数值的平方和为1.0。
　<label id='disMethodRow'>rows Distance Method：</label>计算每一行一个基因在所有样品之间距离时采用的数学方法。
　<label id='disMethodCol'>cols Distance Method：</label>计算每一列单个样品中所有基因之间距离时采用的数学方法。
　<label id='clusterMethod'>Cluster Method：</label>聚类时采用的聚类算法。
　<label id='showRowName'>showRowName：</label>聚类图中是否显示每一行基因的名称。
　<label id='showColName'>showColName：</label>聚类图中是否显示每一列样品的名称。
**高级选项：**
　<label id='isFilterByDiffVal'>Filter by DiffVal：</label>是否过滤掉基因在所有样品中的最大表达值与最小表达值的差值大于Diff Value设置数值的基因。
　<label id='diffVal'>Diff Value：</label>一个基因在所有样本中的最大表达值与最小表达值的差值阈值。
　<label id='centerGenes'>Center Genes：</label>是否以基因为单位进行均一化。
　<label id='centerGeneMethod'>center Gene Method：</label>以基因为单位进行均一化时采用的方法，该参数的值为：
　　　　　　　　　　　　　Mean：均值。即，将每一行的所有值减去这一行的平均值，使这一行的数值相加为0。
　　　　　　　　　　　　　Median：中值。即，将每一行的所有值减去这一行的中位数，使这一行的中位数为0。

　<label id='centerArrays'>Center Arrays：</label>是否以样本为单位进行均一化。
　<label id='centerArrayMethod'>Center Array Method：</label>以样品为单位进行均一化采用的方法，该参数的值为：
　　　　　　　　　　　　　Mean：均值。即，将每一列的所有值减去这一列的平均值，使这一列的数值相加为0。
　　　　　　　　　　　　　Median：中值。即，将每一列的所有值减去这一列的中位数，使这一列的中位数为0。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
　“*.cluster.png”：绘制的基因聚类图。使用颜色（例如红绿的深浅）来展示多个样本多个基因的表达量高低。展示图如下所示： 

<div style="text-align:center">
<img data-src="ClusterPlot1.png" width="200px" height="500px" ></img>
</div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**

　　聚类可以实现将样本以及基因进行分组的目的，从数学的角度上讲，聚类得到的基因分组，一般是组内各成员在数学特征上彼此相似，但与其他组中的成员有差异。从生物学的角度讲，聚类分析方法所隐含的生物学意义或假设是组内基因的表达模式相似，它们可能有相似的功能。
　　大量功能相关的基因的确在相关的一组条件下有非常相似的表达模式，特别是被共同的转录因子共调控的基因，或者产物构成同一个蛋白复合体，或者参与相同的调控路径。因此，在具体的应用中，可以根据对相似表达模式的基因进行聚类，从而预测未知基因的功能。


