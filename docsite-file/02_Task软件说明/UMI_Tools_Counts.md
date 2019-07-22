# **﻿UMI_Tools_Counts**

　 
### **工具介绍**

　  
#### **功能概述**
利用UMI-tools的FeatureCounts功能统计Counts，可以选择是否根据数据量进行标化。

#### **软件官网**
https://github.com/CGATOxford/UMI-tools

　 
### **分析流程**
　  
**上游工具**：UMI_Tools_WhiteList / UMI_Tools_Extract
**下游工具**：ScCountsCombine

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 InputBam**
从上游工具UMI_Tools_Extract获取。（必传参数）

　  
#### **输入文件参数 MappingLogFile**
从上游工具UMI_Tools_Extract获取。（必传参数）

　  
#### **输入文件参数 whitelist**
从上游工具UMI_Tools_Whitelist获取。（必传参数）

<label id='Species'> </label>
#### **页面显示参数 Species**
物种

<label id='SpeciesVersion'> </label>
#### **页面显示参数 SpeciesVersion**
参考基因组文件版本

<label id='GTFVersion'> </label>
#### **页面显示参数 GTFVersion**
基因组注释文件版本

<label id='UMIDistance'> </label>
#### **页面显示参数 UMI Distance**
默认1 UMI码距

<label id='GTFattribute'> </label>
#### **页面显示参数 GTFattribute**
默认gene_name表示结果文件用gene name展示

<label id='NormByMapReadsPerCell'> </label>
#### **页面显示参数 NormByMapReadsPerCell**
不同样本是否根据细胞平均匹配到参考基因组的测序片段做标化，样本之间数据量接近时可以选择true

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
