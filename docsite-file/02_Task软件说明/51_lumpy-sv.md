# lumpy-sv
　　筛选结构变异(SV)检测及在基因组中的分布，能够检测到的结构变异类型有：插入、缺失、倒置、易位等。lumpy-sv构建一套独特的数据筛选处理流程，运用更快捷更有效的算法，由此而不断提高基因组结构变异检测的能力。
**功能：**
　　检测样品中的结构变异。
**使用软件：**
　　LUMPY：StringTie由约翰霍普金斯大学联合德州大学西南医学中心开发，能够组装转录本并预计表达水平。它应用网络流算法和可选的denovo组装，将复杂的数据集组装成转录本。StringTie能够拼接出更完整、更准确的基因，并且StringTie采用拼接和定量同步进行，相对于其他方法，其定量结果更加准确。
　　软件官网：https://github.com/arq5x/lumpy-sv
**应用范围：**
　　检测样本的结构变异。通常应用于DNA seq测序数据的后续分析，用来研究染色体水平变异的。与SNP比较，结构变异虽然发生的频率较低，但累及的序列长度却大大超过了SNP，因此对于人类健康和疾病的影响更为显著。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是RnaSeqMap中的比对结果bam文件。
　　**inputBam：**比对结果bam文件。BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　结构变异（structural variant），以vcf格式存储。
  
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　　**containerNumber：**运行时使用的container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　.vcf：结构变异结果文件，如：
<div style="text-align:center"><img data-src="1.png" width="700px"></img></div>

各列信息解释如下：
　　#CHROM：变异位于的染色体、contig或者scaffold的ID
　　POS：变异所在的位置
　　ID：变异的ID，
　　REF：参考序列的碱基
　　ALT：变异后的碱基
　　QUAL：Phred格式（Phred_scaled）的质量值，表示在该位点存在变异的可能性，该值越高，则变异的可能性越大，计算公式为pread=-10*log(1-p)
　　FILTER：标识出该变异是否可信
　　INFO：变异详细信息
　　FORMAT：基因型字段格式，以冒号隔开
　　NC：样品名，表示每个样品的genotypes详细信息

详细解释如下：
　https://en.wikipedia.org/wiki/Variant_Call_Format
　http://samtools.github.io/hts-specs/VCFv4.2.pdf

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
**SV：**染色体结构变异是染色体变异的一种，通常是指基因内大于1kp的DNA片段缺失、插入、重复、倒位、易位以及DNA拷贝数目变化（CNVs）。染色体结构变异与染色体数目变异引起的疾病统称染色体病。现在可以通过适当手段产前诊断，有利于预防。
参考文献：
Ryan M Layer, Colby Chiang, Aaron R Quinlan, and Ira M Hall. 2014. "LUMPY: a Probabilistic Framework for Structural Variant Discovery." Genome Biology 15 (6): R84. doi:10.1186/gb-2014-15-6-r84.



