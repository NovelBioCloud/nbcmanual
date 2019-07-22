# **﻿Seurat_NormalizedForTab**

　 
### **工具介绍**

　  
#### **功能概述**
对单细胞测序数据进行标准化（Normalization）处理，目的是校正批次效应（Batch Effect）对整个数据分析过程产生的巨大影响，以及过滤UMI-Tools工具处理后数据中残留的死细胞（Dead Cell）,双细胞（Doublet）和低质量细胞（Low Quality Cell）。这些实验偏差（Bias）会对下游细胞聚类分析产生影响。得到准确无偏差的单细胞基因表达数据后，采用PCA（Principal Component Analysis）算法及tSNE(t-Distributed Stochastic Neighbor Embedding)算法对数据进行降维处理和信息展示。本工具使用了SATIJA LAB开发的scRNA-seq分析软件Seurat实现以上功能。

工具特点
Seurat是一个R包。

#### **软件官网**
https://satijalab.org/seurat/

　 
### **分析流程**
　  
**上游工具**：ScCountsCombine
**下游工具**：Seurat_Cluster / ForCellBrowse

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 MTGeneList(Optional)**
人、小鼠、大鼠目前可以不用传入此文件，其它物种需要传入此文件。（选传参数）

　  
#### **输入文件参数 CountsFile**
从上游工具ScCountsCombine获取。（必传参数）

　  
#### **输入文件参数 CellCycleRDS(Optional)**
细胞M期S期对应的基因列表，用于计算细胞周期值，判断细胞处于哪个周期。通常用于干细胞数据分析。从public files中添加。（选传参数）

<label id='Species'> </label>
#### **页面显示参数 Species**
物种

<label id='geneExpMinCell'> </label>
#### **页面显示参数 geneExpMinCell**
默认3表示一个基因至少要在三个细胞里有表达量，否则过滤掉这个基因。

<label id='cellMinGene'> </label>
#### **页面显示参数 cellMinGene**
默认200每个细胞最少有200个基因表达，否则过滤掉这个细胞。

<label id='AutoFilterGene'> </label>
#### **页面显示参数 AutoFilterGene**
默认false会采用cellMaxGene参数来限制细胞基因数上限
细胞基因数计算中位数，超过中位数两倍的细胞可能是双细胞，会被过滤掉。

<label id='cellMaxGene'> </label>
#### **页面显示参数 cellMaxGene**
默认5000表示一个细胞表达基因超过5000有可能是双细胞，被过滤掉

<label id='MaxMTPercent'> </label>
#### **页面显示参数 MaxMTPercent**
默认0.2表示线粒基因超过20%有可能是一个死细胞，会被过滤掉

<label id='NormMethod'> </label>
#### **页面显示参数 NormMethod **
标准化方法
默认LogNormalize 数值加1以e为底取对数
genesCLR
两种Seurat提供算法

<label id='RemoveMTGene'> </label>
#### **页面显示参数 RemoveMTGene**
默认
在counts总表里把线粒体基因删掉

<label id='ScaleModel'> </label>
#### **页面显示参数 ScaleModel**
数据中心化处理的算法 Seurat提供的3种不同算法
默认linear 运算速度最快
poisson
negbinom

<label id='RegressOutBySample'> </label>
#### **页面显示参数 RegressOutBySample**
根据样本做去除批次效应 去除样本间批次效应 例如遇到两个样本在tSNE图上完全分开
默认false

<label id='RegressOutBynGene'> </label>
#### **页面显示参数 RegressOutBynGene**
根据基因数量去除批次效应
默认false 

<label id='MaxcomputerPCs'> </label>
#### **页面显示参数 MaxcomputerPCs**
默认20

<label id='PcaDimUse'> </label>
#### **页面显示参数 PcaDimUse**
默认10

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

<label id='RunFAST'> </label>
#### **页面显示参数 RunFAST**
抽取1000个基因做scale默认false
