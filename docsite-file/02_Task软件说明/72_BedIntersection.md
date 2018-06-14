# BedIntersection
　	对Bed格式文件进行合并或者取交集。
  **功能：**
　	Bed文件是对基因组或者reads的位置信息进行注释的结果文件。该task使用intersectBed软件，可对多个Bed文件取交集（即overlap）。譬如ChIP-Seq中，我们得到两个不同的转录因子所富集的reads序列，每条reads在基因组上的位置信息即为Bed文件，通过该task可对上述所有reads取交集，从而获得两个转录因子都可结合的基因组序列。
**使用软件:**
　　**bedtools：**BEDTools可用于基因组特征（genomic features）的比较和相关操作，并可对基因序列进行注释。
**官网：**http://bedtools.readthedocs.io/en/latest/
**应用范围:**
　	用来获取两个Bed文件中的overlap。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件</span>**
　　该Task的输入数据通常是Bed文件，同时也可以是GTF,VCF,GFF3格式文件。 
**inputFile：**输入文件格式可以是bed格式文件，也可以是如下表所示的格式文件：

| #chr   |  start  |(-10*log10(pvalue)|fold_enrichment|Symbol|
| -------- |  :----: | :----:  |  :----: | :----: |
| chr1     |  3483406 |3483946 |33|5.91|LOC102640548|
| chr1     | 3486866   |3487414|32.48|5.91|LOC102640548|
| chr1     |  3492146  |3492581|34.49|5.91|LOC102640548|
|chr1　|3493785|3494363　|30.63|4.22|LOC102640548|
**注意：**
1.输入列表中要有一行title信息，对于title名称无特殊要求；
2.输入列表中必须要有三列信息，即染色体、起始位置、终止位置。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件</span>**
合并信息或者取交集信息后文件（*.bed）。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置<span>**
<label id='merge'>MergeBed：</label>选择处理文件方式，其选项有：
　 **MergeBed：**将文件对比中group1和group２两个Bed文件合并。
　 **IntersectBed：**将文件对比中group1和group２两个Bed文件取交集。
<label id='outType'>输出结果样式：</label>
　 **AllInfo：**A文件和B文件取交集，并把原始文件都输出。
　 **overlap：**只输出两个文件中的overlap信息。
　 **AFileInfo：**overlap中A文件的信息。
　 **BFileInfo：**overlap中B文件的信息。
　 **A&Boverlap：**A文件与B文件取交集，输出所有A文件信息，并输出与B文件有overlap的信息，以及没有交到B文件的A文件信息，B中显示为0。
　 **A&Boverlaplength：**A文件与B文件取交集，输出与B文件有交集的A文件信息、overlap的B文件信息和overlap次数,不显示没有交到的A文件信息。
　 **A&overlaplength：**输出与B文件有交集的A文件信息，并输出交集信息的overlap次数。
　 **A（no_overlap）：**输出和B文件没有交集的A文件信息。
**Minimum overlap：**设置发生overlap的两个区域长度的最小比值，超过这个比值的在结果文件中输出出来。
**文件比对：**设置比对组
　**group1Array：**选择对比组A；
　**group2Array：**选择对比组B；
　**outFileArray：**输出名称。
**containerNumber：**软件运行使用container数。
**结果文件**
\* .bed：合并信息或者取交集信息后文件。。
***
#### **<i class="fa fa-pencil-square-o" aria-hidden="true" style="color:#3B9C9C"></i> <span style="color:#3B9C9C">详细说明<span>**
　**几种输出结果的格式：**
 **1、AFileInfo：**
```
$ cat A.bed
chr1  10  20
chr1  30   40

$ cat B.bed
chr1  15  20

$ bedtools intersect -a A.bed -b B.bed -wa
chr1  10   20
```

　**2、BFileInfo：**
```
$ cat A.bed
chr1  10  20
chr1  30  40

$ cat B.bed
chr1  15   20

$ bedtools intersect -a A.bed -b B.bed -wb
chr1  15  20  chr 15  20
```

　**3、A&Boverlap：**
```
$ cat A.bed
chr1    10    20
chr1    30    40

$ cat B.bed
chr1    15  20
chr1    18  25

$ bedtools intersect -a A.bed -b B.bed -wao
chr1    10    20    chr1    15  20  5
chr1    10    20    chr1    18  25  2
chr1    30    40    .       -1  -1  0
```

　**4、A&Boverlaplength：**
```
$ cat A.bed
chr1    10    20
chr1    30    40

$ cat B.bed
chr1    15  20
chr1    18  25

$ bedtools intersect -a A.bed -b B.bed -wo
chr1    10    20    chr1    15  20  5
chr1    10    20    chr1    18  25  2
```
　**5、A&overlaplength：**
```
$ cat A.bed
chr1    10    20
chr1    30    40

$ cat B.bed
chr1    15  20
chr1    18  25

$ bedtools intersect -a A.bed -b B.bed -c
chr1    10    20    2
chr1    30    40    0
```
　**6、A（no_overlap）：**
```
$ cat A.bed
chr1  10  20
chr1  30  40

$ cat B.bed
chr1  15  20

$ bedtools intersect -a A.bed -b B.bed -v
chr1  30   40
```
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 参考文献<span>**
Quinlan AR, Hall IM. BEDTools: A flexible suite of utilities for comparing genomic features. Bioinformatics. 2010;26:841–2. doi: 10.1093/bioinformatics/btq033. [PMC free article] [PubMed][Cross Ref]

