# <font color="#007979">TajimaDAnalysisSimple</font>

---

&#160; &#160; &#160; &#160;Tajima's D 检验的目的是区分随机演变的DNA序列（“中性”）和在非随机过程中演化的DNA序列，包括定向选择或平衡选择，群体统计学扩展或收缩。随机进化的DNA序列含有突变，对生物的适应性和存活率没有影响。随机演变的突变被称为“中性”，而选择下的突变是“非中性的”。例如，您可能会发现导致产前死亡或严重疾病的突变正在被选中。从整体上看群体群体时，我们说中性突变的群体频率是通过遗传漂移随机波动的（即突变群体中群体百分比从一代到下一代变化，这个百分比同样可能会发生变化来上升或下降）。

**<font color="#007979">输入文件</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；

**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='tajimaD'>TajimaD：</label> 当bin中有指定数量大小时输出Tajima’s D的值，该参数为整数值。

**<font color="#007979">结果说明</font>**

&#160; &#160; &#160; &#160;后缀为“.Tajima.D”的文件。该文件中一共有4列，分别为“CHROM、BIN_START、N_SNPS、TajimaD”


Tajima’s D的意义
D值 | 数学解释 |  代表意义 |  生物学解释  
-|-|-
D=0 | Theta-Pi=Theta-k(Observed=Expected)，平均杂合度=多态位点的个数 | 观测变异类似于期望变异 | 群体根据突变-漂移平衡演变。没有选择的证据 |
D<0 | Theta-Pi<Theta-k(Observed<Expected)，单倍型数（更低的平均杂合度）<多态位点的个数 | 稀有等位基因以高频率存在（超过稀有等位基因） | 最近的选择性清除，最近瓶颈后的群体扩张，与清除基因连锁 |
D>0 | Theta-Pi>Theta-k(Observed>Expected)，单倍型数（更多平均杂合度）>多态位点的个数 | 稀有等位基因以低频率存在（缺少稀有等位基因） | 平衡选择，突然群体收缩 |

