# DnaSeqMap
　　将DNA-Seq数据比对到参考基因组序列的分析单元, 集成了Bwa_aln、Bwa_mem、Bwa_sw、Bowtie2、Bowtie等比对软件。
**功能：**
　	提供了多种将数据过滤后的clean data比对到参考基因组序列上的比对软件，使之可以根据不同的样品数据情况选择不同的比对算法。
**使用软件：**
　	（1）Bwa：BWA是用于将DNA序列比对到参考基因组（例如人类基因组）的软件。 它由三个比对算法组成：BWA-backtrack，BWA-SW和BWA-MEM。 第一种算法主要用于读长100bp以内的Illumina序列比对，而其余两个主要用于较长序列(70bp至几Mb)。BWA-MEM和BWA-SW共享类似的特征，例如长读取和嵌合比对的支持，但是BWA-MEM，其是最新的，通常被推荐为更快和更准确。 BWA-MEM还具有比BWA-backtrack更好的性能，用于70-100bp Illumina读取。
	软件官网：http://bio-bwa.sourceforge.net/
　	（2）Bowtie/Bowtie2：是一个快速、节省内存的将短序列比对到基因组上的工具。对于50bp-1000bp 的序列比对到相对较大的基因组上很有优势。
 	软件官网：
http://bowtie-bio.sourceforge.net/index.shtml
http://bowtie-bio.sourceforge.net/bowtie2/index.shtml
**应用范围**：DNA-Seq测序得到的Reads 序列比对到参考基因组序列上。

 ***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的数据来源于测序下机数据经过数据过滤后的fastq格式文件。
　　**左端序列文件：**测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz
　　**右端序列文件：**测序右端reads序列，单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz
　　**chrSeq：**需要分析物种的参考序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中则不需要输入该文件。


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　测序得到的fastq文件经过过滤处理得到高质量的clean fastq文件，将clean fastq文件比对到基因组序列之后，通常会得到sam或者bam为扩展名称的文件，SAM的全称是sequence alignment/map format,而BAM就是SAM的二进制文件（B取自于binary）。在此我们最终输出为比对结果的bam格式文件，如\*.bowtie2.bam。该文件可以用于检测变异（如SNP、Indel等）。
**SAM文件格式说明：**
　　SAM由头部注释信息（header section）和比对结果信息（alignment section）两部分组成。注释信息可有可无，都是由一行行以@起始的注释构成。而比对结果信息，每一行表示一个片段（segment）的比对信息，包含11个必须的字段（mandatory fields）和一个可选的字段，字段之间用tag分割。这必须的11个字段，顺序固定，不可用时，根据字段的定义可以用“0”或者“*”来表示，这11个必须字段详细解释如下：
<div style="text-align:center"><img data-src="3.png" width="550px"></img>
</div>

