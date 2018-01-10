# DifGene
　　研究生物体在不同的环境下，或者不同生理状态下的基因表达量之间的差异。不同细胞或同类细胞在不同发育阶段、不同生理状态下的基因表达状况，可为研究生命活动过程提供重要信息，对调控生物的生长发育各阶段及代谢途径具有重大的理论和实践意义。
**功能：**
　　差异表达量计算并筛选显著性差异表达基因。
**使用软件：**
1. Limma：Linear Models for Microarray Data，limmar 包是一系列分析基因表达芯片数据工具的库，特别是使用线性模型来分析实验以及评估差异表达，提供了对多个RNA目标基因进行分析比较的工具。
软件官网：
http://www.bioconductor.org/packages/release/bioc/html/limma.html
2. DEGseq：是一个基于基因表达值来进行差异分析的R包，可用于没有生物学重复的样本分析中。该算法基于MA-plot和随机采样模型进行数据分析。
软件官网：
http://www.bioconductor.org/packages/release/bioc/html/DEGseq.html
3. DESeq：是一个基于Reads的 counts 数来进行差异分析的R包，DESeq采用NB（负二项分布检验的方式）对reads数进行差异显著性检验，同时还增加了对长度引起的误差的矫正，并采用basemean值来估算基因的表达量。
软件官网：
http://www.bioconductor.org/packages/release/bioc/html/DESeq.html
4. EBSeq：是一个用于RNA-Seq实验中鉴定两个或者多个生物学重复条件下差异表达基因或者差异表达异构体的R包。
软件官网：
http://www.bioconductor.org/packages/devel/bioc/html/EBSeq.html
5. EdgeR：EdgeR包主要是用于不同技术平台测序数据（包括RNA-seq，SAGE或者ChIP-seq等）的差异表达基因或者差异标记（ChIP-seq）的鉴定，EdgeR也是采用NB（负二项分布检验）对reads数进行差异显著性检验。主要是利用了多组实验的精确统计模型或者适用于多因素复杂实验的广义线性模型。前者叫做“经典EdgeR”， 后者叫做”广义线性模型 EdgeR“。这里定义的reads数可以代指基因水平、外显子水平、转录本水平或者标签水平等。
软件官网：
http://www.bioconductor.org/packages/release/bioc/html/edgeR.html

**应用范围：**
　　计算差异表达基因的差异倍数并筛选出显著性差异表达基因。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task数据来源文件通常是SamAndRPKM结果中的基因表达值列表，也可输入外源的基因表达值列表。
**inFileName：**基因表达值列表，这里的基因表达值可以是基因表达的counts数也可以是RPKM/FPKM值。如：

| GeneID        | con   | prl_3WT  |prl_3_1043|
| ------- |  :----:| :----:  | :----:  |
| BBX        | 247   | 208  |244|
| WDR83OS        | 802   | 1124 |1067|
| BCR        | 474  |590  |517|
| VOPP1       | 854   | 1071  |1081|

注意：
1、要求输入的表格要有一行title，对于每列的title名称，无特殊要求；
2、输入表格中，第一列为基因名称，从第二列开始的之后列都是基因在样品中的表达值。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　所有差异表达基因列表和根据设定的筛选阈值，筛选出来的显著性差异基因列表（excel、txt）文件。　

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='algorithm'>Algorithm：</label>
　Limma—Microarray，Limma(Limma:Linear Models for Microarray Data)使用线性模型来进行基因表达的计算分析，常应用于分析基因表达芯片数据。
　DEGseq--RPKM(No Rep)，基于RPKM无生物学重复条件下的基因进行差异表达分析。
　DESeq--Counts(Needs Rep)，采用负二项分布检验对counts数进行差异显著性检验，应用于有生物学重复样本的RNA-Seq数据。
　EBSeq—Counts， EBSeq利用经验贝叶斯方法的优点，开发鉴定一个比较两种或多种生物条件的RNA-seq实验中的差异表达亚型。
　EdgeR--Counts(Needs Rep)， 基于基因表达的Counts数， 鉴别RNA-Seq、SAGE 、ChIP-Seq差异基因, 要求输入样本至少有一个表型或实验的重复。
　T test：T-test是差异基因表达检测中常用的统计方法，通过合并样本间可变的数据，来评价差异表达，用于判断某一基因在两个样本中是否有差异表达。t检验建立在重复（至少要3个重复）测量的基础上,用于有生物学重复的样本分析。

| 算法        | 标准化方法   | 差异筛选方法  |基于|
| ------- |  :----:| :----:  | :----:  |
| EB-Seq        | Median   | 负二项分布  |Counts|
| EdgeR        | TMM   | 负二项分布 |Counts|
| DE-Seq        | DE-Seq  |负二项分布  |Counts|
| Limma       | log   | 贝叶斯  |标准化后数据|
| RVM       | log   | 反伽马模拟正态分布的t检验  |标准化后数据|
| DEG-Seq        | 标准化后数据   | 二项分布  |标准化后数据|

　<label id='logFcCutoff'>Log2FC：</label>FC（Fold Change）为设置的差异倍数阈值，通常我们设定在实验组中表达量是对照组中的2倍以上或0.5倍以下的基因为差异基因，即通常情况下设置Fold Change为2，即LogFC为1。
　<label id='pvalueFdr'>PvalueFdr：</label>选择使用FDR值或者P-value值进行显著性差异基因的筛选。其选项有：
 　　　　　　（１）FDR错误发现率阀值，取值范围为(0,1)，默认值为0.05。
 　　　　　　（２）P-value：假设检验概率，统计学根据显著性检验方法所得到的P-value。
