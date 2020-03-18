# **QuSAGE**

　 
### **工具介绍**

　  
#### **功能概述**

QuSAGE（Quantitative Set Analysis for Gene Expression, 基因表达定量集合分析），是一种以基因集合为单位，定量分析不同基因集合在不同样本中差异表达的分析方法。在QuSAGE算法中，生物学意义上有关联的基因组成基因集合作为一个整体，有别于每一个基因作为独立的个体进行数据分析。QuSAGE以概率密度函数（Probability Density Function, PDF）的形式量化基因集合的表达活跃程度，并通过概率密度曲线图（Probability Density Curve Plot）、置信区间图（Confidence Interval Plot），以及热图（Heatmap）等数据可视化方式，展示不同的基因集合在不同的样本间的表达情况。

#### **软件特点**

QuSAGE是用R语言开发的工具。
QuSAGE可通过PDF轻松获得基因集合的P-Value和置信区间。
QuSAGE算法采用方差膨胀因子（Variance Inflation Factor）来消除基因群内不同基因之间的相关性导致的假阳性错误。
用户可通过输入文件灵活自定义基因集合，以不同细胞类群作为样本，从而利用单细胞测序数据分析出不同细胞类群间不同基因集合的差异表达情况。

#### **软件官网**
http://clip.med.yale.edu/qusage/

　 
### **流程搭建**

　  
**上游工具**：Seurat_NormalizedForTab / SeuratFor10X_Normalized / Seurat_Cluster / Seurat_ReCluster 等
**下游工具**：ScHeatMap / QuSAGEPathFilter
**连接示例**：
<div style="text-align:center">
<img data-src="1.png" width="660px" ></img>
</div>
 

　 
### **文件传入**

　  
#### **输入文件 Input Expression Matrix File (required)**
基因表达矩阵文件（tsv文件）（必传文件）
参数说明：
基因表达矩阵文件可以从上游工具获取（例如Seurat_NormalizedForTab / SeuratFor10X_Normalized / Seurat_ReCluster中的SelectedNormalizedCounts.txt.bz2）。基因表达矩阵（Expresssion Matrix）是qusage算法的第1个传入参数。

　  
#### **输入文件 Input CellClusterLinkFile (required)**
细胞及细胞类群关联列表文件（tsv文件）（必传文件）
参数说明：
细胞及细胞类群关联列表文件可以从上游工具获取（例如Seurat_Cluster / Seurat_ReCluster中的GraphClust.Summary_Cell.txt）。细胞及细胞类群关联列表（Cell Cluster Link List）是qusage算法的第2个传入参数。用户也可以根据需要，自定义细胞与细胞类群的关联。当用户需要将细胞类群名称从原始的数字编号转换成有含义的字符串（例如Cluster 0改为B_cell），或将不同细胞类群合并（例如Cluster 0 2 3 合并为T_cell）或拆分（例如Cluster 0细分为CD4-T、CD8-T）时，都可以通过传入自定义细胞及细胞类群关联列表文件来实现。
注：
QuSAGE会将表达矩阵文件和细胞及细胞类群关联列表文件中的细胞取交集。

　  
#### **输入文件 Input GeneSetsFile (optional)**
基因集合文件（tsv文件/gmt文件）（选传文件）
参数说明：
基因集合（GeneSets）是qusage算法的第4个传入参数，可以通过tsv表格文件将基因集合数据传入工具。
tsv表格文件来源可以是其它工具的结果文件或手动生成。格式必须满足：每行前两列分别是基因集合名称和基因名称（二者是集合与所含元素的关系），表头不可缺少。示例：　  

|GeneSet Name|Gene Name|
|:----------:|:-------:|
|B_cell      |CD19     |
|B_cell      |CD79     |
|T_cell      |CD3      |
|...         |...      |
注：
1 支持同时传入多个tsv表格文件，工具会分析出每一个文件各自的结果。
2 如果点选了运行参数MSigDB GeneSetsFile或Novelbio GeneSetsFile中的gmt文件，此处可以不传入基因集合文件；反之，此处必须传入文件。

　 
### **参数设置**

<label id='qusageSpecies'> </label>
#### **运行参数 Species**
物种
参数说明：
支持物种包括但不限于：人、小鼠、大鼠
注：
分析人、小鼠、大鼠之外的物种，此参数不起作用。

