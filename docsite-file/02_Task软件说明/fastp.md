# **fastp**
　 
### **工具介绍**
　  
#### **功能概述**
对fastq数据进行质控和预处理，以保证下游分析输入的数据干净可靠的。本工具采用海普洛斯公司开发的fastq文件预处理软件fastp，可以对fastq进行过滤、接头处理、滑窗质量裁剪、双端测序数据碱基校正等处理，并生成HTML格式的报告。
　  
#### **软件特点**
功能丰富，简化数据预处理流程。
使用C++开发，算法高效并支持多线程。
　  
#### **软件官网**
https://github.com/OpenGene/fastp
　 
### **分析流程**　 
**上游工具**：RawFastq　 
**下游工具**：UMI_Tools_WhiteList / UMI_Tools_Extract

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>　 
### **参数设置**
　  
#### **输入文件参数 leftInputData**
左端fastq文件，从上游工具RawFastq获取。（必传参数）
　  
#### **输入文件参数 rightInputData**
右端fastq文件，从上游工具RawFastq获取。（必传参数）

<label id='minLength'> </label>
#### **页面显示参数 minLength**
序列最小长度
参数说明：
根据序列长度进行过滤，小于设定值的序列会被过滤掉。默认值为50

<label id='BaseNLimit'> </label>
#### **页面显示参数 BaseNLimit**
如果一条序列中N碱基的数量超过NbaseLimit，这条序列会被过滤掉。默认值为5

<label id='QualifiedQuality'> </label>
#### **页面显示参数 QualifiedQuality**
根据碱基质量进行过滤，小于设定值的序列会被过滤掉。默认值为15

<label id='adapterforRead1'> </label>
#### **页面显示参数 adapter for Read1**
过滤左端序列接头

<label id='adapterforRead2'> </label>
#### **页面显示参数 adapter for Read2**
过滤右端序列接头

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

<label id='WindowSize'> </label>
#### **页面显示参数 WindowSize**
滑窗裁剪窗口大小。对滑动窗口中的碱基计算平均质量值，然后将不符合的滑窗直接剪裁掉。

<label id='WindowMeanQuality'> </label>
#### **页面显示参数 WindowMeanQuality**
滑窗裁剪指定平均质量值

<label id='TrimFront_R1'> </label>
#### **页面显示参数 TrimFront_R1**
剪除左端序列起始的低质量碱基数量

<label id='TrimFront_R2'> </label>
#### **页面显示参数 TrimFront_R2**
剪除右端序列起始的低质量碱基数量

<label id='TrimTail_R1'> </label>
#### **页面显示参数 TrimTail_R1**
剪除左端序列末端的低质量碱基数量

<label id='TrimTail_R2'> </label>
#### **页面显示参数 TrimTail_R2**
剪除右端序列末端的低质量碱基数量

<label id='MaxLen1'> </label>
#### **页面显示参数 MaxLen1**
左端序列经过trim后最长长度

<label id='MaxLen2'> </label>
#### **页面显示参数 MaxLen2**
右端序列经过trim后最长长度

<label id='SplitType'> </label>
#### **页面显示参数 SplitType**
对输出的FASTQ进行切分，分成大小均匀的多个文件，这样可以使用比对软件并行地比对，提高并行处理的速度。fastp软件提供两种模式，分别是指定切分后文件的个数，或者指定每个切分后文件的行数。

<label id='SplitParts'> </label>
#### **页面显示参数 SplitParts**
默认值40

<label id='SplitLines'> </label>
#### **页面显示参数 SplitLines**
默认值8000000
