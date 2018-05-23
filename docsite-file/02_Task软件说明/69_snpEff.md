# snpEff
　　SNP（Single Nucleotirle Polymorphisms）是指在基因组水平上由于单个核苷酸的变异而产生的DNA序列多态性。SNP位点通过数据库可对SNP位点进行注释，得到包括染色体上的位置，基因名称以及序列标注等信息。
**功能：**
	&nbsp;&nbsp;&nbsp;&nbsp;进行SNP/Indel的注释分析。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**SnpEff：**SnpEff是一个进行变异注释和突变影响程度预测的软件。
**软件官网： **http://snpeff.sourceforge.net/SnpEff_manual.html
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;应用于外显子、基因组、转录组等测序数据的SNP/Indel注释。


***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是变异检测的结果vcf文件。	
**chrSeq：**需要分析的参考基因组序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
**inputFile：**SNP/Indel突变结果文件。
(1) 输入文件可以是标准的vcf文件格式，如：
<div style="text-align:center">
	<img data-src="1.png" width="800px" ></img>
</div>
VCF的详细说明请见官方文档：http://samtools.github.io/hts-specs/VCFv4.2.pdf
(2) 输入文件也可以是没有vcf 头部注释信息的列表文件，如：
<div style="text-align:center">
	<img data-src="2.jpg" width="800px" ></img>
</div>
注意：
1.	要求输入的表格要有一行title，对于每列的title名称无特殊要求；
2.	输入表格中，必须要有如表中所示的前五列信息，即突变所在染色体信息、突变位置信息、ID、在基因组上碱基和突变后的碱基信息，其他信息可有可无。&nbsp;

**gtfFile：**需要分析的参考基因组注释（gtf）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;注释后结果文件列表（*snpEff.txt）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，通过该参数可选择特定数据库gtf文件。
**ChrID列号：**染色体信息在输入文件中所在的列号。
**containerNumber：**运行过程中使用的container数。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)	**\*.snpEff.txt：**注释后结果文件。
2)	**\*.summary.html：**突变统计信息，可使用浏览器打开。
3)	**\*.summary.genes.txt：**从基因层面统计突变信息。
***

**参考文献：**
1.	Cingolani P, Platts A, Wang LL, Coon M, Nguyen T, Wang L, Land SJ, Lu X, Ruden DM. A program for annotating and predicting the effects of single nucleotide polymorphisms, SnpEff: Snps in the genome of drosophila melanogaster strain w1118; iso-2; iso-3. Fly. 2012;6(2):80–92. doi: 10.4161/fly.19695.
