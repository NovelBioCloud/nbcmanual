# Intersection
　　对两个基因表格进行交集及并集分析，并生成Venn图。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;根据两个表格中的某列信息，将两个文件的其他列进行合并。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**Intersection：**NovelBio编写java代码，实现根据两个表格中的某列值，将两个文件的其他列进行合并的功能。
**应用范围:**
	&nbsp;&nbsp;&nbsp;&nbsp;通常用于对两个文件中的信息进行合并，或获取两个文件中共有或者特有值（如：基因、SNP等）的操作。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是需要进行文件合并或者分析差异的文件。
**inFileName：**需要进行文件合并或者分析差异（共有信息或者特有信息）的文件。将需要做交集的表格拖入右侧inFileName中，“组名”为交集的结果中展示的每组名称；“交集列”是需要保留原表格的列的信息，中间以空格隔开，例如： 结果需要保留３、４、５列，填写３ ４ 5；“文件名”为输入文件的名称。
注意：对于输入的表格要求必须有title行，对于title名称无特殊要求。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;合并信息后的文件列表（intersection.txt）以及绘制得到的venn图（intersection.png）。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**CompareID：**设置需要根据哪些列信息进行信息合并，如果多列可用空格隔开，如“1 2 3 4”，表示两个表中的第1列、第2列、第3列和第4列都相同的，则认为是两个表中共有的，并将两个表中的信息合并成一行信息。
**Memory：**程序运行过程中所使用的内存大小，以M为单位。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)	**intersection.png：**交集Venn图，如：
<div style="text-align:center">
	<img data-src="1.jpg" width="300px" ></img>
</div>
2)	**intersection.txt：**合并信息后得到的列表。

