# **﻿UMI_Tools_Extract**

　 
### **工具介绍**

　  
#### **功能概述**
利用UMI-tools的extract功能根据上游工具得到的细胞条码白名单提取测序序列，并对这些序列进行UMI区段质量过滤。然后使用STAR将过滤后的测序序列比对到参考基因组。

#### **软件官网**
https://github.com/CGATOxford/UMI-tools
https://github.com/alexdobin/STAR

　 
### **分析流程**
　  
**上游工具**：fastp / UMI_Tools_WhiteList
**下游工具**：UMI_Tools_Counts

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **参数设置**

　  
#### **输入文件参数 BarcodeReads**
含有Barcode的左端fastq文件，从上游工具fastp获取。（必传参数）

　  
#### **输入文件参数 cdnaReads**
cDNA右端fastq文件，从上游工具fastp获取。（必传参数）

　  
#### **输入文件参数 Whitelist**
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

<label id='BaseQuality'> </label>
#### **页面显示参数 BaseQuality**
UMI区段过滤质量，默认15表示一条测序片段UMI区段有一个碱基质量低于15时，这条测序片段会被过滤掉。

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
