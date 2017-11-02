# RNASeqMap
　　将RNA-Seq数据进行比对到参考基因组序列的分析单元。
**功能：**
　　提供了多种将数据过滤后的clean data比对到参考基因组序列上的比对软件，使之可以根据不同的样品数据情况选择不同的比对算法。
**使用软件：**
　　（1）Hisat2：Hisat全称为Hierarchical Indexing for Spliced Alignment of Transcripts，由约翰霍普金斯大学开发，能够将RNA-Seq的reads与基因组进行快速比对。这项成果发表在2015年3月9日的《Nature Methods》上。HISAT已经更新到HISAT2.1.0，HISAT2是TopHat2/Bowti2的继任者，使用改进的BWT算法，实现了更快的速度和更少的资源占用，作者推荐TopHat2/Bowti2和HISAT的用户转换到HISAT2。
　　软件官网：http://ccb.jhu.edu/software/hisat2/index.shtml
　　（2）Tophat：是马里兰大学生物信息和计算机生物中心，以及加利福尼亚大学伯克利分校数学系和分子细胞生物学系以及哈弗大学的干细胞与再生生物学系联合开发的软件。它是基于Bowtie的将RNA-Seq数据mapping到参考基因组上，从而鉴定可变剪切（exon-exon splice junctions）。
　　软件官网：http://ccb.jhu.edu/software/tophat/index.shtml
　　（3）MapSplice：是马里兰大学生物信息和计算机生物中心，以及加利福尼亚大学伯克利分校数学系和分子细胞生物学系以及哈弗大学的干细胞与再生生物学系联合开发的软件。它是基于Bowtie的将RNA-Seq数据mapping到参考基因组上，从而鉴定可变剪切（exon-exon splice junctions）。
　　软件官网：http://www.netlab.uky.edu/p/bioinfo/MapSplice2
　　（4）STAR：是encode计划时冷泉港开发的，特点：超级快速（8min map完6gb的reads）、as支持性好、支持长reads、全转录本、发现嵌合转录本等。STAR能够发现非典型拼接和嵌合（融合）转录本，并能够比对全长RNA序列。还可以控制输出格式为SAM或者BAM,并对输出的BAM可进行选择性排序输出。最主要在比对的过程中还提供了ENCODE的比对参数。
　　软件官网：http://code.google.com/p/rna-star/

**应用范围:**
　　RnaSeq测序得到的Reads 序列比对到参考基因组序列上。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的数据来源于测序下机数据经过数据过滤后的fastq格式文件。
　　**左端序列文件：**测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz
　　**右端序列文件：**测序右端reads序列，单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz
　　**chrSeq：**需要分析物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中则不需要输入该文件。
　　**gtfFile：**需要分析物种的注释文件（GTF/GFF），如果该物种的基因组注释文件已经存在于物种版本数据库中则不需要输入该文件。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　当测序得到的fastq文件经过过滤处理以后，得到高质量的clean fastq文件后，再将clean fastq文件比对到基因组序列之后，通常会得到sam或者bam为扩展名称的文件，SAM的全称是sequence alignment/map format。而BAM就是SAM的二进制文件（B取自于binary）。在此我们最终输出为比对结果的bam格式文件，如filename.hisat2.bam。该文件可以用于计算基因表达量。如可作为SamAndRPKM的输入文件。
**SAM文件格式说明：**
　　SAM由头部注释信息（header section）和比对结果信息（alignment section），这两部分组成。注释信息可有可无，都是由一行行以@起始的注释构成。而比对结果信息，每一行表示一个片段（segment）的比对信息，包含11个必须得字段（mandatory fields）和一个可选的字段，字段之间用tag分割。这必须的11个字段，顺序固定，不可用时，根据字段的定义可以用“0”或者“*”来表示，这11个必须字段详细解释如下：
<div style="text-align:center"><img data-src="4.png" width="400px"></img>
</div>
　　可选字段（optional fields)，格式如:TAG:TYPE:VALUE，其中TAG有两个大写字母组成，每个TAG代表一类信息，每一行一个TAG只能出现一次，TYPE表示TAG对应值的类型，可以是字符串、整数、字节、数组等。
详请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf
<hr/>**<i class="fa fa-cog" aria-hidden="true"style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择参考基因组物种。
**物种版本：**参考基因组的版本
**物种类型**：同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
**SoftwareName：** 选择分析使用的软件
　　　　　Hisat2：调用Hisat2软件进行RNAseq的比对；
　　　　　Tophat：调用Tophat软件进行RNAseq的比对；
　　　　　MapSplice：调用MapSplice软件进行RNAseq的比对；
　　　　　STAR：调用STAR软件进行RNAseq的比对；
**minintronLen：**内含子区域最小长度，Tophat将会忽略检测小于设定值区段的donor/acceptor对。默认值为70。Hisat2中，默认值为20。 Mapsplice中，splice junctions最小长度，Mapsplice将不输出含有gap长度小于该设定值的splice junctions，默认值为50。Tophat、Hisat2、mapsplice共有参数
**maxintronLen：**内含子区域最大长度。Tophat将会忽略检测大于设定值区段的donor/acceptor对。默认值为500000。Hisat2中，默认值为500,000。Mapsplice中，splice junctions最大长度，Mapsplice将不输出含有gap长度大于该设定值的splice junctions，默认值为300,000。Tophat、Hisat2、mapsplice共有参数
**trim5：**5’端剪切掉多少碱基。比对之前剪切掉5’端多少bp的碱基，因为一般情况下如HiSeq测序的数据，reads的5’端和3’端碱基质量值会比较低。Hisat2参数
**trim3：**3’端剪切掉多少碱基。比对之前剪切掉3’端多少bp的碱基，因为一般情况下如HiSeq测序的数据，reads的5’端和3’端碱基质量值会比较低。Hisat2参数

