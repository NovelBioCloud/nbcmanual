# RseQC
　　质量控制（Quality Control, QC）对于保证RNA-Seq测序数据高质量且适合随后分析是至关重要的。RseQC是一种方便且全面评估RNA-Seq质量的QC工具，评估指标包括序列质量、GC偏好、PCR偏好、核苷酸组成偏好、序列深度、链特异性、覆盖均一性和基因组结构上的片段分布。
 **功能：**
　　对RNA-Seq测序数据进行全面的质量评估。
 **使用软件：**
　　RseQC：RseQC程序包可以用来全面地评估RNA-Seq测序结果质量，例如序列质量、GC偏好、PCR偏好、核苷酸组成偏好、序列深度、链特异性、覆盖均一性，和基因组结构上的片段分布等，以确保后续分析的可靠性。RSeQC用Python和C编写。
　　软件官网：http://pythonhosted.org/RSeQC/

 **应用范围：**
　　由于许多质控软件，如FastQC、FASTX-ToolKit等，都是集中于原始测序序列相关的度量，而RseQC可以进行比较深入的质控检测，如饱和性检查，GC偏移等。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的数据来源于RnaSeqMap/DnqSeqMap的比对结果bam文件。
　　**gtfFile：**需要分析物种的基因组注释（GTF）文件，如果该物种的序列已经存在于物种版本数据库中则不需要输入该文件。
　　**inputFile：**比对结果bam文件。而BAM就是SAM的二进制文件（B取自于binary）。SAM的全称是sequence alignment/map format。详细信息请见官网说明文档：
  http://samtools.github.io/hts-specs/SAMv1.pdf

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**选择参考基因组物种。
　**物种版本：**参考基因组的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**线程数：**软件运行使用线程数。
　**内存（M）：**运行时使用内存，以M为单位。
　**计算在genebody的覆盖谱：**是否计算gene body区域的reads覆盖谱。 
　**计算两个成对的RNA读长的距离：**指的是对于PE reads，Reads 1的末端与Reads2 末端之间的距离，即PE reads的内部距离，应该与割胶大小匹配。
　**sampleSize：**从SAM/BAM文件中提取的reads数，默认值为100000，当勾选“计算两个成对的RNA读长的距离”参数时，显示该参数。
　**图片下界：**画读长的距离图时，x轴inner distance的起始值，默认-250bp，当勾选“计算两个成对的RNA读长的距离”参数时，显示该参数。
　**图片上界：**画读长的距离图时，x轴inner distance的最大值，默认250bp，当勾选“计算两个成对的RNA读长的距离”参数时，显示该参数。
　**绘图步长：**绘柱状图的步长bp，默认为5，当勾选“计算两个成对的RNA读长的距离”参数时，显示该参数。
　**比较BAM/SAM文件中junction的种类：**将检测到的splice junction分为know，complete novel和partial novel（与ref genome相比）。
**内含子最小长度：**最小内含子长度，默认值为50bp，当勾选“比较BAM/SAM文件中junction的种类”参数时，显示该参数。
　**用于评估样本大小对RPKM的影响：**通过对总的比对reads重采样（jackknifing），使用相对错误率来评估当前测序深度下的RPKMs值的准确性。进而通过对不同测序深度下的RPKMs值的比较，来评估不同测序数据量（即样本大小）对RPKMs值的影响。
　**采样上界：**画评估样本图时，采样起始百分数。取值为0~100，默认值为5，当勾选“用于评估样本大小对RPKM的影响”参数时，显示该参数。
　**采样下界：**画评估样本图时，采样终止百分数。取值为0~100，默认值为100，当勾选“用于评估样本大小对RPKM的影响”参数时，显示该参数。
　**采样步长：**画评估样本图的步长，默认值为5，当勾选“用于评估样本大小对RPKM的影响”参数时，显示该参数。
　**RPKM的cutoff值：**RPKM值小于该设定阈值时将被cutoff，默认为0.01，当勾选“用于评估样本大小对RPKM的影响”参数时，显示该参数。
　**计算reads重复性：**是否绘制reads重复性图。
　**reads重复次数上限：**绘制reads重复性图时，reads的最高重复次数，默认为500，当勾选“计算reads重复性”参数时，显示该参数。
　**检测测序深度可否用于可变剪接分析：**是否判断当前测序深度是否足够用来执行选择性剪接分析。
　**readGC：**是否绘制GC分布图。
　**readNVC：**是否绘制碱基偏好性图。
　**flagOption：**勾选后，碱基偏好性图输出N,X线。
　**splitBam：**是否将原始的Bam文件分离成三类， .in.bam、 .ex.bam和.junk.bam。
　**inferExpreiment：**通过对BAM文件进行采样，判断测序是否是链特异性，并统计正负链的分布情况。
　**readDistribution：**计算比对到编码exons、5’UTR exons、3’UTR exons、introns和intergenic区的reads比例。


