# BedIntersection
　　BedIntersection是对Bed文件进行合并或交集软件。
　　bedtools官网：http://bedtools.readthedocs.io/en/latest/content/tools/intersect.html#wa-reporting-the-original-a-feature
<div style="text-align:center"><img data-src="1.png" width="400px"  ></img></div>
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件</span>**
　　输入Bed文件，同时也可以是GTF,VCF,BED,GFF3格式文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置<span>**
**MergeBed：**MergeBed将文件对比中group1和group２两个Bed文件合并。
　　　　　　　IntersectBed将文件对比中group1和group２两个Bed做交集。

**数据结果样式：**
　AllInfo：A和B交集，并把原始文件都输出。
　overlap：只有overlap的区域
　AFileInfo：overlap中A的序列
　BFileInfo：overlap中B的序列
　A&Boverlap：A与B做交集，输出所有A序列，并输出与之交集的B序列，以及没有交到B的A序列，B中显示为0。
　A&Boverlaplength：A与B做交集，输出与B有交集的A序列、交集的B序列、overlap序列长度,不显示没有交到的A序列。
　A&overlaplength：输出与B有交集的A序列，并输出交集的序列条数。
　A（no_overlap）：输出和B没有交集的A序列

**Minimum overlap：**设置最小overlap区域，长序列和短序列的比例。默认值0.00000001。
**文件比对：**
　group1Array：选择对比组A
　group2Array：选择对比组B
　outFileArray：输出名称。

**containerNumber：**软件运行时，使用container数。

***
#### **<i class="fa fa-pencil-square-o" aria-hidden="true" style="color:#3B9C9C"></i> <span style="color:#3B9C9C">附加说明<span>**
　**AFileInfo：**
```
$ cat A.bed
chr1  10  20
chr1  30   40

$ cat B.bed
chr1  15  20

$ bedtools intersect -a A.bed -b B.bed -wa
chr1  10   20
```

　**BFileInfo：**
```
$ cat A.bed
chr1  10  20
chr1  30  40

$ cat B.bed
chr1  15   20

$ bedtools intersect -a A.bed -b B.bed -wb
chr1  15  20  chr 15  20
```

　**A&Boverlap：**
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

　**A&Boverlaplength：**
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
　**A&overlaplength：**
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
　**A（no_overlap）：**
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
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明<span>**
<div style="text-align:center"><img data-src="2.png" width="900px"/></img><div>

