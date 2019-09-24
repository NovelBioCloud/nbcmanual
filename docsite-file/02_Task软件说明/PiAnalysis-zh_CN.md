# <font color="#007979">PiAnalysis</font>


---

&#160; &#160; &#160; &#160;衡量特定群体多态性高低的参数，是指在同一群体中随机挑选的两条DNA序列在各个核苷酸位点上核苷酸差异的均值。π值越大，说明其对应的亚群多态性越高。

**<font color="#007979">输入参数</font>**

> * &#160; &#160; *Region in chromosome*：选中该标签，表示按照输入染色体区域的方式进行分析，此时需要填写以下三个参数，即：“Chromosome”、“Start position”、“End position”；
> * &#160; &#160;<label id='chromosome'>Chromosome：</label>染色体号；
> * &#160; &#160;<label id='start'>Start position：</label>起始位置；
> * &#160; &#160;<label id='end'>End position：</label>终止位置；
> * &#160; &#160; *Gene locus*：选中该标签，表示按照输入基因名称以及距离该基因上下游位置距离的方式进行分析，此时需要填写以下三个参数，即：“Gene”、“Upstream”、“Downstream”；
> * &#160; &#160;<label id='gene'>Gene：</label>基因名称，如：Os01g0100100；
> * &#160; &#160;<label id='upstream'>Upstream：</label>基因上游长度；
> * &#160; &#160;<label id='downstream'>Downstream：</label>基因下游长度；
> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='windowPi'>windowPi：</label> 窗口大小(--window-pi)，整数；

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;* .windowed.pi，输出文件中有以下这四列信息，分别为“CHROM”、“BIN_START”、“BIN_END”、“N_VARIANTS PI”。
