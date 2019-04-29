文档整理：2019.04.26技术部

# CellPhoneDB
***
**基本介绍**

**功能概述**

CellPhoneDB（细胞通讯数据库），是一个公开的细胞配体-受体互作对的存储库。CellPhoneDB可基于单细胞转录组数据和数据库中记录的配体-受体互作关系，通过计算分析不同细胞类群之间的分子相互作用，从而预测细胞类群之间的通讯关系。

**工具特点**

CellPhoneDB可通过Python包的形式来使用。
CellPhoneDB的细胞通讯信息来源于文献挖掘和整合数据库(UniProt, Ensembl, PDB, the IMEx consortium, IUPHAR）。

**官方网址**
https://www.cellphonedb.org/

**使用说明**

上游工具：Seurat_Cluster
下游工具：ScBubblePlot
连接示例：
 


**参数设置**

**输入文件参数1 Input Seurat rds File (rds)**
基因表达数据文件（.rds文件）
参数说明：
包含单细胞转录组表达数据的rds文件是必需参数。
rds文件可以从Seurat_Cluster、Seurat_ReCluster等上游工具获取。

**输入文件参数2 Cluster Rename File (optional)**
细胞类群重命名文件（.txt文件）
参数说明：
rds文件中的细胞类群（cluster）名称通常为阿拉伯数字。如果要改成有含义字符串，可输入细胞类群重命名文件，规则为每行两列，左列为细胞名称，右列为所属细胞类型名称。例如：
Cell	Cluster
N_AAATCCTGTAACCCTCGGCTACATGCG	MPC
N_AAATCCTGTAACTCATTGACTGAATTC	FC-1
N_AAATCCTGTAAGGACTATAGTTGTTCT	ProFC
注：
1左列细胞名称来源为rds文件。
2右列为替换后的字符串，支持常见字符包括数字、字母、下划线、加号、减号、点号、空格等。
3表头不可缺少
4平台目前不支持Unicode编码的txt文件

**输入文件参数3 Cluster Merge File (optional)**
细胞类群合并文件（.txt文件）
使用下游工具绘制气泡图时，如果要将不同的细胞类群合为一类进行展示，例如将Th1细胞及Th2细胞都作为T细胞进行展示，可输入细胞类群合并文件，规则为每行两列，左列为合并前细胞类群名称，右列为合并后细胞类群名称。例如：
Ori_Cluster	Merged_Cluster
pro_B_cell	B_cell
pre_B_cell	B_cell
Th1_cell	T_cell
Th2_cell	T_cell
注：
1左列细胞类群名称与rds文件中信息一致
2右列细胞类群名称，支持常见字符包括数字、字母、下划线、加号、减号、点号、空格等。
3表头不可缺少
4平台目前不支持Unicode编码的txt文件

**页面显示参数1 Species**
物种
参数说明：
目前支持人和小鼠

**页面显示参数2 Threads**
线程数
参数说明：
设置线程数

**页面显示参数3 Memory(MB)**
内存（MB）
参数说明：
设置内存大小

**结果解读**

**结果文件结构**

┣━ out (CellPhoneDB原始结果文件)
┃   ┣━ pvalues.txt (原始pvalues表)
┃   ┣━ means.txt (原始means表)
┃   ┣━ pvalues_means.txt (原始pvalue和means汇总表)
┃   ┣━ significant_means.txt (原始P值不大于0.05的means表)
┣━ pvalues_revise.txt （修正过顺序的pvalues表
┣━ significant_means_revise.txt （修正过顺序的significant_means表）
┣━ pvalues_0.05.txt （修正过顺序且P值不大于0.05的pvalue和means汇总表）
┣━ BubblePlot (下游气泡图工具的作图输入文件，每cluster一组包含4个文件)
   ┣━ 0_Ligand.cluster.txt （cluster 0作为配体时，cluster互作对列表）
   ┣━ 0_Ligand.gene.txt （cluster 0作为配体时，gene互作对列表）
   ┣━ 0_Receptor.cluster.txt （cluster 0作为受体时，cluster互作对列表）
   ┣━ 0_Receptor.gene.txt （cluster 0作为受体时，gene互作对列表）
...


**修正P值表**

 
说明：
表中每行记录一条配体受体互作对信息。每列含义如下：
LRtype 配体受体类型，LR表示互作对左右分别是配体（Ligand）和受体（Receptor），RR表示两个分子互为对方受体
interacting_pair 互作关系对，用基因名称以下划线间隔表示
id_cp_interaction CellPhoneDB互作关系ID
partner_a 互作分子A Uniprot ID
partner_b 互作分子B Uniprot ID
ensembl_a 互作分子A Ensembl ID
ensembl_b 互作分子B Ensembl ID
source 互作关系注释来源
secreted 互作对是否含分泌性蛋白
is_integrin 互作对是否为整合素
P值 一个互作对的P值是它在两个互作细胞类群中的富集度。其中0_1表示互作分子分别来自细胞类群0和1
注：原始P值文件配体受体顺序不统一，修正后统一左右两边分别为配体受体，其中RR类型的条目在列表中出现两次

**修正significant_means表**

 

说明：
本表与P值表前10列相同，不同部分如下：
rank 互作关系的独特性，值越接近0，代表该互作关系在全部细胞类群中越独特，比如某两个细胞类群独有的互作关系，其它细胞类群之间没有这个关系。
means 互作对两个分子平均表达值的和，p值小于0.05对应的means会被保留，称为significant_means。该值越大表示该互作关系强度越强。

**pvalues_0.05表**

 
说明：
本表与上面两张表前10列相同，后面5列是前两张表信息的汇总。其中a和b是互作细胞类群名称，P-value/rank/significant_means取自上面两张表中满足p值小于0.05的数据。

**气泡图作图输入文件**

     
说明：
XXX.gene.txt 是气泡图作图用的互作基因对列表
XXX.cluster.txt 是气泡图作图用的互作细胞类群对列表

