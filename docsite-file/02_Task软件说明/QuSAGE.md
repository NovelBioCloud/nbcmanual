# **QuSAGE**
　  

### **工具介绍**
　  

#### **功能概述**

QuSAGE（Quantitative Set Analysis for Gene Expression, 基因表达定量集合分析），是一种定量分析基因群在不同样本中差异表达的分析方法。QuSAGE通过概率密度函数（Probability Density Function, PDF）量化被分析的基因群体的整体表达活跃程度，并通过概率密度曲线图（Probability Density Curve Plot）、置信区间图（Confidence Interval Plot）等数据可视化方式，展示被分析的基因群体的整体表达情况。
　  

#### **软件特点**

QuSAGE可通过PDF轻松获得相应的P-Value和置信区间。  
在计算过程中，QuSAGE通过方差膨胀因子（Variance Inflation Factor）来消除基因群内不同基因之间的相关性导致的假阳性错误。
　  
#### **软件官网**
http://clip.med.yale.edu/qusage/
　  

### **分析流程**

上游工具：Seurat_Cluster/Seurat_ReCluster  
下游工具：sc_heatmap  
连接示例：
<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　  

### **参数设置**
　  

#### <label id='rdsFile'> **输入文件参数 Input Seurat rds File** </label>
基因表达数据文件（.rds文件）  
参数说明：
Seurat rds文件可以从Seurat_Cluster、Seurat_ReCluster等上游工具获取。rds文件内部的基因表达矩阵（Expresssion Matrix）和细胞分群列表（Cluster List）分别是qusage算法的前2个输入参数，因此Seurat rds文件是必需参数。
　  
<label id='genesetFile'></label>
####  **输入文件参数 Input GeneSet File (optional)**
基因集合文件（.gmt或其它表格文件）  
参数说明：
基因集合（GeneSets）是qusage算法的第4个输入参数，包含此数据的.gmt或其它表格文件是必需参数。
gmt文件可通过数据库（如MSigDB）下载，或按其规定格式手动生成。
其它表格文件可从上游工具获取或手动生成。格式必须满足：每行记录1个基因条目，前两列分别是基因集合名称和基因名称，表头不可缺少。例如：  

|GeneSet Name|Gene Name|
|:----------:|:-------:|
|B_cell      |CD19     |
|B_cell      |CD79     |
|T_cell      |CD3      |

注：  
1 支持多个以上不同格式的文件同时作为输入参数。  
2 如果点选了页面显示参数Select GeneSet File的.gmt文件，此处可以不传入基因集合文件。
　  

#### <label id='qusageSpecies'> **页面显示参数 Species** </label>
物种  
参数说明：
目前支持物种包括：人、小鼠、大鼠
　  

#### <label id='MSigDB'> **页面显示参数 Select GeneSet File (optional)**</label>
基因集合文件（.gmt文件）   
参数说明：
来自MSigDB数据库的19个.gmt文件，可以选择一个或多个。
注：  
1 本参数和输入文件参数Input GeneSet File都可以传入基因集合文件，两种方式至少选择一种，以保证传入基因集合文件总数不少于1。  
2 小鼠和大鼠gmt文件是通过转换人类gmt文件中同源基因名称所得，并非数据库原始数据。
　  

#### <label id='curveNum'> **页面显示参数 MaxCurveNum**</label>
最大曲线数量  
参数说明：
本参数为结果文件置信区间图中被展示基因集合的数量上限。例如：默认值50表示在P值升序和差异倍数降序综合排序表中，取不超过50个基因集合作图。
　  

#### <label id='XFontSize'> **页面显示参数 LabelFontSize**</label>
标签字体大小  
参数说明：
本参数为结果文件置信区间图中标签字体大小。
　  

#### <label id='thread'> **页面显示参数 ThreadNum**</label>
线程数  
参数说明：
设置线程数，默认4线程
　  

#### <label id='memory'> **页面显示参数 Memory(MB)**</label>
内存（MB）  
参数说明：
设置内存大小，默认8000MB


### **结果解读**
　  

#### **结果文件结构**

┣━ <font color=#00BFFF>**QuSAGE_rds**</font> （QuSAGE作图文件目录）  
┃　┣━ <font color=#00BFFF>**GeneSetsFile Name1**</font> （基因集合文件名子目录，每个cluster对应1个文件）  
┃　┃　┣━ **ClusterID.qs.rds** （QuSAGE rds文件）  
┃　┃　┣━ ...  
┃　┣━ <font color=#00BFFF>**GeneSetsFile Name2**</font>  
┃　 　 ┣━ ...  
┣━ <font color=#00BFFF>**QuSAGE_result**</font> （QuSAGE结果目录）  
┃　┣━ <font color=#00BFFF>**GeneSetsFile Name1**</font> （基因集合文件名子目录，每个cluster对应3个文件）  
┃　┃　┣━ **plotDC_ClusterID_GeneSets.png** （概率密度曲线图）  
┃　┃　┣━ **plotCI_ClusterID_GeneSets.png** （置信区间图）  
┃　┃　┣━ **table_ClusterID_GeneSets.txt** （基因集合数据汇总表）  
┃　┃　┣━ ...  
┃　┣━ <font color=#00BFFF>**GeneSetsFile Name2**</font>  
┃　 　 ┣━ ...  
┣━ <font color=#00BFFF>**QuSAGE_for_heatmap**</font> （下游热图工具输入文件目录，每个基因集合文件对应1张表)   
　　┣━ **GeneSets1_heatmap.txt** （热图用矩阵表）  
　　┣━ **GeneSets2_heatmap.txt**  
　　┣━ ...  
　  

#### **QuSAGE rds文件**
QuSAGE rds文件是程序运行中间文件，内容是算法中qusage函数返回的R数据结构，可以直接用于生成QuSAGE结果图表。在重新运行Task时，不删除QuSAGE_rds文件夹可以跳过qusage函数运算，节省大量运行时间。  
　  
　  
#### **概率密度曲线图**

<div style="text-align:center">
<img data-src="2.png" width="600px" ></img>
</div>
说明：
图中每条概率密度曲线代表一个基因群，曲线顶点在横轴上的位置表示这个基因群的活跃度。活跃度大于零，表示相对于其它细胞群，这群基因在这个细胞群中整体表达上调，对应功能加强；反之，整体表达下调，对应功能减弱。  
　  

#### **置信区间图**

<div style="text-align:center">
<img data-src="3.png" width="600px" ></img>
</div>
说明：
图中每条竖线代表一个基因群，竖线的中点在纵轴上的位置表示这个基因群的活跃度。活跃度大于零，表示相对于其它细胞群，这群基因在这个细胞群中整体表达上调，对应功能加强；反之，整体表达下调，对应功能减弱。每条竖线两端的短线表示概率密度曲线的95%置信区间。竖线的颜色表示P值大小，颜色越亮，P值越小，表达上下调分别用红绿表示。  
　  

#### **基因集合数据汇总表**

<div style="text-align:center">
<img data-src="4.png" height="300px" ></img>
</div>
说明：
表中每行记录一个基因群的数据。表头含义分别为：基因集合名称，差异倍数对数值，P值，FDR校正P值。条目默认排序规则是按P值从小到大排序，如果P值相等，按差异倍数对数值从小到大排序。  
　  
文档更新：2019.06.17 技术部 李亚当  
文档整理：2019.04.19 技术部 李亚当
