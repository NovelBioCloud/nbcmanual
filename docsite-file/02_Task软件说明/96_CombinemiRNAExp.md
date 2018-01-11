# CombinemiRNAExp
　　成熟的miRNA是由较长的初级转录物经过一系列核酸酶的剪切加工而产生的，随后组装进RNA诱导的沉默复合体，通过碱基互补配对的方式识别靶基因，并根据互补程度的不同指导沉默复合体降解靶mRNA或者阻遏靶mRNA的翻译。
**功能：**
　　将多个样本的miRNA表达量整合成一个表达量列表或将单个样本多种不同miRNA的表达结果进行汇总。
**使用软件：**
　　	NovelBio使用java编写程序。
**应用范围**
　　通常是对多个样本（此处要求每个文件中只含有一个样本的miRNA表达量）的miRNA表达量进行整合，以用于后续的差异miRNA筛选分析。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是miRNA的表达量列表。
　**inputFile:**需要进行整合的miRNA表达量列表。如：\*.miRNA.mature.Counts.exp.txt，文件格式为：

| miRNAName   |  miRNApreName  |mirSequence|  1-OP_R1  |
| -------- |  :----: | :----:  | :----:  |
| hsa-miR-4446-3p     |  hsa-mir-4446 |cagggctggcagtgacatgggt |  21.0    |
| hsa-miR-4687-3p    | hsa-mir-4687   |tggctgttggagggggcaggc|4.0|
| hsa-miR-6730-5p        |  hsa-mir-6730  |agaaaggtggaggggttgtcaga|1.0|

　　**注意：**
　1.输入的每个文件必须都是只含有一个样本的miRNA表达量（通常是counts数），即只有一列表达量信息；  
　2.列表中必须有一行title，title名称无特殊限制。

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　整合后的miRNA表达量列表（txt）文件。
<hr/>**<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**TpmCoefficient：**在计算TPM值时乘以的系数，默认为1000000。
 ***
**<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
　　1)Sample_Exp ： 每个样本的TPM列表文件。
　　2)All.Counts.exp.txt ：整合后的所有样本的miRNA表达（counts数）列表。
　　3)All.TPM.exp.txt：整合后的所有样本的miRNA表达（TPM值）列表。
***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细解释**
TMP：Transcripts Per Kilobase of exon model per Million mapped reads (每千个碱基的转录每百万映射读取的Transcripts)。
TPM的计算公式为：
    TPMi=(Ni/Li)*1000000/sum(Ni/Li+……..+ Nm/Lm)
Ni：mapping到基因i上的read数； Li：基因i的外显子长度的总和
在一个样本中一个基因的TPM：先对每个基因的read数用基因的长度进行校正，之后再用校正后的这个基因read数(Ni/Li)与校正后的这个样本的所有read数（sum(Ni/Li+……..+ Nm/Lm)）求商。
