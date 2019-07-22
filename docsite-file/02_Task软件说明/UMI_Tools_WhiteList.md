# **﻿UMI_Tools_WhiteList**
　 
### **工具介绍**

　  
#### **功能概述**
利用UMI-tools的whiteList功能建立真实细胞条码的白名单。根据Scanner情况选择不同策略。如果有Scanner传入的细胞数信息，则采用Scanner的结果；如果没有Scanner传入的细胞数信息，工具会自动判断细胞数。UMI-tools是由CGATOxford开发的处理Unique Molecular Identifiers(唯一分子标识符)的软件。

#### **软件官网**
https://github.com/CGATOxford/UMI-tools
　 
### **分析流程**
　  
**上游工具**：fastp / ScanerCellNum
**下游工具**：UMI_Tools_Extract / UMI_Tools_Counts

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>　 
### **参数设置**

　  
#### **输入文件参数 BarcodeReads**
含有Barcode的左端fastq文件，从上游工具fastp获取。（必传参数）

　  
#### **输入文件参数 CellNumList**
细胞计数表格文件，从上游工具ScannerCellNum获取。（选传参数）

<label id='CellNumSetType'> </label>
#### **页面显示参数 CellNumSetType**
细胞数量设置方式
ExpectCells（预计细胞数）UMI_Tools会自动将输入值作为细胞数上限，在一定范围内进行细胞数判断，例如输入10000，会在1000到10000这个区间内找到合适的数值
SetCellNumber（设定细胞数）当预先知道细胞数量时，点选此项。例如有Scanner传入的细胞计数文件。

<label id='CellNumber'> </label>
#### **页面显示参数 CellNumber**
设定细胞数量
默认10000表示每个样本细胞数量都设定为10000。
注：当传入Scanner技术表时，此参数无效。

<label id='BarcodeHammingdistance'> </label>
#### **页面显示参数 Barcode Hamming distance**
条码码距
默认1表示码距不大于1的条码会被认为是相同条码

<label id='WhiteListMethod'> </label>
#### **页面显示参数 WhiteListMethod**
计数方式
默认umis表示下游的统计分析以UMI数量为准
reads

<label id='SubSetReads'> </label>
#### **页面显示参数 SubSetReads**
测序片段子集
用于分析的测序片段数量，如果需要快速分析可输入一个较小值，例如1000表示选前1000条测序片段进行分析。如果需要准确分析可输入一个较大值，例如1000000000以保证选取全部测序片段进行分析。

<label id='Threads'> </label>
#### **页面显示参数 Threads**
默认8

<label id='Memory(MB)'> </label>
#### **页面显示参数 Memory(MB)**
默认30000
