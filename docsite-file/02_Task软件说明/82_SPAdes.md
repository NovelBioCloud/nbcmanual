# SPAdes
　　SPAdes主要用于进行单细胞测序的细菌基因组组装。输入数据可以是 Illumina、IonTorrent reads,或 PacBio、Sanger reads，也可以把一些contigs序列作为long reads进行输入。该软件可以同时接受多组paired-end、mate-pairs和unpaired reads 数据的输入。同时该软件有一个独立的模块用于进行杂合基因组的组装。
  注意：Illumina 数据和 IonTorrent 数据不能同时用于组装；SPAdes 支持的 Paired-end 和 Mate-Paired 的数据。
　　官网：http://spades.bioinf.spbau.ru/release3.0.0/manual.html#sec2.1
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
PE Left (FASTQ,BAM)\PE Right (FASTQ,BAM)：输入左端和右端数据，格式为FASTQ或BAM。
Mate Left (FASTQ)\Mate Right (FASTQ)：大片段的左端和右端数据

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
threadNum：使用线程
maxMemory(G)：最大内存数。
数据类型：选取数据类型
k-mer size：k-mer大小。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
final_contigs.fasta：组装完成的contig。
scaffolds.fasta：组装完成scaffolds。