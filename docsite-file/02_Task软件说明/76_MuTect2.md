# Mutect2
　　Mutect2是GATK（The Genome Analysis Toolkit）下的一个子模块，可以得到高可信度的体细胞变异信息，有助于肿瘤体细胞突变精准筛选。
**功能：**
　　通常用于肿瘤相关的体细胞变异检测，MuTect不支持涉及插入/删除的突变，同时它会过滤掉比对质量低的reads、覆盖reads数低的位点、以及reads比对时出现链偏好性的位点。
**使用软件：**
　　Mutect2：Mutect2是GATK下的一个子模块，采用突变热点局部重比对和贝叶斯统计的方法，可以针对成对的正常-肿瘤样本进行体细胞变异分析，并对分析的结果进行校正过滤，去除正常样本和dbSNP库中的突变位点，最终得到高可信度的体细胞变异信息。
	软件官网：https://hpc.nih.gov/apps/muTect.html

**应用范围：**
　　适用于混杂的不纯肿瘤样本，检测体细胞SNP，运用精密的统计模型，假阳性产出率很低。


***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　GATKTools中的碱基质量值经过重新校正（即，“base quality score recalibration”）后的结果bam文件。
　  **InputBam：**经过GATK碱基质量值重新校正（即，base quality score recalibration）后的bam文件。校正后的bam文件中reads碱基的质量值能够更加接近真实的与参考基因组之间错配的概率。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　  **Interval_Bed：**指定capture region的Bed 文件。
**用途：**如果需要在对指定区域进行变异检测，则使用该输入文件来指定区域范围，如果该参数无输入文件，则表示对全基因组进行变异检测。
**格式：** BED格式详细解释，请见：http://genome.ucsc.edu/FAQ/FAQformat.html#format1


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　检测的SNP和indel结果文件，以VCF文件格式存储。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考基因组的版本。
**unsafe：**GATK运行时，输入文件较严格，Unsafe选项是在运行前是否对输入文件做检查。该参数值有以下几个：
　　(1) SAFE：严格，输入文件格式做检查。
　　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许输入不指定排序方式的排序后bam文件。
　　(5) LENIENT_VCF_PROCESSING：允许输入的VCF文件是非标准的VCF文件
　　(6) NO_READ_ORDER_VERIFICATION：不要求reads的顺序与bam文件中的reads顺序完全一致。
　　(7) ALL：以上都允许。
**AltFreqCutOff：**突变频率的阈值，默认值为0.08。
文件对比：加入对比的两个组份。选择实验组与对照组比较。
　　　　　group1Array：选择对比组1；
　　　　　group2Array：选择对比组2；
　　　　　outFileArray：输出文件名称。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
  \* .vcf：所有结构变异（SNP、Indel）结果文件，如：
<div style="text-align:center"><img data-src="2.png" width="750px" ></img></div>
表中各列信息解释如下：
<div style="text-align:center"><img data-src="3.png" width="450px"  ></img></div>
VCF的详细说明请见官方文档： 　　　
　　　http://samtools.github.io/hts-specs/VCFv4.2.pdf
　　　https://en.wikipedia.org/wiki/Variant_Call_Format

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种，占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。
　　**Indel：**insertion-deletion，插入缺失标记，指的是一个样本的基因组序列，相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。

参考文献：
Cibulskis K. et al. Sensitive detection of somatic point mutations in impure and heterogeneous cancer samples. Nat. Biotechnol. 31, 213–219 (2013). [PMC free article] [PubMed]



