# Blast
　　Blast能够实现比较两段核酸或者蛋白序列之间的同源性的功能，它能够快速地找到两段序列之间的同源序列，并对比对区域进行打分以确定同源性的高低。Blast的运行方式是先用目标序列建数据库（这种数据库称为database，里面的每一条序列称为subject），然后用待查的序列（称为query）在database中搜索，每一条query与database中的每一条subject都要进行双序列比对，从而得出全部比对结果。
  **功能：**
  快速地找到两段序列之间的同源序列。

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 使用软件**
**BLAST**: 是“Basic Local Alignment Search Tool”的缩写，即局部序列比对基本检索工具，是由美国国立生物技术信息中心（NCBI）开发的一个基于序列相似性的数据库搜索程序，Blast是一个程序包，其中包含了很多个独立的程序，这些程序是根据查询的对象和数据库的不同来定义的。
	**软件官网**：https://blast.ncbi.nlm.nih.gov/Blast.cgi
   **应用范围**：Blast通过两两比对，找到数据库中与输入序列最相似的序列，或者是最相似的序列片段。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
该Task的输入数据是序列文件，是fasta格式文件。
**querySeq**：查询序列fasta文件，当querySeq为空时，只对subjectSeq序列进行建索引的操作，不会进行比对分析。
 **subjectSeq/BlastDB**：目标序列fasta文件（即作为比对对象数据库的序列文件）或者是BlastDB文件，，BlastDB表示，该比对对象的数据库序列文件的索引文件是已经存在的，注意：当输入是已经存在有索引的序列文件时，在参数设置时需要勾选“BlastNR”。
 #### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
比对后结果文件（txt）。　　
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='mappingTo'>blast To：</label>
　　　　　　Chromosome：比对到所选物种的genome序列上。
　　　　　　refSeq_All_Iso：比对到所选物种的所有转录组序列上。
　　　　　　refSeq_One_Iso：比对到所选物种的每个基因上的最长的一条转录本上。
　<label id='mappingTo'>结果格式：</label>选择blast比对后结果文件输出格式。其选项有以下两个：
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ResultType_Simple：简单结果格式，不显示比对结果的一致性。选择该参数值时，相当于blast的“-outfmt”值设置为“6”。一般情况下，选用这种输出文件格式，便于查看以及后续分析处理。
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ResultType_Normal：显示具体匹配信息。选择该参数值时，相当于blast的“-outfmt”值设置为“0”。
&nbsp; **BlastNR**：当勾选时，要求输入的目标序列是BlastDB文件，即是创建索引以后的序列文件（并要求序列文件与索引文件在相同路径下）；此时，程序会直接使用已经存在的索引文件，进行下一步的比对分析。 
　<label id='blastType'>blastType：</label>选择比对方式，根据输入序列的情况，选择合适的比对方式，其选项有以下五种。
　　　　　 TBLASTN_AA2NR_WITH_AA：蛋白序列对核酸库的比对。
　　　　　　TBLASTX_NR2NR_WITH_AA：核酸序列对核酸库在蛋白级别的比对，将库和待查序列都翻译成蛋白序列，然后对蛋白序列进行比对。
　　　　　　BLASTN_NR2NR_WITH_NR：核酸序列对核酸库的比对，直接比较核酸序列的同源性。
　　　　　　BLASTX_NR2AA_WITH_AA：核酸序列对蛋白库的比对，将核酸序列翻译成蛋白序列，与蛋白质数据库进行比对。
　　　　　　BLASTP_AA2AA_WITH_AA：蛋白序列对蛋白库的比对，直接比对蛋白序列的同源性。
　<label id='evalue'>evalue：</label>期望值，这一参数控制搜索的灵敏度，取值范围在0-1之间，通常取0.01。e值越大，随机匹配的可能性越大；e值接近零或为零时，完全匹配。
　<label id='resultNum'>resultNum：</label>当输出文件格式为tabular格式时，（即：当参数“结果样式”选择为“ResultType_Simple”时）输出结果的条数。
　**alignmentNum**：显示一条reads比对到数据库序列的比对结果条数，如：当一条reads比对到基因组5个位置，当该值设置为1时，结果文件中文件中只输出比对上的1个位置的信息；当该值设置为3时，结果文件中文件中输出比对上的3个位置的信息；当该值设置为6时，结果文件中输出比对上的全部5个位置的信息。
　<label id='threadNum'>threadNum：</label>Task使用的线程数。
　**containerNumber**：Task使用的container数。
**高级选项**：
　**isSuperTask**：是否设置为supertask，如果选中，会根据组名（即：prefix）进行task切分，例如，如果组名有3个就切分成3个子task进行运行。将输入查询序列进行切分后，就可以并行运行切分后的文件，实现大幅度减少程序运行时间的目的。
　**SplitNum**：切分份数，即将输入查询序列切分成多少份，当勾选“isSuperTask”时生效，切分后多个小文件可并行进行balst比对，最后每个小文件都运行完成以后，将结果文件进行合并。　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**　
　　比对后结果文件，如下图所示。
<div style="text-align:center">
	<img data-src="1.png" width="600px" ></img>
</div>
各列值详细解释如下：
QueryID：输入序列ID
SubjectID：数据库中的序列ID
%identity：相似程度，即输入序列和搜索到序列的匹配率
AlignmentLength：比对上的序列长度
Mismatch：mismatch数
Gap：Gap长度
QueryStart：比对上的输入序列的起始位置
QueryEnd：比对上的输入序列的终止位置
SubjectStart：比对上的数据库中序列的起始位置
SubjectEnd：比对上的数据库中序列的终止位置
E-value：表示随机匹配的可能性。E值越大，随机匹配的可能性也越大。E值接近零或为零时，基本上就是完全匹配了。
Score：比对得分，如果序列匹配上得分，不一样，减分，分值越高，两个序列相似性越高

**参考文献：**
1.Camacho C, Coulouris G, Avagyan V, Ma N, Papadopoulos J, Bealer K, et al. BLAST: Architecture and applications. BMC Bioinformatics. 2009;10:421. [PMC free article] [PubMed]
***
