# BetaDiversity
　　Beta多样性（Beta Diversity）是生态系统之间的物种多样性，可用来衡量群落之间的差别。Beta多样性不仅描述生境内生物种类的数量，同时也考虑到这些种类的相同性及其彼此之间的差异性。不同生境间或某一生态梯度上不同地段间生物种类的相似性越差，Beta生物多样性越高。
**功能：**
　　分析Beta多样性。
**使用软件：**
**QIIME2：**QIIME （Quantitative Insights Into Microbial Ecology）是一个专门针对于微生物群落的分析流程，主要用Python编写，也整合了很多其它的工具包，可以进行OTU分析和多样性分析等。QIIME拥有处理16s rRNA测序数据所需要的软件，并呈现出相应的处理结果。
**软件官网：**http://qiime.org/
**应用范围**
&nbsp;&nbsp;&nbsp;&nbsp;计算样品间的相同和不同。
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
每个样本的Beta 多样性文件。
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='seqpersample'>Seqs Per Sample：</label>每个样本的序列条数。因为不同样本测序深度不同，产生的序列条数不同，所以需要对每个样本的序列数目进行标准化，即resampling，具体数值可设置为输入样品中序列数目最少的样本序列数，默认值为30000。
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
　1)**beta_diversity：**距离矩阵结果。
 结果文件详细说明，请见官方文档：http://qiime.org/scripts/beta_diversity_through_plots.html
　2)**jackknifed_beta_diversity：**包括距离矩阵结果，一些稀有OUT列表， UPGMA数，一些支持文件和newick tree文件。结果文件详细说明，请见官方文档：
http://qiime.org/scripts/jackknifed_beta_diversity.html

****

**参考文献：**
1.	Caporaso, J. Gregory, Justin Kuczynski, Jesse Stombaugh, Kyle Bittinger, Frederic D. Bushman, Elizabeth K. Costello, Noah Fierer et al. “QIIME allows analysis of high-throughput community sequencing data.” Nature methods 7, no. 5 (2010): 335-336.
2.	Schloss, Patrick D., Sarah L. Westcott, Thomas Ryabin, Justine R. Hall, Martin Hartmann, Emily B. Hollister, Ryan A. Lesniewski et al. “Introducing mothur: open-source, platform-independent, community-supported software for describing and comparing microbial communities.” Applied and environmental microbiology 75, no. 23 (2009): 7537-7541.
