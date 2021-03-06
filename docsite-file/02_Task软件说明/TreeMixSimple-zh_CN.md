# <font color="#007979">TreeMixSimple</font>

---

&#160; &#160; &#160; &#160;基因流：又叫迁移压力或基因迁移，是指从一个物种的一个种群向另一个种群引入新的遗传物质，从而改变群体“基因库”的组成。通过基因交流向群体中引入新的等位基因，是遗传变异一个非常重要的来源，影响群体遗传多样性，产生新的性状组合。即由于某种原因，具有某一基因频率的群体的一部分移入基因频率与其不同的另一群体，并杂交定居，就会引起迁入群体的基因频率发生改变。
TreeMix是一个用户全基因组等位基因频率数据推断种群分化和融合的程序，如果给定一些群体的等位基因频率，该程序会得到该群体的最大似然树以及一些可能的融合时间。

**<font color="#007979">输入文件</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；
(3) strainInfo.txt：品种对应亚种的文本文件，至少要有两列信息，第一列品种，第二列品种对应的亚种；


**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='disequilibrium'>Disequilibrium：</label>为了说明周围snp不是独立事件，使用k标志将他们组合在一个大小为nSNP的窗口中。假设snp在基因组上的顺序与输入文件中的顺序相同（例如是3），那么建议使用远远超过该生物已知LD范围的n值（当然，这个取决于SNP密度）。
> * &#160; &#160;<label id='migration'>Migration：</label>如果想让树中有更多的迁移事件，可以使用该（-m）参数，参数值为允许的迁移事件的数量。


**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;1. *.stem.cov.gz. 由数据估计的群体间的协方差矩阵
&#160; &#160; &#160; &#160;2. *.stem.covse.gz. 协方差矩阵中每一项的标准误差
&#160; &#160; &#160; &#160;3. *.stem.modelcov.gz. 根据模型拟合协方差
&#160; &#160; &#160; &#160;4. *.stem.treeout.gz. 拟合的树模型和迁移事件
&#160; &#160; &#160; &#160;5. *.stem.vertices.gz.包含推断图的内部结构。如果您尝试重新读取图表，修改这些文件将会导致一些问题，因此我们建议不要这样做。
&#160; &#160; &#160; &#160;6. *.stem.edges.gz. 从数据中推断的树在outstem.treeout.gz中。该文件的第一行是Newick format ML树，其余行包含迁移边缘。这些线的第一列是边缘上的权重，然后(可选地)是权重的jackknife估计数、标准误差的jackknife估计数和p值。然后是迁移边缘原点以下的子树，以及迁移边缘终点以下的子树。
&#160; &#160; &#160; &#160;7. * .treemix.png，系统进化树图形化展示png格式文件
&#160; &#160; &#160; &#160;8. * .treemix.pdf，系统进化树图形化展示PDF格式文件
