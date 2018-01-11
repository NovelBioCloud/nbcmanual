# GATKTools
　　GATKTools包含recalibtate和 realign两个工具。 
**功能：**
　1.realign是将比对到Indel附近的reads进行局部重新比对，由于在Indel周围出现mapping错误的概率很高，而在Indel周围进行一些重排可以大大减少由于Indel而导致的很多SNP的假阳性。
　2.recalibtate对bam文件reads的碱基质量值进行重新校正，使最后输出的bam文件中reads中碱基的质量值能够更加接近真实的与参考基因组的错配概率。

**使用软件：**
　　GATK (全称The Genome Analysis Toolkit)是Broad Institute开发的用于二代重测序数据分析的一款软件，里面包含了很多有用的工具，主要注重于变异的查找和基因分型分析，且对于所分析的数据质量有很高要求。它拥有强大的架构，强大的处理引擎，以及高性能计算功能，使它能够适用于任何规模的项目。
　　软件官网：https://software.broadinstitute.org/gatk/ 

**应用范围:**
　1）比对到Indel附近的reads进行局部重新比对，将比对的错误率降到最低。一般情况下，绝大部分需要进行重新比对的基因组区域，都是因为插入/缺失的存在而出现大量的碱基错配，这些碱基的错配很容易被误认为SNP。
　2）对bam文件里reads的碱基质量值进行重新校正，使最后输出的bam文件中reads中碱基的质量值能够更加接近真实的与参考基因组的错配概率。适用于多种数据类型，包括illumina、solid、454、CG等数据格式。在GATK2.0以上版本中还可以对Indel的质量值进行校正，对变异检测非常有帮助。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是DnaSeqMap中的比对结果bam文件。
　  **InputBam：**比对结果bam文件。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　  **InputVCF(dbSNP)：**已知可靠的indel位点，通常为dbSNP、1000G、EXAC等数据库的VCF文件，重比对将主要围绕这些位点进行。
　  **Interval_Bed：**指定capture region的Bed 文件。
   **用途：**用来指定基因组上的某些区域，即，如果该参数处有输入文件，则只统计输入文件中指定区域的比对信息，如果该处无输入文件，则对全基因组范围进行分析。
   **格式：**BED格式详细解释，请见：http://genome.ucsc.edu/FAQ/FAQformat.html#format1

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　重比对后的文件和recalibtate后的bam文件。可用于后续的SNP和Indel的检测。  

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**参考序列物种。
　**物种版本：**参考序列物种的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**ToolsType：**选择GATK的功能，其选项值有：
　　　　　　　　Recalibtate：对bam文件里reads的碱基质量值进行重新校正。
　　　　　　　　Realign：重比对，比对到indel附近的raeds进行局部重新比对，将比对的错误率降到最低。
             
　**Unsafe：**GATK运行时，输入文件较严格，Unsafe选项是在运行过程中输入文件是否做检查。该参数值有以下几个：
　　(1) SAFE：严格，输入文件格式做检查。
　　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许bam文件sort的时不指定sort方式。
　　(5) LENIENT_VCF_PROCESSING：允许输入的VCF文件是非标准的VCF文件。
　　(6) NO_READ_ORDER_VERIFICATION：不要求reads的顺序与bam文件中的reads顺序不一致。
　　(7) ALL：以上都允许。
　**线程：**分析过程中使用CPU数。
　**Memory：**分析过程中占用内存大小，单位为Mb。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　(1)\*_ recal.bam：碱基质量值重新校正后的结果bam文件，BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　(2)\*.intervals：通过运行RealignerTargetCreator来确定要进行重新比对的区域。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
　　**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性，包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种，占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
　　**Indel：**insertion-deletion，插入缺失标记，指的是一个样本的基因组序列相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。

**参考文献：**
　1.McKenna A. et al. The Genome Analysis Toolkit: A MapReduce framework for analyzing next-generation DNA sequencing data. Genome Res. 20, 1297–1303 (2010). [PMC free article] [PubMed]

