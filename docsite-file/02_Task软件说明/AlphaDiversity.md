# AlphaDiversity
　　Alpha多样性（Alpha Diversity），是一种用于度量群落内生物种类数量以及生物种类间相对丰度的衡量指标，可分为物种丰富度指数、物种均匀度指数和物种多样性指数三类。Alpha多样性反映了群落内不同物种通过竞争资源或利用同种生境而产生的共存结果。
**功能：**
　　Alpha多样性可用来描述单个样本的物种多样性。
**使用软件：**
**QIIME2：**QIIME （Quantitative Insights Into Microbial Ecology）是一个专门针对于微生物群落的分析流程，主要用Python编写，也整合了很多其它的工具包，可以进行OTU分析和多样性分析等。QIIME拥有处理16s rRNA测序数据所需要的软件，并呈现出相应的处理结果。
**软件官网：**http://qiime.org/
**应用范围**
&nbsp;&nbsp;&nbsp;&nbsp;分析物种的Alpha多样性可用于探讨物种的进化史，以及种群、群落、生物地理学和保护生物学等研究分析中。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是OTUAnalysis的结果文件，如：otu_table.biom。
　　**InputBiom：**输入BIOM格式的OTU文件。\*.biom文件为QIIME软件分析过程中生成的OTU table文件， 即OTU丰度以及注释的矩阵文件。文件详细说明请见官方文档：http://qiime.org/scripts/make_otu_table.html
　  **InputTree：**newick tree文件。该文件是树形文件格式之一，比如下图中的树形图转化为Newick格式即为：(A,B(C,D))
   <div style="text-align:center">
	<img data-src="1.png" width="300px" ></img>
</div>
Newick文件说明具体请见 https://en.wikipedia.org/wiki/Newick_format。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
每个样本的alpha 多样性文件。
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　	**MinSeqNumber：**抽选的最小序列条数。在计算alpha多样性时，要去除因测序深度不一致产生的影响，因此需要重采样，默认为10。
　	**MaxSeqNumber：**抽选的最大序列条数。在计算alpha多样性时，要去除因测序深度不一致产生的影响，因此需要重采样，默认为26000。
　	**StepSize：**步长，即下一次采样的序列条数,默认为2500条。
　	

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
　1)**alpha.txt：**alpha 多样性结果文件。
 结果文件详细说明，请见官方文档：http://qiime.org/scripts/alpha_diversity.html
　2)**alpha_div_collated：**该结果是将名为alpha_rarefaction（例如alpha_rarefaction_20_0.txt，alpha_rarefaction_20_1.txt等，分别代表一个OTU）的一系列文件整合转换为较小的一组文件（例如chao1.txt，PD_whole_tree.txt等），每个文件表示一个分集度量，文件中的每一行表示一个（稀有）OTU表，文件中的每一列（从第四列开始）表示一个样本，如下所示：
<div style="text-align:center">
	<img data-src="2.png" width="600px" ></img>
</div>
详细说明请见官方文档：http://qiime.org/scripts/collate_alpha.html
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">详细解释**
　**OTU**
&nbsp;&nbsp;&nbsp;&nbsp;OTU即Operational Taxonomic Units的缩写，意为分类操作单元，是在系统发生学或群体遗传学研究中，为了便于进行分析，人为给某一个分类单元（品系，属，种、分组等）设置的统一标志。理论上一个OTU代表一个微生物物种。对于测序获得的大量reads，首先需要进行归类（cluster），通常根据97%的相似水平划分为不同的OTU，将OTU代表序列与相应的微生物数据库比对（Silva、RDP、Greengene等），得到每个样本所含的物种信息，进而进行后续生物信息统计分析。
　**Q值**
&nbsp;&nbsp;&nbsp;&nbsp;Q值用来评估测序的碱基质量，Q值与测序错误E值之间关系为：如果一个碱基的Q值为20，那表示这个碱基的可能测错的可能性，即测序错误率E为1%。实际操作中常用Q20/Q30(Q20与Q30即表示质量值大于等于20或30的碱基所占的百分比)作为标准，一般要求Q20大于90%即可。
<div style="text-align:center">
	<img data-src="3.png" width="300px" ></img>
</div>
　**Chao1**
 &nbsp;&nbsp;&nbsp;&nbsp;chao1算法是用于评估群落中所含OUT种类多少的指数，在生态学中常用来估计物种总数。Chao1值越大代表物种总数越多，计算公式为：Schao1=Sobs+n1(n1-1)/2(n2+1)。
 　**Shannon-Wiener曲线**
 &nbsp;&nbsp;&nbsp;&nbsp;Shannon-Wiener曲线利用shannon指数（shannon指数是反映样本中微生物多样性的衡量指标之一）进行绘制。利用各样本的测序量在不同测序深度时的微生物多样性指数构建曲线，以此反映各样本在不同测序量时的微生物多样性。当曲线趋向平坦时，说明测序数据量足够大，可以反映样品中绝大多数的微生物物种信息。
  　**Simpson指数**
 &nbsp;&nbsp;&nbsp;&nbsp;Simpson指数是用来估算样品中微生物多样性的指数之一，在生态学中常用来定量描述一个区域的生物多样性。Simpson指数值越大，说明群落多样性越高。
 
**参考文献：**
1.	Caporaso, J. Gregory, Justin Kuczynski, Jesse Stombaugh, Kyle Bittinger, Frederic D. Bushman, Elizabeth K. Costello, Noah Fierer et al. “QIIME allows analysis of high-throughput community sequencing data.” Nature methods 7, no. 5 (2010): 335-336.
2.	Schloss, Patrick D., Sarah L. Westcott, Thomas Ryabin, Justine R. Hall, Martin Hartmann, Emily B. Hollister, Ryan A. Lesniewski et al. “Introducing mothur: open-source, platform-independent, community-supported software for describing and comparing microbial communities.” Applied and environmental microbiology 75, no. 23 (2009): 7537-7541.
