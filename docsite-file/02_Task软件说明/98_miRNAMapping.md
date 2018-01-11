# miRNAMapping 
　　Small RNA是一类重要的体内调节分子，主要包含miRNA、piRNA和siRNA等。可参与基因转录后调控，调节细胞生长、分化，以及个体发育、生殖等主要生物学过程。通过高通量技术，研究者不仅可以精确定量small RNA的表达，还能从全small RNA组进行深入研究，寻找致病、影响发育、受药物调控、影响免疫机制或者受胁迫调控的small RNA。
**功能**
　 1) small RNA测序得到的序列比对到所分析物种的miRNA数据库，并统计表达量；
　 2) 提取没有比对到物种miRNA数据库的reads，将其再比对到物种的基因组序列上；
　 3) 统计small RNA测序得到的reads在Rfam数据库中的分类情况。
**使用软件**
　　**Bwa：**BWA是用于将DNA序列比对到参考基因组（例如人类基因组）的软件。 它由三个比对算法组成：BWA-backtrack，BWA-SW和BWA-MEM。 第一种算法主要用于读长100bp以内的Illumina序列比对，而其余两个主要用于较长序列(70bp至几Mb)。该模块使用BWA- backtrack算法。
  软件官网：http://bio-bwa.sourceforge.net/

**应用范围**
　　Small RNA测序reads比对，并计算表达量，可用于后续进行差异small RNA分析。亦可统计small RNA在Rfam数据库中的分布情况。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的数据来源于 fastq格式文件，通常是经过数据过滤后，得到的高质量fastq文件。
**InputFile：**测序reads序列。通常Small RNA测序得到的reads是单端序列。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz。


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　输出为比对到所分析物种的small RNA数据库后，得到的bam文件以及small RNA的表达量信息，本文件可以用于做差异small RNA分析等后续工作，如作为DifGene的输入文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**选择参考基因组物种。
　**物种版本：**参考基因组的版本。
　**物种类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**mappingTo：**选择将测序得到的reads比对到哪种参考序列上，该参数可多选，其选项有：
　**miRNA：**所分析物种的small RNA数据库。用于统计small RNA表达量。
　**genome：**所分析物种的genome序列。通常情况下，当small RNA比对到物种small RNA数据库上，比对率较低时，可提取出没有比对到物种small RNA上的reads，将这些reads比对到genome上，查看这些unmapped reads在基因组上的分布情况，可为质控提供信息。
　**Rfam：**Rfam数据库，将reads比对到Rfam数据库中，统计reads在Rfam数据库中的分布情况。
　**Mismatch：**比对时，允许一条reads上最多错配碱基个数。
　**Gap Extensions：** 比对结果中，比对上的序列含有的gap的最大长度。（gap是指在序列比对过程中，考虑到插入/缺失突变，采用插入空位的方法来增加匹配残基的数量，这些插入的空位即为gap）
　**Seed Length：**seed序列长度，如果设置的seed长度大于检测（query）序列长度，那么直接使用query序列进行比对，对于长reads，该值通常会被设置的范围是25-35。
　**Maximum number of alignments：**输出的最多比对条数，即，一条reads比对到多个位置，最多只输出设定值的比对位置信息。
　**Threads：**运行时使用线程数。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1).Sample_Exp：每个样本small RNA表达量列表文件存放在该文件夹中。每个样本分为成熟miRNA的表达量（counts数和TPM值），以及miRNA前体的表达量（counts数和TPM值）。
　2).map_statistics：small RNA比对统计表
 #Mapping_Statistics
#Item	1-OP_R1

| Statistics   |  Result  |
| ----- |  :--: |
|  All |  4101087 |
| UnMapped    | 3363785   |
| Mapped        |  737302  |
| MappedRate        |  0.180  |
| UniqueMapped        |  527882  |
| UniqueMappedRate        |  0.129  |
| RepeatMapped        |  209420  |
| AllBase        |  112844752  |
| UnMappedBase        |  11137204  |
| RepeatMappedBase        |  4404970  |
| InsertSize        |  51  |
Chr_Distribution

| ChrID   |  MappedReadsNum  |MappedReadsProp|  ChrLen  |  ChrLenProp  |
| -------- |  :----: | :----:  | :----:  | :----:  |
| hsa-mir-1-2     | 140 |1.898814868262937E-4 |  85    |  5.519408838846249E-4    |
| hsa-mir-1-1    | 117   |1.586866711334026E-4|71|4.610329735977455E-4|

　3）miRNAMapping_Result：与参考序列比对后得到的bam文件。如果“mappingTo”选中了“miRNA”,则输出unmapped reads。
　4）All.miRNA.mature.Counts.exp.txt：成熟miRNA在多个样本中counts数总列表。
　5）All.miRNA.mature.TPM.exp.txt：成熟miRNA在多个样本中TPM值总列表。
　6）All.miRNA.pre.Counts.exp.txt：miRNA前体在多个样本中counts数总列表。
　7）All.miRNA.pre.TPM.exp.txt：miRNA前体在多个样本中TMP值总列表。
***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**Rfam：**Rfam 是一个用于鉴定non-coding RNAs的数据库。Rfam的主要目的是使用敏感BLAST过滤器结合协方差模型(Covariance Models, CMs)，对核苷酸序列，特别是完整基因组，注释已知RNA家族的新成员。具有一个非常广泛的分类学区域的少数家族（例如，tRNA和rRNA）提供了大多数的序列注释，同时大多数Rfam家族（例如，snoRNAs和miRNAs）具有有限的分类范围，并提供了有限数目的注释。
  详细信息请查看官网：http://rfam.xfam.org。

参考文献：
1.Li H. and Durbin R. (2009) Fast and accurate short read alignment with Burrows-Wheeler Transform. Bioinformatics, 25:1754-60. [PMID: 19451168]

2.Li H. and Durbin R. (2010) Fast and accurate long-read alignment with Burrows-Wheeler Transform. Bioinformatics, Epub. [PMID: 20080505]
