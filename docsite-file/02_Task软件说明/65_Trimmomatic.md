# Trimmomatic
　　尽管已经存在许多NGS片段预处理工具，但是我们不能找到在灵活性、正确处理双端数据和高性能方面满足我们需求的任何工具或工具组合。Trimmomatic作为一种更加灵活和高效的预处理工具，它能够正确地处理双端数据。Trimmomatic用两种策略来去除adapter: Palindrome and Simple。
**功能：**
　　1）切除reads两端质量差的碱基。
　　2）过滤掉含有adapter序列的文件。
　　3）过滤掉整条reads质量值低的reads序列。
　　4）截取指定长度的reads序列
**使用软件：**
　　Trimmomatic：一个针对 Illumina高通量测序的测序数据的修剪工具。既能够针对paired-end 也能够用于single ended。
**软件官网：**
　　http://www.usadellab.org/cms/index.php?page=trimmomatic

**应用范围**
　　用于处理测序下机reads序列文件。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
　　该Task的输入数据是测序得到的reads序列fastq格式文件，最终生成高质量的fastq文件，可用于比对到参考基因组上。
　如果为双端测序输入左端文件和右端文件，如果为单端测序只拖入左端文件即可。
　　**左端序列文件：**测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz
　　**右端序列文件：**测序右端reads序列，单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz
　　**adapterFile：**adapter序列文件，文件格式为fasta格式，如：
\>PrefixPE/1
AATGATACGGCGACCACCGAGATCTACACTCTTTCCCTACACGACGCTCTTCCGATCT
\>PrefixPE/2
CAAGCAGAAGACGGCATACGAGATCGGTCTCGGCATTCCTGCTGAACCGCTCTTCCG
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**<span>
　　处理后fastq格式文件，可用于后续比对分析。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>

**线程数：**软件运行时，使用线程数。
**使用内存：**软件运行时，使用内存数，以M为单位。
**切除首端最小质量值：**从 reads 的起始端开始切除质量值低于设定阈值的碱基，直到有一个碱基质量值达到阈值为止，默认为３。
**切除末端最小质量值：**从 reads 的末端开始切除质量值低于设定阈值的碱基，直到有一个碱基质量值达到阈值为止，默认为３。
**Windows长度：**滑动窗口扫描阅读的碱基个数，默认为４个碱基，结合下面的“**windows最小平均质量**”参数使用。
**windows最小平均质量：**滑动窗口选中碱基的最小平均质量值，默认为15，结合上面的“**Windows长度**”参数使用，当长度为“**Windows长度**”设定长度的windows内碱基的平均质量值小于“**windows最小平均质量**”设置阈值时，则切除。
**reads最小长度：**reads的最小长度，当reads小于该长度则舍弃，默认为36bp。
保留reads长度：保留的reads长度，将reads剪切到该指定的长度。
**剪切长度：**在reads的首端切除指定的长度。
**最低平均质量值：**丢掉质量低于这个值的reads。
**最大mismatch数：**允许的最大mismatch数。
**palindrome匹配碱基数：**指定针对 PE 的 palindrome clip 模式下，需要 R1 和 R2 之间至少多少比对分值，才会进行接头切除，默认值为 30。
**simple匹配碱基数：**指定切除接头序列的最低比对分值，通常 7-15 之间，默认值为10。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
1)\*.filter.fq.gz：对于single-ended（单末端）数据的结果文件。
对于paired-end（双末端）数据，输出四个文件：
2)\*.P.1.fq.gz/\*.P.2.fq.gz：reads的两端pair（R1和R2）均通过数据质控的结果文件。
3)\*.U.1.fq.gz/\*.U.2.fq.gz：reads的其中一端pair（R1或R2）通过数据质控，另一端无法通过数据质控，仅保留了一端的数据结果。
**参考文献：**
Bolger AM, Lohse M, Usadel B. Trimmomatic: a flexible trimmer for Illumina sequence data. Bioinforma Oxf Engl. 2014;30:2114–2120. doi: 10.1093/bioinformatics/btu170. [PMC free article][PubMed] [Cross Ref]

