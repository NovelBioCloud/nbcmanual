# RseQC
 
　　一种方便且全面的QC工具以评估RNA-seq质量。例如序列质量、GC偏好、PCR偏好、核苷酸组成偏好、序列深度、链特异性、覆盖均一性，和基因组结构上的片段分布。

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**

　　RNA-seq提供了有关基因组中所有转录元件的有价值的信息，已经被广泛地用于转录组研究。
　　基于原始测序数据的质控，如FastQC，不足以保证RNA-seq数据的可用性。例如，在执行许多RNA-seq应用时测序深度必须饱和，如表达谱，选择性剪接分析，新亚型（isoform）鉴定，转录组重建等。非饱和测序深度不能够给出准确的评估（例如RPKM和剪接索引），也不能够检测低丰度剪接联结点（splice junctions），因此限制了许多分析的准确性。
　　使用RSeQC程序包来全面地评估RNA-seq结果质量，例如序列质量、GC偏好、PCR偏好、核苷酸组成偏好、序列深度、链特异性、覆盖均一性，和基因组结构上的片段分布等，以确保后续分析的可靠性。RSeQC用Python和C编写。
　　RseQC官网：http://pythonhosted.org/RSeQC/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
**gtfFile：**输入文件为bam文件；
**inputFile：**参考序列gtf文件。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
**物种：**选择参考基因组物种。
**物种版本：**参考序列的版本。
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
**线程数：**软件运行使用线程数。
**内存：**软件运行使用内存数。
**计算在genebody的覆盖谱：**将所有转录本缩放到100nt，并计算每个核苷酸覆盖的reads数，最后计算出一个沿gene body的覆盖谱。
**计算两个成对的RNA读长的距离：**配对reads间的内部距离分布，应该与割胶大小匹配。
**图片下界：**画读长的距离图时的x轴inner distance下界，默认-250bp。
**图片上界：**画读长的距离图时的x轴inner distance上界，默认250bp。
**绘图步长：**绘柱状图的步长bp，默认为5。
**比较BAM/SAM文件中junction的种类：**将检测到的splice junction分为know，complete novel和partial novel（与ref genome相比）。
**用于评估样本大小对RPKM的影响：**通过对总的比对reads重采样（jackknifing），评估在当前测序深度下的RPKMs。使用相对错误率来测量评估的RPKM的准确性。
**采样上界：**画评估样本图时，采样起始百分数。取值为0~100，默认值为5。
**采样下界：**画评估样本图时，采样终止百分数。取值为0~100，默认值为100。
**采样步长：**画评估样本图的步长，默认值为5。
**RPKM的cutoff值：**小于RPKM的值将被cutoff，默认为0.01。
**计算reads重复性：**用于计算读长的重复性图。
**reads重复次数上限：**画计算读长的重复性，reads的最高重复次数，默认为500。
**检测测序深度可否用于可变剪接分析：**判断当前测序深度是否足够用来执行选择性剪接分析。
**内含子最小长度：**做可变剪接分析时，最小内含子长度bp，默认值为50。
**readGC：**画GC分布图。
**readNVC：**画碱基偏好性图。
**flagOption：**勾选后，碱基偏好性图输出N,X线。
**splitBam：**将原始的Bam文件分离成三份，.in.bam、.ex.bam、.junk.bam。
**inferExpreiment：**通过对BAM文件进行采样，判断测序是否是链特异及分布情况。
**sampleSize：**从SAM/BAM文件中取样的reads数，默认值为200000。
**readDistribution：**计算比对到编码exons、5’UTR exons、3’UTR exons、introns和intergenic区的read比例。
**containerNumber：**软件运行所使用container数。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>

1.geneBodyCoverage.pdf：genebody的覆盖谱图
<div style="text-align:center"><img data-src="1.png" width="500px"  ></img></div>

2.inner_distance_plot.pdf：成对的RNA读长的距离图
<div style="text-align:center"><img data-src="2.png" width="500px"  ></img></div>
3.splice_events.pdf：文件中junction的事件
<div style="text-align:center"><img data-src="3.png" width="300px"  ></img></div>
4.splice_junction.pdf：文件中junction的种类
<div style="text-align:center"><img data-src="4.png" width="300px"  ></img></div>
5.saturation.pdf：用于评估样本大小对RPKM的影响
<div style="text-align:center"><img data-src="5.png" width="500px"  ></img></div>
6.DupRate_plot.pdf：reads重复性图
<div style="text-align:center"><img data-src="6.png" width="500px"  ></img></div>
7.saturation.pdf：检测测序深度可否用可变剪接
<div style="text-align:center"><img data-src="7.png" width="500px"  ></img></div>
8.GC_plot.pdf:  GC分布图
<div style="text-align:center"><img data-src="8.png" width="500px"  ></img></div>
9.splitBam的输出文件为：
　output.in.bam：(Reads consumed by input gene list)
　output.ex.bam：(Reads not consumed by input gene list)
　output.junk.bam：(qcfailed, unmapped reads)

10.experiment.txt：判断测序是否是链特异及分布情况
<div style="text-align:center"><img data-src="10.png" width="500px"  ></img></div>
11.readDistribution.txt：reads分布情况
<div style="text-align:center"><img data-src="12.png" width="400px"  ></img></div>
