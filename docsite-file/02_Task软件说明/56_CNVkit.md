# CNVkit
　　应用一个Python库和命令行软件工具包来推断基因拷贝数变异。它是一个基于基因组测序数据分析鉴定并展示拷贝数变异的有效手段。它也可以一定程度上分析外显子捕获测序，或者芯片靶向捕获测序的测序结果，而基于全基因组测序，它有更好的准确性，并且能够以全基因组作为范围寻找CNV。
　　官网：http://cnvkit.readthedocs.io/en/stable/index.html

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　InputBam (BAM)：需要分析的样品bam数据文件
　TargetBed (BED)：基因组位置文件

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**参考序列物种
**版本：**物种的版本
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
**BedSpelit：**最小gap的碱基数，默认为5000
**Thread：**运行时，使用线程数
**ContainerNumber：**运行时，使用Container数

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center">
<img data-src="1.png" width="450px"  ></img>
</div>
　chromosome：Chromosome or reference sequence name.
　start：Start position.
　end：End position.
　gene：Gene name.
　log2：Log2 ratio．
　probes：indicating the number of bins covered by the segment.
　weight：Proportional weight to be used for segmentation.
