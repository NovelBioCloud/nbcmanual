# Taxonomy_Plot 
　　OTU表中最重要的注释信息是物种注释信息。通常的物种注释信息分为7个级别：界、门、纲、目、科、属、种。我们除了可以比较样本间和组间的OTU水平差异外，还可以研究不同分类级别上的差异，来研究它们是否存在共同的变化规律。
**功能：**
　		按照注释的级别进行分类汇总。
 **使用软件：**
　　**QIIME2：**QIIME （Quantitative Insights Into Microbial Ecology）是一个专门针对于微生物群落的分析流程，主要用Python编写，也整合了很多其它的工具包，可以进行OTU分析和多样性分析等。QIIME2拥有处理16s rRNA所需要的软件，并呈现出相应的处理结果。
**软件官网：**http://qiime.org/
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;按照门、纲、目、科、属五个级别进行分类汇总。


***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是OTUAnalysis的结果文件，如：otu_table.biom。
**InputBiom：**输入BIOM格式的OTU文件。\*.biom文件为QIIME软件分析过程中生成的OTU table文件， 即OTU丰度以及注释的矩阵文件。文件详细说明请见官方文档：http://qiime.org/scripts/make_otu_table.html
**MapFile：**样本metdata mapping文件，文件详细解释说明请见，官方文档说明：http://qiime.org/documentation/file_formats.html#metadata-mapping-files。
***


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　分类汇总结果列表（txt），以及对应的bar图（pdf）。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='isplotGroup'>Plot in Group：</label>是否根据mapping文件，将输入的biom文件进行分组统计，并输出用于LefSe分析的数据。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1)	**taxa_summary：**统计每个样品内分类群组的摘要信息。如：
<div style="text-align:center">
	<img data-src="1.png" width="500px" ></img>
</div>
结果文件详细说明，请见官方文档：http://qiime.org/scripts/summarize_taxa.html
2) **taxa_summary_group：**根据mapping 文件对biom表进行重新分配的结果文件。如：
<div style="text-align:center">
	<img data-src="2.jpg" width="300px" ></img>
</div>
结果文件详细说明，请见官方文档： 
http://qiime.org/scripts/jackknifed_beta_diversity.html
3)	**ForDif.txt：**种群在各个样本中的分布量标准化列表，可用于后续进行差异分析。
4)	**ForLefse.txt：**生成的LEfSe输入文件。

***

**参考文献：**
1.	Caporaso, J. Gregory, Justin Kuczynski, Jesse Stombaugh, Kyle Bittinger, Frederic D. Bushman, Elizabeth K. Costello, Noah Fierer et al. “QIIME allows analysis of high-throughput community sequencing data.” Nature methods 7, no. 5 (2010): 335-336.
2.	Schloss, Patrick D., Sarah L. Westcott, Thomas Ryabin, Justine R. Hall, Martin Hartmann, Emily B. Hollister, Ryan A. Lesniewski et al. “Introducing mothur: open-source, platform-independent, community-supported software for describing and comparing microbial communities.” Applied and environmental microbiology 75, no. 23 (2009): 7537-7541.

