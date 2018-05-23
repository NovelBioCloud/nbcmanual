# GetSequence
　　通过基因名称、序列位置、基因结构等从参考序列文件中提取指定序列。
**功能：**
1.提取基因（全长、CDS、EXON、INTRON、UTR5/UTR3等）序列。
2.提取所有转录本序列。
3.提取指定染色体区域的序列。
4.提取指定位置上下游设定值区域序列。
**使用软件:**
　　	**GetSequence：**该软件由NovelBio研发团队编写java代码开发而成，可根据不同需求提取指定序列。
**应用范围**
根据参数设置，提取指定区域的序列。
***

#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是基因名称（或含有位置信息）列表，文件格式为txt。 
**lnputFile：**如果从数据库序列和注释文件中提取所有的基因全长或者所有基因的CDS等区域的序列，则该处可以为空。如果提取指定基因序列，则该处需要输入基因名称（或者位置等信息）列表，该输入文件可以是以下几种类型：
1. 如果按照基因名称以及注释文件（GTF）提取基因全长或者CDS区域或者EXON区域等，输入文件中包含基因名称信息即可，如：
<div style="text-align:center">
	<img data-src="1.jpg" width="200px" ></img>
</div>
2. 如果提取染色体上指定位置（指定起始位置和终止位置）的序列，输入文件中必须含有“染色体”、“起始位置”和“终止位置”的信息，如：
<div style="text-align:center">
	<img data-src="2.jpg" width="500px" ></img>
</div>
3. 如果提取染色体上指定位置上下游指定长度的序列，输入文件中必须含有“染色体”、“位置”的信息，如：
<div style="text-align:center">
	<img data-src="3.jpg" width="400px" ></img>
</div>
注意：对于以上的所有输入表格要求输入的表格中要有一行title，对于每列的title名称，无特殊要求。&nbsp;

**参考基因组序列：**需要提取的物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
 **gtfFile：**需要提取物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中，则不需要输入该文件。
***

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;提取到的指定区域的序列文件，以fasta格式存储。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，通过该参数可选择特定数据库gtf文件。
**Genomewide：**提取该物种的整个基因组序列，如果选中此项，参数“lnputFile”可为空，否则“lnputFile”不能为空。
**获取所有的ISO：**获取所有转录本序列。
**获取Aminoacid：**获取氨基酸序列，即将结果以氨基酸序列形式输出。
**geneStructure：**按基因结构选择需要提取部分，当参数“Genomewide”选中时，或者当参数“seqType”选值为“Gene”时，该参数显示出来并有效，该参数值有ALLLENGTH、TSS、TES、ATG、UAG、CDS、EXON、INTRON、UTR5、UTR3。
**SeqType：**选择按照什么方式提取序列，当参数“Genomewide”不选中时，该参数显示并有效，其选项有Region、Site、Gene。
**染色体列号：**设置染色体在输入文件中的列号，当参数“SeqType”的选项值为“Region”或者“Site”时，该参数显示并有效。
**Start列号：**设置需要提取序列的起始位置所在的列号，当参数“SeqType”的选项值为“Region”时，该参数显示并有效。
**End列号：**设置需要提取序列的终止位置所在的列号，当参数“SeqType”的选项值为“Region”时，该参数显示并有效。
**Site列号：**设置需要提取序列的位置所在的列号，当参数“SeqType”的选项值为“Site”时，该参数显示并有效。
**位点上游：**设置需要提取序列位置上游长度，当参数“SeqType”的选项值为“Site”时，该参数显示并有效。
**位点下游：**设置需要提取序列位置下游长度，当参数“SeqType”的选项值为“Site”时，该参数显示并有效。
**基因列号：**设置需要提取序列的基因所在的列号，当参数“SeqType”的选项值为“Gene”时，该参数显示并有效。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\*.fa：**提取到的序列文件，以fasta文件格式存储。