<label id='MSigDB'> </label>
#### **运行参数 MSigDB GeneSetsFile (optional)**
基因集合文件（gmt文件）
参数说明：
来自MSigDB数据库的19个gmt文件，可以选择一个或多个。
注：
1 本参数和Input GeneSetsFile参数 / Novelbio GeneSetsFile参数都可以传入基因集合文件，三种方式至少选择一种，以保证传入基因集合文件总数不少于1。  
2 小鼠和大鼠gmt文件是通过转换人类gmt文件中同源基因名称所得，并非数据库原始数据。

<label id='NBgmt'> </label>
#### **运行参数 Novelbio GeneSetsFile (optional)**
基因集合文件（gmt文件）
参数说明：
烈冰科技技术部制作的gmt文件，可以选择一个或多个。
注：
1 本参数和Input GeneSetsFile参数 / MSigDB GeneSetsFile参数都可以传入基因集合文件，三种方式至少选择一种，以保证传入基因集合文件总数不少于1。  

<label id='curveNum'> </label>
#### **运行参数 MaxCurveNum**
最大曲线数量
参数说明：
本参数为结果文件概率密度曲线图与置信区间图中被展示基因集合的数量上限。例如：默认值50表示在基因集合数据表中按显著性排序，取不超过50个基因集合作图。

<label id='FontSize'> </label>
#### **运行参数 LabelFontSize**
标签字体大小
参数说明：
本参数为结果文件置信区间图中标签字体大小，默认3。

<label id='thread'> </label>
#### **运行参数 ThreadNum**
线程数
参数说明：
设置线程数，默认8线程

<label id='mem'> </label>
#### **运行参数 Memory(MB)**
内存（MB）
参数说明：
设置内存大小，默认36000MB

<label id='keepQuSAGErds'> </label>
#### **运行参数 keepQuSAGErds**
保留QuSAGE结果rds文件
参数说明：
qusage函数返回的R数据结构，可以直接用于生成QuSAGE结果图表。在重新运行Task时，保留QuSAGE_rds文件夹可以跳过qusage函数运算。

<label id='color'> </label>
#### **运行参数 Color**
配色
参数说明：
本参数控制热图配色。
默认为blue,white,red，表示低表达至高表达颜色从蓝经白到红渐变。支持自定义颜色。必填参数。

<label id='cluster_cols'> </label>
#### **运行参数 ClusterCols**
对横轴聚类
参数说明：
本参数对热图横轴聚类。默认不勾选。

