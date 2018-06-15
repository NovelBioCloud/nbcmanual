# BedOperate

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该模块实现与bed文件相关的一些处理。
**功能：**
1.将比对后的bam文件转化为bed文件；
2.bed文件过滤，根据最少比对数和最大比对数过滤bed文件；
3.bed文件转化为bam文件；
4.bed文件排序；
5.bed文件延伸；
6.根据bed文件中信息，提取指定区域的序列；
7.bed文件合并；
**使用软件:**
　　**bedtools：**BEDTools由Utah大学的Quinlan实验室开发，可用于基因组特征（genomic features）的比较和注释等相关操作，目前版本由三十多个工具/命令组成，用来实现各种不同的功能。其中，Genomic features可以是功能元素（gene），可以是遗传多态性（SNPs, Indels, Structure Variation等），也可以是由测序或者其他方法得到的注释信息，以及自定义的一些特征信息等。
**软件官网：**http://bedtools.readthedocs.io/en/latest/

**应用范围：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;实现与bed文件相关的一些操作，如将bam文件转化为bed、将bed文件转化为bam、bed文件排序、bed文件过滤、根据bed文件提取序列等。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据通常是Bed文件，也可以是bam文件。 
**inputFile：**输入文件格式可以是bed格式文件，也可以是bam文件，bedtools主要使用bed格式的前三列，如：
<div style="text-align:center">
	<img data-src="1.png" width="300px" ></img>
</div>
注意：
1.	输入列表中要有一行title信息，对于title名称无特殊要求；
2.	输入列表中必须要有三列信息，即染色体、起始位置、终止位置。
***
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
处理后的结果文件（\*.bed、\*.bam、*.fa）
***
 #### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>物种版本：</label>参考基因组的版本。
<label id='dbType'>物种类型：</label><label id='speciesVersion'>物种版本：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，通过该选项可选择不同数据库gtf文件。
<label id='threadNum'>线程数：</label>运行过程中使用的线程数。
<label id='memory'>内存：</label>运行过程中使用的最大内存。
<label id='Operate'>Operate：</label>选择对输入文件进行的操作，有以下几个选项：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bamToBed：将bam格式文件转化为bed格式文件；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BedFilter：Bed文件过滤；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bedToBam：将bed格式文件转化为bam格式文件；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sortBed：bed文件排序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;extendBed：bed文件延伸；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;fastaFormBed：根据bed文件提取指定区域的序列；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;MergeBed：将bed文件进行合并；
<label id='extend'>ExtendValue：</label>延长值，即bed文件延伸的碱基长度。当Operate参数选择extendBed选项时，该参数有效。
<label id='minMappingNum'>minMappingNum：</label>最少的比对reads数。
<label id='maxMappingNum'>maxMappingNum：</label>最多的比对reads数。
<label id='sortType'>排序方式：</label>对bed文件进行排序时，排序的方式，其选项值为：
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sizeA：根据特征值进行升序排序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sizeD：根据特征值进行降序排序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;chrThenSizeA：首先根据染色体进行升序排序，然后根据特征值进行升序排序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;chrThenSizeD：首先根据染色体进行升序排序，然后根据特征值进行降序排序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;chrThenScoreA：首先根据染色体进行升序排序，然后根据score进行升序排序；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;chrThenScoreD：首先根据染色体进行升序排序，然后根据score进行降序排序；
**containerNumber：**软件运行使用container数。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
输出如下几种结果文件：
1.	*.bed： 当参数“Operate”选择为“bamToBed”时，输出该格式结果文件。
2.	*.bam：当参数“Operate”选择为“bedToBam”时，输出该格式结果文件。
3.	*.sorted.bed：当参数“Operate”选择为“sortBed”时，输出该格式结果文件。
4.	*.fasta：当参数“Operate”选择为“fastaFormBed”时，输出该格式结果文件。
***
**参考文献：**
1.	Quinlan AR, Hall IM. BEDTools: A flexible suite of utilities for comparing genomic features. Bioinformatics. 2010;26:841–2. doi: 10.1093/bioinformatics/btq033. [PMC free article] [PubMed][Cross Ref]


