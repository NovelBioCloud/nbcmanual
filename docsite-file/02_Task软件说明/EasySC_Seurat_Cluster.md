# **﻿Seurat_Cluster**

　 
### **工具介绍**

　  
#### **功能概述**
细胞聚类（Cluster）分析是对于tSNE降维结果中的细胞，根据基因表达的情况，通过基于图形聚类（Graph-based clustering）或k均值聚类(k-means clustering)两种无监督聚类算法进行细胞群体的划分。同时，通过差异筛选算法计算出不同细胞类群的标识基因（Marker Gene），并通过这些标识基因对所属细胞类群进行推测和鉴定。本工具使用了SATIJA LAB开发的scRNA-seq分析软件Seurat实现以上功能。

工具特点
Seurat是一个R包。

#### **软件官网**
https://satijalab.org/seurat/

　 
### **分析流程**
　  
**上游工具**：Seurat_NormalizedForTab
**下游工具**：GoPathway / EasySC_Pseudotime / EasySC_DBCellType / ForCellBrowse

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 inputRDS**
从上游工具Seurat_NormalizedForTab获取。（必传参数）

　  
#### **输入文件参数 ClusterFile(Optional)**
自行输入Cluster分类，ClusterMethod选Manual（选传参数）

<label id='Species'> </label>
#### **页面显示参数 Species**
物种

<label id='SpeciesVersion'> </label>
#### **页面显示参数 SpeciesVersion**
参考基因组文件版本

<label id='GTFVersion'> </label>
#### **页面显示参数 GTFVersion**
基因组注释文件版本

<label id='ClusterMethod'> </label>
#### **页面显示参数 ClusterMethod**
细胞类群分类方法
Auto 表示graphbased 和Kmeans都做
graphbased
Kmeans
Manual

<label id='minKmean'> </label>
#### **页面显示参数 minKmean**
默认2

<label id='ReductionType'> </label>
#### **页面显示参数 ReductionType**
3种不同的降维方法
默认pca
cca
mnn

<label id='maxKmean'> </label>
#### **页面显示参数 maxKmean**
默认10

<label id='MarkerGeneMethod'> </label>
#### **页面显示参数 MarkerGeneMethod**
Seurat提供的MarkerGene算法
默认Wilcoxon Rank Sum Test 
MAST
Likelihood-ratio Test Bimod
Standard AUC classifier
Student’s t-test
Tobit-test
Likelihood-ratio Test Poisson Distribution
Likelihood-ratio Test Negative Binomial Distribution
DESeq2

<label id='Logfc.Threshold'> </label>
#### **页面显示参数 Logfc.Threshold**
差异倍数 0.25以下不算显著Marker，会被去除
默认0.25

<label id='MinPct'> </label>
#### **页面显示参数 MinPct**
pct是MarkerGene表达占总体细胞的百分比 
默认0.1表示低于10%会被认为表达比例太低，低于这个值的基因不能作为Marker。例如1个cluster中100个细胞至少要有10个细胞有这个基因表达

<label id='OnlyReturnPositiveMarkers'> </label>
#### **页面显示参数 OnlyReturnPositiveMarkers**
只返回显著的Marker默认true

<label id='resolution'> </label>
#### **页面显示参数 resolution**
分辨率
采用graphbased方法 分群的时候分辨率越大 类型越多 反之越少
默认0.8

<label id='isEnsemblID'> </label>
#### **页面显示参数 isEnsemblID**
输入文件是EnsemblID 默认false

<label id='MarkerGenePlotNum'> </label>
#### **页面显示参数 MarkerGenePlotNum**
默认20
选多少个MakerGene画图  feature plot violin plot

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
