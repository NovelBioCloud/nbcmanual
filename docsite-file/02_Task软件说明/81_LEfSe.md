# LEfSe
　　LefSe（LDA Effect Size）分析即组间群落差异分析，可以实现多个分组之间的比较，还可以在分组比较的内部进行亚组比较分析，从而找到组间在丰度上有显著差异的物种（即biomaker）。利用LEfSe 软件进行数据分析，并采用LDA 值分布柱状图和进化分支图(系统发育分布图)来展示LEfSe的统计结果。为进一步挖掘分组样品间的群落结构差异，选用T-test、Metastats、Anosim和MRPP等统计分析方法对分组样品的物种组成和群落结果进行差异显著性检验。同时，结合环境因素进行CCA/RDA分析和多样性指数与环境因子的相关性分析，得到显著影响组间群落变化的环境影响因子。
**功能：**
　		在物种分类的所有水平上（门纲目科属种），采用线性判别分析（LDA），估算每个物种丰度对差异效果影响的大小，找出对样品差异产生显著性影响的物种。
**LEfSe分析原理：**
&nbsp;&nbsp;&nbsp;&nbsp;主要分为以下三步，如下图所示：
<div style="text-align:center">
	<img data-src="1.png" width="500px" ></img>
</div>
（a）	首先在多组样本中采用非参数因子Kruskal-Wallis秩和检验检测不同分组间丰度差异显著的物种；
（b）	然后用成组的Wilcoxon秩和检验，对上一步中获得的显著差异物种进行组间差异分析；
（c）	最后用线性判别分析（LDA）对数据进行降维，并评估差异显著物种对样品组间差异的影响力（即LDA score）。
**使用软件：**
　　**LEfSe：**LEfSe软件用于发现两组或两组以上的biomarker，主要是通过非参数因子Kruskal-Wallis秩和检验来实现。。
**软件官网：**
https://bitbucket.org/biobakery/biobakery/wiki/lefse
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;在组与组之间寻找具有统计学差异的Biomarker，即组间差异显著的物种。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是Taxonomy_Plot的结果文件，如：ForLefse.txt。
**InputFile：**各个样本分类汇总结果列表，通常Taxonomy_Plot的结果文件ForLefse.txt是作为该task的输入文件。
格式如下：
<div style="text-align:center">
	<img data-src="2.png" width="600px" ></img>
</div>
&nbsp;&nbsp;&nbsp;&nbsp;其中前两行为title信息，第一行为样本分组信息，第二行为样品ID，建议表格第一列title，如图中表格设置。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;LDA值分布图（png）和进化分支图（png）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**Normalization Value：**标准值，通过将输入的丰度值与该标准值相乘，使得丰度值变大，默认值为30000。
**AnovaAlphaValue: **Kruskal-Wallis秩和检验筛选biomarker的p-value值，默认值为0.05。
**WilcoxonAlphaValue：**两组组间Wilcoxon秩和检验筛选biomarker的p-value值，默认值为0.05。
**LDAValue：**对LDA值取对数后的最小绝对值，默认值为2。
**Strategy for multi-class analysis：**设置测试运行模式，其选项有one-against-one（比较严格）和one-against-all（不太严格），默认值为：one-against-all。
**MaxLevel：**绘制进化分布图时，在图中显示的最多物种分类级别。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
1)	**\* _res.png：**LDA值分布柱状图，展示了LDA score大于设定值的物种，即具有统计学差异的biomaker。展现不同组中丰度有显著差异的物种，柱状图的长度代表显著差异物种的影响力大小。
<div style="text-align:center">
	<img data-src="5.jpg" width="300px" ></img>
</div>
2)	**\* _cladogram.png：** 进化分支图，由内至外辐射的圆圈代表了由门至属（或种）的分类级别。在不同分类级别上的每一个小圆圈代表该水平下的一个分类，小圆圈直径大小与相对丰度大小呈正比。
<div style="text-align:center">
	<img data-src="4.png" width="500px" ></img>
</div>
着色原则：无显著差异的物种统一着色为黄色，差异物种 Biomarker跟随组进行着色，红色节点表示在红色组别中起到重要作用的微生物类群，绿色节点表示在绿色组别中起到重要作用的微生物类群，其它圈颜色意义类同。图中英文字母表示的物种名称在右侧图例中进行展示。
***
**参考文献：**
1.	Segata N, Izard J, Waldron L, et al. Metagenomic biomarker discovery and explanation[J]. Genome Biol, 2011, 12(6): R60.


