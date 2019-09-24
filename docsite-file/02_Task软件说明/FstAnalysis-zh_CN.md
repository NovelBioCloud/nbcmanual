# <font color="#007979">FstAnalysis</font>

---

&#160; &#160; &#160; &#160;Fst：群体间固定指数，衡量群体中等位基因频率是否偏离遗传平衡论比例的指标，用来研究不同群体间的分化程度。其取值为0到1，0代表两个群体未分化，其成员间是完全随机交配的；1代表两个群体完全分化，形成物种隔离，且无共同的多样性存在。
&#160; &#160; &#160; &#160;VCFTools 可以进行不同群体间的Fst统计，它是根据Weir and Cockerham’s 1984的文件进行计算的。使用者需要提供每一个群体中包含哪些个体的text 文件（每一个个体写一行）。可以使用--weir-fst-pop 参数进行多个群体一起分析。

**<font color="#007979">输入参数</font>**

> * &#160; &#160; *Region in chromosome*：选中该标签，表示按照输入染色体区域的方式进行分析，此时需要填写以下三个参数，即：“Chromosome”、“Start position”、“End position”；
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>染色体号；
> * &#160; &#160;<label id='start'>Start position：</label>起始位置；
> * &#160; &#160;<label id='end'>End position：</label>终止位置；
> * &#160; &#160;*Gene locus*：选中该标签，表示按照输入基因名称以及距离该基因上下游位置距离的方式进行分析，此时需要填写以下三个参数，即：“Gene”、“Upstream”、“Downstream”；
> * &#160; &#160;<label id='gene'>Gene：</label>基因名称，如：Os01g0100100；
> * &#160; &#160;<label id='upstream'>Upstream：</label>基因上游长度；
> * &#160; &#160;<label id='downstream'>Downstream：</label>基因下游长度；
> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='winSize'>winSize:</label> (--fst-window-size)  窗口大小，整数
> * &#160; &#160;<label id='winStep'>winStep:</label>  (--fst-window-step)  窗口步长，这两个参数可以与“--weir-fst-pop”一起使用，实现在窗口基础上而不是在每个位点的基础上进行Fst的统计，整数。
> * &#160; &#160;<label id='subSp'>subSpA：</label>选择分析亚种，可以选择多个亚种（该下拉框中的值是来源于输入文件strainInfo.txt的第二列，所以，需要先输入strainInfo.txt文件以后，该参数值才是可选的）；
> * &#160; &#160;<label id='subSp'>subSpB：</label>选择分析亚种，可以选择多个亚种（该下拉框中的值是来源于输入文件strainInfo.txt的第二列，所以，需要先输入strainInfo.txt文件以后，该参数值才是可选的）；

**<font color="#007979">结果文件</font>**

*.windowed.weir.fst 列表文件
结果文件中包含六列，分别为染色体序号、Bin起始位置、Bin终止位置、变异数、WEIGHTED_FST、MEAN_FST
