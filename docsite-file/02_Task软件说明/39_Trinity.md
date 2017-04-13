# Trinity
　　Trinity是由 the Broad Institute开发的转录组denovo组装软件，由三个独立的软件模块组成：Inchworm,Chrysalis和Butterfly。三个软件依次来处理大规模的RNA-seq的reads数据。　　Trinity发表在 NatureBiotechnology。Trinity的简要工作流程为：
　（1）Inchworm: 将RNA-seq的原始reads数据组装成Unique序列；
　（2）Chrysalis: 将上一步生成的contigs聚类，然后对每个类构建Bruijn图；
　（3）Butterfly: 处理这些Bruijn图，依据图中reads和成对的reads来寻找路径，从而得到具有可变剪接的全长转录子，同时将旁系同源基因的转录子分开。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　leftInputData 、 rightInputData ：分别拖入左端文件和右端文件，数据格式为：FASTA,FASTQ。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='seqType'>序列格式：</label>输入的reads类型，fa或fq。
　<label id='max_memory'>最大内存：</label>Trinity在运行过程中使用的最大内存。
　<label id='SS_lib_type'>链特异性：</label>Strand-specific RNA-Seq reads 方向。
　<label id='CPU'>CPU：</label>Trinity在运行过程中使用的CPU数量。
　<label id='min_contig_length'>最小长度：</label>组装的最小序列长度。
　<label id='bflyHeapSpaceMax'>bflyHeapSpaceMax：</label>运行Butterfly时java最大的堆积空间。
　<label id='bflyHeapSpaceInit'>bflyHeapSpaceInit：</label>java初始的堆积空间。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　**Trinity.fasta：**Trinity组装得到的序列文件，以fasta格式存储。
　**Trinity.fasta.stat.xls：**对组装后的序列文件进行的统计结果文件。
 
必须的参数：
--seqType     reads的类型：(cfa, cfq, fa, or fq)
--JM   jellyfish使用多少G内存用来进行k-mer的计算，包含‘G’这个字符--left        左边的reads的文件名
--rigth       右边的reads的文件名
--single      不成对的reads的文件名
可选参数：
Misc：
--SS_lib_type        reads的方向。成对的reads: RF or FR; 不成对的reads
: F or R。在数据具有链特异性的时候，设置此参数，则正义和反义转录子能得到区分。默认情况下，不设置此参数，reads被当作非链特异性处理。FR: 匹配时，read1在5'端上游, 和前导链一致, read2在3'下游, 和前导链反向互补. 或者read2在上游, read1在下游反向互补; RF: read1在5'端上游, 和前导链反向互补, read2在3'端下游, 和前导链一致;
--output 　输出结果文件夹。默认情况下生成trinity_out_dir文件夹并将输出结果保存到此文件夹中。
--CPU　使用的CPU线程数，默认为2
--min_contig_length  报告出的最短的contig长度。默认为200
