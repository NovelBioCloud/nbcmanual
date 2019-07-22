# **﻿ScCountsCombine**

　 
### **工具介绍**

　  
#### **功能概述**
多样本Counts合并
一个java工具，可以降低合并counts使用的计算资源
细胞名前面加上样本名

　 
### **分析流程**
　  
**上游工具**：UMI_Tools_Counts
**下游工具**：Seurat_NormalizedForTab

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 Counts**
从上游工具UMI_Tools_Count获取。（必传参数）

　  
#### **输入文件参数 OrderList**
全部基因的列表，合并时要根据这个基因列表排序
从GTF中提取的基因列表
从上游工具UMI_Tools_Count获取。（必传参数）

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
