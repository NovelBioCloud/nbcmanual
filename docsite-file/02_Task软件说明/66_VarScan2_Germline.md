# VarScan2_Germline
　　Varscan2可用来检测来自肿瘤-正常样本对的外显子组数据中的体细胞突变和拷贝数变异（copy number variations，CNVs）。VarScan2工具将突变点分为三种突变状态：体细胞（Somatic）突变、基因组胚系（Germline）突变、杂合性缺失（LOH）突变。
　　基因组胚系的突变（Germline nutations）来自上一代，这种mutation会存在于个体整个胚胎发育过程，在研究方法上，基因组胚系突变在家系分析中，以及在对很多遗传病（包括遗传型“肿瘤”）的研究中占有重要地位。
**功能：**
　　检测样本的germline mutation。
**使用软件：**
　　**Varscan2：**由华盛顿大学基因组研究所开发，是一个基于Java，用于检测插入/缺失 (SNP/InDel)的变异预测软件工具。Varscan2特别针对肿瘤外显子测序数据，检测体细胞突变和CNV。
　　**软件官网：** http://varscan.sourceforge.net/index.html

**应用范围**
　　用于检测样本的遗传突变。在测序过程中，除了个体测序之外，还会加上个体的家属一同测序，病理分析时也会考虑家族背景的影响。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
该Task的输入数据来源于Samtools模块的PileUp结果文件。
　  **InputData：**PileUp文件，使用Samtools的mpileup命令，生成的bcf文件。该文件每一行代表了参考序列中某一个碱基位点的比对结果，如：
   
|  |   |||||
| -------- |  :----: | :----:  | :----: | :----:  | :----:  |
|scaffold_1 |  2842 |C |12|,$,,...,....^I.|CFGEGEGGCFF+|
| scaffold_1 | 2845 |G|11|,,...,.....|F656666166*|
| scaffold_1  | 2846 |A|11|,,...,.....|(1.1111)11*|
|scaffold_1|2847|A|11|,,+9acggtgaag.+9ACGGTGAAG|%.+....-..)|
|scaffold_1|2848|N|11|agGGGgGGGGG|!!$!!!!!!!!|
各列信息解释如下：

|  |   |
| -------- |  :----: |
|1 |  参考序列名 |
|2 | 位置 |
|3  | 参考碱基 |
|4|比对上的reads数|
|5|比对情况|
|6|比对上的碱基的质量|

其中第5列比较复杂，解释为：

|  |   |
| -------- |  :----: |
|1 |  ‘.’代表与参考序列正链匹配 |
|2 | ‘,’代表与参考序列负链匹配 |
|3  | ‘ATCGN’代表在正链上的不匹配 |
|4|‘atcgn’代表在负链上的不匹配|
|5|‘*’代表模糊碱基|
|6|‘^’代表匹配的碱基是一个read的开始；’^'后面紧跟的ascii码减去33代表比对质量；这两个符号修饰的是后面的碱基，其后紧跟的碱基(.,ATCGatcgNn)代表该read的第一个碱基|
|7|‘$’代表一个read的结束，该符号修饰的是其前面的碱基|
|8|正则式’\+[0-9]+[ACGTNacgtn]+’代表在该位点后插入的碱基；比如上例中在scaffold_1的2847后插入了9个长度的碱基acggtgaag。表明此处极可能是indel|
|9|正则式’-[0-9]+[ACGTNacgtn]+’代表在该位点后缺失的碱基|
Pileup 文件详细说明，请见官方文档： 
http://samtools.sourceforge.net/pileup.shtml
 ***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**选择参考基因组物种。
　**物种版本：**参考基因组的版本。
　**minCoverage：**reads的最小覆盖度，默认值为8。
　**minCovNor：**正常组（对照组）的最小覆盖度，默认值为8。
　**minCovTum：**患病组（实验组）的最小覆盖度，默认值为6。
　**minVarFeq：**杂合子的最小变异频率，默认值为0.01。
　**minFreForHom：**纯合子的最小变异率，默认值为0.75。
　**pValue：**杂合子检测突变的p阈值，默认值为0.99。
　**pValueSom：**检测突变的p阈值，默认值为0.05。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
　　 \*.vcf：检测到的所有变异结果，如：
<div style="text-align:center"><img data-src="2.png" width="700px" ></img></div>
表中各列信息解释如下：

| Field  |  Description |
| -------- |  :----: |
|Chrom |  Chromosome or reference name |
|Position | Position from pileup (1-based)|
|Ref | Reference base at this position|
|Cons|Consensus genotype or variant called|
|Reads1|Number of reads supporting reference|
|Reads2|Number of reads supporting variant|
|VarFreq|Allele frequency of variant by read count|
|Strands1|Number of strands on which reference observed (0-2)|
|Strands2|Number of strands on which variant observed (0-2)|
|Qual1|Average base quality of reference-supporting bases|
|Qual2|Average base quality of variant-supporting bases|
|Pvalue|P-value from Fisher's exact test (0.98 means not calculated)|
|MapQual1|Average mapping quality of reference-supporting reads|
|MapQual2|Average mapping quality of variant-supporting reads|
|Reads1Plus|Number of reference-supporting reads in + orientation|
|Reads1Minus|Number of reference-supporting reads in - orientation|
|Reads2Plus|Number of variant-supporting reads in + orientation|
|Reads2Minus|Number of variant-supporting reads in - orientation|
|VarAllele|Most prevalent variant allele (even if site not not called variant)|
结果详细说明请见官方文档：
http://varscan.sourceforge.net/germline-calling.html

**详细解释**
**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种。占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
Indel：insertion-deletion，插入缺失标记，指的是一个样本相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。
**参考文献：**
Koboldt DC, Zhang Q, Larson DE, Shen D, McLellan MD, Lin L, Miller CA, Mardis ER, Ding L, Wilson RK. VarScan 2: somatic mutation and copy number alteration discovery in cancer by exome sequencing. Genome Res. 2012;22:568–576. [PMC free article] [PubMed]