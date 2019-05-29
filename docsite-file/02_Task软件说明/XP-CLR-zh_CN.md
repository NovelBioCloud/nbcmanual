# <font color="#007979">XP-CLR</font>

---

&#160; &#160; &#160; &#160;选择性清除：指由于最近的较强的正向自然选择，一个突变位点相邻DNA上的核苷酸之间的差异下降或消除。
&#160; &#160; &#160; &#160;XP-CLR使用了复合似然的方法，通过分析两个种群的差异来进行选择性清除的检测。

**<font color="#007979">输入参数</font>**

> * &#160; &#160; Region in chromosome：是否按照输入染色体区域的方式进行分析，该参数为单选框，如果选中该参数，则需要填写以下三个参数，即：“Chromosome”、“Start position”、“End position”；
> * &#160; &#160;<label id='chromosome'>Chromosome：</label>染色体号；
> * &#160; &#160;<label id='start'>Start position：</label>起始位置；
> * &#160; &#160;<label id='end'>End position：</label>终止位置；
> * &#160; &#160;Gene locus：是否按照输入基因名称以及距离该基因上下游位置距离的方式进行分析，该参数为单选框，如果选中该参数，则需要填写以下三个参数，即：“Gene”、“Upstream”、“Downstream”；
> * &#160; &#160;<label id='gene'>Gene：</label>基因名称，如：Os01g0100100；
> * &#160; &#160;<label id='upstream'>Upstream：</label>基因上游长度；
> * &#160; &#160;<label id='downstream'>Downstream：</label>基因下游长度；
> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='snpWin'>snpWin：</label>窗口内最大snp数，XP-CLR分数取决于SNPs的数量，为了使 XP-CLR值在区域内有可比性，有必要控制一个窗口内SNP的最大数据量，根据输入数据的snp密度选择设置窗口内最大snp数量；
> * &#160; &#160;<label id='gridSize'>gridSize：</label>两个grid之间的距离，单位是bp;
> * &#160; &#160;<label id='isPhased'>IsPhased：</label>基因型数据已经分阶段;
> * &#160; &#160;<label id='corrLevel'>corrLevel：</label>该值范围为[0,1]，如果该值在(0,1]之间，改值会在加权综合似然比检验的过程中被作为加权标准，如果两个SNP的相关性比较高(r2> corrLevel),它们对XP-CLR是低权的影响。如果corrLevel设置为0，那么XP-CLR就是无权计算;
> * &#160; &#160;<label id='chrNum'>chrNum：</label>染色体数;


**<font color="#007979">结果文件</font>**
&#160; &#160; &#160; &#160;\*.XPCLR.xpclr.txt，该文件中含有以下六列信息：“染色体号”、“grid号”、“window内snp数”、“物理位置”、“遗传位置”、“XPCLR值”。    
