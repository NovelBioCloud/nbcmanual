# DriverGene
　　将测序得到的所有突变包含（同义突变，非同义突变，内含子突变，启动子突变等突变类型）的结果，用于后续的驱动基因分析。驱动基因是一类一旦发生改变就有可能促进癌症进展的基因，研究人员使用癌症突变基因与蛋白质结构数据库在病人肿瘤中发现了导致正常蛋白间相互作用发生改变的基因突变。
　　DriverGene采用的算法为SomInaClust，是从整个外显子组/基因组中标识癌症驱动基因的体细胞突变数据的方法。它筛选的基因是一个聚类结果以及比预期数目更发高蛋白截断的体细胞突变，并进一步它们推定为癌基因（OG）或肿瘤抑制基因（肿瘤抑制基因）进行分类。

　SomInaClust 官网：（http://bioinformatics.intec.ugent.be/sominaclust/）

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　inputFile选择的是vcf2maf产生的.maf格式文件。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　containerNumber：运行时使用的container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

<div style="text-align:center">
<img data-src="1.png" width="600px" ></img>
</div>

　当qDG<=0.05是，则判断为驱动基因：
　当OG score的值大于20%，且 TSG score的值<20%的时候，归类于OG基因
　当TSG score值>20%时，归类于TSG基因
**结果文件说明，每列注释信息如下：**
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





