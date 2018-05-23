# FreeBayes
　　SNP（single nucleotide polymorphism），即单核苷酸多态性，是由于单个核苷酸改变而导致的核酸序列多态性。 SNP只涉及到单个碱基的变异，这种变异可以是单个碱基的转换(transition)或颠换(transversion)，也可以是碱基的插入或缺失。DNA序列的变化将影响疾病的发生和演变，以及人体对病原体，化学试剂，药品及疫苗的病理反应，因此SNPs的正确解读被认为是未来实现个性化医疗的关键环节。另外，SNP的相关研究在农作物培育和畜牧业发展中也占据着重要地位。 目前SNP检测已广泛应用于群体遗传学和疾病相关基因的研究，在药物基因组学、诊断学和生物医学研究中发挥着重要作用。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;进行变异检测分析。
**使用软件：**
**FreeBayes：**是一个基于贝叶斯（Bayesian）算法的 基因变异检测软件，主要用于检测小多态性，如SNP（single-nucleotide polymorphisms）、Indel（insertions and deletions）、MNP（multi-nucleotide polymorphisms）和complex events（composite insertion and substitution events）。
**软件官网:**
&nbsp;&nbsp;&nbsp;&nbsp;https://github.com/ekg/freebayes
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;可针对外显子测序和全基因组重测序数据，进行SNP和Indel检测。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是经过一系列处理后的bam文件，这些处理包括排序、去重复、添加read group信息以及建索引。
**InputBam：**经过处理后的bam文件。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
**chrSeq：**需要分析物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
***

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;检测的SNP和Indel结果文件，以VCF文件格式存储。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>参考序列物种。
　<label id='speciesVersion'>版本：</label>基因组数据库版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　<label id='pvar'>polymorphism probability：</label>该位点存在多态性的可能性阈值（最小值）。
　<label id='theta'>mutation rate：</label>群体分析中，预期的突变率或者群体中成对核苷酸差异比率，这是EWens采样公式先验模型中的一个参数。
　<label id='ploidy'>ploidy：</label>需要分析的物种是几倍体，默认为：2。
　<label id='nosnps'>Ignore SNP alleles：</label>是否忽略SNP alleles。
　<label id='noindel'>Ignore indel alleles：</label>是否忽略 indel alleles。
　<label id='nocomplex'>Ignore comples events：</label>是否忽略 comples events(composite insertion and substitution events,即复杂的插入和置换事件)。

**高级设置：**
　<label id='minRepeatSize'>min repeat size：</label>当识别重复序列时，要求总重复序列的最小长度。
　<label id='usedupreads'>use duplicate reads：</label>是否使用重复reads。
　<label id='minMapQua'>min mapping quality：</label>检测变异过程中使用的reads的最小mapping 质量值。
　<label id='minCoverage'>minCoverage：</label>位点的最小覆盖数。
　<label id='repGenoLikeMax'>report genotype likelihood max：</label>是否在基因分型过程中使用最大似然估计（Maximum Likelihood，简称ML，是一种统计方法,它用来求一个样本集的相关概率密度函数的参数）。
　<label id='genotypeMaxIter'>genotypeing max iterations：</label>在基因分型过程中迭代的次数不超过该阈值，默认为：25。
 &nbsp; <label id='exclUnobserGeno'>exclude unobserved genotypes：</label>是否跳过没有reads支持的样品。
　<label id='useMapQua'>use mapping quality：</label>是否在计算最大似然估计值的时候使用等位基因的比对质量值。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　**\*.vcf ：** 结构变异结果文件，如：
<div style="text-align:center">
	<img data-src="1.png" width="600px" ></img>
</div>
表中各列信息解释如下：
<div style="text-align:center">
	<img data-src="2.jpg" width="500px" ></img>
</div>
VCF的详细说明请见官方文档： http://samtools.github.io/hts-specs/VCFv4.2.pdf
https://en.wikipedia.org/wiki/Variant_Call_Format
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">详细解释**
&nbsp;&nbsp;&nbsp;&nbsp;**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。单个核苷酸的变异包括转换、颠换、缺失和插入，形成的遗传标记的数量很多，多态性丰富。SNP是人类可遗传的变异中最常见的一种，占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
&nbsp;&nbsp;&nbsp;&nbsp;**Indel：**insertion-deletion，插入缺失标记，指的是在全基因组水平，一个样本相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。
***
**参考文献：**
1.	Garrison, E. & Marth, G. Haplotype-based variant detection from short-read sequencing. ArXiv Preprint. Arxiv:1207.3907 [q-bio.GN] (2012).
