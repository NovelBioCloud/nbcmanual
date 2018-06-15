# Prodigal
　　对于基因组中的蛋白质编码基因预测，传统的方法是使用实验方法进行验证，但是这种方法费时费力，且带有较大的盲目性。因此，基因组注释不可避免的要依靠自动化注释软件来对大规模的基因序列进行分析和注释。
**功能：**
	&nbsp;&nbsp;&nbsp;&nbsp;prodigal主要应用于细菌和古生菌的基因预测，不能用于真核生物。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**prodigal：**全称是Prokaryotic Dynamic Programming Genefinding Algorithm，即原核的动态编程基因查找算法，由Oak Ridge National Laboratory和University of Tennessee-Knoxville 于2007年联合开发。
**软件官网：**https://github.com/hyattpd/Prodigal
**应用范围:**
		&nbsp;&nbsp;&nbsp;&nbsp;prodigal主要应用于细菌和古生菌的基因预测，不能用于真核生物，如果要对meta样品做基因预测，prodigal还专门提供了meta的版本。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是SPAdes的结果文件，如：scaffolds.fasta。
　  **inputFile：**组装后序列文件，文件格式为fasta格式。 
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;基因预测结果文件（\*.gff或者*.gbk）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

<label id='outputFormat'>Output Format：</label>选择输出文件格式，选择值有gbk、gff、sco。
&nbsp;&nbsp;&nbsp;&nbsp;gbk：Genbank-like feature table格式，详细说明请见：http://www.insdc.org/files/feature_table.html
&nbsp;&nbsp;&nbsp;&nbsp;gff：Generic Feature Format Version 3，细说明请见：https://github.com/The-Sequence-Ontology/Specifications/blob/master/gff3.md。
&nbsp;&nbsp;&nbsp;&nbsp;sco：Simple coordinate output，详细说明请见：http://tico.gobics.de/ioexamples.jsp
<label id='closedEnds'>Exclude Run off Edges Gene：</label>不允许基因一边断开，也就是要求完整的开放阅读框（Open Read Frame,ORF），含有起始和终止结构。
<label id='tranTable'>Translation Table：</label>指定翻译表编码，默认为11。
<label id='treatN'>Treat N as masked Seq：</label>屏蔽基因组中含N碱基序列。
**containerNumber：**软件运行时，使用container数。

***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\*.gff/\*.gbk/*.sco：**注释后结果文件。
***
**参考文献：**
1.	Hyatt D, Chen G-L, Locascio PF, Land ML, Larimer FW, Hauser LJ. Prodigal: prokaryotic gene recognition and translation initiation site identification. BMC Bioinformatics. 2010;11:119. doi: 10.1186/1471-2105-11-119. [PMC free article] [PubMed] [Cross Ref]