　<label id='pvalueCutoff'>CutOff：</label>选择P值或FDR值，填写的筛选阈值数值取值范围为(0,1)，FDR，默认值为0.05。对于P-value值，一般以p-value<0.05为显著，p<0.01为非常显著。所以，该阈值通常情况下会设置为0.05，具体的数据也可根据差异基因数量的多少，做适当调整。
 
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
（１）\*alldiff.xls：两组比较后的全部的差异基因。
<div style="text-align:center"><img data-src="1.png" width="800px"></img></div>

　AccID：基因名称。
　实验组：标准化后实验组基因表达值。
　对照组：标准化后对照组基因表达值。
　FoldChange：实验组与对照组表达值差异倍数。
　Log2FC：以2为底，实验组和对照组表达值差异倍数的对数。
　FDR：多重假设检验误判率。FDR越小，误判率越低。
　实验组1：基因在实验组1中的表达值。
　实验组2：基因在实验组2中的表达值。
　对照组1：基因在对照组1中的表达值。
　对照组2：基因在对照组2中的表达值。
&nbsp;
（２）\*.diff.xls/*diff.txt：根据设定阈值筛选出来的显著性差异基因列表如：
<div style="text-align:center"><img data-src="2.png" width="800px"></img></div>
表格详细说明如下：
AccID：基因名称
实验组：标准化后实验组基因表达值
对照组：标准化后对照组基因表达值
FoldChange：实验组与对照组表达值差异倍数
Log2FC：以2为底，实验组和对照组表达值差异倍数的对数。
FDR：多重假设检验误判率。FDR越小，误判率越低。
Style：差异circRNA、差异基因、差异miRNA的上下调方式，up表示差异上调，down表示差异下调。
实验组1：基因在实验组1中的表达值
实验组2：基因在实验组2中的表达值
对照组1：基因在对照组1中的表达值
对照组2：基因在对照组2中的表达值
****
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**
**PRKM**
是Reads Per Kb per Million reads的缩写，代表每百万reads中来自于某基因每千碱基长度的reads数。RPKM是二代测序技术中用来表示基因表达量或丰度的方法。计算公式为：
RPKM=（1E+09）C/NL
 C为唯一比对到该基因上reads数，N为唯一比对到参考基因上的总reads数，L为该基因编码区的碱基数。RPKM法能消除基因长度和测序量差异对计算基因表达的影响，计算得到的基因表达量可直接用于比较不同样品间的基因表达差异。如果一个基因存在多个转录本，则用该基因的最长转录本计算其测序覆盖度和表达量。
**Log2FC**
其中Fold Change是指实验组和对照组的基因表达量的比值，简称为FC。对FC取log2，即为Log2FC。
**P-value**
p值就是在原假设下，该总体出现现有数据的概率，或者说在现有数据下，原假设成立的一种合理性，p值越大，原假设成立的可能性就越大；p值越少，就说明原假设成立的可能性越小。通常当p值小于0.05时，就认为原假设不成立。详细说明请见： https://en.wikipedia.org/wiki/P-value
**FDR**
FDR错误控制法是Benjamini和Hochberg于1995年提出一种方法,通过控制FDR(False Discovery Rate)来决定P值的域值，FDR为阳性检验结果中判断错误的比例。https://en.wikipedia.org/wiki/False_discovery_rate

**T-test**
T-test检验是差异基因表达检测中常用的统计方法，通过合并样本间可变的数据，来评价差异表达，用于判断某一基因在两个样本中是否有差异表达。当样本量较少时，T-test对总体方差的估计不太准确，因而T-test的检验效能会降低。说明文档：https://en.wikipedia.org/wiki/Test_statistic

**参考文献**
1.	Diboun I, Wernisch L, Orengo CA, Koltzenburg M. Microarray analysis after RNA amplification can detect pronounced differences in gene expression using limma. BMC Genomics. 2006;7:252. doi: 10.1186/1471-2164-7-252. [PMC free article] [PubMed] [Cross Ref]
2.	Wang L, Feng Z, Wang X, Zhang X. DEGseq: an R package for identifying differentially expressed genes from RNA-seq data. Bioinformatics. pp. 136–138. [PubMed]
3.	Anders S, Huber W. Differential expression analysis for sequence count data. Genome Biol. 2010;11:1. doi: 10.1186/gb-2010-11-10-r106. [PMC free article] [PubMed] [Cross Ref]
4.	Anders S, Huber W. Differential expression analysis for sequence count data. Genome Biol. 2010;11:1. doi: 10.1186/gb-2010-11-10-r106. [PMC free article] [PubMed] [Cross Ref]
5.	Leng N., Dawson J.A., Thomson J.A., Ruotti V., Rissman A.I., Smits B.M.G., Haag J.D., Gould M.N., Stewart R.M., Kendziorski C. EBSeq: an empirical Bayes hierarchical model for inference in RNA-seq experiments. Bioinformatics. 2013; 29:1035–1043. [PMC free article] [PubMed]
6.	Robinson MD, McCarthy DJ, Smyth GK. edgeR: a bioconductor package for differential expression analysis of digital gene expression data. Bioinformatics. 2010;26:139–140. doi: 10.1093/bioinformatics/btp616. [PMC free article]  [PubMed]  [Cross Ref]
7.	Storey J.D. (2002), A direct approach to false discovery rates, JRSS-B 64(3):479-498

　