　　可选字段（optional fields)，格式如：TAG:TYPE:VALUE，其中TAG有两个大写字母组成，每个TAG代表一类信息，每一行一个TAG只能出现一次，TYPE表示TAG对应值的类型，可以是字符串、整数、字节、数组等。实例如：  
<span style="color:#F88158">ST-E00291:130:hktyvalxx:3:1101:9272:2294        83      chr5    25760843        255     140M    =       25760767        -216    GTTGATTCCTATAAACGAAAACACCCAAGCAGATTCGAGAAAAACAATGACGACCCATCTGAAGGAACTGATTCTTTTGATTAAAGAACTAGTTGGAAACATGCCTGAGGCTAAAGTAAGGCTAGCTCAGGTGCGTAAAT  ,FAF< FAKFFAAFKKK7KF7AKFFKFAKKA,AKF,<< A,KF7,,< A< F,,(<,KKF,7KKKKKKFKAKKKKKKFKKKKK< K7KKF7<,KFAFKFAAKF< KAKKFFKKKKKKKA,FKKKKAF7,F7FAKKFKKKKKKKKKF  <span style="color:#3090C7">MD:Z:122G17     XG:i:0  NH:i:1  NM:i:1  XM:i:1  XN:i:0  XO:i:0  AS:i:-3 YS:i:0  YT:Z:CP
<span style="color:#F88158">ST-E00291:130:hktyvalxx:3:1101:9272:2294        163     chr5    25760767        255     138M    =       25760843        216     TGGAGGCAAGTGTGAATGCAAATGTTGAGTTCCGTAGACTGGAAGCTCTTGATTTGATCACTGAAACTCTGAGATCGTTGATTCCTATAAACGAAAACACCCAAGCAGATTCGAGAAAAACAATGACGACCCATCTGA    KKKKKKKKKKKKKKKKKKKKKKAFFAK7FAFF< F7FK,F7FAKKKK7F7FFF,FFFFAFFAFKKKKF,< FKKKK< FKKAFKAKFK7FKFKKKKFKFKKKFKFFK,,7FKA,AAAKKKKKKKKK7<7AFKAKKKAK,AF    <span style="color:#3090C7">MD:Z:138        XG:i:0  NH:i:1  NM:i:0  XM:i:0  XN:i:0  XO:i:0  AS:i:0  YS:i:-3 YT:Z:CP

其中橙色标志出的为11个必选项，蓝色标示出的可选项。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf


 ***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>物种版本：</label>参考序列的版本。
　<label id='dbType'>物种类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　<label id='software'>softwarName：</label>选择比对使用的软件，其选项有：
　　　　　bwa_aln：调用bwa软件的aln算法进行比对，主要用于读长100bp以内的Illumina序列比对；
　　　　　bwa_mem：调用bwa软件的mem算法进行比对，支持较长reads的比对，同时也支持剪接性比对，该算法是最新的，通常被推荐为更快和更准确，对于 70bp-100bp 的 Illumina 数据来说，效果也更好些；
　　　　　bwa_sw：调用bwa软件的sw算法进行比对，可用于较长序列(70bp至1Mb)的比对，同时支持剪接性比对；
　　　　　bowtie2：调用bowtie2软件进行比对，主要适用于长度大于50bp的reads比对；
　　　　　bowtie：调用bowtie软件进行比对，该软件出现的最早，比较适用于长度在50bp以下的reads比对。

　<label id='threadNum'>线程数：</label>运行时使用线程数。
　<label id='memory'>内存：</label>运行时使用内存。
　<label id='isLocal'>is local：</label> 默认为End-to-end模式，当“SoftwareName”选择为“bowtie2”或者“bowtie”时，显示该参数。显示该参数；该参数有以下几个选项：very-fast、fast、sensitive、very-sensitive。　<div style="text-align:center"><img data-src="4.png" width="430px" ></img></div>
 其中设置的参数具体说明如下：
```
-D <int> 比对时, 将一个种子延长后得到比对结果, 如果不产生更好的或次好的比对结果, 则该次比对失败. 当失败次数连续达到<int>次后, 则该条read比对结束. Bowtie2才会继续进行下去. Default: 15. 当具有-k或-a参数, 则该参数所产生的限制会自动调整.
-R <int> 如果一个read所生成的种子在参考序列上匹配位点过多. 当每个种子平均匹配超过300个位置, 则通过一个不同的偏移来重新生成种子进行比对. <int>则是重新生成种子的次数. Default: 2.
-N <int> 进行种子比对时允许的mismatch数. 可以设为0或者1. Default: 0.
-L <int> 设定种子的长度.
-i <func> 设定两个相邻种子间所间距的碱基数。

```
 
 
　<label id='mismatch'>mismatch：</label>允许一条reads上最多错配碱基个数。
　<label id='gapLength'>gapLength：</label>gap长度。
　<label id='trim5'>trim5：</label>5’剪切掉5’端多少bp的碱基，默认值为：0，当“SoftwareName”选择为“bowtie2”或者“bowtie”时，显示该参数。
　<label id='trim3'>trim3：</label>剪切掉3’端多少bp的碱基，默认值为：0，当“SoftwareName”选择为“bowtie2”或者“bowtie”时，显示该参数。
　**score-min：**判断一条比对是否“有效”的最小阈值，这是一个reads长度相关的函数，当“SoftwareName”选择为“bowtie2”时，显示该参数。


**高级选项：**
　<label id='maxDiffInSeed'>maxDiffInseed：</label>使用bwa_aln软件进行比对时, seed序列的最大差异碱基数，默认值为2。
　<label id='excludeIndelInEnd'>excludeIndelInEnd：</label>使用bwa_aln软件进行比对时, reads末端indel序列长度大于此值时，被过滤掉。默认值为5。
　<label id='skipFirstIntReads'>skipFirstIntReads：</label>比对时reads的前几个bp不参与比对。
　<label id='minFragLength'>minFragLengt：</label>最小fragment长度，默认值为0。
　<label id='maxFragLength'>maxFragLeng：</label>最大fragment长度，默认值为500。
　<label id='maxMismatchesInSeed'>maxMismatchesInSeed：</label>seed中最大的mismatches数。
　<label id='seedLength'>seedLength：</label>seed长度。
　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1）*chr_distribution.png：reads在每条染色体上的分布图，如：
<div style="text-align:center"><img data-src="2.png" width="450px" ></img>
</div>
　2）*.mapping_statistics.xls，比对后统计结果，如：
 ```
 #Mapping_Statistics
#Item	S53
Statistics	Result
All	97377056
UnMapped	40838166
Mapped	56538890
MappedRate	0.581
UniqueMapped	47042307
UniqueMappedRate	0.483
RepeatMapped	9496583
AllBase	14342810735
UnMappedBase	6044864645
MappedBase	8297946090
UniqueMappedBase	6929094117
RepeatMappedBase	1368851973

########################

Chr_Distribution
ChrID	MappedReadsNum	MappedReadsProp	ChrLen	ChrLenProp
chr1	4264139	0.07541957403125531	249250621	0.08051526492275723
chr2	3215383	0.05687028875168933	243199373	0.07856053424293556
chr3	3299643	0.058360590383008934	198022430	0.06396705592199166
chr4	1564412	0.02766966242174192	191154276	0.061748440631800294

```
 
 ***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
**参考文献：**
1.	Li H. and Durbin R. (2009) Fast and accurate short read alignment with Burrows-Wheeler Transform. Bioinformatics, 25:1754-60. [PMID: 19451168]

2.	Li H. and Durbin R. (2010) Fast and accurate long-read alignment with Burrows-Wheeler Transform. Bioinformatics, Epub. [PMID: 20080505]

3.	Langmead B., Salzberg S.L. Fast gapped-read alignment with Bowtie 2. Nat. Methods. 2012;9:357–359. [PMC free article] [PubMed]

4.	Langmead B, Trapnell C, Pop M, Salzberg SL. Ultrafast and memory-efficient alignment of short DNA sequences to the human genome. Genome Biol. 2009;10(3):R25. doi: 10.1186/gb-2009-10-3-r25.[PMC free article] [PubMed] [Cross Ref]
