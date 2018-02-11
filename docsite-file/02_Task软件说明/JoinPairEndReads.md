# JoinPairEndReads
　　16S扩增子测序数据主要来自HiSeq2500产出的双端各250 bp (PE250)数据，读长长且价格便宜(性价比高)。HiSeqX PE150和MiSeq PE300也比较常见，但PE150读长过短且分辨率低，而PE300价格高且末端序列质量过低，因此推荐度不及PE250。在PE250测序中，reads右端的尾部碱基质量下降比较严重，但只要左端的碱基质量较好，即可将双端序列合并并进行校正，经过校正的序列可有效用于后续分析。
**功能：**
　　对PE reads的双端序列进行合并。
**使用软件：**
**fastq-join：**根据reads两侧序列末端的互补配对，可以合变为我们扩增区域的序列，同时还可以对重叠区的碱基质量进行校正，保留最高测序质量的碱基。
**软件官网：**
https://code.google.com/p/ea-utils/wiki/FastqJoin
**应用范围**
&nbsp;&nbsp;&nbsp;&nbsp;对PE reads双端序列进行校正合并，通常只对合并后的*.join 格式文件进行后续分析。
****

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据来源于fastq格式文件，最终生成合并后的序列文件。
**leftInputData：**测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz
**rightInputData：**测序右端reads序列。单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;合并后序列文件，以fastq文件格式存储，可作为FastQC的输入文件。
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**Min Overlap：**overlap 最少碱基数，默认值为6bp。
**MaxDifPercent：**最大差异百分比（即两条序列的重叠区域，差异碱基所占的百分比），默认值为8%。
****

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
1)	**\*.fq.join：**合并后的序列文件。
2) **\*.fq.un1：**左端合并成功的序列。
3)	**\*.fq.un2：**右端合并成功的序列。
