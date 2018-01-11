# BamCoverage
　　对bam文件进行统计，得到基因组覆盖度统计信息。
**功能：**
　　对比对的结果bam文件进行统计，得到基因组覆盖度统计信息。
**使用软件：**
　　GATK：GATK (全称The Genome Analysis Toolkit)是Broad Institute开发的用于二代重测序数据分析的一款软件，里面包含了很多有用的工具，主要注重于变异的查找，基因分型且对于数据质量保证高度重视。它拥有强大的架构，强大的处理引擎，以及高性能计算功能，使它能够适用于任何规模的项目。该模块已为GATK版本3，主要是调用GATK3的“DepthOfCoverage”来进行覆盖度的统计。
　　软件官网：https://software.broadinstitute.org/gatk/ 

**应用范围：**
　　统计比对后得到的bam文件，得到覆盖度信息。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的数据通常来源于排序后的bam文件。
　　**InputBam：**比对bam文件。要求Bam文件是排序后的。而BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。
　　详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　　**Interval_Bed：**指定区域的bed文件。用来指定基因组上的某些区域，即，如果该参数处有输入文件，则只统计输入文件中指定区域的比对信息，如果该处无输入文件，则统计全基因组范围的比对信息。
　　BED格式详细信息请见官网说明文档：http://genome.ucsc.edu/FAQ/FAQformat.html#format1

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**选择参考基因组物种
　**物种版本：**参考基因组的版本
　**物种类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**Unsafe：**GATK运行时，输入文件较严格，Unsafe选项是在运行过程中输入文件是否做检查。该参数值有以下几个：
　　　(1) SAFE：严格，输入文件格式做检查。
　　　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　　　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　　　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许输入不指定排序方式的排序后bam文件。
　　　(5) LENIENT_VCF_PROCESSING：允许输入的VCF文件是非标准的VCF文件
　　　(6) NO_READ_ORDER_VERIFICATION：不要求reads的顺序与bam文件中的reads顺序一致。
　　　(7) ALL：以上都允许。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1)\*.sample_cumulative_coverage_counts：输出基因区段中大于某个覆盖度值的基因区段和覆盖度值信息。
　2)\*.sample_cumulative_coverage_proportions：输出基因区段中大于某个覆盖度值的基因区段和覆盖度值的比例信息。
　3)\*.sample_interval_summary：如果输入了特定区域文件，则特定区域里相关的整体信息记录在里面
　4)\*.sample_interval_statistics：如果输入了特定区域文件，则特定区域里相关的统计信息记录在里面
　5)\*.sample_statistics：某个覆盖度范围之间碱基的数目，这边是一个直方图的统计结果，可以根据这个做出一个覆盖度的分布图。
　6)\*.Sequencing_Depth_Plot.png：根据“.sample_statistics”的结果，做出来的直方图，可以很直观的显示出覆盖度的信息。
<div style="text-align:center"><img data-src="1.png" width="400px" ></img></div>
图中，X轴为测序深度，Y轴为指定基因区段的覆盖度。

***

**参考文献：**
McKenna A. et al. The Genome Analysis Toolkit: A MapReduce framework for analyzing next-generation DNA sequencing data. Genome Res. 20, 1297–1303 (2010). [PMC free article] [PubMed]
