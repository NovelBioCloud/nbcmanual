# DifGene
　　研究生物体在不同的环境下，或者不同生理状态下的基因表达量之间的差异。不同细胞或同类细胞在不同发育阶段、不同生理状态下的基因表达状况，可为研究生命活动过程提供重要信息，对调控生物的生长发育各阶段及代谢途径具有重大的理论和实践意义。
　　基因表达系列分析是一种高效、快捷、低成本的研究生物基因表达水平的方法,可在整体水平对细胞或组织中的大量转录本同时进行分析,从而全面反映细胞或组织中的基因表达情况,同时还可进行不同组织或细胞的所有差别表达基因的比较和研究。
　　算法：Limma用于基因表达芯片；DEGseq--RPKM(No Rep) 用于无生物学重复条件，DESeq--Counts(Needs Rep)、EdgeR--Counts(Needs Rep)、T test用于有生物学重复条件、EBSeq—Counts 不受生物学重复限制。
****
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**

1.参数说明
1）FoldChange
　　FoldChange是两样品中同一个基因表达水平的变化倍数。基因表达水平可以用RPKM值或FPKM值来计算。FoldChange 方法在探测差异表达基因时，能够直接的得到差异变化值，是用于检测差异表达基因的最基本的方法，简单，易理解和不错的实验结果。
　　　　 LogFC=log2（A/B）
　　　 A: sampleA表达值；B :sampleB表达值

2）P值
　　P值即概率，反映某一事件发生的可能性大小。统计学根据显著性检验方法所得到的P 值，一般以P < 0.05 为显著， P<0.01 为非常显著。

3）FDR值
　　FDR错误控制法是Benjamini和Hochberg于1995年提出一种方法,通过控制FDR(False Discovery Rate)来决定P值的域值，FDR为阳性检验结果中判断错误的比例。
　　对所有候选基因的p值进行从小到大排序，则若想控制fdr不能超过q，则只需找到最大的正整数i，使得 p( i )<= (i×q)/m.然后，挑选对应p(1),p(2),...,p( i)的基因做为差异表达基因，这样就能从统计学上保证fdr不超过q。因此，FDR的计算公式：    
　　  q-value( i)=p( i)*length(p)/rank(p)

软件官网：
　http://www.bioconductor.org/packages/release/bioc/html/qvalue.html
　文献：Benjamini, Y. and D. Yekutieli (2001). The control of the false discovery rate in multiple testing under dependency. The Annals of Statistics. 29: 1165-1188.

2.算法说明
1）Limma—Microarray
　　Limma（Linear Models for Microarray Data）是一系列功能比较全的软件包，分析基因表达芯片数据工具。使用差异化基因分析的“线性”算法来分析实验以及评估差异表达，提供多个RNA目标基因进行分析比较的工具。Limma 由Bioconductor团队开发。
软件官网：
　http://www.bioconductor.org/packages/release/bioc/html/limma.html         
     
2）DEGseq--RPKM(No Rep)
　　DEGseq是从RNA-seq数据中识别差异表达基因的一个R软件包，基于RPKM无生物学重复条件下的基因进行差异表达分析。DEGseq识别来自不同样品中的RNA-seq数据的差异表达基因或亚型。DEGseq整合了三种现有的方法，引入了两种基于MA-绘图来检测和可视化基因表达差异的新方法。
软件官网：
　http://www.bioconductor.org/packages/release/bioc/html/DEGseq.html

参考文献：
　Likun Wang, Zhixing Feng, Xi Wang, Xiaowo Wang, and Xuegong Zhang, DEGseq: an R package for identifying differentially expressed genes from RNA-seq data, Bioinformatics, 1 January 2010; 26: 136 – 138
文献网址：
　http://bioinformatics.oxfordjournals.org/content/26/1/136.abstract

3）DESeq--Counts(Needs Rep)
　　DESeq是基于高通量测序分析统计数据，使用count数据的R包。采用负二项分布检验对reads数进行差异显著性检验，有生物学重复差异表达基因的RNA-seq的数据。
R source：
 　http://www.bioconductor.org/biocLite.R
软件官网：
　http://www.bioconductor.org/packages/release/bioc/html/DESeq.html
参考文献：
　Simon Anders, Wolfgang Huber: Differential expression analysis for sequence count data.Genome Biology 11 (2010) R106,
文献网址：
　http://www-huber.embl.de/users/anders/DESeq/

4）EBSeq—Counts
　　利用统计模型来保证获得准确的鉴定，鉴定出RNA-seq全基因组规模上进行差异表达基因及它们相应亚型的鉴定。EBSeq利用经验贝叶斯方法的优点，开发鉴定一个比较两种或多种生物条件的RNA-seq实验中的差异表达亚型。
软件官网：
　http://www.bioconductor.org/packages/release/bioc/html/EBSeq.html

