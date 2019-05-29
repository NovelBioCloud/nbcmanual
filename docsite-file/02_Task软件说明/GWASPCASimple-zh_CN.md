# <font color="#007979">GWASPCASimple</font>


---

&#160; &#160; &#160; &#160;PCA全称是Principal Component Analysis ，又叫做主成分分析。是一种分析、简化数据集的常用方法。主成分分析经常用于减少数据集的维数，同时保持数据集中对方差贡献最大的特征。例如：对于一个群体进行重测序，得到的snp位点是百万级别的，PCA分析过程就是从这百万级别的信息中提取关键的信息，以便我们使用更少的变量（指标）就可以对样本进行有效区分。这些被提取出的信息，按照其效应从大到小排列，我们称之为主成分1（principal component1）、主成分2、主成分3… ….。从生物学层面理解，PCA分析的过程就是信息浓缩的过程，会从原始的各个SNP位点信息中提取相似的信息，浓缩为新的变量PC1、PC2、PC3…. 输出。所以不同的主成分可能会对应不同的生物学意义，产生不同的聚类分类效果。

**<font color="#007979">输入方式</font>**

(1) 输入ped文件，ped文件是一个纯文本的文件，至少需要6列，每列有空格或者\t分隔。这6列分别表示：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) 输入bim文件，PLINK extended MAP file，bim文件是对map文件的拓展，总共有六行，包含了snp（variants）的具体信息，6列分别是：“染色体信息”、“snp的名字”、“摩尔距离”、“物理距离”、“要等位基因”、“主要等位基因”；

**<font color="#007979">输入参数</font>**

> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='maf'>Maf: </label>过滤掉等位基因频率（MAF）小于该设定值的位点，如0.01。
> * &#160; &#160;<label id='pca'>pca：</label>输出第n（默认n=20）个特征向量（保存为以*. Eigenvec为后缀的text文件）和所有的特征值（保存为以*.eigenval为后缀的text文件），这些特征值与EIGENSTRAT程序计算的值相等。这个选项唯一可能的目的是计算第一个m特征向量，然后在估计所有SNPs解释的方差时将它们作为协变量包含在模型中。如果你需要更复杂的总体结构的主成分分析，请使用EIGENSTRAT软件。

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;(a)	*.pca.eigenval样品名称的文件，该文件没有title行，第一个m特征值 
&#160; &#160; &#160; &#160;(b)	*.pca.eigenvec PCA结果文件，该文件没有title行，内容是特征向量值，第一列是family ID；第二列是individual ID，剩下列是特征向量值

