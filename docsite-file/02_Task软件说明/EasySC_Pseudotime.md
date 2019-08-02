# **﻿EasySC_Pseudotime**

　 
### **工具介绍**

　  
#### **功能概述**
拟时序（Pseudotime）分析,是一种通过对不同细胞在时间轴上进行排序，从而对细胞的演进过程进行描述的分析。拟时序分析有助于了解细胞的分化与分类，发现识别某些调控细胞分化或决定细胞命运的基因。本工具采用经典的Monocle软件完成拟时序分析。

工具特点
Monocle是一个R包。

#### **软件官网**
https://cole-trapnell-lab.github.io/monocle-release/

　 
### **分析流程**
　  
**上游工具**：Seurat_Cluster
**下游工具**：ForCellBrowse

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 MarkerGeneList**
从上游工具Seurat_Cluster获取。（必传参数）

　  
#### **输入文件参数 InputRDS**
从上游工具Seurat_Cluster获取。（必传参数）

　  
#### **输入文件参数 CellList**
用户关注的细胞做拟时序分析（选传参数）

<label id='Reduction_Method'> </label>
#### **页面显示参数 Reduction_Method**
默认DDRTree
tSNE
ICA
SimplePPT
L1-graph
SGL-tree

<label id='RandomCells'> </label>
#### **页面显示参数 RandomCells**
随机选细胞 默认false 

<label id='CellsPercent'> </label>
#### **页面显示参数 CellsPercent**
细胞数量特别大时随机选10%的细胞分析。0？默认0.1

<label id='MinCellsPerCluster'> </label>
#### **页面显示参数 MinCellsPerCluster**
每个cluster最小细胞数。0表示完全按照百分比选细胞。默认1000表示当按百分比选细胞数小于1000时，调整为1000 总数不到1000？

<label id='RandomType'> </label>
#### **页面显示参数 RandomType**
默认random 无放回随机取样
kmean 先用kmean分类 然后每类取一个
hclust 用hclust做树状聚类 然每类取一个

<label id='SelectedCluster'> </label>
#### **页面显示参数 SelectedCluster**
选择指定cluster分析
编号 字符串，号隔开 混合
应用 确定了每个cluster celltype后把同类拿出来做

<label id='Threads'> </label>
#### **页面显示参数 Threads**
线程数
参数说明：
设置线程数

<label id='Memory(MB)'> </label>
#### **页面显示参数 Memory(MB)**
内存（MB）
参数说明：
设置内存大小
