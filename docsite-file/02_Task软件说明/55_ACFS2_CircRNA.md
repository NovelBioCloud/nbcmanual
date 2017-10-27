## ACFS2_ CircRNA
　　CircRNA是一组闭环形式的单链RNA。它们是剪接产生的，在各种组织中广泛表达并且在发育和疾病中具有功能性影响，该模块可以快速准确地检测circRNA。 
**功能：**
　	检测及定量circRNA。
**使用软件：**
　　ACFS2：Acfs可以从单端和双端RNA测序数据中准确快速鉴定以及定量环状RNA丰度。
　　软件官网：https://github.com/arthuryxt/acfs
**应用范围：**
　　需要从Rna Seq测序得到的单端或者双端的Reads 中，检测出circRNA。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的数据来源于通常是unmapped reads，文件格式为Fastq，即首先将测序得到的reads比对到参考序列上以后，然后提取unmapped reads，作为该task的输入文件。
**GTF：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。
**LeftFastq：**左端reads序列。要求输入与参考序列比对得到的unmapped reads的左端序列。文件格式要求是Fastq。
**RightFastq：**右端reads序列，要求输入与参考序列比对得到的unmapped reads的右端序列。文件格式要求是Fastq。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　检测到的circRNA位置信息表达丰度以及circRNA splicing 处上下游各150bp的序列文件。


***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　<label id='filter'>FilterReadsWithN：</label>是否过滤掉含N的reads，其值有两个选项Filter和NotFilter。
　<label id='seq_len'>SeqLength：</label>输入的reads长度。
　**isCallFusionCirc：**是否检测融合circRNA。
　<label id='thread'>Threads：</label>线程数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**





　　1. BlockCountsStatisticsPlot.png：BlockCounts统计图是circRNA的外显子数分布图，X轴外显子数，Y轴表示CircRNA个数，如：
<div style="text-align:center"><img data-src="5.png" width="400px" ></img></div>

　　2. CircRNAChrDistributionPlot.png： circRNA在染色体上的分布图，X轴表示染色体，Y轴表示CircRNA个数，如：
<div style="text-align:center"><img data-src="6.png" width="300px" ></img></div>

　　3. StrandStatisticsPlot.png：circRNA在正负链上的分布图，X轴表示正负链，Y轴表示CircRNA个数，如：
<div style="text-align:center"><img data-src="7.png" width="100px" ></img></div>

　　4. all.counts.exp.txt：circRna表达统计列表，如：
<div style="text-align:center"><img data-src="4.png" width="700px" ></img></div>

　　5. unmap.trans.splicing.tsloci.fa：circRNA 的splicing 处上下游各150bp的序列文件，以fasta文件存储。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**circRNA**（环状RNA）是一类特殊的非编码RNA分子，与传统的线性RNA（linear RNA，含5’和3’末端）不同，circRNA分子呈封闭环状结构，不受RNA外切酶影响，表达更稳定，不易降解。在功能上，近年的研究表明，circRNA分子富含microRNA（miRNA）结合位点，在细胞中起到miRNA海绵（ miRNA sponge）的作用，进而解除miRNA对其靶基因的抑制作用，升高靶基因的表达水平；这一作用机制被称为竞争性内源RNA（ceRNA）机制。通过与疾病关联的miRNA相互作用，circRNA在疾病中发挥着重要的调控作用。


**参考文献**
　　1.You,X. and Conrad,T.O. (2016) Acfs: accurate circRNA identification and quantification from RNA-Seq data. Sci. Rep., 6, 38820.