****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>

　1.geneBodyCoverage.pdf：genebody的覆盖谱图
<div style="text-align:center"><img data-src="1.png" width="400px"  ></img></div>

　2.inner_distance_plot.pdf：PE reads内部距离图
<div style="text-align:center"><img data-src="2.png" width="400px"  ></img></div>

　3.splice_events.pdf：样本中的splice事件与已知参考基因模型中的splice 事件相比，已知splice 事件和novel splice事件所占的比例分布图。
<div style="text-align:center"><img data-src="3.png" width="300px"  ></img></div>

　4.splice_junction.pdf：样本中的splice junctions与已知参考基因模型中的splice junctions相比，已知splice junctions和novel splice junctions所占的比例分布图。
<div style="text-align:center"><img data-src="4.png" width="300px"  ></img></div>

　5.saturation.pdf：用于评估样本数据量大小对RPKM的影响
<div style="text-align:center"><img data-src="5.png" width="500px"  ></img></div>
将所有transcripts根据RPKM值的大小进行降序排列，然后将其分为以下4组：
Q1（0~25%）：表达水平低于25%的transcripts
Q1（25%~50%）：表达水平处于25%到50%之间的transcripts
Q1（50%~75%）：表达水平处于50%到75%之间的transcripts
Q1（75%~100%）：表达水平大于75%的transcripts
图中横坐标为采样比例，纵坐标为相对误差百分比。从这个图中可以看出该数据量下计算出的基因表达量是否可信。
　6.DupRate_plot.pdf：reads重复性图
<div style="text-align:center"><img data-src="6.png" width="400px"  ></img></div>
使用两种方式评估reads的重复率：
1. Sequence based（基于序列） ,reads序列完全相同的reads认为是重复reads;
2. Mapping based（基于比对），比对到相同基因组位置的reads，认位置重复reads。
图中横坐标为read重复次数，纵坐标为Reads数取log10后的值，蓝色“x”表示使用第一种方式（sequence based）计算出来的reads重复性分布情况，红色”.”表示，使用第二种方式（mapping based）计算出来的reads重复性分布情况。
　7.saturation.pdf：分析当前的测序深度/测序数据量是否可以用于可变剪接的检测
<div style="text-align:center"><img data-src="7.png" width="400px"  ></img></div>
图中蓝色曲线是所有splicing junctions 数，红色曲线为已知splicing junctions 数，绿色曲线为novel splicing junctions 数，该图中红色曲线比较平滑，说明该数量满足分析已知可变剪切；绿色曲线呈上升趋势，并没有达到平滑的趋势，说明该数据量不能满足分析novel可变剪切的分析。
　8.GC_plot.pdf: GC分布图
<div style="text-align:center"><img data-src="8.png" width="400px"  ></img></div>

　9.splitBam的输出文件为：
　　output.in.bam：(Reads consumed by input gene list)
　　output.ex.bam：(Reads not consumed by input gene list)
　　output.junk.bam：(qcfailed, unmapped reads)

　10.experiment.txt：判断测序是否是链特异性，并统计正负链的分布情况
<div style="text-align:center"><img data-src="10.png" width="400px"  ></img></div>

　11.readDistribution.txt：reads分布情况
<div style="text-align:center"><img data-src="12.png" width="400px"  ></img></div>

 ***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true"style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
参考文献：
　1.Wang L, Wang S, Li W. RSeQC: quality control of RNA-seq experiments. Bioinformatics. 2012;28:2184–5. [PubMed]
　2.RSeQC RNA-seq data QC Sourceforge Web site. http://sourceforge.net/projects/rseqc/files/
　3.Rseqc RNA-seq quality control package Google Code Web site.https://code.google.com/p/rseqc/downloads/list

