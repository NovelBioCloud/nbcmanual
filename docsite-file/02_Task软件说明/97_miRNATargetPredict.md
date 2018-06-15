# miRNATargetPredict
　　成熟的miRNA是由较长的初级转录物经过一系列核酸酶的剪切加工而产生的，随后组装进RNA诱导的沉默复合体，通过碱基互补配对的方式识别靶基因，并根据互补程度的不同指导沉默复合体降解靶mRNA或者阻遏靶mRNA的翻译。
**功能：**应用靶基因预测算法miranda和RNAhybrid，对circRNA、lncRNA、ncRNA和miRNA进行靶向调控预测。
 **使用软件：**
　**Miranda：**miRanda是最早利用生物信息学对miRNA靶基因进行预测的软件，由Enright等人于2003年开发设计。其对3’UTR的筛选依据主要是从序列匹配、miRNA与mRNA双链的热稳定性以及靶位点的保守性三个方面进行分析。综合这3条原则，miRanda选取与miRNA序列互补的3’UTR所对应的排名前十位的基因，作为miRNA的候选靶基因，对于多个miRNA对应于同一靶位点的情况，miRanda使用贪心算法（Greedy Algorithm）选取其中得分最高且自由能最低的那一对。
　　**软件官网：**http://www.microrna.org/microrna/home.do
　**RNAhybird：**RNAhybrid （bibiserv.techfak.uni-bielefeld.de/rnahybrid/）通过最小自由能算法计算一条长链RNA和一条短链RNA的最小配对自由能，借此来评估RNA二级结构的稳定性。这一工具由德国Bielefeld大学的研究团队发布，作为microRNA靶点预测的软件被广泛使用。
　　**软件官网：**https://bibiserv.cebitec.uni-bielefeld.de/rnahybrid/
 **应用范围：**通常是对显著性差异miRNA进行靶基因预测分析。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据通常是差异miRNA的序列。
**miRNASeq：**需要分析的miRNA序列，通常数据处理方法是，首先对miRNA进行差异筛选，得到显著性差异miRNA，然后提取出显著性差异miRNA的序列，作为该task的输入文件，文件格式为fasta文件。
**3’UTRSeq：**基因的3’UTR序列，文件格式为fasta文件。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　预测出的miRNA与靶基因对应的关系列表（txt）文件。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='software'>software：</label>选择所使用软件，Miranda和RNAhybird可以同时选择。
<label id='strict'>Seed_Strict：</label>选中参数。对于miranda软件表示，添加这个参数-strict；添加这个参数的意思是要求miRNA的第2到第8个碱基必须是完全比对上的；对于RNAhybrid软件表示添加-f的参数，且其值为 2,7 ；-f 2,7 表示要求miRNA的第2到第7个碱基必须是完全比对上的。
<label id='score'>Miranda_Score：</label>miRNA和靶基因结合的效率水平。
<label id='energy'>Miranda_Energy：</label>miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
<label id='type'>RNAhybrid_Model：</label>参考基因组的物种。
<label id='maxtargetlen'>RNAhybrid_MaxTargetLen：</label>RNAhybrid 中3`UTR序列最大长度。
<label id='maxquerylen'>RNAhybrid_MaxQueryLen：</label>RNAhybrid 中miRNA序列最大长度。
<label id='hyenergy'>RNAhybrid_Energy：</label>miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
<label id='pvalue'>RNAhybrid_Pvalue：</label>靶向关系的结合显著性值，统计学根据显著性检验方法所得到的P值。
<label id='hits'>RNAhybrid_HitsPerTarget：</label>一个小RNA和一个靶基因的某一段序列匹配情况最多列出几次，比如一个小RNA和一个靶基因的某一段序列匹配存在多种情况，则为1的话只列出最优的匹配情况，一般选1就比较好。
**文件对比：**增加数据处理对应关系，miRNA_Seq为需要分析的miRNA序列文件；3’UTR_Seq可以选择circRNA、mRNA、ncRNA序列文件；outFileArray为输出文件名。
组名修改：
　　　　　group1Array：选择对比组1，在该task中此参数通常选择为miRNA；
　　　　　group2Array：选择对比组2，在该task中此参数通常选择为circRNA、mRNA或者ncRNA；
　　　　　outFileArray：输出名称。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
1)\*.targetPredict.RNAhybrid.gz：使用RNAhybrid软件预测靶基因的结果文件。
2)\*.targetPredict.RNAhybrid.modify.txt ：提取出RNAhybrid软件预测靶基因原始结果中的miRNA和靶基因对应关系的列表。
3)\*.targetPredict.miranda.gz：使用miranda软件预测靶基因的结果文件。
4)\* targetPredict.miranda.modify.txt：提取出miranda软件预测靶基因原始结果中的miRNA和靶基因对应关系的列表。
5)\* _overlap.txt：如果参数“software”选中了两种软件，则会对这两种软件的结果进行整合分析，该文件为使用两种软件分析都预测到靶基因的结果。
6)\* _venn.png：如果参数“software”选中了两种软件，则会对这两种软件的结果进行整合分析，该文件为使用两种软件分析结果的维恩图。
<div style="text-align:center"><img data-src="2.png" width="300px"></img></div>
7)\* _venn.txt：如果参数“software”选中了两种软件，则会对这两种软件的结果进行整合分析，该文件是用来绘制维恩图的文本文件。
8)\*_venn_OneLine.xls：如果参数“software”选中了两种软件，该文件是对这两种软件的结果进行整合分析的结果。

**参考文献：**
1.RNAhybrid: microRNA target prediction easy, fast and flexible.,
Krüger, Jan, and Rehmsmeier Marc, Nucleic Acids Res, 2006 Jul 1, Volume 34, Issue Web Server issue, p.W451-4, (2006)
2.Enright A J, John B, Gaul U, et al.MicroRNA targets in Drosophila. Genome Biol, 2003, 5(1): R1