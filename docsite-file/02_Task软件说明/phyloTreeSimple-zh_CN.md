# <font color="#007979">phyloTreeSimple</font>

---

&#160; &#160; &#160; &#160;系统进化树（phylogenetic tree，又称evolutionary tree进化树）是描述群体间分化顺序的分支图或树，用来表示群体间的进化关系。根据群体的物理或遗传学特征等方面的共同点或差异可以推断出它们的亲缘关系远近。
&#160; &#160; &#160; &#160;PHYLIP是一个综合的系统发生分析软件包，由华盛顿大学的Joseph Felsenstein开发的。现在该软件包可完成许多系统发生分析。软件包中可用的方法包括了简约法、距离矩阵和似然法，以及bootstrap和一致 性树。可以处理的数据类型有分子序列、基因频率、限制性位点、距离矩阵和二进制离散字符。

**<font color="#007979">输入文件</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；

**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='treeType'>TreeType：</label>建数使用的方法，其选项值有NJ、MP和ML；NJ表示基于距离矩阵的方法（邻接法）;MP（最大简约法）；ML最大似然法
> * &#160; &#160;<label id='seqType'>SeqType：</label>输入序列类型，其选项为DNA或者AA，DNA表示核酸序列；AA表示蛋白序列；
> * &#160; &#160;<label id='dootstrapDup'>DootstrapDup：</label>设置bootstrap的值，即重复的replicate的数目，通常使用1000或者100

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;*.tre 为constree文件，可以在treeview中直接查看进化树的内容。
&#160; &#160; &#160; &#160;*.png/pdf 进化树图形化以png/pdf格式保存。
