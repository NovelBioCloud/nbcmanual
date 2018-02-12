# Prokka
　　对于基因组中的蛋白质编码基因预测，传统的方法是使用实验方法进行验证，但是这种方法费时费力，且带有较大的盲目性。因此，基因组注释不可避免的要依靠自动化注释软件来对大规模的基因序列进行分析和注释。细菌基因组、宏基因组的基因注释一直是一个非常复杂的问题，而Prokka的出现很好的解决了这一问题。
**功能：**
	&nbsp;&nbsp;&nbsp;&nbsp;prokka主要应用于细菌基因组和宏基因组基因预测，不能用于真核生物。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**prokka：**全称rapid prokaryotic genome annotation，即快速的原核生物基因组注释软件，Prokka由澳大利亚莫纳什大学开发，是一款利用Perl算法实现原核生物基因组快速注释的软件，它产生标准兼容的输出文件以进行进一步分析或者在基因组浏览器中查看。
**软件官网：**
http://www.vicbioinformatics.com/software.prokka.shtml
**应用范围:**
		&nbsp;&nbsp;&nbsp;&nbsp;prokka主要应用于细菌基因组和宏基因组的基因预测，不能用于真核生物。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是SPAdes的结果文件，如：scaffolds.fasta。
　  **inputFile：**组装后序列文件，文件格式为fasta格式。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;基因预测结果文件（*.gff）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**threadNum：**设置软件运行时使用的线程数。
**Add Genes：**在注释的gtf文件中是否添加基因注释信息，如果选中表示添加Gene信息。
**Add mRNA：**在注释的gtf文件中是否添加mRNA的注释信息，如果选中表示添加mRNA的信息。
**Kingdom：**设置所分析物种所属的界名称。
**Genus：**设置所分析物种所属的属名称。
**Species：**设置所分析物种所属的种名称。
**No rRNA：**选择是否注释出rRNA，如果选中表示不注释出rRNA。
**No trna：**选择是否注释出tRNA，如果选中表示不注释出tRNA。
**containerNumber：**软件运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1）**\*.gff：**注释结果gff格式文件，包括注释信息和序列信息。
2）**\*.txt：**注释后统计结果文件，其中包括contigs数量、总碱基个数、tRNA数量、基因数量以及CDS数量等信息。
3）**\*.fna：**输入的原始fasta格式文件，为核酸序列。
4）**\*.faa：**将CDS序列翻译为氨基酸的序列文件。
5）**\*.ffn：**所有转录本核酸序列。
6）**\*.fsa：**有sqn描述的核酸序列，可用于使用tbl2asn软件生成sqn文件。
7）**\*.tbl：**特征表，该文件用于使用tbl2asn软件生成sqn文件。
8）**\*.sqn：**用于提交到NCBI的格式文件。
9）**\*.gbk：**Genbank格式文件，来自于注释的gff文件。
10）**\*.log：**输出的软件运行日志信息。
11）**\*.tsv：**所有注释基因特征表格。
***
**参考文献：**
1.	Seemann T. Prokka: rapid prokaryotic genome annotation.  Bioinformatics.  2014;30(14):2068–9. doi: 10.1093/bioinformatics/btu153. [PubMed] [Cross Ref]





