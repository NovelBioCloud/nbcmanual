# Polyphen2
　　一些点突变改变引起氨基酸的改变从而影响蛋白的折叠，来影响蛋白的的相互作用区间和它的稳定性 。蛋白结构如果改变，蛋白的功能就更可能会发生改变，所以软件整合了序列和蛋白三维结构的一些特征进行预测。
**功能：**
　　预测氨基酸改变对人类蛋白稳定性和功能的影响。
**使用软件：**
　　PolyPhen-2: (Polymorphism Phenotyping v2) 是一个研究突变对蛋白功能影响的软件，它进行SNP的功能注释，将编码区域的snps比对到基因/转录本，提取蛋白序列注释和蛋白结构，并构建保守性分布。然后根据这所有的属性综合评估错义突变的有害程度。
  　软件官网： http://genetics.bwh.harvard.edu/pph2/
 **应用范围：**
　　要对SNP以及点突对蛋白功能影响程度的预测，但预测限于错义突变，其他无义突变（突变为终止密码）、碱基缺失、插入所造成的移框突变，以及起始密码子的突 变均不可预测。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是vcf2maf的结果maf文件。
　　**Inputmaf：**结构变异注释maf结果文件，maf文件格式说明，请见官方文档：
https://wiki.nci.nih.gov/display/TCGA/Mutation+Annotation+Format+(MAF)+Specification

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　存在突变的驱动基因列表（txt）文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='ChrCol'>染色体号：</label>染色体号列
　<label id='posCol'>Position列号：</label>突变位点列。　
　<label id='refCol'>Ref列号：</label>原本的碱基列。
　<label id='altCol'>Alt列号：</label>改变的碱基列。
　
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1) SomlnaClust.txt：分析结果文件，如
　　MutationTaste分值越高越显著， PolyPhen2越接近于1，对蛋白质的影响越大。
<div style="text-align:center"><img data-src="1.png" width="800px" ></img>
</div>
　　表中各列信息解释如下：
　　　CDS：基因CDS长度。
　　　n_mut：Mutations总几个数。
　　　n_clulst：Mutation clusters个数。
　　　n_OG：OG(oncogene) mutations数。
　　　n_mut_in_clust：位于hot spot 区域的OG(oncogene) mutations 数。
　　　min_clustersize：Cluster中最少的mutation数。
　　　corr_factor_OG：背景mutation率修正系数, 用于计算OG(oncogene)参数。
　　　n_TSG_total：TSG(tumour suppression genes) mutations数,i.e. 无义突变或者移码框 indels。
　　　n_TSG_nonsense：TSG(tumour suppression genes)上的非同义突变数。
　　　corr_factor_TSG：背景mutation率修正系数, 用于计算TSG参数。
　　　n_sil：Silent mutations数
　　　OG_score：OG(oncogene)值。
　　　TSG_score：TSG(tumour suppression genes)值。
　　　OG_p：OG(oncogene) p-value，经过FDR。
　　　log_OG_p：TSG(tumour suppression genes)：p-value 的 logarithm。
　　　TSG_p：TSG(tumour suppression genes) p-value.
　　　log_TSG_p：TSG(tumour suppression genes) p value的logarithm.
　　　DG_p：驱动基因p value。
　　　log_OG_p：驱动基因p value的logarithm。
　　　OG_q：OG(oncogene) q value，经过DG_p的FDR 校正。
　　　TSG_q：TSG(tumour suppression genes) q value，经过DG_p的FDR 校正。
　　　DG_q：驱动基因q value，经过DG_p的FDR 校正

2) SomInaClust_CDS.maf：是原始的maf文件，其中添加了包含突变的CDS（数字）位置的信息。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　驱动基因：driver oncogenes，该概念与2002年由Weinstein首先提出，他指出肿瘤细胞的生成及维持其恶性生物学表型依赖于某个或某些活化癌基因，也称为癌基因成瘾或癌基因依赖（oncogene addiction）。驱动癌基因编码的蛋白通常在细胞内复杂的信号调控网络中发挥重要的作用。驱动癌基因的发现为肿瘤的分子靶向治疗提供了有力的理论依据。
　　美国癌症中心Kris报告研究显示，60%的肺腺癌患者存在基因驱动突变，可通过联合检测多基因突变的情况，指导个体化靶向治疗。

参考文献：
　1.Van den Eynden J, Fierro A, Verbeke L, Marchal K: SomInaClust: Detection of Cancer Genes Based on Somatic Mutation Patterns of Inactivation and Clustering. BMC Bioinformatics 2015, 16:125


