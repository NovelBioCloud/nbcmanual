# cpat

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;基因组中存在大量的非编码RNA（ncRNA）,并在基因表达调控等方面发挥重要的作用，该模块可以从RNA-Seq数据中预测出ncRNA。
**功能：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;预测输入序列的编码能力，进而实现预测ncRNA的目的。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**CPAT：**从RNA-Seq分析得到的转录本中预测RNA的编码能力，进而筛选出编码和非编码RNA的软件。
**软件官网：**
http://rna-cpat.sourceforge.net/
**应用范围：**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;通常是先将RNA-Seq数据进行重构转录本的分析，然后根据重构的转录本文件（通常是gtf文件），得到novel转录本，然后提取novel转录本的序列，作为该模块的研究对象。
***

#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;该Task的输入数据是根据重构的转录本gtf文件，提取出来的novel转录本序列文件。
**inputFile：**通常是需要预测编码能力的序列文件，文件格式为fasta；
**CDSseqFile： **CDS序列文件，该CDS序列应该是以起始密码子开始，终止密码子结束的序列，也就是说，CDS序列的长度应是3的倍数；如果CDS序列是从负链提取的，那么就需要将提取的序列进行反向互补转化，文件格式为fasta；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;用途：与“NONCODseqFile”文件一起，构建分析序列的训练集；
**NONCODseqFile：** noncoding序列文件，最好是已知的 noncoding genes，而不是编码基因的非编码序列，如“3’UTR”或者“5’UTR”，文件格式为fasta；
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;用途：与“CDSseqFile”文件一起，构建分析序列的训练集；
**注：**当所分析的物种是模式物种（人、果蝇、小鼠、斑马鱼）时，由于软件已经自带了这几个物种的训练集，因此不用输入“CDSseqFile”和“NONCODseqFile”文件来构建训练集；如果所分析的物种不是以上的这几个模式物种，那么可以选择与其关系比较近的模式物种，或者通过输入 “CDSseqFile”和“NONCODseqFile”文件来构建训练集，如果所分析的物种没有注释明确的编码和非编码的基因序列，也可以使用近源物种的序列来构建训练集。
***

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　	输入RNA序列的编码能力预测结果列表与筛选出来的ncRNA的结果列表（txt）。
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='startCodons'>StartCodons：</label>设置起始密码子，默认为：ATG；
<label id='stopCodons'>StopCodons：</label>设置终止密码子，默认为：TAG,TAA,TGA；
<label id='isModelOrganism'>是否是模式生物：</label>需要分析的序列是否是模式物种；
<label id='organism'>模式物种名称：</label>如果分析的序列是模式物种，选择设置模式物种的物种名称；
<label id='codingThreshold'>coding Threshold：</label>设置判断是否是编码RNA的阈值，小于该阈值的为ncRNA。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
**\*.cpat.result.txt：**所有输入RNA的编码能力预测结果列表，结果格式如下所示：
<div style="text-align:center">
	<img data-src="1.png" width="600px" ></img>
</div>
各列详细信息说明如下：
<div style="text-align:center">
	<img data-src="2.png" width="300px" ></img>
</div>
**\*.cpat.filter.txt：**预测出的ncRNA结果列表，该文件是由\*.cpat.result.txt文件过滤得到的，过滤原则（coding_prob< coding Threshold 设定值），格式与\*.cpat.result.txt文件相同。
***

**参考文献**
1.	Wang, L., Park, H. J., Dasari, S., Wang, S., Kocher, J.-P., & Li, W. (2013). CPAT: Coding-Potential Assessment Tool using an alignment-free logistic regression model. Nucleic Acids Research, 41(6), e74. doi:10.1093/nar/gkt006


