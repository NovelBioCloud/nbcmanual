# ClusterPlot
　　聚类可以实现将样品以及基因进行分组的目的，从数学的角度上讲，聚类得到的基因分组，一般是组内各成员在数学特征上彼此相似，但与其他组中的成员有差异。从生物学的角度讲，聚类分析方法所隐含的生物学意义或基因假设是组内基因的表达谱相似，它们可能有相似的功能。
　　大量功能相关的基因的确在相关的一组条件下有非常相似的表达谱，特别是被共同的转录因子共调控的基因，或者产物构成同一个蛋白复合体，或者参与相同的调控路径。因此，在具体的应用中，可以根据对相似表达谱的基因进行聚类，从而指派未知基因的功能。该模块功能为绘制聚类图。
　　为了全面的直观的展示样品之间的关系及差异情况，将表达基因做聚类分析。用挑选的差异基因的表达情况来计算样品直接的相关性。一般来说，同一类样品能通过聚类出现在同一个簇（cluster）中，聚在同一个簇的基因可能具有类似的生物学功能。
　　
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　在inputFile中输入diff基因列表；组名可修改，为输出后组名。 RPKMFile处输入FPKM列表，如all.fpkm.exp.txt；输入格式：txt、xls。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='isFilterByPre'>Filter by Present：</label>是否过滤掉基因缺少值的在所有样品的比例大于present设置比例的基因。
　<label id='present'>present：</label>百分比值，作为基因在样品中缺少值的百分比阈值。
　<label id='isFilterBySD'>Filter by SD：</label>是否过滤掉基因标准方差值小于SD所设置的数值的基因。
　<label id='sd'>SD：</label>基因标准方差。
　<label id='isFilterByAbs'>Filter by Abs：</label>是否过滤掉少于sample count(设置的数值)个表达值大于Abs Value(设置的数值)的基因。
　<label id='number'>sample count：</label>样品个数。
　<label id='absValue'>Abs Value：</label>基因表达绝对值。
　<label id='isLogTran'>Log Transform Data：</label>输入的基因表达值是否取log转换后，再进入下一步的聚类分析。
　<label id='normalizeGene'>Normalize Genes：</label>是否标准化基因。　
　<label id='normalizeArray'>Normalize Arrays：</label>是否标准化样品。
　<label id='disMethodRow'>rows Distance Method：</label>计算每一行一个基因在所有样品之间距离时采用的数学方法。
　<label id='disMethodCol'>cols Distance Method：</label>计算每一列单个样品中所有基因之间距离时采用的数学方法。
　<label id='clusterMethod'>Cluster Method：</label>聚类时采用的聚类算法。
　<label id='showRowName'>showRowName：</label>聚类图中是否显示每一行基因的名称。
　<label id='showColName'>showColName：</label>聚类图中是否显示每一列样品的名称。
**高级选项：**
　<label id='isFilterByDiffVal'>Filter by DiffVal：</label>是否过滤掉基因在所有样品中的最大表达值与最小表达值的差值大于Diff Value(设置的数值)的基因。
　<label id='diffVal'>Diff Value：</label>一个基因在所有样品中的最大表达值与最小表达值的差值。
　<label id='centerGenes'>Center Genes：</label>是否均一化基因。
　<label id='centerGeneMethod'>center Gene Method：</label>均一化基因采用的方法，中值（Median）还是均值（Mean）。
　<label id='centerArrays'>Center Arrays：</label>是否均一化列，即是否均一化样品。
　<label id='centerArrayMethod'>Center Array Method：</label>均一化样品采用的方法，中值（Median）还是均值（Mean）。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　cluster.png 绘制的聚类结果图：

<div style="text-align:center">
<img data-src="ClusterPlot1.png" width="200px" height="500px" ></img>
</div>



