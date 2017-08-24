# Samtools
　　Samtools是一系列处理Bam格式序列的应用。它从SAM(Sequence Alignment/Map)格式输入或者输出为Sam格式，可以进行排序，合并和建立索引，并且允许快速地检索任意区域的reads。Bam文件优点：Bam文件为二进制文件，占用的磁盘空间比Sam文本文件小；利用Bam二进制文件的运算速度快。
　　官网：http://samtools.sourceforge.net/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　在inputFile处输入Sam和Bam文件，输出为sort.bam，in.bam.bai。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='isSortBam'>sortBam：</label>Bam文件排序。只能对bam文件进行sort, 不能对sam文件。
　<label id='isIndexBam'>indexBam：</label>构建索引。必须对bam文件进行默认情况下的排序后，才能进行index。
　<label id='removeDuplicate'>removeDuplicate：</label>去除Duplicate序列。
　
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　　排序的结果文件为sort.bam；
　　对bam文件建立index结果文件名为in.bam.bai。
