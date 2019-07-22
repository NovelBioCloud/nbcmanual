# **﻿ForCellBrowser**

　 
### **工具介绍**

　  
#### **功能概述**
本工具的功能是生成单细胞浏览器需要的输入文件。
单细胞浏览器（Single Cell Browser）是烈冰生物研发的国内首款将单细胞测序数据分析结果进行三维立体化展示的软件。单细胞浏览器的主要功能包括：提供细胞分群情况的统计信息；对于t-SNE和Pseudotime以及Velocity分析结果，提供2D和3D两种图形化展示方式；提供所有细胞亚群差异基因表达的热图；指定基因根据其表达量对细胞进行染色；自动生成小提琴图等。

　 
### **分析流程**
　  
**上游工具**：Seurat_NormalizedForTab / Seurat_Cluster / EasySC_Pseudotime / ScRNAVelocity

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 NormData**
从上游工具Seurat_NormalizedForTab获取。（必传参数）

　  
#### **输入文件参数 tsneFile**
从上游工具Seurat_NormalizedForTab获取。（必传参数）

　  
#### **输入文件参数 CellUmiInfo**
从上游工具Seurat_NormalizedForTab获取。（必传参数）

　  
#### **输入文件参数 ClusterFile**
从上游工具Seurat_Cluster获取。（必传参数）

　  
#### **输入文件参数 MarkerFile**
从上游工具Seurat_Cluster获取。（必传参数）

　  
#### **输入文件参数 tsne3dFile**
从上游工具Seurat_NormalizedForTab获取。（必传参数）

　  
#### **输入文件参数 TsneVelocityArrow**
从上游工具ScRNAVelocity获取。（选传参数）

　  
#### **输入文件参数 pseudoTimeCoords**
从上游工具EasySC_Pseudotime获取。（选传参数）

　  
#### **输入文件参数 PseudoVelocityArrow**
从上游工具ScRNAVelocity获取。（选传参数）

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
