# TSSPlot 
　　TSS，全称Transcription Start Site，即转录起始位点。
**功能：**
	&nbsp;&nbsp;&nbsp;&nbsp;绘制转录起始位点附近的reads分布图。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**TSSPlot：**该软件由NovelBio研发团队编写java代码实现，用于绘制转录起始位点附近的reads分布图。

 **应用范围:**
	&nbsp;&nbsp;&nbsp;&nbsp;用于绘制转录起始位点附近的reads分布图。



***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是Samtools排序后的Bam文件。
**InputBam：**排序后的bam文件。SAM的全称是sequence alignment/map format，而BAM就是SAM的二进制文件（B取自于binary）。SAM文件详细说明，请见官方文档：http://samtools.github.io/hts-specs/SAMv1.pdf。
**GeneSet：**用于统计的基因列表，如：
<div style="text-align:center">
	<img data-src="1.png" width="100px" ></img>
</div>
注意：1.表格中必须要有一行title ,对于title名称无特殊要求；2.输入表格中必须要有一列基因名称。&nbsp;

**LocationFile：**用于统计的bed区域列表，要求输入的格式与结果中的gene.Bed一致，gene.Bed的格式如下所示：
<div style="text-align:center">
	<img data-src="2.png" width="300px" ></img>
</div>
其中第一列为基因名称，第二列为基因在染色体上的位置信息。

***
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　转录起始位点附近reads的分布图（png）。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。　 
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，通过该参数可选择特定数据库gtf文件。
**geneStructure：**选择基因结构。
**StartExtend：**起始位点向上游延伸的碱基数(bp)，默认为-1000。
**EndExtend：**终止位点向下游延伸的碱基数(bp)，默认为1000。
**Splitpart：**选择的需要绘制区域等分份数。
**GenomeWideGene：**是否获取全基因组上的基因。
**GeneCol：**如果参数“GeneSet”有输入文件，通过该参数设置该输入文件中基因所在的列数。
**isUniqueReads：**是否使用UniqueReads来进行统计（即，如果有多条reads比对到同一个位置，并且首位相同，是否仅保留其中一条reads）。
**isuniqueMapping：**是否使用uniqueMappingreads进行统计计算。
**pileUpType：**当绘制基因外显子区域的分布时，对于外显子区域的标准化方法，有以下几种方式：
&nbsp;&nbsp;&nbsp;&nbsp;cn: 即connect norm，直接把外显子区域连起来，然后标准化为指定长度；
<div style="text-align:center">
	<img data-src="3.jpg" width="400px" ></img>
</div>
&nbsp;&nbsp;&nbsp;&nbsp;cc: 即connect cut，直接把外显子区域连起来，然后把比指定长度长的区域剪掉，如果连接起来的区域比指定长度短，则将长度补齐到指定的长度，被补的区域reads覆盖为0。		
<div style="text-align:center">
	<img data-src="4.jpg" width="400px" ></img>
</div>
&nbsp;&nbsp;&nbsp;&nbsp;pnl: 即pileup norm to length，把外显子区域堆叠起来，并且把每个区域标准化到相同的长度，即先标准化后合并；	
<div style="text-align:center">
	<img data-src="3.jpg" width="400px" ></img>
</div>
&nbsp;&nbsp;&nbsp;&nbsp;plnl: 即pileup long norm to length，把外显子区域堆叠起来，并且把长度大于指定长度的区域标准化到相同的长度，短于指定长度的舍弃掉然后直接合并，即先标准化后合并；
 <div style="text-align:center">
	<img data-src="4.jpg" width="400px" ></img>
</div>
&nbsp;&nbsp;&nbsp;&nbsp;pc: 即pileup cut，将外显子区域简单堆叠起来，不等长的区域就直接堆叠起来，最后截取为指定长度，即先合并后截取为指定长度；
 <div style="text-align:center">
	<img data-src="5.jpg" width="400px" ></img>
</div>
&nbsp;&nbsp;&nbsp;&nbsp;pn: 即pileup norm，将外显子区域简单堆叠起来，不等长的区域就直接堆叠起来，最后标准化为指定长度，即先合并后标准化为指定长度。
 <div style="text-align:center">
	<img data-src="6.jpg" width="400px" ></img>
</div>
**normalType：**每个碱基的覆盖reads数的标准化方法，计算方法有以下几种：
		&nbsp;&nbsp;&nbsp;&nbsp;allreads：将每个点的reads数除以测序深度；
		&nbsp;&nbsp;&nbsp;&nbsp;per_gene：将每个点的reads数除以该gene的平均测序深度；
		&nbsp;&nbsp;&nbsp;&nbsp;no_normalization：不进行标准化。
**ReadsExtend：**该参数是指从起点开始读取该reads的碱基个数， 小于等于0表示不延长，小于reads长度则截短，大于reads长度的则延长，默认-1。
**invNum：**对基因组碱基的reads覆盖数，每隔多少位碱基采样取均值录入内存。默认值为10。详细解释如下：在计算过程中，若将基因组中每个碱基的reads覆盖数会占用很多内存，所以系统默认每隔10位碱基，对这10个碱基的reads数取平均数，得到这10个碱基的平均覆盖reads数，录入内存。这样对内存的占用率只有前者的十分之一。
**coefficient：**reads数乘以一定的系数，使绘制的图好看一些。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\*_TSS_Plot.png：**转录起始位点附近reads的分布图，横轴代表基因结构位置，纵轴代表标准化后的reads数，如下图所示：
<div style="text-align:center">
	<img data-src="9.jpg" width="400px" ></img>
</div>&nbsp;
	