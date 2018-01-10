# DriverGene
　　将测序得到的所有突变包含（同义突变，非同义突变，内含子突变，启动子突变等突变类型）的结果，用于后续的驱动基因分析。驱动基因是一类一旦发生改变就有可能促进癌症进展的基因，研究人员使用癌症突变基因与蛋白质结构数据库在病人肿瘤中发现了导致正常蛋白间相互作用发生改变的基因突变。
**功能：**
　　分析突变是否发生在驱动基因上。
**使用软件：**
　　**SomInaClust：**(Detection of Cancer Genes Based on Somatic Mutation Patterns of Inactivation and Clustering)是从整个外显子组或者基因组体细胞突变数据中鉴定癌症驱动基因的软件。它会优先考虑含有高于预期数量体细胞突变的基因，或者含有会引起protein-truncating(蛋白质截断)的体细胞突变基因，并进一步将它们划分为癌基因（OG）或肿瘤抑制基因。
　　软件官网：http://bioinformatics.intec.ugent.be/sominaclust/
**应用范围：**
　　通常应用于人类突变结果vcf文件，分析突变是否发生在驱动基因上，以及发生在了那些驱动基因上。

  ***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是vcf2maf的结果maf文件。
　　**Inputmaf：**结构变异注释maf结果文件，maf文件格式说明，请见官方文档：https://wiki.nci.nih.gov/display/TCGA/Mutation+Annotation+Format+(MAF)+Specification
&nbsp;
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　存在突变的驱动基因列表（txt）文件。
 　　
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　　**containerNumber：**运行时使用的container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　1) SomlnaClust.txt：分析结果文件，如：
<div style="text-align:center">
<img data-src="1.png" width="500px" ></img>
</div>
　　表中各列信息解释如下：
　　　CDS：基因CDS长度。
　　　n_mut：Mutations总几个数。
　　　n_clulst：Mutation clusters个数。
　　　n_OG：OG mutations数。
　　　n_mut_in_clust：位于hot spot 区域的OG mutations 数。
　　　min_clustersize：Cluster中最少的mutation数。
　　　corr_factor_OG：背景mutation率修正系数, 用于计算OG参数。
　　　n_TSG_total：TSG mutations数,i.e. 无义突变或者移码框 indels。
　　　n_TSG_nonsense：TSG上的非同义突变数。
　　　corr_factor_TSG：背景mutation率修正系数, 用于计算TSG参数。
　　　n_sil:Silent mutations数。
　　　OG_score：OG值。
　　　TSG_score：TSG值。
　　　OG_p：OG p-value，经过FDR。
　　　log_OG_p：TSG p-value 的 logarithm。
　　　TSG_p：TSG p-value.
　　　log_TSG_p：TSG p value的logarithm.
　　　DG_p：驱动基因p value。
　　　log_OG_p：驱动基因p value的logarithm。
　　　OG_q：OG q value，经过DG_p的FDR 校正。
　　　TSG_q：TSG q value，经过DG_p的FDR 校正。
　　　DG_q：驱动基因q value，经过DG_p的FDR 校正。

　　2) SomInaClust_CDS.maf：是在输入maf文件的基础上，添加了突变在CDS上的位置信息。
　　3) SomInaClust_log.txt：软件运行的日志文件，包括参数设置信息和生成的文件信息等。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true"style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　**驱动基因：**driver oncogenes，该概念于2002年由Weinstein首先提出，他指出肿瘤细胞的生成及维持其恶性生物学表型依赖于某个或某些活化癌基因，也称为癌基因成瘾或癌基因依赖（oncogene addiction）。驱动癌基因编码的蛋白通常在细胞内复杂的信号调控网络中发挥重要的作用。驱动癌基因的发现为肿瘤的分子靶向治疗提供了有力的理论依据。
美国癌症中心Kris报告研究显示，60%的肺腺癌患者存在基因驱动突变，可通过联合检测多基因突变的情况，指导个体化靶向治疗。
&nbsp;
**参考文献：**
　　1.Van den Eynden J, Fierro A, Verbeke L, Marchal K: SomInaClust: Detection of Cancer Genes Based on Somatic Mutation Patterns of Inactivation and Clustering. BMC Bioinformatics 2015, 16:125



