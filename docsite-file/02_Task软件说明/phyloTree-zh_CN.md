# <font color="#007979">phyloTree</font>

---

&#160; &#160; &#160; &#160;系统进化树（phylogenetic tree，又称evolutionary tree进化树）是描述群体间分化顺序的分支图或树，用来表示群体间的进化关系。根据群体的物理或遗传学特征等方面的共同点或差异可以推断出它们的亲缘关系远近。
&#160; &#160; &#160; &#160;PHYLIP是一个综合的系统发生分析软件包，由华盛顿大学的Joseph Felsenstein开发的。现在该软件包可完成许多系统发生分析。软件包中可用的方法包括了简约法、距离矩阵和似然法，以及bootstrap和一致 性树。可以处理的数据类型有分子序列、基因频率、限制性位点、距离矩阵和二进制离散字符。

**<font color="#007979">输入参数</font>**

> * &#160; &#160; Region in chromosome：选中该标签，表示按照输入染色体区域的方式进行分析，此时需要填写以下三个参数，即：“Chromosome”、“Start position”、“End position”；
> * &#160; &#160;<label id='chromosome'>Chromosome：</label>染色体号；
> * &#160; &#160;<label id='start'>Start position：</label>起始位置；
> * &#160; &#160;<label id='end'>End position：</label>终止位置；
> * &#160; &#160;Gene locus：选中该标签，表示按照输入基因名称以及距离该基因上下游位置距离的方式进行分析，此时需要填写以下三个参数，即：“Gene”、“Upstream”、“Downstream”；
> * &#160; &#160;<label id='gene'>Gene：</label>基因名称，如：Os01g0100100；
> * &#160; &#160;<label id='upstream'>Upstream：</label>基因上游长度；
> * &#160; &#160;<label id='downstream'>Downstream：</label>基因下游长度；
> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='seqType'>SeqType：</label>输入序列类型，其选项为DNA或者AA，DNA表示核酸序列；AA表示蛋白序列；
> * &#160; &#160;<label id='fastest'>fastest</label>search the visible set (the top hit for each node) only Unlike the original fast neighbor-joining, -fastest updates visible(C) after joining A and B if join(AB,C) is better than join(C,visible(C)),-fastest also updates out-distances in a very lazy way,-fastest sets -2nd on as well, use -fastest -no2nd to avoid this.
> * &#160; &#160;<label id='lg'>lg</label> 用Le-Gascuel 2008 模型代替默认的Jones-Taylor-Thorton 1992 模型 (a.a. only)
> * &#160; &#160;<label id='gtr'>gtr</label> generalized time-reversible instead of (default) Jukes-Cantor (nt only)
> * &#160; &#160;<label id='gamma'>gamma</label> 使用 CAT 模型最后一轮优化分支长度后, 报告离散 gamma 模型下相同分类数量的可能性。FastTree使用相同的分支长度，但优化了gamma的形状参数并调节了长度。最后进化树将重新调节长度。为了使用CONSEL，也可以用-log产生每一个位点的可能性, 请参阅GammaLogToPaup.pl和FastTree网站文档.
> * &#160; &#160;<label id='noml'>noml</label>关闭最大似然法
> * &#160; &#160;<label id='nome'>nome</label>关闭最小进化 NNIs 和 SPRs,(用-intree额外运行ML NNIs时建议勾选)
> * &#160; &#160;<label id='wag'>wag</label>Whelan-And-Goldman 2001模型（仅限氨基酸比对）

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;*.tre 为constree文件，可以在treeview中直接查看进化树的内容。
&#160; &#160; &#160; &#160;*.png/pdf 进化树图形化以png/pdf格式保存。
