# <font color="#007979">XP-CLRSimple</font>

---

&#160; &#160; &#160; &#160;选择性清除：指由于最近的较强的正向自然选择，一个突变位点相邻DNA上的核苷酸之间的差异下降或消除。
&#160; &#160; &#160; &#160;XP-CLR使用了复合似然的方法，通过分析两个种群的差异来进行选择性清除的检测。

**<font color="#007979">输入文件</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；

**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='snpWin'>snpWin：</label>窗口内最大snp数，XP-CLR分数取决于SNPs的数量，为了使 XP-CLR值在区域内有可比性，有必要控制一个窗口内SNP的最大数据量，根据输入数据的snp密度选择设置窗口内最大snp数量；
> * &#160; &#160;<label id='gridSize'>gridSize：</label>两个grid之间的距离，单位是bp;
> * &#160; &#160;<label id='isPhased'>IsPhased：</label>基因型数据已经分阶段;
> * &#160; &#160;<label id='corrLevel'>corrLevel：</label>该值范围为[0,1]，如果该值在(0,1]之间，改值会在加权综合似然比检验的过程中被作为加权标准，如果两个SNP的相关性比较高(r2> corrLevel),它们对XP-CLR是低权的影响。如果corrLevel设置为0，那么XP-CLR就是无权计算;
> * &#160; &#160;<label id='chrNum'>chrNum：</label>染色体数;


**<font color="#007979">结果文件</font>**
&#160; &#160; &#160; &#160;\*.XPCLR.xpclr.txt，该文件中含有以下六列信息：“染色体号”、“grid号”、“window内snp数”、“物理位置”、“遗传位置”、“XPCLR值”。    