**AlignNum：**每条reads输出的最多比对上的位置数。 Hisat2参数。
**ReportNovelSplicesite：**选中的话，将剪切位点输出到一个文件中。
**Dta：**为转录本重构软件(如：Stringtie)输出比对方式，选中此项，HISAT2需要更长的锚定长度来检测新的剪切位点，这样做会得到比短的锚定长度相比比较少的比对信息，进而有助于提高转录本组装软件的运算效率和内存使用。 Hisat2参数。
**使用Bowtie1：**选中此项，表示Tophat内部选用Bowtie1进行比对，否则默认使用Bowtie2，如果输入数据是colorspace reads，必须选中该选项，因为Bowtie2不支持colorspace reads的比对。Tophat参数
**colorspace reads文件说明如下：**
　　如测序平台式AB 5500xl Genetic Analyzer，输出的数据文件后缀名为.csfasta 和.qual，可以使用程序将.csfasta转化为.csfastq格式。
　　csfastq数据格式如下，还是四行代表一条read：
```
@SRR2967009.1 100_1000_1168_F3
T10011023211201220121202030102221012302121010131001
+
2@@@@>@?@@@@<@@//;@@/@9?@8@=@@@6;6@66;<@6@67?2?;/@
@SRR2967009.2 100_1000_1211_F3
T20132312201120021312220200023110220113100012321011
+
@@@@@@@@@<@@@@@@@@@@@@@@@@@@@@@@?@@@@/?@@@@@@@@<?@

```
　　该格式文件与普通的fastq数据格式略有区别，与普通的Fastq文件相比，csfastq里面记录的不是序列信息而是color的编码。

