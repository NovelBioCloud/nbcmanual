### CircRNA分析流程
#### **流程介绍**
　　环状RNA（circRNA）是一类不具有5' 末端帽子和3' 末端poly(A)尾巴、并以共价键形成环形结构的非编码RNA分子。区别于传统线性RNA的一类新型RNA，具有闭合环状结构，大量存在于真核转录组中。大部分的环状RNA是由外显子序列构成，在不同的物种中具有保守性，同时存在组织及不同发育阶段的表达特异性。环状RNA在不同物种中起到miRNA海绵的作用，称之为竞争性內源RNA（ceRNA），能竞争性结合miRNA，从而调控靶基因的表达。
　　环状RNA测序分析平台包括：数据质量质控、参考基因组比对、预测circRNA、circRNA来源基因分析、host基因GO分析、Pathway分析、circRNA表达量定量及差异富集分析等分析流程。平台整合了多个物种及版本，一站式解决分析方案，大幅度提高了数据分析效率。

***
#### **平台流程** 
 <div style="text-align:center"><img data-src="1.png" width="600px" ></img>

图1 数据分析流程图</div>

****


#### **主要分析流程**

　　mRNA分析： 原始序列（[RawData](filePage?path=02_Task软件说明/29_RawDataTask.md)）-->数据质控（[FastQC](filePage?path=02_Task软件说明/01_FastQC.md)）-->参考基因组比对（[RnaSeqMap](filePage?path=02_Task软件说明/43_RnaSeqMap.md)）--> 表达量分析（[SamAndRPKM](filePage?path=02_Task软件说明/33_SamAndRPKM.md)）--> 差异基因注释（[GeneAnno](filePage?path=02_Task软件说明/05_GeneAnno.md)）-->绘图（[盒形图](filePage?path=02_Task软件说明/06_GeneExpPlot.md)、[密度分布图](filePage?path=02_Task软件说明/06_GeneExpPlot.md)、[相关性图](filePage?path=02_Task软件说明/06_GeneExpPlot.md)）-->[GO分析](filePage?path=02_Task软件说明/19_GoPathway.md)-->[Pathway分析](filePage?path=02_Task软件说明/19_GoPathway.md)

　　circRNA分析：参考基因组比对（[DnaSeqMap](filePage?path=02_Task软件说明/13_DnaSeqMap.md)）-->比对信息统计绘图（（[盒形图](filePage?path=02_Task软件说明/06_GeneExpPlot.md)、[密度分布图](filePage?path=02_Task软件说明/06_GeneExpPlot.md)、[相关性图](filePage?path=02_Task软件说明/06_GeneExpPlot.md)））-->预测环状RNA（[ACFS_CircRNA](filePage?path=02_Task软件说明/08_ACFSCicRNA.md)）-->差异circRNA基因筛选（[DifGene](filePage?path=02_Task软件说明/04_DifGene.md)）;-->circRNA与miRNA互做（[MiRNATarget](filePage?path=02_Task软件说明/48_MiRNATarget.md)）-->GO\KEGG分析（[GO分析](filePage?path=02_Task软件说明/19_GoPathway.md)、[Pathway分析](filePage?path=02_Task软件说明/19_GoPathway.md)）

<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
图2 平台流程页面</div>

*****
#### **必填参数设置**
1.RawDataInput输入文件
　导入原始数据，输入需要分析的测序数据。[查看详细](filePage?path=02_Task软件说明/29_RawDataTask.md)
<div style="text-align:center"><img data-src="3.png" width="500px" ></img></div>
<div style="text-align:center"><img data-src="5.png" width="500px" ></img></div>

2.DifGene
　选择需要比对实验组和对照组，填写group1Array和group2Array。 [查看详细](filePage?path=02_Task软件说明/04_DifGene.md)
<div style="text-align:center"><img data-src="4.png" width="500px" ></img></div>
<div style="text-align:center"><img data-src="6.png" width="300px" ></img></div>

*****
#### **Task说明**
1.	RawData
　　RawData为一个pipeline的起点，是输入文件的节点，在RawData中输入需要分析的测序数据。[查看详细](filePage?path=02_Task软件说明/29_RawDataTask.md)
 
2.	FastQC
　　对测序数据进行质量评估，同时也进行数据过滤和去接头等工作。[查看详细](filePage?path=02_Task软件说明/01_FastQC.md)

3.  DNASeqMap
　　集成了Bwa_aln、Bwa_men、Bowtie2、HISAT的DNA比对软件的平台,得到外显子上reads的覆盖深度。[查看详细](filePage?path=02_Task软件说明/13_DnaSeqMap.md)

4.  SamToFastQ
　　提取指定的序列，在cicRNA分析中，提取没有比对上的序列。[查看详细](filePage?path=02_Task软件说明/35_SamToFastQ.md)

5.  ACFS_CircRNA（环状RNA预测）
　　采用环状RNA预测算法，得到每一个样本中的环状的序列以及表达情况，并将之分类Exonic和Intronic环状RNA。并从基因结构来源，长度来预测环状RNA进行评估。[查看详细](filePage?path=02_Task软件说明/08_ACFSCicRNA.md)

6.   DifGene （差异基因分析）
　　差异基因筛选。根据有无生物学重复、测序类型分别有Limma、DEGseq、DESeq、EBSeq、EdgeR等多种软件算法可供选择。[查看详细](filePage?path=02_Task软件说明/04_DifGene.md)

7.   GeneExPlot
　　对基因的表达水平来绘制盒形图、密度分布图、相关性图。[查看详细](filePage?path=02_Task软件说明/06_GeneExpPlot.md)

8.    GOPathway
　　进行GO、KEGG pathway、COG等功能富集分析。[查看详细](filePage?path=02_Task软件说明/19_GoPathway.md)

9.   MiRNAtarget 
　　将circRNA和miRNA的靶向结合关系进行预测，得到miRNA-circRNA的结合情况以及MRE位点，将结合到circRNA上的miRNA与mRNA同时进行靶向作用关系分析。[查看详细](filePage?path=02_Task软件说明/48_MiRNATarget.md)

10.   CoExp
　　基于基因间表达数据的相似性，得到基因与circRNA间的相关性，用于构建共表达网络。[查看详细](filePage?path=02_Task软件说明/11_CoExp.md)

***
#### **流程使用说明**
　　Pipeline流程使用说明。[查看详细](filePage?path=001_帮助文档/03_Pipeline说明/01_Pipeline使用说明.md)

***
#### **烈冰成功案例**
[1].Zheng, Q. et al. Circular RNA profiling reveals an abundant circHIPK3 that regulates cell growth by sponging multiple miRNAs. Nat. Commun. 7, 11215 (2016).
[2].Liu, Q. et al. Circular RNA Related to the Chondrocyte ECM Regulates MMP13 Expression by Functioning as a MiR-136 ‘Sponge’ in Human Cartilage Degradation. Sci. Rep. 6, 22572 (2016).
