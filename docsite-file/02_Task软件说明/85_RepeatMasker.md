# RepeatMasker
　　生物的基因组中，特别是高等生物的基因组中含有大量的重复序列，根据重复序列在基因组中的分布形式可将其分为串联重复序列（Tandem Repeats Sequence，TRS）和散布重复序列（Dispersed Repeats Sequence，DRS）。其中，串联重复序列是由相关的重复单位首尾相连、成串排列而成的。发现的串联重复序列主要有两类：一类是由功能基因组成的（如rRNA和组蛋白基因）；另一类是由无功能的序列组成的。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;RepeatMasker是一款专门用于基因组重复序列识别注释，并分类统计的软件，几乎用于所有物种。是研究基因组、非编码RNA、转座子和着丝粒的有力工具。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**RepeatMasker：**是一个屏蔽DNA序列中转座子重复序列和低复杂序列的程序，由Arian Smit和Robert Hubley开发，它将输入序列中已知的重复序列都屏蔽为N或X，并给出相应的重复序列统计列表。一般情况下，人的基因组数据大约56%会被该程序屏蔽。RepeatMasker可以选择nhmmer、cross_match、ABBlast/WUBlast、RMBlast或Decypher作为比对的搜索引擎，数据库选用Dfam和Repbase。
**软件官网：**http://www.repeatmasker.org/
**应用范围:**
	&nbsp;&nbsp;&nbsp;&nbsp;RepeatMasker是一款广泛应用于基因鉴定和分类的软件，可屏蔽低复杂度序列和散布重复序列。它通过将输入的基因组序列与数据库（如Repbase）中已知的重复序列进行比对，来搜索其中的重复序列。


***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据通常是组装的基因组序列文件，如SPAdes的结果文件\*.scaffolds.fasta。
　  **inputFile：**组装后序列文件，文件格式为fasta格式。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;将重复序列区用N或者X替换后的基因组序列文件（* .masked）。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**ThreadNum：**设置软件运行时使用的线程数。
**Species：**所分析序列的物种名称。
**Slow Search：**是否使用低速检索算法。
**Quick Search：**是否使用快速检索算法。
**No simple repeats mark：**不标记简单重复序列。
**Olny mask simple repeats：**只标记简单重复序列。
**Not mask small RNA：**不标记小RNA或者假基因。
**Skips Bacterial Insertion：**跳过细菌插入的序列。
**Complete Lower Case：**把序列改为小写。
**Repetitive Lowercase：**把重复序列改为小写。
**Masked Repeat with Xs：**重复区域用X代替。
**containerNumber：**软件运行时，使用container数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1）	**\*.out.gff：**重复序列基因组注释文件，与基因注释类似。
2）	**\*.tbl：**重复序列注释结果报告信息汇总(overview)表格。
3）	**\*.out.html: **网页版详细结果，同RepeatMasker在线注释结果报告。
4）	**\*.masked: **将重复序列区用N或者X替换后的基因组序列文件。
5）	**\*.out：**RepeatMasker默认输出结果格式，信息基本与gff相关。
6）	**\*.cat.gz:** 输入序列与重复序列数据库比对的文件。
***



**参考文献：**
1.	Smit A., Hubley R., Green P. RepeatMasker Open-3.0. 2004. Seattle (WA): Institute for Systems Biology; 2004.
