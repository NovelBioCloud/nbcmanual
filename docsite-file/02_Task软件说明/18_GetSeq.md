# GetSeq
　　通过基因名称、序列位置、基因结构等从参考序列文件中提取基因的序列。
**功能：**
1. 提取基因（全长、CDS、EXON、INTRON、UTR5/UTR3等）序列。
2. 提取所有转录本序列。
3. 提取指定染色体区域的序列。
4. 提取指定位置上下游设定值区域序列。

**使用软件:**
　　	**GetSeq：**该软件由NovelBio研发团队编写java代码开发而成，可根据不同需求提取指定序列。
**应用范围**
&nbsp;&nbsp;&nbsp;&nbsp;根据参数设置，提取指定区域的序列。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是基因名称（或含有位置信息）列表，文件格式为txt。 
**lnputFile：**如果从数据库序列和注释文件中提取所有的基因全长或者所有基因的CDS等区域的序列，则该处可以为空。如果提取指定基因序列，则该处需要输入基因名称（或者位置等信息）列表，该输入文件可以是以下几种类型：
1.	如果按照基因名称以及注释文件（GTF）提取基因全长或者CDS区域或者EXON区域等，输入文件中包含基因名称信息即可，如：
<div style="text-align:center">
	<img data-src="1.jpg" width="200px" ></img>
</div>
2.	如果提取染色体上指定位置（指定起始位置和终止位置）的序列，输入文件中必须含有“染色体”、“起始位置”和“终止位置”的信息，如：
<div style="text-align:center">
	<img data-src="2.jpg" width="400px" ></img>
</div>
3.	如果提取染色体上指定位置上下游指定长度的序列，输入文件中必须含有“染色体”和“位置”的信息，如：
<div style="text-align:center">
	<img data-src="3.jpg" width="300px" ></img>
</div>
注意：对于以上的所有输入表格，要求输入的表格中要有一行title，对于每列的title名称，无特殊要求。
**参考基因组序列：**需要提取的物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
 **gtfFile：**需要提取物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中，则不需要输入该文件。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;提取到的指定区域的序列文件，以fasta格式存储。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>版本：</label>参考序列的版本。
<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，通过该参数可选择特定数据库的gtf文件。
<label id='chrIdCol'>染色体所在列号：</label>染色体信息在输入文件中的列号。
<label id='getAllIso'>获取所有的ISO：</label>是否获取所有转录本序列。
<label id='getmiRNA'>获取miRNA：</label>是否获取miRNA序列。
**SeqType：**选择按照什么方式提取序列，当参数“Genomewide”不选中时，该参数显示并有效，其选项有：Region、Site、Gene。
<label id='startCol'>开始：</label>需要提取序列的起始位置在输入文件中所在的列号。
<label id='endCol'>结束：</label>需要提取序列的终止位置在输入文件中所在的列号。
<label id='genomwide'>Genomewide：</label>提取该物种的整个基因组序列。
<label id='geneStructure'>基因结构：</label>按基因结构选择需要提取部分，该参数值有：ALLLENGTH、TSS、TES、ATG、UAG、CDS、EXON、INTRON、UTR5、UTR3。
<label id='tssUp'>转录起始位点-上游：</label>设置提取转录起始位点上游碱基数。
<label id='tssDown'>转录起始位点-下游：</label>设置提取转录起始位点下游碱基数。
<label id='getAminoacid'>&获取Aminoacid：</label>获取氨基酸序列，即将结果以氨基酸序列形式输出。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
**\*.fa：**提取到的序列文件，以fasta文件格式存储。
