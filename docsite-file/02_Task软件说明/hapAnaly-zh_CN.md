# <font color="#007979">hapAnalysis</font>

---

&#160; &#160; &#160; &#160;单体型网络（Haplotype Network）是谱系地理研究的重要手段。通过单体型网络，我们可以推断群体的起源、扩散历史。单体型（haplotype）在单体型网络中是指一段遗传连锁的核酸序列。不同的单体型，通过序列中的变异来区分（常用SNP）。

**<font color="#007979">输入文件</font>**

品种对应亚种的文本文件，有两列信息，第一列品种，第二列品种对应的亚种；

**<font color="#007979">输入参数</font>**

> * &#160; &#160; Region in chromosome：选中该标签，表示按照输入染色体区域的方式进行分析，此时需要填写以下三个参数，即：“Chromosome”、“Start position”、“End position”；
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>染色体号；
> * &#160; &#160;<label id='start'>Start position：</label>起始位置；
> * &#160; &#160;<label id='end'>End position：</label>终止位置；
> * &#160; &#160;Gene locus：：选中该标签，表示按照输入基因名称以及距离该基因上下游位置距离的方式进行分析，此时需要填写以下三个参数，即：“Gene”、“Upstream”、“Downstream”；
> * &#160; &#160;<label id='gene'>Gene：</label>基因名称，如：Os01g0100100；
> * &#160; &#160;<label id='upstream'>Upstream：</label>基因上游长度；
> * &#160; &#160;<label id='downstream'>Downstream：</label>基因下游长度；
> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='SNPNum'>SNPNum：</label>筛选指定数量的突变进行单倍型分析，如当设置为10时，会将输入文件等分位10份，然后提出每小份中的第一行突变，生成筛选结果文件;
> * &#160; &#160;<label id='MaxNodeNum'>MaxNodeNum：</label>设置单倍型网络图中的最多节点数;

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;Haplotype Network：图中一个圆圈表示一个单体型，两个圆圈之间的连线表示这两个单体型相关（一个是由另一个突变而来），连线上面的短竖线表示从一个单体型到与其相连的单体型需要经历的碱基替换数，一个竖线表示一个替换。彩色的圆圈表示我们实际取样到的单体型，圆圈大小表示这种单体型的个数。灰色圆圈表示推断出来可能存在的中间单体型，没有被取样到。一种颜色一般表示一个群体，如按地理划分，品种划分等。图中例子一个单体型只存在于一个群体中，实际情况一个单体型往往在多个群体中出现。此时，一个单体型圆圈中填充多种颜色，以饼图的形式展示。
