# PeakCalling
　　Peak calling是一种用于鉴定ChIP-Seq或MeDIPSeq得到的比对读段富集在基因组哪些区域的计算方法。当免疫沉淀的蛋白质是一种转录因子时，DNA的富集区域就是这种转录因子的结合位点（TFBS）。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;进行Peak calling的分析。
**使用软件：**
**MACS：**Model-based Analysis for ChIP-Seq，主流的Peak calling软件。
**软件官网：**http://liulab.dfci.harvard.edu/MACS/
**应用范围:**
&nbsp;&nbsp;&nbsp;&nbsp;应用于转录组/外显子组测序；亦可用于对MeRIP测序或m6A测序的RNA甲基化测序数据进行分析，利用exomePeak等软件，可检测出转录后RNA修饰位点。
****

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是Samtools排序后的Bam文件。
	**InputFastaFile：**需要分析的参考基因组序列（Fasta）文件，如果该物种的序列已经存在于物种版本数据库中，则不需要输入该文件。
**InputFile：**排序后的bam文件，SAM的全称是sequence alignment/map format。而BAM就是SAM的二进制文件（B取自于binary）。SAM文件详细说明，请见官方文档：http://samtools.github.io/hts-specs/SAMv1.pdf。
***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;peak calling 结果文件列表（*.xls）。
****

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>版本：</label>参考序列的版本。
<label id='software'>software：</label>选择使用软件的版本，有两个版本macs1.4和macs2，macs2在很多方面都对macs1.4做了重大改进，但目前还在测试阶段。
<label id='EffectSize'>EffectSize：</label>分析过程中需将基因组中染色体的长度进行缩放，该参数为设置的缩放比例，即将染色体长度乘以该值。默认值为0.9。
<label id='mFoldMin'>mFoldMin：</label>构建双峰模型时使用，表示选择那些倍数变化大于该设定值的富集区域。默认值为2。
<label id='mFoldMax'>mFoldMax：</label>构建双峰模型时使用，表示选择那些倍数变化小于该设定值的富集区域。默认值为50。
<label id='pvalue'>pvalue：</label>设定peak置信概率的临界值（threshold），Pvalue小于该值，说明检测到的peak准确度高，可信度高。默认是不设置的，该参数值与参数“qvalue”是互斥的，如果“pvalue”的阈值做了设置，那么就不会计算参数“qvalue”。
<label id='qvalue'>qvalue：</label>设置peak检测最小的q-value(FDR）阈值，q-value小于该值，说明检测到的peak准确度高，可信度高。默认为0.05。该参数值与参数“pvalue”是互斥的。
<label id='buffersize'>buffersize：</label>设置软件运行时的缓存区大小，通常情况下不用修改此参数，当参数“software”选择为“macs2”时，显示该参数，默认值：100000。
<label id='nolambda'>nolambda：</label>如果选中，软件会使用固定的λ值作为每个peak区域的局部λ值，否则，软件计算动态区域λ值来反映由于染色质结构造成的局部偏差。
****

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
1)	**\*_peaks.bed：**详细列出了每一个peak的位置信息和可信度（最后一列)，BED文件格式详见：http://genome.ucsc.edu/FAQ/FAQformat.html#format1
2)	**\*_peaks.xls：**相比\*_peaks.bed包含了更多信息，包括本次程序运行的详细参数，每个peak的summit（顶点）信息等。
3)	**\* _model.r：**以代码的形式保存了“双峰模型”。运行该r代码生成如下图所示图片。
<div style="text-align:center">
	<img data-src="1.png" width="300px" ></img>
</div>
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 详细说明**
**ChIP-Seq：**染色质免疫共沉淀技术（Chromatin Immunoprecipitation，ChIP）也称结合位点分析法，是研究体内蛋白质与DNA相互作用的有力工具，通常用于转录因子结合位点或组蛋白特异性修饰位点的研究。
***
**参考文献：**
1.	Zhang Y, Liu T, Meyer CA, Eeckhoute J, Johnson DS, et al. . (2008) Model-based Analysis of ChIP-Seq (MACS). Genome Biology 9: R137. [PMC free article] [PubMed]


