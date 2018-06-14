# Sprai
　　采用PacBio SMRT单分子实时测序技术，对细菌基因组进行从头测序组装，可以达到完成图级别，一次性获得完整的细菌基因组图谱，实现零gap的组装，同时可以获得质粒基因组信息。基于细菌完成图的精确组装，可为病原菌的预防控制、工业发酵、定向育种、农业微生物功能基因挖掘等各领域应用提供准确全面的数据支持。
**功能：**
	进行细菌基因组的PacBio 测序序列组装。
**使用软件：**
**Sprai：**Sprai(single-pass read accuracy improver)是一个为基因组denovo拼装（denovo assembly）进行single-pass reads（Pacbio数据的文库模型是两端加接头的哑铃型结构，测序时会环绕着文库进行持续的检测，pass即环绕测序的次数）纠错的软件。它最初的开发目的是为单分子DNA测序reads进行数据纠错，特别是针对于PacBio RS 测序产生的 Continuous Long Reads(在用于基因组denovo时，通常会构建10kb/20kb的文库，对长插入片段文库的测序基本是少于2 passes，得到的reads称为Continuous Long Reads (CLR)，这样的reads测序错误率等同于原始的测序错误率。)。Sprai的目的不是最大程度地纠正错误的reads，而是让使用纠错后数据组装得到的contigs尽可能地最长。
	**软件官网：** http://zombie.cb.k.u-tokyo.ac.jp/sprai/
    **应用范围**
	可用于PacBio测序数据，独立完成微生物基因组的完整拼接。

****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
该Task的输入数据是测序下机的PacBio序列文件。
　  **inputFile：**测序下机的PacBio数据，fastq格式文件。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
组装好的序列文件，可用于后续的基因序列方向确定，以及基因组分析和注释。
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='minLenForQuery'>minLenForQuery：</label>进行数据校正的reads的最短长度。
<label id='estimatedGenomeSize'>estimatedGenomeSize：</label>组装物种基因组大小的估计值。
<label id='estimatedDepth'>estimatedDepth：</label>测序深度估计值。
<label id='threadNum'>线程数：</label>组装过程中使用的线程数。
<label id='merSize'>merSize：</label>K-mer长度，默认为22。
<label id='merylMemory'>merylMemory：</label>CA（Celera Assembler，一种基因组组装算法）软件中调用的Mighty Meryl软件使用的内存总量。
<label id='merylThreads'>merylThreads：</label>CA软件中调用的Mighty Meryl软件使用的线程数。
<label id='ovlStoreMemory'>ovlStoreMemory：</label>使用内存的总量，以MB为单位，用来构建overlap store（即所有的overlap序列集合）。
**containerNumer：**运行过程中使用的contatiner数。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　最终结果都在9-terminator的文件夹中。
　	1) \*asm：该文件为Celera Assembler的输出文件，它提供了一个精确的以分层数据结构方式组装的描述信息，它不重复输入reads序列，但是包含了构成contig和scaffold的所有序列。该文件格式为Celera Assembler特定的文件格式 详细描述请见ASM guide（http://wgs-assembler.sourceforge.net/wiki/index.php/ASM_guide）　或者 ASM spec（http://wgs-assembler.sourceforge.net/wiki/index.php/ASM_spec）。
　	2) \*. qc文件：质量控制文件，它包含了100多个组装统计信息。
　	3) \*. fasta：组装后的序列文件。

**参考文献：**
Kim D, Langmead B, Salzberg SL. HISAT: a fast spliced aligner with low memory requirements. Nature Methods. 2015. April;12(4):357–360. doi: 10.1038/nmeth.3317 [PMC free article] [PubMed]