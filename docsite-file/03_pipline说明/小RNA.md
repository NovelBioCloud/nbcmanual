### 小RNA测序分析流程
#### **流程介绍**
　　SmallRNA是一类调控基因表达的小分子RNA，约18~30nt核苷酸，包括miRNA、siRNA和piRNA，广泛存在于真核生物和细胞中。分析流程快速鉴定不同物种、组织、阶段等状态下，已知和未知的SmallRNA及其表达差异和相关靶基因。
　　SmallRNA分析流程分析包含miRNA的鉴定与预测；miRNA表达量分析；miRNA靶基因预测；miRNA靶基因注释分类及富集等分析，为研究microRNA对细胞进程的作用及其生物学影响提供了有力工具。

***
#### **平台流程** 
 <div style="text-align:center"><img data-src="1.png" width="600px" ></img>

图1 数据分析流程图</div>

****

#### **分析流程**
　　原始序列（[RawData](filePage?path=02_Task软件说明/29_RawDataTask.md)）-->数据质控（[FastQC](filePage?path=02_Task软件说明/01_FastQC.md)）-->miRNA鉴定（[MiRNASeqAnalysis](filePage?path=02_Task软件说明/49_MiRNASeqAnalysis.md)）--> 差异基因筛选（[DifGene](filePage?path=02_Task软件说明/04_DifGene.md)）-->序列提取（[GetSeq](filePage?path=02_Task软件说明/18_GetSeq.md))） -->靶向预测（[MiRNATarget](filePage?path=02_Task软件说明/48_MiRNATarget.md))）-->GO分析（[GO分析](filePage?path=02_Task软件说明/19_GoPathway.md)）、Pathway分析（[Pathway分析](filePage?path=02_Task软件说明/19_GoPathway.md)）

<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
图2 平台流程页面</div>

*****
#### **Task说明**
1.RawData：
 　 RawData为一个pipeline的起点，是输入文件的节点，在RawData中输入需要分析的测序数据。[查看详细](filePage?path=02_Task软件说明/29_RawDataTask.md)
2.FastQC
　对测序数据进行质量评估，同时也进行数据过滤和去接头等工作。[查看详细](filePage?path=02_Task软件说明/01_FastQC.md)

3.MiRNASeqAnalysis：
　　与miRBase数据库、Rfam数据进行比对，快速鉴定已知miRNA的表达量和种类分布。同时还可以进行通过Miranda、RNAhybrid进行Novel microRNA预测。[查看详细](filePage?path=02_Task软件说明/23_miRNASeqAnalysis.md)

4.DifGene
　　差异基因筛选。根据有无生物学重复、测序类型分别有Limma、DEGseq、DESeq、EBSeq、EdgeR等多种软件算法可供选择。[查看详细](filePage?path=02_Task软件说明/04_DifGene.md)

5.GetSeq：
　　通过GetSeq来提取按照基因名称或者基因区域、位置提取序列。分别提取miRNA序列和mRNA序列，以便进行下一步负相关分析。[查看详细](filePage?path=02_Task软件说明/18_GetSeq.md)

6.MiRNATarget：
　　circRNA、lncRNA、ncRNA与miRNA进行靶向调控进行预测，应用靶基因预测算法miranda和RNAhybrid来进行负相关调控关系预测。[查看详细](filePage?path=02_Task软件说明/48_MiRNATarget.md)

7.GoPathway
　　进行GO、KEGG pathway、COG等功能富集分析。[查看详细](filePage?path=02_Task软件说明/19_GoPathway.md)

8.EnrichmentPlot
　　 对GoPathway的结果进行富集作图。[查看详细](filePage?path=02_Task软件说明/14_EnrichmentPlot.md)

***
#### **流程使用说明**
　　Pipline流程使用说明。[查看详细](filePage?path=01_平台说明/08_项目操作/07_pipline使用说明.md)
***
#### **案例解析**
　　小RNA分析成功案例解析。[查看详细](filePage?path=05_文献解读/小RNA/金陵医院和南方医科大学药物拉帕替尼处理miRNA.md)
***
#### **烈冰成功案例**
[1]. Su, X. et al. miRNomes of haematopoietic stem cells and dendritic cells identify miR-30b as a regulator of Notch1. Nat. Commun. 4, 1–12 (2013).
[2]. Zhang, C., Lu, J., Liu, B., Cui, Q. & Wang, Y. Primate-specific miR-603 is implicated in the risk and pathogenesis of Alzheimer’s disease. Aging (Albany. NY). 8, 272–290 (2016).
[3]. Cheng, T. L. et al. MeCP2 Suppresses Nuclear MicroRNA Processing and Dendritic Growth by Regulating the DGCR8/Drosha Complex. Dev. Cell 28, 547–560 (2014).
[4]. Cong, P. et al. Integrated miRNA and mRNA transcriptomes of porcine alveolar macrophages (PAM cells) identifies strain-specific miRNA molecular signatures associated with H-PRRSV and N-PRRSV infection. Mol. Biol. Rep. 41, 5863–5875 (2014).
[5]. Nie, W. et al. miR-1470 mediates lapatinib induced p27 upregulation by targeting c-jun. J. Cell. Physiol. 230, 1630–1639 (2015).



