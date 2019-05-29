# <font color="#007979">PiAnalysisSimple</font>


---

&#160; &#160; &#160; &#160;衡量特定群体多态性高低的参数，是指在同一群体中随机挑选的两条DNA序列在各个核苷酸位点上核苷酸差异的均值。π值越大，说明其对应的亚群多态性越高。

**<font color="#007979">输入文件</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；

**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='windowPi'>windowPi：</label> 窗口大小(--window-pi)，整数；
> * &#160; &#160;<label id='windowStep'>windowStep：</label> 窗口步长(--window-pi-step) ，以设置的数值为窗口大小，计算窗口中的核苷酸多态性。第二个参数是设定窗口之间的步长，整数。

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;* .windowed.pi，输出文件中有以下这四列信息，分别为“CHROM”、“BIN_START”、“BIN_END”、“N_VARIANTS PI”。
