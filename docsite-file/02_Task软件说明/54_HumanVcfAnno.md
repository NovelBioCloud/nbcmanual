# HumanVcfAnno
　　使用GATK3中的注释功能，对变异结果进行基因注释，有助于预测变异的生物学功能或意义。
　　**功能：**
　　对变异（SNP、Indel）结果进行dbsnp、EXAC、1000G以及cosmic数据库的注释。
　　**使用软件：**
　　GATK：GATK (全称The Genome Analysis Toolkit)是Broad Institute开发的用于二代重测序数据分析的一款软件，里面包含了很多有用的工具，主要注重于变异的查找和基因分型的分析，且对于所分析的数据质量有比较高的要求。它拥有强大的架构，强大的处理引擎，以及高性能计算功能，使它能够适用于任何规模的项目。该模块使用的GATK版本为3X系列（3.6与3.8），主要是调用GATK3的“VariantAnnotator”来进行重新注释。
　　**软件官网：**https://software.broadinstitute.org/gatk/ 
　　**应用范围:**
　　可用于GATK检测出来的变异结果（vcf）文件。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是GATK3产生的变异结果VCF文件。
　　**dbsnpVCF：**dbSNP数据库文件，要求VCF文件。
　　用途：用来注释输入的变异是否记录在dbSNP数据库中，如果已经收录在dbSNP中，给出在dbSNP中的编号，如rs 7417504。
　　**cosmicVCF：**cosmic数据库文件，要求VCF文件，
　　用途：用来注释输入的变异是否记录在cosmic数据库中，如果已经收录在cosmic中，给出在cosmic中的编号，如COSN6039437。
　　**thousandGenomeVCF：**千人基因组突变数据库文件，要求VCF文件。
　　用途：用来注释输入的变异是否记录在千人基因组数据库中，如果已经收录在千人基因组数据库中，则给出该突变在千人基因组数据库中各个种群中的突变率信息。
　　**EXAC-VCF：**EXAC数据库文件，要求VCF文件。
　　用途：用来注释输入的变异是否记录在EXAC数据库中，如果已经收录在EXAC基因组数据库中，则给出该突变在EXAC中各个种群中的突变率信息。
　　**InputVCF：**GATK检测变异结果VCF文件，VCF的详细说明请见官方文档： http://samtools.github.io/hts-specs/VCFv4.2.pdf


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　变异注释结果文件，以xls文件格式存储。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　**物种：**选择参考基因组物种。
　**物种版本：**参考基因组的版本。
　**Unsafe：**GATK运行时，输入文件较严格，Unsafe选项为在运行过程中输入文件是否做检查。该参数值有以下几个：
　　(1) SAFE：严格，输入文件格式做检查。
　　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许输入不指定排序方式的排序后bam文件。
　　(5) LENIENT_VCF_PROCESSING：允许输入的VCF文件是非标准的VCF文件。
　　(6) NO_READ_ORDER_VERIFICATION：不要求reads的顺序与bam文件中的reads顺序一致。
　　(7) ALL：以上都允许。
　**线程数：**分析过程中使用CPU数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1) * .xls：结构变异注释结果文件，如：
<div style="text-align:center"><img data-src="1.png" width="800px"  ></img></div>
表中各列信息解释如下：
　　#CHROM：变异位于的染色体、contig或者scaffold的ID。
　　POS：变异所在的位置。
　　ID：如果call出的SNP存在于dbsnp数据库里，就会显示相应的dbsnp里的rs编号。
　　REF：参考序列的碱基。
　　ALT：变异后的碱基。
　　QUAL：Phred格式（Phred_scaled）的质量值，表示在该位点存在变异的可能性，该值越高，则变异的可能性越大，计算公式为pread=-10*log(1-p)。
　　FILTER：标识出该变异是否可信。
　　INFO：变异详细信息。
　　FORMAT：基因型字段格式，以冒号隔开。
　　Test1：突变在样品中的基因型。
　　COSMIC：COSMIC数据库ID。
　　TG_All：千人基因组数据库中记载的总体突变频率。
　　TG_AFR：千人基因组数据库中记载的非洲群体的突变频率。
　　TG_AMR：千人基因组数据库中记载的美洲群体的突变频率。
　　TG_EAS：千人基因组数据库中记载的东亚群体的突变频率。
　　TG_EUR：千人基因组数据库中记载的欧洲群体的突变频率。
　　TG_SAS：千人基因组数据库中记载的南亚群体的突变频率。
　　EXAC_All：EXAC数据库中记载的总体突变频率。
　　EXAC_AFR：EXAC数据库中记载的非洲群体的突变频率。
　　EXAC_AMR：EXAC数据库中记载的美洲群体的突变频率。
　　EXAC_EAS：EXAC数据库中记载的东亚群体的突变频率。
　　EXAC_FIN：EXAC数据库中记载的欧洲（芬兰区域）的突变频率。
　　EXAC_NFE：EXAC数据库中记载的欧洲（芬兰之外区域）的突变频率。
　　EXAC_OTH：EXAC数据库中记载的其他群体的突变频率。
　　EXAC_SAS：EXAC数据库中记载的南亚群体的突变频率。

VCF的详细说明请见官方文档：
　　http://samtools.github.io/hts-specs/VCFv4.2.pdf
　　https://en.wikipedia.org/wiki/Variant_Call_Format
  
  ***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451"> 详细解释**

　　dbSNP：database of SNP（Wikipedia：The Single Nucleotide Polymorphism Database）单核苷酸多态性数据库dbSNP（http://www3.ncbi.nlm.nih.gov/SNP/) 是由NCBI与人类基因组研究所（National Human Genome Research Institute）合作建立的，它是集合了单碱基替换以及短插入/删除多态性相关信息的资源库。因为开发dbSNP 是为了补充和辅助 GenBank, 所以它包含了来自任何生物体的核苷酸序列。
　　cosmicVCF： Catalogue Of Somatic Mutations In Cancer ，主要由英国威康信托基金会桑格研究所（Wellcome Trust Sanger Institute）开发和运作，主要记录与人类各种类型癌症相关的体细胞突变信息，这个数据库对于突变位点的信息记录较为详细，包括文献出处、样本名称、组织类型、涉及到的癌症种类和具体的突变内容，这个库既有对某一基因突变现象的综合统计，也有针对某一肿瘤组织或癌症细胞系的所有突变信息统计。
　　1000G：1000 Genomes Project， 国际千人基因组计划将对SNPs(single nucleotide polymorphisms)、拷贝数突变(copy number variants)和短插入缺失突变(short insertions and deletions)这三类人类常见的遗传突变类型进行补充和完善,为人类遗传学和医学研究提供资源。
　　EXAC-VCF：Exome Aggregation Consortium，是目前规模最大的外显子组测序项目，ExAC是一个免费的、具有高分辨率编录的人类遗传变异数据库，包含了上千万个DNA变异——很多都是罕见变异，而且大多数为首次被发现，它对罕见遗传病的临床研究和诊断有重大的意义。

参考文献：
1.	McKenna A. et al. The Genome Analysis Toolkit: A MapReduce framework for analyzing next-generation DNA sequencing data. Genome Res. 20, 1297–1303 (2010).

  


