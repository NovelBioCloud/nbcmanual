# SamToolsVariant
　　该模块使用samtools中的mpileup命令生成bcf文件（mpileup是samtools中一个很重要的命令，以前为pileup），然后使用bcftools对该bcf文件进行SNP和Indel的分析。
**功能：**
　　将samtools和bcftools联合使用，进行变异检测分析。
**使用软件：**
　　Samtools：是一个用于操作sam和bam文件的工具合集,包含有许多命令。
  **软件官网：**http://www.htslib.org/doc/samtools.html

**应用范围:**
　　可针对外显子和全基因组重测序数据，进行SNP和indel检测。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是GATKTools中的碱基质量值经过重新校正（即，“base quality score recalibration”）后的结果bam文件。
　　**chrSeq：**需要分析物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
　　**InputBam：**经过GATK（base quality score recalibration）碱基质量值重新校正后的bam文件。校正后的bam文件中reads碱基的质量值能够更加接近真实的与参考基因组之间错配的概率。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
　　**BedFile：**指定capture region的Bed 文件。
　　**用途：**如果需要在对指定区域进行变异检测，则使用该输入文件来指定区域范围，如果该参数无输入文件，则表示对全基因组进行变异检测。
　　**格式：**BED格式详细解释，请见：http://genome.ucsc.edu/FAQ/FAQformat.html#format1
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　检测的SNP和indel结果文件，以VCF文件格式存储。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**参考序列物种
　**版本：**物种的版本
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　**maxDepth：**碱基的最大测序深度。
　**minBaseQuality：**碱基的最小质量值，低于该值的碱基会被过滤掉。碱基质量值过小会影响Variant预测的可信度。
　**minMappingQuality:**最小比对质量值。
　**VCF合并方式：**是否将多个样本的SNP/Indel结果进行合并，以及合并的方式。
　　　　　　none：不合并，输出多条记录。
　　　　　　snps：按照SNP记录进行合并。
　　　　　　indels:按照Indel记录合并。
　　　　　　both：按照SNP和Indel分别合并。
　　　　　　all：都合并在一起。
　　　　　　id:按照ID号合并。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1) * .vcf：所有结构变异结果文件，如：
<div style="text-align:center"><img data-src="2.png" width="750px" ></img></div>
表中各列信息解释如下：
<div style="text-align:center"><img data-src="3.png" width="450px"  ></img></div>
VCF的详细说明请见官方文档： 　　　
　　　http://samtools.github.io/hts-specs/VCFv4.2.pdf
　　　https://en.wikipedia.org/wiki/Variant_Call_Format

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种。占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
　　**Indel：**insertion-deletion，插入缺失标记，指的是一个样本相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。

参考文献：
Li H. A statistical framework for SNP calling, mutation discovery, association mapping and population genetical parameter estimation from sequencing data. Bioinformatics. 2011;27:2987–2993. [PMC free article] [PubMed]