**高级选项：**
**MateInnerDist：**mate pairs之间平均插入距离，计算公式为：插入距离 = 建库fragment长度-每一端reads的长度。例如：一对paired reads,插入片段长度为300bp，两端reads长度为50bp，那么MateInnerDist=建库fragment长度[300bp] - 每一端reads的长度[50bpX 2] = 200bp，默认值为50bp。Tophat参数
**ReadMismatches：**reads最小mismatch碱基数，也就是说，在比对时，当一条reads的mismatch数大于设定值时，该条reads就会被认为是 比对上的reads，默认值为2。Tophat参数
**MinAnchor：**junction reads一边最小的匹配碱基数，即Tophat会输出junction reads两端大于设定长度的junction reads，最小值为3，默认值为8。Tophat参数
**SpliceMismatches：**spliced比对时，出现在”anchor”区域最大的mismatch数，默认值为0。 Tophat参数
**ReadGapLength：**reads比对时，如果一条reads的gap的总碱基数超过该设定的参数值，则舍弃该reads，默认值为2。 Tophat参数
**MaxInsertLength：**比对时，允许reads存在的最大插入片段长度，Tophat中默认为3bp。在mapsplice中默认参数为6，取值范围为【0,10】。 Tophat参数、mapsplice参数
**MaxDeletionLength：**比对时，允许reads存在的最大缺失长度，在Tophat中默认为3bp。在mapsplice中默认参数为6，取值范围为【0,10】
Tophat参数、mapsplice参数
**SegmentLength：**比对时reads被切分的最小片段长度，默认为25bp。
建议设置范围为【18,25】，片段长度小于18会引起比较高的假阳性，并且MapSplice运行会特别慢。当该reads 长度大于50bp时，强烈推荐将该参数设置为25。mapsplice参数
**minMapLen：**mapsplice仅输出完全比对碱基数不小于此设定值的reads，默认值为50。mapsplice参数
**isTophatFusion：**选中该参数，tophat进行fusion transcripts的检测。即reads会比对到fusion transcripts上，这种fusion 比对结果会输出到SAM格式文件中，在custom fields中使用“XF”与”XP”标记而且，关于fusion的更多信息也会比记录输出出来（数据结果文件为fusions.out），当比对完成以后，可以使用tophat-fusion-post进行过滤，得到可信的fusion transcripts，更详细的信息可以查看Tophat-Fusion 官网（http://ccb.jhu.edu/software/tophat/fusion_index.shtml）。
**MaxMultimappingScore：**得分范围低于多重比对的最大分数，默认值为1。STAR参数
**MaxNumberMapTo：**当reads maps小于该设定值时，才输出，否则不输出，默认值为10。STAR参数
**MaxMismatch：**比对时，reads上的最大mismatch数，默认值为10。 STAR参数
**MaxIntronSize：**最大的内含子长度，默认为0，当设置为0时，gap的长度为 (2^winBinNbits)XwinAnchorDistNbins。STAR参数
**MaximumMatesGap：**两个mates之间的最大gap长度，默认为0，当设置为0时，gap的长度为 (2^winBinNbits)X winAnchorDistNbins。STAR参数
**ExtraAlignmentScore：**提取跨越数据库junctions比对的比对值，默认为2。STAR参数
**MinOverhang：**注释spliced 比对的overhang(例如，block size)，默认值为3，该值应设置为大于零的整数。STAR参数
**MatchNminOverLread：**用read 长度标准化后的outFilterMatchNmin值，默认值为0.66。 STAR参数
**FilterScoreMinOverLread：**用read 长度标准化后的outFilterScoreMin值，默认值为0.66。 STAR参数
**Cufflinks-likeStrandFlag：**使用类似于Cufflinks的strand flag。
该参数有两个值None和intronMotif，None表示不使用，即不进行strand的鉴定；intronMotif表示strand的鉴定来源于内含子的motif。当reads的与非标准的内含子不一致时会被过滤出来。默认值为：None, STAR参数
**microexonSearch：**使用该参数，软件会检测micro-exons。该参数只有当输入reads长度大于50bp才起作用。Tophat参数
**fusion：**检测标准的和半标准的fusion junctions。Mapsplice参数
**minFusionDistance：**候选fusion的两个segments之间的最小距离。默认为10,000，如果检测Circurlar RNA，建议设置为200。Mapsplice参数


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**HISAT2结果说明：**
1.	*novel_splicesite.txt： 是hisat2输出的剪切位点信息。结果文件一共有四列分别为：染色体名称、位于内含子左侧侧翼碱基在基因组上的位置、位于内含子右侧侧翼碱基在基因组上的位置、正负链（+，-和.，其中‘.’表示非标准剪切位点处于未知链），每一列用tab键隔开。如：
`chr1	15037	15795`

**Tophat结果说明：**

1.	Junctions.bed： tophat检测到的junction信息，以UCSC BED文件格式进行存储，每一个junctions包含两个BED blocks， BED格式文件详情，请查看官方文档： http://genome.ucsc.edu/FAQ/FAQformat.html#format1
2.	deletions.bed：tophat检测到的deletions信息，以UCSC BED文件格式进行存储，BED格式文件详情，请查看官方文档： http://genome.ucsc.edu/FAQ/FAQformat.html#format1
3.	insertions.bed：tophat检测到的insertions信息，以UCSC BED文件格式进行存储，BED格式文件详情，请查看官方文档： http://genome.ucsc.edu/FAQ/FAQformat.html#format1
4.	Unmapped.bam 没有比对上的序列文件，以bam格式文件输出。
5.	Align_summary.txt reads比对结果统计文件，
```
Left reads:
          Input     :    440147
           Mapped   :    386226 (87.7% of input)
            of these:     14104 ( 3.7%) have multiple alignments (19 have >20)
Right reads:
          Input     :    440147
           Mapped   :    374372 (85.1% of input)
            of these:     13693 ( 3.7%) have multiple alignments (19 have >20)
86.4% overall read mapping rate.

Aligned pairs:    350748
     of these:     13091 ( 3.7%) have multiple alignments
                    1365 ( 0.4%) are discordant alignments
79.4% concordant pair alignment rate.

```

