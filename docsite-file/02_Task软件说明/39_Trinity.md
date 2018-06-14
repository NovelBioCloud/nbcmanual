# Trinity
　　现有的转录组组装技术主要有三大方向：基于参考序列的组装，从头组装，两者结合的组装方法。其中，从头组装是指直接利用测序reads之间的overlap进行组装，最常用的组装软件即为Trinity。
**组装原理：**
　　1.首先通过Inchworm软件，使用k-mer算法对测序reads进行快速有效的组装。
　　2.然后通过Chrysalis软件对这些转录本进行聚类，并对这些类进行de Bruijn路径图的构建，每条路径反映了这些变异转录本重叠部分的复杂度。
　　3.最后通过Butterfly软件，结合相关reads分析路径图，报告出可信的转录本序列，对不同转录本亚型和来源于同一基因的转录本进行解析。
**功能：**
　　利用测序的reads之间的overlap进行转录组的组装。
**使用软件：**
**Trinity：**Trinity是由 the Broad Institute开发的转录组denovo组装软件，由三个独立的软件**模块组成：**Inchworm,Chrysalis和Butterfly。三个软件依次来处理大规模的RNA-Seq的reads数据。Trinity发表在国际期刊《NatureBiotechnology》。
**软件官网：**https://github.com/trinityrnaseq/trinityrnaseq/wiki
**应用范围**
对无参考基因组的物种进行转录组denovo拼接。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是经过数据过滤后的fastq文件。
　如果为双端测序，输入左端文件和右端文件；如果为单端测序，只拖入左端文件即可。
　　**左端序列文件：**测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz
　  **右端序列文件：**测序右端reads序列，单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
组装后序列文件（\* .trinity.Trinity.fasta），可用于后续的RNA分析中，当做参考序列使用。
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='seqType'>序列格式：</label>输入的reads类型，fa或fq。
<label id='max_memory'>最大内存：</label>Trinity在运行过程中使用的最大内存。
<label id='SS_lib_type'>链特异性：</label>测序reads 的链特异性方向。
<label id='thread'>CPU：</label>Trinity在运行过程中使用的CPU数量。
<label id='min_contig_length'>最小长度：</label>组装的最小序列长度。
<label id='bflyHeapSpaceMax'>bflyHeapSpaceMax：</label>运行Butterfly时java最大的堆积空间。
<label id='bflyHeapSpaceInit'>bflyHeapSpaceInit：</label>java初始的堆积空间。 
**contaionerNumber：**任务运行时使用contaioner数。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1)**\*.trinity.Trinity.fasta：**组装后序列文件，以fasta格式存储。
　2)**\*.contigLenDis.png：**组装后序列长度分布图，如：
<div style="text-align:center">
<img data-src="1.png" width="600px"  ></img>
</div>
　3)**\*.GeneToTran.txt：**组装的unigenes ID对应转录本ID，本文件中转录本的ID与unigenes ID相同，用于后续的表达量计算。
注：unigenes指组装后序列文件经过去冗余之后得到的基因序列。
　4)**\*.trinity.Trinity.fasta.stat.xls：**组装后结果统计信息，如：
 
 | Item       |  Result  |
| -------- |  :----: |
|Number of contigs  |  26153 |
|Number of characters(bp)  | 24776129|
| Average Length(bp)  | 947|
|Minimum Contigs Length  　|301|
|Maximum Contigs Length  　|11610|
|N50 Length      |1294　|　
|Median Length      |650　|　
**参考文献：**
Grabherr MG, Haas BJ, Yassour M, Levin JZ, Thompson DA, AmitI , et al. Full-length transcriptome assembly from RNA-Seq data without a reference genome. Nature Biotechnology. 2011; 29:644–652. pmid:21572440
