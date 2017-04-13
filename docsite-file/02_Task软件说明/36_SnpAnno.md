# SnpAnno　
　　SNP（Single Nucleotirle Polymorphisms）是指在基因组水平上由于单个核苷酸的变异而产生的一种DNA序列多态性。应用于外显子、重测序、转录组等SNP、indel的注释。SNP功能分析SNP可以在DNA、RNA和蛋白水平影响基因功能。SNP位点通过数据库注释包括染色体上的位置，基因名称以及序列标注等信息。平台具有丰富的数据库支持最新的信息分析，如NCBI，EBMI，uniprot，以及GO，KEGG PATHWAY收费版的数据库，OMIM，SNPdb,以及专业的小鼠数据库MGI，水稻数据库RAP-DB、IRGSP，拟南芥TAIR数据库，人类的千人基因组HapMap等等。
　　软件官网：http://www.snp-nexus.org/

****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　gtfFile：参考基因组注释文件，当数据库信息不全时或者非模式物种，我们可以在此输入上传该物种的GTF注释文件。
　chrSeq：参考基因组文件，FASTA序列文件，输入文件格式：FASTA。
　inFileArray：添加SNP位点注释的文件，输入文件格式：.txt 或.xls; .xlsx。
　数据输入格式：.vcf或txt、xls数据输出格式：xls。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本
　<label id='chrIDColumn'>ChrID列号：</label>染色体位置。
　<label id='startColumn'>StartSite列号：</label>突变位置列起始位点。
　<label id='refNrColumn'>RefNr列号：</label>数据库中记载参考基因组所对应的碱基。
　<label id='thisNrColumn'>ThisNr列号：</label>突变研究对象基因组中所对应的碱基。
　
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　将外显子上覆盖的reads与Ref基因组进行比对，利用GATK软件进行分析，将发生SNP/indel的位点挑选出来，并注明该位点的具体位置信息。将得到的SNP/indel与SNP/indel数据库进行比较，把在SNP/indel数据中没有但在样本中明显的SNP/indel筛选出来。
　　对实验组与对照组进行比对，得到差异的SNP、indel位点，同时对差异SNP、indel位点进行数据库比对过滤，除去已知的SNP、indel变异位点，得到全新的SNP、indel位点信息，对SNP、indel位点及相关信息进行统计。
<div style="text-align:center">
<img data-src="1.png" width="700px"></img>
</div>
**表头信息**
　**Symbol：**发生差异SNP、indel的基因名称。
　**AccID：**发生差异SNP、indel的基因转录本信息。
　**Description：**基因的描述。
　**#CHROM：**基因所在的染色体信息。
　**POS：**突变碱基所在的染色体位置。
　**REF：**参考序列记录碱基信息。
　**ALT：**测序结果突变碱基信息。
　**LocationDescription：**位置描述信息。
　**PropToGeneStart：**突变发生在基因层面的位置信息。
　**RefNr：**数据库记载三联密码子信息。
　**RefAA：**数据库记载氨基酸信息。
　**ThisNr：**突变后三联密码子信息。
　**ThisAA：**突变后氨基酸信息。
　**ConvertType：**转换类型。
　**SplitType：**突变分型。
　**ChamicalConvert：**化学性质转变。
　**AD：**Allelic depths for the ref and alt alleles in the order listed.
　**DP：**Approximate read depth (reads with MQ=255 or with bad mates are filtered).
　**GQ：**Genotype Quality.
　**GT：**Genotype.
　**PL：**Normalized, Phred-scaled likelihoods for genotypes as defined in the VCF specification.
　**AC：**Allele count in genotypes, for each ALT allele, in the same order as listed.
　**AF：**Allele Frequency, for each ALT allele, in the same order as listed.
　**AN：**Total number of alleles in called genotypes.
　**DB：**dbSNP Membership.
　**DP：**Approximate read depth; some reads may have been filtered.
　**DS：**Were any of the samples downsampled.
　**Dels：**Fraction of Reads Containing Spanning Deletions.
　**FS：**Phred-scaled p-value using Fisher's exact test to detect strand bias.
　**MQ：**Float,Description="RMS Mapping Quality.
　**QD：**Variant Confidence/Quality by Depth.




