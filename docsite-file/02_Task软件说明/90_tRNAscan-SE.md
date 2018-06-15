# tRNAscan-SE
　　tRNAscan-SE能在基因组水平上进行tRNA扫描。该软件实际上是一个perl 脚本，整合了tRNAscan、EufindRNA 和Cove 这3个独立的tRNA检测软件。
**功能：**
	&nbsp;&nbsp;&nbsp;&nbsp;基因组上预测tRNA的序列。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**tRNAscan-SE：**tRNAscan-SE 首先调用 tRNAscan和EufindRNA鉴定基因组序列中 的tRNA区域，然后调用Cove进行验证。前者保证了鉴定的灵敏性， 后者则保证了较低的假阳性概率，同时使搜索速度得到了提升。
	**软件官网：**http://lowelab.ucsc.edu/tRNAscan-SE/


**应用范围:**
		&nbsp;&nbsp;&nbsp;&nbsp;tRNAscan-SE主要应用于细菌基因组和宏基因组的tRNA预测。


***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是SPAdes的结果文件，如scaffolds.fasta。
　  **inputFile：**组装后序列文件，文件格式为fasta格式。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;预测tRNA结果文件（* tRNA.txt）。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='type'>Type：</label>设置需要分析物种所属的分类，其选项有:
（1）	细菌：当输入序列是细菌的序列时，选择该值。
（2）	古细菌：当输入序列是古细菌的序列时，选择该值。
（3）	混合序列：当输入序列是古细菌、细菌和真核生物的混合序列时，选择该参数值，该参数使用general tRNA covariance model。
（4）	线粒体/叶绿体：当输入序列是线粒体或者叶绿体的序列时，选择该参数值。如果选择该参数，则仅使用Cove进行分析，搜索速度会很慢，同时也不能给出假基因（pseudogenes）检测结果。
**containerNumber：**软件运行时，使用container数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1）	**\*.tRNA.txt：**注释出来的tRNA位置信息。
2）	**\*.stats.txt：**统计结果文件，其中包括输入序列的统计信息和注释后tRNA的统计信息，如：
<div style="text-align:center">
	<img data-src="1.jpg" width="600px" ></img>
</div>
注：（1）tRNAscan-SE 的结果中, 如果 begin 比 end 的值大，则表示 tRNA 在负义链上。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（2）有些结果中第5 列为 pseudogene， 表示其一级或二级结构比较差。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（3）最后一列是Cove Score，该分值最低阈值为20。该值是一个对ratio值取对数的log值。此处的ratio 是符合 tRNA 协方差模型概率与随机序列模型概率的比值。
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;（4）最后最好将表格格式转换为GFF3格式，以利于在基因组上的可视化展现。
3）	**\*.ss.txt：**预测的tRNA二级结构，文件中的二级结构使用大于号或小于号表示互补配对区域，使用点号表示环形域或非互补配对区域。
***
**参考文献：**
1.	Lowe T.M., Eddy S.R. tRNAscan-SE: a program for improved detection of transfer RNA genes in genomic sequence. Nucleic Acids Res. 1997;25:955–964. [PMC free article] [PubMed]


  
  
