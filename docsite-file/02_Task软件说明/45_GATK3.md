# GATK3
　　基于Illumina数据格式的人类全基因组和外显子组的测序数据，进行variant calling，（SNP、INDEL）的工具。 
　　功能：进行变异（SNP、Indel）检测并且可以输出gVCF（genomic VCF）文件格式。
  ***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451"> 详细说明**
　**GATK：**全称The Genome Analysis Toolkit，是Broad Institute开发的用于二代重测序数据分析的一款软件，里面包含了很多有用的工具，主要注重于变异的查找，基因分型且对于数据质量保证高度重视。它拥有强大的架构，强大的处理引擎，以及高性能计算功能，使它能够适用于任何规模的项目。该模块已为GATK版本3，主要是调用GATK3的“HaplotypeCaller”来进行变异检测。
　　软件官网：https://software.broadinstitute.org/gatk/ 

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　该Task的输入数据是GATKTools中的碱基质量值经过重新校正（即，“base quality score recalibration”）后的结果bam文件。
　  **InputBam：**经过GATK（base quality score recalibration）碱基质量值重新校正后的bam文件。校正后的bam文件中reads碱基的质量值能够更加接近真实的与参考基因组之间错配的概率。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　  **Interval_Bed：**指定capture region的Bed 文件。如果需要在对指定区域进行变异检测，则使用该输入文件来指定区域范围，如果该参数无输入文件，则表示对全基因组进行变异检测。

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　检测的SNP和indel结果文件，以VCF文件格式存储。


***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>参考序列物种。
　<label id='speciesVersion'>物种版本：</label>物种的版本。　
　**Unsafe：** GATK运行时，输入文件较严格，Unsafe选项是在运行前是否对输入文件做检查。该参数值有以下几个：
　　(1) SAFE：严格，输入文件格式做检查。
　　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配
　　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许bam文件sort的时不指定sort方式。
　　(5) LENIENT_VCF_PROCESSING：允许输入的VCF文件是非标准的VCF文件
　　(6) NO_READ_ORDER_VERIFICATION：不要求reads的顺序与bam文件中的reads顺序不一致。
　　(7) ALL：以上都允许。
　**Version：**选择GATK的版本，此处提供了两个版本GATK 3.6 和 3.8
　**线程数：**分析过程中使用CPU数
　**Memory：**分析过程中使用内存大小，单位为Mb
　**OutGVCF**：变异结果以gVCF文件格式输出，通过这个选项来输出与reference一致的碱基的相关信息，这样最终的结果其实就相当于包含了所有的位点，而不再仅仅是原先的variants位点。

**高级选项：**
　<label id='standCallConf'>stand Call Conf：</label>可信度阈值的设定，Set the minimum phred-scaled confidence threshold at which variants should be call，默认值30.0。
　<label id='standEmitConf'>stand Emit Conf：</label>在变异检测过程中，所容许的最小质量值。只有大于等于这个设定值的变异位点会被输出到结果中，默认值为10.0。
　<label id='mmq'>MapQuality：</label>在变异检测过程中，每条reads所容许的最小mapping质量值，默认值为20。
　<label id='mbq'>BaseQuality：</label>在变异检测过程中，每个碱基所容许的最小质量值，默认值为10。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　　记录突变位点的vcf文件：
<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
</div>

表中各列信息解释如下：
　#CHROM：变异位于的染色体、contig或者scaffold的ID
　POS：变异所在的位置
　ID：变异的ID
　REF：参考序列的碱基
　ALT：变异后的碱基
　QUAL：Phred格式（Phred_scaled）的质量值，表示在该位点存在变异的可能性，该值越高，则变异的可能性越大，计算公式为pread=-10*log(1-p)
　FILTER：标识出该变异是否可信
　INFO：变异详细信息
　FORMAT：基因型字段格式，以冒号隔开
　NC：样品名，表示每个样品的genotypes详细信息

　VCF的详细说明，请见官方文档： http://samtools.github.io/hts-specs/VCFv4.2.pdf
https://en.wikipedia.org/wiki/Variant_Call_Format
***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种。占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
　　**Indel：**insertion-deletion，插入缺失标记，指的是两种样本中在全基因组中的差异，相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。
　　gVCF: 格式详细说明，请见官方文档：
https://software.broadinstitute.org/gatk/documentation/article.php?id=4017

**参考文献：**
　1.	McKenna A. et al. The Genome Analysis Toolkit: A MapReduce framework for analyzing next-generation DNA sequencing data. Genome Res. 20, 1297–1303 (2010). [PMC free article] [PubMed]