5）EdgeR--Counts(Needs Rep)
　　edgeR是一个研究数字基因表达（digital gene expression，DGE）重复计数数据差异表达的Bioconductor软件包。基于Counts 鉴别RNA-Seq、SAGE 、ChIP-Seq差异基因。贝叶斯方法被用于减轻跨转录本的过度离散程度，改进了推断的可靠性。该方法甚至能够用最小重复水平使用，要至少一个表型或实验条件是重复的。
软件官网：
　http://www.bioconductor.org/packages/release/bioc/html/edgeR.html
参考文献：
　Mark D. Robinson et al. edgeR: a Bioconductor package for differential expression analysis of digital gene expression data. BIOINFORMATICS. Vol. 26 no. 1 2010, pages 139–140
　http://www.ncbi.nlm.nih.gov/pmc/articles/PMC2796818/pdf/btp616.pdf

6）T test
　　基于小样本数据的随即方差模型: t检验建立在重复（至少要3个重复）测量的基础上,误差方差的估计为基因特异性的,即用于检验某基因是否具有差异表达的t值的误差方差的估计仅使用该基因在两种条件下测量值,而独立于其他基因。
**** 
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

 　　输入文件为基因Expression表格，通常来自Expression Task或者Other(来源于其他途径)，选择相应的算法及卡值标准，可获得两组样本的差异基因,将差异基因列表（all.counts.exp.txt 或 all.fpkm.exp.txt）拖入inFileName，输入数据:.txt 或.xls; .xlsx；输出数据:.txt.xls

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='algorithm'>Algorithm：</label>
　Limma—Microarray，差异化基因分析的“线性”算法来分析实验以及评估差异表达，分析基因表达芯片数据工具。
　DEGseq--RPKM(No Rep)，基于RPKM无生物学重复条件下的基因进行差异表达分析。
　DESeq--Counts(Needs Rep)，采用负二项分布检验对reads数进行差异显著性检验，有生物学重复差异表达基因的RNA-seq的数据。
　EBSeq—Counts， EBSeq利用经验贝叶斯方法的优点，开发鉴定一个比较两种或多种生物条件的RNA-seq实验中的差异表达亚型。
　EdgeR--Counts(Needs Rep)， 基于Counts 鉴别RNA-Seq、SAGE 、ChIP-Seq差异基因, 要至少一个表型或实验条件是重复。
　T test：t检验建立在重复（至少要3个重复）测量的基础上,误差方差的估计为基因特异性的。

| 算法        | 标准化方法   | 差异筛选方法  |基于|
| ------- |  :----:| :----:  | :----:  |
| EB-Seq        | Median   | 负二项分布  |Counts|
| EdgeR        | TMM   | 负二项分布 |Counts|
| DE-Seq        | DE-Seq  |负二项分布  |Counts|
| Limma       | log   | 贝叶斯  |标准化后数据|
| RVM       | log   | 反伽马模拟正态分布的t检验  |标准化后数据|
| DEG-Seq        | 标准化后数据   | 二项分布  |标准化后数据|

　<label id='logFcCutoff'>Log2FC：</label>即为log2 Fold Change。Fold Change表达量倍数的比值，通常差异表达基因在实验组中的表达量是对照组中的2倍以上或低于0.5倍差异。通常用Fold Change为2，即LogFC为1。
　<label id='pvalueFdr'>PvalueFdr：</label>选择FDR值或者Pvalue值进行筛选。FDR错误发现率阀值，取值范围为(0,1)，默认值为0.05。P value是t检验用于判断两个平均数的差异是否显著的值，通过控制FDR来决定P值的阈值。
　<label id='pvalueCutoff'>CutOff：</label>选择P值或FDR值，填写的筛选数值。
　<label id='colAccId'>GeneColNum：</label>输入文件的基因名称列。
　<label id='colAccId'>文件对比：</label>增加对比组，group1Array、group2Array分别为两个对比组，outFileArray为输出文件名。
　<label id='group1Array'>组名修改：</label>
　　　　　group1Array：选择对比组1；
　　　　　group2Array：选择对比组2；
　　　　　outFileArray：输出名称。
　<label id='样本加和>=该值'>样本加和>=该值：</label>去掉表达量过低的基因，基因所有样本中表达值加和大于此值，默认值为10。
　<label id='单个样本>=该值'>单个样本>=该值：</label>去掉表达量过低的基因，基因单个样本表达值大于此值，默认值为5。
　<label id='isSensitive'>IsSensitive：</label>是否把临界值计算在差异基因内，筛选出差异基因数量较少时可勾选。
　<label id='needToBeLog'>LogTransformData：</label>是否将输入数据取log值，通常算法为Limma，芯片没有进行标准化的信号值中使用。
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　alldiff.xls：两组比较后的全部的差异基因。
<div style="text-align:center">
<img data-src="1.png" width="800px"></img>
</div>
　diff.xls、diff.txt：两组比较后的通过参数设置中条件设置FDR、P值等条件筛选后的基因。
<div style="text-align:center">
<img data-src="2.png" width="800px"></img>
</div>