<label id='cluster_rows'> </label>
#### **运行参数 ClusterRows**
对纵轴聚类
参数说明：
本参数对热图纵轴聚类。默认勾选。

　 
### **结果解读**

　  
#### **结果文件结构**
├─ <font color=#00BFFF>**QuSAGE_results **</font>(QuSAGE结果文件路径) 
┊　 ├─ **GeneSetsFileName.heatmap.png/pdf **(热图)
┊　 ├─ **GeneSetsFileName.heatmap.matrix.tsv **(热图用矩阵表)
┊　 ├─ **GeneSetsFileName.GeneSetInfoSummary.tsv **(基因集合信息汇总表) 
┊　 ├─ ...
├─ <font color=#00BFFF>**QuSAGE_GeneSet_details **</font>(基因集合分析结果路径)
┊　 ├─ <font color=#00BFFF>**GeneSetsFileName1 **</font>(基因集合文件名子目录)
┊　 ┊　 ├─ **GeneSetCIplot_ClusterID_GeneSetsFileName.png **(置信区间图)
┊　 ┊　 ├─ **GeneSetDCplot_ClusterID_GeneSetsFileName.png **(概率密度曲线图)
┊　 ┊　 ├─ ...
┊　 ├─ <font color=#00BFFF>**GeneSetsFileName2**</font>
┊　 ┊　 ├─ ...
├─ <font color=#00BFFF>**QuSAGE_Gene_details **</font>(基因分析结果路径)
┊　 ├─ <font color=#00BFFF>**GeneSetsFileName1 **</font>(基因集合文件名子目录) 
┊　 ┊　 ├─ **ClusterID_GeneInfoSummary.tsv **(基因信息汇总表)
┊　 ┊　 ├─ **GeneCIplot_ClusterID_GeneSetName.png **(置信区间图)
┊　 ┊　 ├─ **GeneDCplot_ClusterID_GeneSetName.png **(概率密度曲线图)
┊　 ┊　 ├─ ...
┊　 ├─ <font color=#00BFFF>**GeneSetsFileName2**</font>
┊　 ┊　 ├─ ...
├─ <font color=#00BFFF>**for_CellBrowser **</font>(对接CellBrowser文件路径) 
┊　 ├─ **GeneSetsFileName.heatmap.top10.matrix.tsv **(浏览器热图矩阵表)
┊　 ├─ **GeneSetsFileName.heatmap.config.txt **(浏览器热图聚类结构)
┊　 ├─ **GeneSetsFileName.heatmap.GeneInfoSummary.tsv **(浏览器热图基因信息表)
┊　 ├─ ...

　  
#### **热图**
<div style="text-align:center">
<img data-src="9.png" width="660px" ></img>
</div>
说明： 
横轴标签表示细胞类群名称。
纵轴标签表示基因集合名称。
色块从蓝到红渐变表示基因集合在不同的细胞类群中激活程度从低到高。

　  
#### **热图用矩阵表**
<div style="text-align:center">
<img data-src="8.png" height="220px" ></img>
</div>
说明：
表中第1列是基因集合名称，第1行是细胞类群名称，矩阵中数值是对应基因集合在对应细胞类群中相较其它所有细胞类群的表达量差异倍数对数值。

　  
#### **基因集合信息汇总表**
<div style="text-align:center">
<img data-src="4.png" height="120px" ></img>
</div>
说明：
表中每行对应1个基因集合。表头含义分别为：基因集合名称，表达量差异倍数对数值，P值，FDR，细胞类群，置信区间下限，置信区间上限。条目默认排序规则是按P值从小到大排序，如果P值相等，按差异倍数对数值从大到小排序。

　  
#### **基因集合置信区间图**
<div style="text-align:center">
<img data-src="3.png" width="660px" ></img>
</div>
说明：
图中，横轴是基因集合的名称，代表基因集合的竖线的中点对应纵轴上的位置表示这个基因集合的活跃度。活跃度大于零，表示这群基因在本细胞类群中较其它细胞类群整体表达上调，对应功能加强；反之，整体表达下调，对应功能减弱。每条竖线两端的短线表示概率密度曲线的95%置信区间。竖线的颜色表示P值大小，颜色越亮，P值越小，表达上下调分别用红绿表示。

　  
#### **基因集合概率密度曲线图**
<div style="text-align:center">
<img data-src="2.png" width="660px" ></img>
</div>
说明：
图中，每条曲线代表一个基因集合，曲线顶点在横轴上的位置表示对应基因集合的活跃度。活跃度大于零，表示相对于其它细胞类群，这群基因在本细胞类群中整体表达上调，对应功能加强；反之，整体表达下调，对应功能减弱。

　  
#### **基因置信区间图**
<div style="text-align:center">
<img data-src="6.png" width="660px" ></img>
</div>
说明：
图中，横轴是基因名称，代表基因的竖线的中点对应纵轴上的位置表示这个基因的活跃度。活跃度大于零，表示对应基因在本细胞类群中较其它细胞类群表达上调；反之，表达下调。每条竖线两端的短线表示概率密度曲线的95%置信区间。蓝色虚线和灰色长条表示基因集合整体的活跃度和置信区间

　  
#### **基因概率密度曲线图**
<div style="text-align:center">
<img data-src="5.png" width="660px" ></img>
</div>
说明：
图中，黑色加粗曲线代表标题中的基因集合，其它曲线代表组成这个基因集合的基因，曲线顶点在横轴上的位置表示对应基因集合或基因的活跃度。活跃度高低反映了对应基因或基因集合的激活程度。

　  
#### **基因信息汇总表**
<div style="text-align:center">
<img data-src="7.png" height="120px" ></img>
</div>
说明：
表中每行对应1个基因。表头含义分别为：基因名称，均值，P值，FDR，置信区间下限，置信区间上限，细胞类群，从属基因集合名称，基因集合表达量差异倍数对数值，基因集合P值。条目默认排序规则是按P值从小到大排序。

　  
#### **浏览器热图矩阵表**


说明：
本表数据源自/QuSAGE_results/GeneSetsFileName.heatmap.matrix.tsv
在源文件基础上，进行了每个Cluster取Top10，再取并集的处理。

#### **浏览器热图聚类结构**

说明：
本文件用小括号的形式描述了/QuSAGE_results/GeneSetsFileName.heatmap.png/pdf文件中热图的树形聚类结构。

　  
#### **浏览器热图基因信息表**


说明：
本文件包含了/QuSAGE_results/GeneSetsFileName.heatmap.png/pdf热图文件中涉及的所有基因集合与它们对应的基因信息。文件分为上下两部分用井号隔开，格式如下：
<div style="text-align:center">
<img data-src="10.png" height="90px" ></img>
</div>
　  
文档更新 2020.03.18 技术部 李亚当
文档整理 2019.04.19 技术部 李亚当

