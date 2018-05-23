# CoExp
　　基因共表达网络（Coexpression Network）多是以基因间数据的相关性为基础而实现构建的。在基因共表达网络中，经常使用图模型来描述基因之间的关系。节点代表基因，线表示两个基因之间的共表达相互作用关系。共表达网络构建主要分两个步骤，一是对所有基因进行相似性度量；二是通过阈值的选择确定共表达网络的边界。
**功能：**
　　共表达网络图基于基因之间的共表达关系构建。根据基因在样本中的信号表达值，计算每两个基因之间的皮尔森（Pearson）相关系数，并设立阈值。当两基因之间的皮尔森相关系数超过阈值时，则认为该两基因之间存在共表达关系。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;由NovelBio编写的计算共表达关系的软件。
**应用范围：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通常会对差异表达基因进行共表达分析。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　该Task的输入数据是差异表达基因的原始表达值（RPKM，counts、信号值等）列表。
**inFileName：**差异表达基因的原始表达值（RPKM，counts、信号值等）列表。
<div style="text-align:center">
	<img data-src="1.png" width="500px" ></img>
</div>

***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;基因之间的Pearson相关系数列表(txt)文件。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　　<label id='threshold'>阈值：</label>p值和FDR值的阈值,，默认值为0.05。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　coExp.gene.txt：基因之间的Pearson相关系数列表，如：
<div style="text-align:center">
	<img data-src="2.png" width="500px" ></img>
</div>
各列说明如下：
<div style="text-align:center">
	<img data-src="3.png" width="300px" ></img>
</div>