**mapsplice结果说明：**
1.junctions.txt：splice junctions结果文件，
结果文件格式如下：
chr1 17055 17233 JUNC_2 43 - 17055 17233 255,0,0 2 93,95, 0,274, 2.797654 6 CTAC 0.999110 1.000000 0 4 0.883721 32 11 32 9 23 0 32 11 2
**文件详细说明如下：**
　　chrom:splicing 所在的染色体名称
　　donerEnd:splicing 外显子doner的最后一个碱基位置
　　acceptorStart:splicing外显子acdeptor第一个碱基位置
　　name:splice junction 名称
　　coverage:比对到junction上的reads数
　　strand:junction所在的链信息
　　blockEnd:与donerEnd相同
　　blockStart:与acceptorStart相同
　　itemRgb:一个 RGB 值
　　blockCount:一行BED中包含的blocks数
　　maxPrefixSuffixAnchorLength:最大anchor长度的prefix和suffix，中间使用逗号隔开
　　blockStarts:blocks起始位置中间使用逗号隔开
　　entropy:junction的熵值
　　flank string case:junctions 数值表示，标准和半标准的junctions为非零整数。如
　　flank string:供体位点后两个碱基和受体位点前两个碱基的组合
　　intron score:内含子长度分值，该值越小越好
　　anchor score:供体 anchor和受体anchor的分值
　　min mismatch:junction reads的最小mismatch数
　　max mismatch:junction reads的最大mismatch数
　　average mismatch:所有junction reads的平均mismatch数
　　unique read count:比对到fusion上的uniquely mapped reads数
　　multiple read count:比对到fusion上的非uniquely mapped reads数
　　paired reads count:比对到fusion上的reads并且与比对到附近的fusion的reads具有PE关系的reads 数
　　left paired reads count: paired reads一端比对到另外一端基因组左侧位置的reads 数
　　right paired reads count:paired reads一端比对到另外一端基因组右侧位置的reads 数
　　multiple paired reads count:成对比对到fusion多个位置的reads数
　　unique paired reads count:对比对到fusion的uniquely mapped reads数
　　single reads count:非成对比对到fusion处的reads数
　　minimal anchor difference:供体位点和受体位点的最少差异
文件格式详情，请见官方文档：http://www.netlab.uky.edu/p/bioinfo/MapSplice2JunctionFormat
2.deletions.txt ： mapsplice检测到的deletions结果文件，文件格式详细解释，请见下方官方说明：
http://www.netlab.uky.edu/p/bioinfo/MapSplice2JunctionFormat
3.insertions.txt：mapsplice检测到的insertions结果文件，文件格式详细解释，请见下方官方说明：
http://www.netlab.uky.edu/p/bioinfo/MapSplice2InsertionFormat
**STAR结果文件**
1. *Log.out：软件运行过程中的运行细节log输出文件，该文件主要用于查找运行过程中的错误信息和调试软件时使用。
2. *Log.progress.out：软件运行进程信息的log文件，例如已经运行的reads比率等，每1分钟更新记录一次信息。
3. *Log.final.out：软件运行完成后，mapping 情况统计信息文件。 其中还用重要的质控信息。注意，STAR将一个paired-end reads按照一个read来进行统计。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
**Junction reads: **分段比对到两个外显子的测序序列（也称为Splice reads）
参考文献：
1.	Kim D, Langmead B, Salzberg SL. HISAT: a fast spliced aligner with low memory requirements. Nature Methods. 2015. April;12(4):357–360. doi: 10.1038/nmeth.3317 [PMC free article] [PubMed]
2.	Kim D, Pertea G, Trapnell C, Pimentel H, Kelley R, Salzberg SL. TopHat2: accurate alignment of transcriptomes in the presence of insertions, deletions and gene fusions. Genome Biology. 2013;14(4):R36 doi: 10.1186/gb-2013-14-4-r36 [PMC free article] [PubMed]
3.	Wang K., Singh D., Zeng Z., Coleman S.J., Huang Y., Savich G.L., He X., Mieczkowski P., Grimm S.A., Perou C.M., et al. MapSplice: Accurate mapping of RNA-seq reads for splice junction discovery. Nucleic Acids Res. 2010;38:e178. [PMC free article] [PubMed]
4.	Dobin A, Davis CA, Schlesinger F, Drenkow J, Zaleski C, Jha S, Batut P, Chaisson M, Gingeras TR. STAR: ultrafast universal RNA-seq aligner. Bioinformatics. 2013;29:15–21.  [PMC free article][PubMed]

