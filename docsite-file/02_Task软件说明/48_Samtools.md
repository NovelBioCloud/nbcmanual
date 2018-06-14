# Samtools
　　Samtools是一系列处理Bam格式文件的应用集合，可对bam文件进行排序、索引创建、比对结果统计、bcf文件（用于后续使用bcftools进行SNP和Indel的检测）生成以及PCR扩增reads（duplicates reads）过滤。
**功能：**
　(1)bam文件排序：可以将bam文件按照序列在参考序列（fasta文件）中的顺序（即header）或序列在参考序列上比对坐标的大小进行排序。
　(2)bam文件索引创建：必须对排序后的bam文件才能创建索引。
　(3)bam比对结果统计：调用samtools中的flagstat命令，统计比对后bam文件的比对结果。
　(4)bcf文件生成：对生成的bcf文件，可以使用bcftools进行SNP和Indel的分析。
　(5)duplicates reads过滤：NGS上机测试前需要对样品进行PCR扩增，使一个模板扩增出一簇，从而在上机测序的时候表现出为1个点，即一个reads，若一个模板扩增出了多簇，结果得到了多个reads，这些reads的坐标是相近的。在进行了reads比对后需要将这些由PCR扩增获得的reads去掉，并只保留最高比对质量的reads。

**使用软件：**
　　**Samtools：**是一个用于操作sam和bam文件的工具合集。包含有许多命令。
  软件官网：http://www.htslib.org/doc/samtools.html

**应用范围：**
　　应用于测序reads比对到参考序列上得到的bam文件，对bam文件进行排序、索引创建、比对结果统计、bcf文件生成以及 duplicates reads过滤。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于RnaSeqMap或者DnaSeqMap的比对结果bam文件，也可以是外源bam文件。
　　**inputFile：**RnaSeqMap或者DnaSeqMap的比对结果bam文件。SAM的全称是sequence alignment/map format。而BAM就是SAM的二进制文件（B取自于binary）。SAM文件详细说明，请见官方文档：http://samtools.github.io/hts-specs/SAMv1.pdf 。

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　\*.sorted.bam：排序后的bam文件。
　　\*.bam.bai：对排序后bam文件进行创建索引得到的索引文件，用于快速随机处理。
　　\*.rmdup.bam：过滤后得到的bam文件，
　　\*.pileup.gz：生成的bcf文件，可再使用bcftools软件进行SNP和indel的分析。 

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>参考基因组的物种。
　<label id='speciesVersion'>版本：</label>增加参考基因组的物种。　
　<label id='isSortBam'>sortBam：</label>是否对Bam文件进行排序(sort)。只能对bam文件进行排序, 不能对sam文件排序。
　<label id='isIndexBam'>indexBam：</label>是否对Bam文件构建索引（index）。必须对bam文件进行默认情况下的排序后，才能进行索引的构建。
　<label id='removeDuplicate'>removeDuplicate：</label>是否去除Duplicate序列。 
　<label id='GeneratePileUpFile'>GeneratePileUpFile：</label>是否生成bcf文件。
　<label id='minMQ'>MinMapQuality：</label>最小比对质量值，当勾选“GeneratePileUpFile”参数时，显示该参数。
　<label id='minBQ'>MinBaseQuality：</label>最小碱基质量值，当勾选“GeneratePileUpFile”参数时，显示该参数。
　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1)\*.bamStat.txt：对bam文件进行比对统计的，统计结果文件，如：
```
892039 + 0 in total (QC-passed reads + QC-failed reads)
20093 + 0 secondary
0 + 0 supplementary
0 + 0 duplicates
863979 + 0 mapped (96.85% : N/A)
871946 + 0 paired in sequencing
435973 + 0 read1
435973 + 0 read2
809268 + 0 properly paired (92.81% : N/A)
833358 + 0 with itself and mate mapped
10528 + 0 singletons (1.21% : N/A)
1494 + 0 with mate mapped to a different chr
1314 + 0 with mate mapped to a different chr (mapQ>=5)
```
　　每一项统计数据都由两部分组成，分别是QC pass和QC failed，表示通过QC的reads数据量和未通过QC的reads数量。每行详细说明如下：
<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>
　2)\*.pileup.gz：当勾选“**GeneratePileUpFile**”参数时，产生该结果文件，结果文件格式为：

<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>


　　结果文件包含6行：参考序列名；位置；参考碱基；比对上的reads数；比对情况；比对上的碱基的质量。其中第5列比较复杂,解释如下：
　1 ‘.’代表与参考序列正链匹配。
　2 ‘,’代表与参考序列负链匹配。
　3 ‘ATCGN’代表在正链上的不匹配。
　4 ‘atcgn’代表在负链上的不匹配。
　5 ‘*’代表模糊碱基
　6 ‘^’代表匹配的碱基是一个read的开始；’^'后面紧跟的ascii码减去33代表比对质量；这两个符号修饰的是后面的碱基，其后紧跟的碱基(.,ATCGatcgNn)代表该read的第一个碱基。
　7 ‘$’代表一个read的结束，该符号修饰的是其前面的碱基。
　8 正则式’\+[0-9]+[ACGTNacgtn]+’代表在该位点后插入的碱基；比如上例中在scaffold_1的2847后插入了9个长度的碱基acggtgaag。表明此处极可能是indel。
　9　正则式’-[0-9]+[ACGTNacgtn]+’代表在该位点后缺失的碱基。

**参考文献：**
Li H. A statistical framework for SNP calling, mutation discovery, association mapping and population genetical parameter estimation from sequencing data. Bioinformatics. 2011;27:2987–2993. [PMC free article] [PubMed]

