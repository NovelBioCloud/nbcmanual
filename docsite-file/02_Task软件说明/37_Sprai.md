# Sprai
　　Sprai(single-pass read accuracy improver)是一个为denovo assembly做single-pass reads纠错的软件。它最初的开发目的是为单分子DNA测序reads做测序的数据纠错的，特别是针对于PacBio RS 测序产生的 Continuous Long Reads(CLRS)。Sprai的目的不是最大程度的纠正错误的reads，而是，让使用纠错后数据组装得到的contigs尽可能的最长。
　　官网：http://zombie.cb.k.u-tokyo.ac.jp/sprai/
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　inputFile输入文件：.fastq序列。
　输出文件：asm、qc、fasta。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='minLenForQuery'>minLenForQuery：</label>reads的最短长度进行数据校正。
　<label id='estimatedGenomeSize'>estimatedGenomeSize：</label>组装物种基因组大小的估计值。
　<label id='estimatedDepth'>estimatedDepth：</label>测序深度估计值。
　<label id='cpuNum'>线程数：</label>组装过程中使用的线程数。
　<label id='merSize'>merSize：</label>K-mer长度，默认为22。
　<label id='merylMemory'>merylMemory：</label>CA软件中调用的Mighty Meryl软件使用的内存总量。
　<label id='merylThreads'>merylThreads：</label>CA软件中调用的Mighty Meryl软件使用的线程数。
　<label id='ovlStoreMemory'>ovlStoreMemory：</label>使用内存的总量，以MB为单位，用来构建overlap store。

****

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　最终结果都在9-terminator的文件夹中。

1. asm文件：它提供了一个精确的以分层数据结构方式组装的描述信息，它不重复输入reads序列，但是包含了所有构成contig和scaffold的所有序列。该文件格式为Celera Assembler特定的文件格式 详细描述请见ASM guide（http://wgs-assembler.sourceforge.net/wiki/index.php/ASM_guide）或者 ASM spec（http://wgs-assembler.sourceforge.net/wiki/index.php/ASM_spec）。
2. qc文件：质量控制文件，它包含了100多个组装统计信息。
3. fasta：组装后的序列文件。
