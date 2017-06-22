### WGS分析流程
#### **流程介绍**
　　WGS是对已有参考基因组的物种，进行个体或群体全基因组测序，并进行生物信息分析的挖掘。基于WGS技术，我们能够快速寻找到大量基因变异，并实现遗传进化分析及重要性状候选基因预测。WGS已成为动植物育种、人类遗传学、转化医学和群体进化领域研究中最为迅速有效的方法之一。
　　WGS测序分析平台包括：单碱基突变、插入缺失变异、拷贝数变异和结构变异，在全基因组水平上扫描并检测与表型差异、疾病、进化等相关的突变位点，可更全面地挖掘基因序列差异和结构变异。

***
#### **平台流程** 
原始序列（[RawData](filePage?path=02_Task软件说明/29_RawDataTask.md)）-->数据质控（[FastQC](filePage?path=02_Task软件说明/01_FastQC.md)）-->参考基因组比对（[DnaSeqMap](filePage?path=02_Task软件说明/13_DnaSeqMap.md)）--> Bam文件排序（[SamTools](filePage?path=02_Task软件说明/48_SamTools.md)）-->SV（[lumpy-sv](filePage?path=02_Task软件说明/51_lumpy-sv.md)）、CNV（[CNVkitCompare](filePage?path=02_Task软件说明/52_CNVkitCompare.md)）--> SNP\Indel预测（[GATKtools](filePage?path=02_Task软件说明/53_GATKtools.md)）-->蛋白功能破坏预测（[polyphen](filePage?path=02_Task软件说明/46_polyphen2.md) -->驱动基因分析（[DriverGene](filePage?path=02_Task软件说明/50_DriverGene.md))-->数据库注释(dbsnp EXAC TG cosmic数据库注释)（[HumanVcfAnno](filePage?path=02_Task软件说明/54_HumanVcfAnno.md) )-->突变功能注释（[SNPAnno](filePage?path=02_Task软件说明/36_SnpAnno.md) )-->GO分析（[GO分析](filePage?path=02_Task软件说明/19_GoPathway.md)）、Pathway分析（[Pathway分析](filePage?path=02_Task软件说明/19_GoPathway.md)）

 <div style="text-align:center"><img data-src="1.png" width="600px" ></img>

图1 数据分析流程图</div>

****

#### **分析流程**


<div style="text-align:center"><img data-src="2.png" width="800px" ></img>
图2 平台流程页面</div>
*****
#### **Task说明**
1.	RawData
　　RawData为一个pipeline的起点，是输入文件的节点，在RawData中输入需要分析的测序数据。[查看详细](filePage?path=02_Task软件说明/29_RawDataTask.md)
 
2.	FastQC
　　对测序数据进行质量评估，同时也进行数据过滤和去接头等工作。[查看详细](filePage?path=02_Task软件说明/01_FastQC.md)

3.  DNASeqMap
　　集成了Bwa_aln、Bwa_men、Bowtie2、hisat的DNA比对软件的平台,得到外显子上reads的覆盖深度。[查看详细](filePage?path=02_Task软件说明/13_DnaSeqMap.md)

4.  Samtools
　　Samtools是一个用于操作sam和bam文件，主要功能是将sam文件与bam文件互换；对bam文件进行各种操作，比如数据的排序和提取等。[查看详细](filePage?path=02_Task软件说明/48_Samtools.md)

5.  lumpy-sv
　　筛选结构变异(SV)检测及在基因组中的分布，能够检测到的结构变异类型有：插入、缺失、倒置、易位等。

6.  CNVkitCompare
　　CNVkitCompare可用于生物学和医学中多个领域的研究，来检测CNV检测。

7.  VarScan
　　插入/缺失的(SNP和InDel)变异预测软件工具。通过高通量测序获得的paired-end reads 和参考基因组比对，检测其中纯合的 SNP 和 InDel，获得测序样本和参考基因组的差异位点。[查看详细](filePage?path=02_Task软件说明/41_Varscan.md)

8.  GATK
　　GATK主要检测全基因组和外显子组的测序数据的进行variant calling，包括SNP、INDEL。[查看详细](filePage?path=02_Task软件说明/45_GATK3.md)

9.  PolyPhen
　　对于SNP以及点突变来进行人类蛋白结构和功能预测。[查看详细](filePage?path=02_Task软件说明/46_polyphen2.md)

10.  GO、KEGG分析
　　生进行GO、KEGG pathway、COG等功能富集分析。[查看详细](filePage?path=02_Task软件说明/19_GoPathway.md)

***
#### **流程使用说明**
　　Pipline流程使用说明。[查看详细](filePage?path=01_平台说明/08_项目操作/07_pipline使用说明.md)

***
#### **烈冰成功案例**
Jiang, J. H. et al. Clinical significance of the ubiquitin ligase UBE3C in hepatocellular carcinoma revealed by exome sequencing. Hepatology 59, 2216–2227 (2014).
