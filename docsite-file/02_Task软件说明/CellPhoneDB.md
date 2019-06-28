# **CellPhoneDB**

　  
### **基本介绍**

　  
#### **功能概述**

CellPhoneDB（细胞通讯数据库），是一个公开的细胞配体-受体互作对的存储库。CellPhoneDB可基于单细胞转录组数据和数据库中记录的配体-受体互作关系，通过计算分析不同细胞类群之间的分子相互作用，从而预测细胞类群之间的通讯关系。

#### **工具特点**

CellPhoneDB软件是一个Python包。
CellPhoneDB的细胞通讯信息来源于文献挖掘和整合数据库(UniProt, Ensembl, PDB, the IMEx consortium, IUPHAR）。

#### **软件官网**
https://www.cellphonedb.org/

　  
### **分析流程**

　  
**上游工具**：Seurat_Cluster / Seurat_ReCluster
**下游工具**：ScBubblePlot
**连接示例**：
<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>

　  
### **参数设置**

　  
#### **输入文件参数 Input Seurat rds File**
基因表达数据文件（.rds文件）
参数说明：
包含单细胞转录组表达数据的rds文件是必需参数。
rds文件可以从Seurat_Cluster、Seurat_ReCluster等上游工具获取。

　  
#### **输入文件参数 Cluster Rename File (optional)**
细胞类群重命名文件（.txt文件）
参数说明：
rds文件中的细胞类群（cluster）名称通常为阿拉伯数字。需要改成有含义的字符串时，可传入细胞类群重命名文件，进行细胞类群名称替换。文件格式为每行两列，左列为细胞名称，右列为所属细胞类群名称。例如：
|Cell      |Cluster|
|:--------:|:-----:|
|N_TGCG... |MPC    |
|N_ATTC... |FC-1   |
|N_TTCT... |ProFC  |
|...       |...    |

注：
1左列细胞名称来源为rds文件。
2右列为替换后的字符串，支持常见字符包括数字、字母、下划线、加号、减号、点号、空格等。
3表头不可缺少
4平台目前不支持Unicode编码的txt文件

<label id='cellphonedb_species'></label>
#### **页面显示参数 Species**
物种
参数说明：
目前支持物种包括：人、小鼠、大鼠

<label id='thread'></label>
#### **页面显示参数 Threads**
线程数
参数说明：
设置线程数

<label id='memory'></label>
#### **页面显示参数 Memory(MB)**
内存（MB）
参数说明：
设置内存大小

<label id='topGenePairNum'></label>
#### **页面显示参数 Output GenePair Num**
输出基因互作对数量
参数说明：
本参数限制了结果文件/BubblePlot/XXX.gene.txt中基因互作对的个数。例如，默认值50表示按选取前50个基因互作对用于下游工具绘制气泡图。
注：
本参数为必填参数，且必须大于零

　  
### **结果解读**

　  
#### **结果文件结构**

├─ <font color=#00BFFF>**out**</font> (CellPhoneDB原始结果文件)
┆   ├─ **pvalues.txt** (原始P值表)
┆   ├─ **means.txt** (原始均值表)
┆   ├─ **pvalues_means.txt** (原始P值和均值汇总表)
┆   ├─ **significant_means.txt** (原始显著均值表)
├─ **pvalues_revise.txt** （修正过顺序的P值表）
├─ **significant_means_revise.txt** （修正过顺序的显著均值表）
├─ **pvalues_0.05.txt** （修正过顺序的显著P值和均值汇总表）
├─ <font color=#00BFFF>**BubblePlot**</font> (下游气泡图工具的输入文件，其中每个cluster对应4个文件) 
┆   ├─ **Means_for_Plot.txt** （作图用均值表）
┆   ├─ **Pvalues_for_Plot.txt** （作图用P值表）
┆   ├─ **0_Ligand.cluster.txt** （cluster 0作为配体时，cluster互作对列表）
┆   ├─ **0_Ligand.gene.txt** （cluster 0作为配体时，gene互作对列表）
┆   ├─ **0_Receptor.cluster.txt** （cluster 0作为受体时，cluster互作对列表）
┆   ├─ **0_Receptor.gene.txt** （cluster 0作为受体时，gene互作对列表）
┆   ├─ ...

　  
#### **修正P值表**

　  
<div style="text-align:center">
<img data-src="2.png" height="60px" ></img>
</div>
说明：
表中每行记录一条配体受体互作对信息。每列含义如下：
**LRtype** 配体受体类型，LR表示互作对左右分别是配体（Ligand）和受体（Receptor），RR表示两个分子互为对方受体
**interacting_pair** 互作关系对，用基因名称以下划线间隔表示
**id_cp_interaction** CellPhoneDB互作关系ID
**partner_a** 互作分子a Uniprot ID
**partner_b** 互作分子b Uniprot ID
**ensembl_a** 互作分子a Ensembl ID
**ensembl_b** 互作分子b Ensembl ID
**source** 互作关系注释来源
**secreted** 互作对是否含分泌性蛋白
**is_integrin** 互作对是否为整合素
**P值** 一个互作对的P值是它在两个互作细胞类群中的富集度。其中0 >> 1表示互作分子分别来自细胞类群0和1
注：原始P值表配体受体次序不统一，修正后统一左右两边分别为配体受体，其中RR类型的条目在列表中出现两次，第1次表示a、b分别为配体受体，第2次表示b、a分别为配体受体。

　  
#### **修正显著均值表**

<div style="text-align:center">
<img data-src="3.png" height="60px" ></img>
</div>
说明：
本表与P值表前10列相同，不同部分如下：
**rank** 互作关系的独特性，值越接近0，代表该互作关系在全部细胞类群中越独特，比如某两个细胞类群独有的互作关系，其它细胞类群之间没有这个关系。
**means** 互作对两个分子平均表达值的和，其中0 >> 1表示互作分子分别来自细胞类群0和1。只有p值小于0.05对应的means会被保留，称为significant_means。该值越大表示该互作关系强度越强。

　  
#### **修正显著P值和均值汇总表**

<div style="text-align:center">
<img data-src="4.png" height="60px" ></img>
</div>
说明：
本表与上面两张表前10列相同，后面5列是前两张表信息的汇总。其中a和b是互作细胞类群名称，P-value/rank/significant_means取自上面两张表中满足p值小于0.05的数据。

　  
#### **气泡图工具输入文件**

<div style="text-align:center">
<img data-src="5.png" height="80px" ></img>
<img data-src="6.png" height="80px" ></img>
</div>
<div style="text-align:center">
</div>
说明：
Means_for_Polt.txt是气泡图作图用的均值表
Pvalues_for_Plot.txt是气泡图作图用的P值表
XXX.gene.txt 是气泡图作图用的互作基因对列表
XXX.cluster.txt 是气泡图作图用的互作细胞类群对列表

　  
文档更新：2019.06.28 技术部 李亚当 
文档整理：2019.04.26 技术部 李亚当 
