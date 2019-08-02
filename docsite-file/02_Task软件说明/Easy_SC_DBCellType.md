# **﻿EasySC_DBCellType**

　 
### **工具介绍**

　  
#### **功能概述**
根据数据库对细胞类型进行初步注释
仅适用人和小鼠

#### **软件官网**

　 
### **分析流程**
　  
**上游工具**：Seurat_Cluster

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 AllMarkerGenes**
从上游工具Seurat_Cluster获取。（必传参数）

　  
#### **输入文件参数 dbFile(Optional)**
保证 第一列 celltype 第二列marker gene（选传参数）

<label id='Species'> </label>
#### **页面显示参数 Species**
物种

<label id='isConsiderTissue'> </label>
#### **页面显示参数 isConsiderTissue**
考虑组织 默认true

<label id='TissueType'> </label>
#### **页面显示参数 TissueType**
默认T0表示全部组织

<label id='isConsiderCancer'> </label>
#### **页面显示参数 isConsiderCancer**
考虑癌症 默认false 

<label id='CancerType'> </label>
#### **页面显示参数 CancerType**
默认C0表示全部癌症

<label id='GeneCol'> </label>
#### **页面显示参数 GeneCol**
默认1

<label id='ClusterCol'> </label>
#### **页面显示参数 ClusterCol**
默认7

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
