# vcf2maf
　　vcf2maf将VCF文件注释，生成MAF格式，相当于将VCF格式转换成MAF格式。
　　MAF格式Mutation Annotation Format (MAF) ，是对突变进行注释的格式。一些和癌症分析相关的软件，要求MAF格式文件作为输入。经过GATK或samtools检测出突变的格式一般为VCF格式
　　官网：https://github.com/ckandoth/vcf2maf
　　

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
　　**inputVCF (VCF)：**输入VCF文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**选择参考基因组物种。
　**版本：**参考序列的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**BinSize:**每次计算的突变位点数量。
　**线程：**软件运行时，使用线程数。
　**内存：**软件运行时，使用内存数。
　**containerNumber：**软件运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>

　　生成maf文件。
<div style="text-align:center"><img data-src="1.png" width="600px"  ></img></div>


**Hugo_Symbol：**HUGO symbol for the gene (HUGO symbols are always in all caps). If no gene exists within 3kb enter "Unknown".
**Entrez_Gene_Id：**Entrez gene ID (an integer). If no gene exists within 3kb enter "0". **Center：**Genome sequencing center reporting the variant. If multiple institutions report the same mutation separate list using semicolons. Non-GSC centers will be also supported if center name is an accepted center name.
**NCBI_Build：**Any TGCA accepted genome identifier.  Can be string, integer or a float.
**Chromosome：**Chromosome number without "chr" prefix that contains the gene.
**Start_Position：**Lowest numeric position of the reported variant on the genomic reference sequence. Mutation start coordinate (1-based coordinate system).
**End_Position：**Highest numeric genomic position of the reported variant on the genomic reference sequence. Mutation end coordinate (inclusive, 1-based coordinate system).
**Strand：**Genomic strand of the reported allele. Variants should always be reported on the positive genomic strand. (Currently, only the positive strand is an accepted value).
**Variant_Classification：**Translational effect of variant allele.
**Variant_Type：**Type of mutation. TNP (tri-nucleotide polymorphism) is analogous to DNP but for 3 consecutive nucleotides. ONP (oligo-nucleotide polymorphism) is analogous to TNP but for consecutive runs of 4 or more.
**Reference_Allele：**The plus strand reference allele at this position. Include the sequence deleted for a deletion, or "-" for an insertion.
**Tumor_Seq_Allele1：**Primary data genotype. Tumor sequencing (discovery) allele 1. " -" for a deletion represent a variant. "-" for an insertion represents wild-type allele. Novel inserted sequence for insertion should not include flanking reference bases.
**Tumor_Seq_Allele2：**Primary data genotype. Tumor sequencing (discovery) allele 2. " -" for a deletion represents a variant. "-" for an insertion represents wild-type allele. Novel inserted sequence for insertion should not include flanking reference bases.
** HGVSc：**the coding sequence of the variant in HGVS recommended format
**HGVSp：**the protein sequence of the variant in HGVS recommended format
**HGVSp_Short：**Same as HGVSp, but using 1-letter amino-acid codes
**Transcript_ID：**transcript onto which the consequence of the variant has been mapped
**Exon_Number：**the exon number (out of total number)
**all_effects：**a semicolon delimited list of all possible variant effects, sorted by priority
 **Allele：**the variant allele used to calculate the consequence
** Gene：**stable Ensembl ID of affected gene
** Feature：**stable Ensembl ID of feature
** Feature_type：**type of feature. Currently one of Transcript, RegulatoryFeature, MotifFeature
** Consequence：**consequence type of this variation; comma-delimited if more than one
** cDNA_position：**relative position of base pair in cDNA sequence
 **CDS_position：**relative position of base pair in coding sequence
** Protein_position：**relative position of amino acid in protein
** Amino_acids：**only given if the variation affects the protein-coding sequence
 **Codons：**the alternative codons with the variant base in upper case
 Existing_variation：known identifier of existing variation
 **ALLELE_NUM：**allele number from input; 0 is reference, 1 is first alternate etc
 **DISTANCE：**shortest distance from variant to transcript
** STRAND_VEP：**the DNA strand (1 or -1) on which the transcript/feature lies
** SYMBOL：**the gene symbol
 **SYMBOL_SOURCE：**the source of the gene symbol
 **HGNC_ID：**gene identifier from the HUGO Gene Nomenclature Committee
** BIOTYPE：**biotype of transcript
** CANONICAL：**a flag indicating that the VEP-based canonical transcript was used for this gene
 **CCDS：**the CCDS identifier for this transcript, where applicable
** ENSP：**the Ensembl protein identifier of the affected transcript
 **SWISSPROT：**UniProtKB/Swiss-Prot accession
 **TREMBL：**UniProtKB/TrEMBL identifier of protein product
** UNIPARC：**UniParc identifier of protein product
 **RefSeq：**RefSeq identifier for this transcript
** SIFT：**the SIFT prediction and/or score, with both given as prediction (score)
**EXON：**the exon number (out of total number)
**INTRON：**the intron number (out of total number)
 **DOMAINS：**the source and identifier of any overlapping protein domains
 **CLIN_SIG：**clinical significance of variant from dbSNP
 **SOMATIC：**somatic status of each ID reported under Existing_variation
 **PUBMED：**pubmed ID(s) of publications that cite existing variant
 **MOTIF_NAME：**the source and identifier of a transcription factor binding profile aligned at this position
**MOTIF_POS：**the relative position of the variation in the aligned TFBP
** HIGH_INF_POS：**a flag indicating if the variant falls in a high information position of a transcription factor binding profile (TFBP)
**MOTIF_SCORE_CHANGE：**the difference in motif score of the reference and variant sequences for the TFBP
** IMPACT：**the impact modifier for the consequence type
 **PICK：**indicates if this block of consequence data was picked by VEP's pick feature
 **VARIANT_CLASS：**Sequence Ontology variant class
** TSL：**Transcript support level
 **HGVS_OFFSET：**Indicates by how many bases the HGVS notations for this variant have been shifted
 **PHENO：**Indicates if existing variant is associated with a phenotype, disease or trait
 **MINIMISED：**Alleles in this variant have been converted to minimal representation before consequence calculation
** FILTER：**Copied from input MAF/VCF, with ExAC-based common_variant tag added, as explained below

