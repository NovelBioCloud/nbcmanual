# <font color="#007979">FstAnalysisSimple</font>

---

&#160; &#160; &#160; &#160;Fst：群体间固定指数，衡量群体中等位基因频率是否偏离遗传平衡论比例的指标，用来研究不同群体间的分化程度。其取值为0到1，0代表两个群体未分化，其成员间是完全随机交配的；1代表两个群体完全分化，形成物种隔离，且无共同的多样性存在。
&#160; &#160; &#160; &#160;VCFTools 可以进行不同群体间的Fst统计，它是根据Weir and Cockerham’s 1984的文件进行计算的。使用者需要提供每一个群体中包含哪些个体的text 文件（每一个个体写一行）。可以使用--weir-fst-pop 参数进行多个群体一起分析。

**<font color="#007979">输入文件</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；

**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='winSize'>winSize:</label> (--fst-window-size)  窗口大小，整数
> * &#160; &#160;<label id='winStep'>winStep:</label>  (--fst-window-step)  窗口步长，这两个参数可以与“--weir-fst-pop”一起使用，实现在窗口基础上而不是在每个位点的基础上进行Fst的统计，整数。

**<font color="#007979">结果文件</font>**

*.windowed.weir.fst 列表文件
结果文件中包含六列，分别为染色体序号、Bin起始位置、Bin终止位置、变异数、WEIGHTED_FST、MEAN_FST
