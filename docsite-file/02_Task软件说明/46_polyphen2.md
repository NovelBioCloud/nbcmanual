# Polyphen2
　　DNA序列上一些碱基的点突变会引起氨基酸的改变，从而影响蛋白的折叠，进而影响蛋白的相互作用和稳定性。蛋白结构如果改变，蛋白的功能就很可能会发生变化。该软件整合了蛋白序列和三维结构特征，来预测点突变对蛋白功能的影响。
**功能：**
　　预测氨基酸改变对人类蛋白稳定性和功能的影响。
**使用软件：**
　　**PolyPhen-2** : (**Poly**morphism **Phen**otyping v**2**) 是一个研究碱基突变对蛋白功能影响的软件，它可对SNP进行功能注释，将编码区域的SNPs比对到基因组或者转录本，提取蛋白序列注释和蛋白结构，并进行序列保守性分析。然后根据这所有的属性综合评估错义突变的有害程度。
  　软件官网： http://genetics.bwh.harvard.edu/pph2/
 **应用范围：**
　　用于预测点突变对蛋白功能的影响程度，但预测仅限于错义突变，其他无义突变（突变为终止密码）、碱基缺失、插入所造成的移框突变，以及起始密码子的突变均不可预测。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是GATK3产生的变异结果VCF文件。
　　**Inputmaf：**变异结果VCF文件，VCF的详细说明请见官方文档： http://samtools.github.io/hts-specs/VCFv4.2.pdf
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　突变功能预测结果文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='ChrCol'>染色体号：</label>在输入文件列表中，染色体号所在列。
　<label id='posCol'>Position列号：</label>在输入文件列表中，突变位点所在列。　
　<label id='refCol'>Ref列号：</label>在输入文件列表中，突变前的碱基所在列。
　<label id='altCol'>Alt列号：</label>在输入文件列表中，突变后的碱基所在列。 
　
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　\* .polyphen.result：分析结果文件，结果详细信息请见官方说明文档： http://genetics.bwh.harvard.edu/pph2/dokuwiki/_media/hg0720.pdf 。
参考文献：
　1.Adzhubei I, Jordan DM, Sunyaev SR. Predicting functional effect of human missense mutations using PolyPhen-2. Curr Protoc Hum Genet 2013; Chapter 7: Unit 7.20. [PMC free article] [PubMed]