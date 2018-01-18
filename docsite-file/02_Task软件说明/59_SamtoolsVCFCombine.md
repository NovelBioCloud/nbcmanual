# SamtoolsVCFCombine
　　使用Samtools软件对SamtoolsVariant结果中的vcf文件进行变异检测，并对检测结果进行合并。
　　**功能：**对多个样品中分别使用Samtools中的mpileup命令生成的vcf文件进行变异检测并将结果进行合并。
  **使用软件：**
  **Samtools：**是一个用于操作sam和bam文件的工具合集，包含有许多命令。bcftools是samtool中附带的软件，bcftools和samtools类似，用于处理vcf(variant call format)文件和bcf(binary call format)文件。前者为文本文件，后者为其二进制文件
	**软件官网：**http://www.htslib.org/doc/samtools.html
   **应用范围：**对多个样品中分别使用Samtools中的mpileup命令生成的vcf文件，进行变异检测并将结果进行合并。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
该Task的输入数据是SamtoolsVariant结果中的\* genome.vcf.gz文件。
**InputVCF(.gz)：**输入SamtoolsVariant生成的vcf文件（.gz）。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
检测的SNP和indel结果文件，以VCF文件格式存储。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**VCF合并方式：**是否对多个样本的SNP/Indel结果进行合并，以及合并的方式。
　　　　　　　　none：不排序，输出多条记录。
　　　　　　　　snps：按照SNP记录进行合并。
　　　　　　　　indels:按照indel记录合并。
　　　　　　　　both：按照SNP和indel分别合并。
　　　　　　　　all：都合并在一起。
　　　　　　　　id:按照ID号合并。
　**Memory（Mb）：**软件运行时，使用内存数，以M为单位。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
\* .vcf：结构变异结果文件，如：
<div style="text-align:center">
<img data-src="2.png" width="700px"  ></img>
</div>
表中各列信息解释如下：
1	#CHROM	变异位于的染色体、contig或者scaffold的ID
2	POS	变异所在的位置
3	ID	变异的ID，
4	REF	参考序列的碱基
5	ALT	变异后的碱基
6	QUAL	Phred格式（Phred_scaled）的质量值，表示在该位点存在变异的可能性，该值越高，则变异的可能性越大，计算公式为pread=-10*log(1-p)
7	FILTER	标识出该变异是否可信
8	INFO	变异详细信息
9	FORMAT	基因型字段格式，以冒号隔开
10	NT-10A	样品名，表示每个样品的genotypes详细信息
VCF的详细说明请见官方文档： http://samtools.github.io/hts-specs/VCFv4.2.pdf
https://en.wikipedia.org/wiki/Variant_Call_Format

**详细说明**
　SNP：全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种。占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
Indel：insertion-deletion，插入缺失标记，指的是一个样本相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失。
**参考文献：**
1.Li H, Handsaker B, Wysoker A, Fennell T, Ruan J, Homer N, Marth G, Abecasis G, Durbin R, Subgroup GPDP. The sequence alignment/map format and SAMtools. Bioinformatics. 2009;25(16):2078–2079. doi: 10.1093/bioinformatics/btp352. [PMC free article] [PubMed] [Cross Ref]
2.Li H. A statistical framework for SNP calling, mutation discovery, association mapping and population genetical parameter estimation from sequencing data. Bioinformatics. 2011;27:2987–2993. [PMC free article] [PubMed]
3.BCFtools; available from: http://github.com/samtools/bcftools.
4.Li H, Handsaker B, Wysoker A, Fennell T, Ruan J, Homer N, Marth G, Abecasis G, Durbin R. The sequence alignment/map (SAM) format and SAMtools 1000 genome project data processing subgroup. Bioinformatics. 2009;25:1–2. doi: 10.1093/bioinformatics/btn594. [PMC free article] [PubMed][Cross Ref]