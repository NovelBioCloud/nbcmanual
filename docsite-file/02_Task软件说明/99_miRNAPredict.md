# miRNAPredict 
　　Small RNA是一类重要的体内调节分子，主要包含miRNA、piRNA和siRNA等。可参与基因转录后调控，调节细胞生长、分化，以及个体发育、生殖等主要生物学过程。通过高通量技术，研究者不仅可以精确定量small RNA的表达，还能对全small RNA组进行深入研究，寻找致病、影响发育、受药物调控、影响免疫机制或者受胁迫调控的small RNA。
**功能**
　 预测miRNA以及筛选novel miRNA。
**使用软件**
　　**Bwa：**BWA是用于将DNA序列比对到参考基因组（例如人类基因组）的软件。 它由三个比对算法组成：BWA-backtrack，BWA-SW和BWA-MEM。第一种算法主要用于读长100bp以内的Illumina序列比对，而其余两个主要用于较长序列(70bp至几Mb)的比对。该模块使用BWA- backtrack算法。
软件官网：
http://bio-bwa.sourceforge.net/
　　**Mirdeep2：**miRDeep2的前身是发表在《Nat. Biotechnol》上的miRDeep, 目前和miREvo（Wen et al., 2012）作为预测miRNA的两个主流软件，具有广泛的应用性。
软件官网：
https://www.mdc-berlin.de/8551903/en/
**应用范围：**
　　通常情况是提取没有比对到所分析物种miRNA数据库上的reads，进行miRNA的预测分析。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据来源于miRNAMapping得到的unmapped reads。
**inputFastq：**reads序列。miRNAMapping得到的unmapped reads，如 filename. miRNA.unmapped.fq.gz。当有多个输入文件时，模块会自动将这多个输入文件进行合并，使用合并后的数据做后续分析。
***

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　输出文件为预测的miRNA或者novel miRNA，以及其表达量文件列表。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='blastSpecies'>blastSpecies：</label>选择在预测novel miRNA时，需要与之比对的物种名称，没有比对到该物种miRNA数据库上的即为novel miRNA，该参数值可多选。
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>版本：</label>选择参考基因组的版本。
<label id='ispredictnovel'>PredictNovelmiRNA：</label>选择是否预测novel miRNA。
<label id='thread'>Threads：</label>运行时使用线程数。
**高级选项：**
<label id='useknown'>UseKnownMiRNA：</label>预测过程中是否将预测序列比对到已知的miRNA;
<label id='mismatch'>BWA_Mismatch：</label>允许一条reads上最多错配碱基个数；
<label id='gap'>BWA_GapExtensions：</label>每个gap允许的最大长度；
<label id='seed'>BWA_SeesLen：</label>seed长度。应用BWA对DNA序列进行比对时，会先将read切分成较短的序列，该序列即为seed序列，切分之后将seed序列比对到参考基因组;
<label id='seeddif'>BWA_MaxSeedDif：</label>seed序列与参考基因组序列比对时，seed序列与比对到的参考序列的最大差异碱基（mismatch）数，默认值为2；
<label id='maxhit'>BWA_MaxHits：</label>每对reads输出到结果中的最多比对数；
<label id='minlen'>minLen：</label>预测novel miRNA的最小长度；
<label id='maxlen'>MaxLen：</label>预测novel miRNA的最大长度；
<label id='TPMCoefficient'>TPMCoefficient：</label>计算TPM值（基因表达量的一种衡量指标）时乘以的系数；
<label id='ScoreCutoff'>mirDeep_ScoreCut：</label>预测novel miRNAs时的最小score阈值，默认为0。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**1）	Sample_Exp：**每个样本的small RNA表达量列表文件（如果选择多个“blastSpecies”物种，则会分别列出在每个物种中的表达量列表文件）。small RNA表达量分为成熟miRNA的表达量（counts数和TPM值），以及miRNA前体的表达量（counts数和TPM值）。
**2）	UnmappedReads：**与“blastSpecies”参数选择的物种按照所选顺序做比对，即先与第一个物种作比对，提取unmapped reads，然后再与第二个物种作比对，再提取unmapped reads，再与第三个物种做比对，以此类推，最终提取得到unmapped reads。以fastq文件格式存储。
**3）	map_statistics：**reads与“blastSpecies”参数选择的物种做比对（比对方式如2中所述）的统计信息。
**4）	miRNAMapping_Result：**reads与“blastSpecies”参数选择的物种做比对（比对方式如2中所述）得到的bam文件，以及提取的对应的unmapped reads，以fastq文件格式进行存储。
**5）	miRNApredict：**预测的miRNA结果文件，详细说明请见miRDeep2，官方说明文档：https://www.mdc-berlin.de/36105849/en/research/research_teams/systems_biology_of_gene_regulatory_elements/projects/miRDeep/documentation。
**6）	novelMiRNA：**预测的novel miRNA结果。
**7） All.miRNA.mature.Counts.exp.txt：**成熟miRNA与“blastSpecies”参数选择的物种进行比对后得到的counts数总列表。
**8）	All.miRNA.mature.TPM.exp.txt：**成熟miRNA与“blastSpecies”参数选择的物种进行比对后得到TPM值总列表。
**9）	All.miRNA.pre.Counts.exp.txt：**miRNA前体与“blastSpecies”参数选择的物种进行比对后得到counts数总列表。
**10）	All.miRNA.pre.TPM.exp.txt：**miRNA前体与“blastSpecies”参数选择的物种进行比对后得到TMP值总列表。

***

**参考文献：**
1. Friedlander MR, Mackowiak SD, Li N, Chen W, Rajewsky N. miRDeep2 accurately identifies known and hundreds of novel microRNA genes in seven animal clades. Nucleic Acids Res. 2012;40:37–52. doi: 10.1093/nar/gkr688. [PMC free article] [PubMed] [Cross Ref]
