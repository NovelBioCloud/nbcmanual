# GetmiRNASeq
　　通过miRNA名称或者注释文件从参考序列文件中提取miRNA序列。
**功能：**
1.提取物种所有的miRNA序列。
2.提取物种指定miRNA名称的序列。
**使用软件：**
　　	**GetmiRNASeq：**NovelBio编写java代码实现根据miRNA的名称提取miRNA序列的功能。
**应用范围：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;提取物种所有miRNA序列，或者根据输入的miRNA名称提取miRNA的序列。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是miRNA名称列表，文件格式为txt。 
**GeneList：**如果从数据库序列和注释文件中提取所有的miRNA序列，则该处可以为空。如果提取指定miRNA序列，则该处需要输入miRNA名称（或者位置等信息）列表，如：
<div style="text-align:center">
	<img data-src="1.jpg" width="200px" ></img>
</div>
注意：
(1)	要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
(2)	输入表格中，必须要有一列为miRNA基因名称，其他列信息可有可无。
**AllCounts：** miRNA表达量的总表（\* .All.Counts.exp.txt）。
&nbsp;&nbsp;&nbsp;&nbsp;用途：该表中含有miRNA序列信息，可直接从中进行序列提取，适用于提取novel预测和梯度比对的结果。
&nbsp;&nbsp;&nbsp;&nbsp;格式：miRNAMapping的结果文件列表，如：
<div style="text-align:center">
	<img data-src="2.jpg" width="600px" ></img>
</div>
注意：
(1)	要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
(2)	输入表格中，第一列为miRNA基因名称，第二列为前体miRNA，第三列为miRNA 序列信息，第四列以及之后列都是miRNA样本中的表达情况，这些表达量信息可有可无。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;提取到的指定miRNA序列文件，以fasta格式存储。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>版本：</label>参考序列的版本。
<label id='isGetAllSeq'>GetAllSeq：</label>勾选后根据参考序列输出所有的miRNA序列，不勾选输入文件列中的miRNA序列。
<label id='GeneCol'>GeneCol：</label>设置需要提取序列的基因所在的列号。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**　
**\*.fa：**提取到的miRNA序列文件，以fasta文件格式存储。如：
<div style="text-align:center">
<img data-src="3.jpg" width="600px" ></img>
</div>&nbsp;