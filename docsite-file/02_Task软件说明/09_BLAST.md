# BLAST

　　Blast，全称Basic Local Alignment Search Tool，即"基于局部比对算法的搜索工具"，由Altschul等人于1990年发布。Blast能够实现比较两段核酸或者蛋白序列之间的同源性的功能，它能够快速的找到两段序列之间的同源序列并对比对区域进行打分以确定同源性的高低。Blast的运行方式是先用目标序列建数据库（这种数据库称为database，里面的每一条序列称为subject），然后用待查的序列（称为query）在database中搜索，每一条query与database中的每一条subject都要进行双序列比对，从而得出全部比对结果。

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　　BLAST，全称Basic Local Alignment Search Tool，基于局部比对算法的序列比对搜索工具。BLAST程序可根据database和infile文件序列类型自动从四种比对程序（blastn、blastp、blastx和tblastn）中选择合适的程序，四种比对方式说明如下：
　　blastn：用核酸序列搜索核酸序列数据库。
　　blastp：用蛋白质序列搜索蛋白质序列数据库。
　　blastx：核酸序列按照6条链翻译成蛋白质序列后搜索蛋白质序列数据库。
　　tblastn：用蛋白质序列搜索翻译过的核酸序列数据库。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　查询序列的fa文件，目标序列的fa文件或者数据库中对应物种的选择。
　　输入格式：fasta； 输出格式：txt。
　　输入文件querySeq支持输入多个querySeq进行并行，且Subject可以输入以BlastDB命名的文件
　　
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='mappingTo'>blast To：</label>Chromosome：比对到染色体。
　　　　　　refSeq_All_Iso：比对到转录组序列。
　　　　　　refSeq_One_Iso：比对到转录本。
　<label id='resultType'>结果格式：</label>ResultType_Simple，简单结果。
　　　　　　ResultType_Normal，正常结果。
　**BlastNR：**当输入为BlastDB文件时需要勾选，常用于blastNR以及跟比较大的数据库进行blast分析。另外，当输入的querySeq为空，且不勾选blastNR时，只会创建blastdb，不会进行后续分析。
　<label id='blastType'>blastType：</label>为比对类型。
　　　　　　TBLASTN_AA2NR_WITH_AA：蛋白序列对核酸库的比对。
　　　　　　TBLASTX_NR2NR_WITH_AA：核酸序列对核酸库在蛋白级别的比对，将库和待查序列都翻译成蛋白序列，然后对蛋白序列进行比对。
　　　　　　BLASTN_NR2NR_WITH_NR：核酸序列对核酸库的比对，直接比较核酸序列的同源性。
　　　　　　BLASTX_NR2AA_WITH_AA：将核酸序列翻译成蛋白序列，与蛋白质数据库进行比对。
　　　　　　BLASTP_AA2AA_WITH_AA：蛋白序列与蛋白库做比对，直接比对蛋白序列的同源性。
　<label id='evalue'>evalue：</label>表示随机匹配的可能性。e值越大，随机匹配的可能性越大。 e值接近零或为零时，完全匹配，通常取0.01。
　<label id='resultNum'>resultNum：</label>BLAST的结果输出个数。
　**alignmentNum：**显示数据库序列的对比结果的数目
　<label id='threadNum'>threadNum：</label>Task使用的线程数。
　**containerNumber：**Task使用的container数。

**高级选项：**
　**isSuperTask：**是否为supertask（会根据prefix进行task切分，例如如果组名有3个就切分成3个子task进行运行）
　**SplitNum：**切分份数，当设置为supertask时生效，意为将文件切分成SplitNum个小份，每份分别进行blast运算

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**　
　　Blast结果依次为：ContigName	Blast2ara（第一列为原来物种的基因名称）、一致百分数	比对长度（第二列为blast到新物种的基因名称）、错配数、空位数、比对起始位点、比对终止位点、Subject比对起始位点、Subject比对终止位点、E-value、Sore。

<div style="text-align:center">
<img data-src="Blast1.png" width="800px" ></img>
</div>
