# FastQC
　　用于去除低质量数据和偏差的数据，进行数据过滤和质控。高通量测序得到海量的数据，我们在对数据进行分析之前，首先确保原始数据的可用性，低质量数据和偏差的数据会影响数据的有效性及分析的可信度，因此首先要采用FastQC软件进行数据过滤和质控。 
　**功能包括：**
　(1) 去接头。输入左端和右端接头序列，去除接头序列。
　(2) 低质量序列过滤。通过对序列质量分数的判定，按照多种标准过滤掉低质量的Reads。同时，可过滤掉左端或右端测序接头序列。
　(3) 质控。对测序的序列质量值评估、统计序列的每一个位置ATCG四种碱基的分布、对所有序列的每个位置统计GC含量评估、统计duplication情况。
　**过滤标准：**针对于Hiseq、454、Proton三个平台，设有strict、moderate、relax过滤标可选择。
　　FastQC由剑桥巴布拉汉研究所开发，可进行数据质控、过滤低质量reads，并生成质控报告。 
　　软件官网：http://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/

***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　**Q20：**指测序过程碱基识别（Base Calling）过程中，对所识别的碱基给出的错误概率。如果质量值是Q20，则错误识别的概率是1%，即错误率1%，或者正确率是99%；
　**Q30：**指错误识别的概率是0.1%，即错误率0.1%，或者正确率是99.9%；

FASTQ数据例如： 

       @SEQ_ID
       GATTTGGGGTTCAAAGCAGTATCGATCAAATAGTAAATCCATTTGTTCAACTCACAGTTT
       +
       !""*((((***+))%%%++)(%%%%).1***-+*""))**55CCF>>>>>>CCCCCCC65

FASTQ数据四行描述，如下： 

     Sequence identifier

     Sequence

     Quality score identifier line (consisting of a +)

     Quality score



　　其中第一行以“@”开头，随后为illumina 测序标识符(Sequence Identifiers)和描述文字(选择性部分)；第二行是碱基序列；第三行以“+”开 头，随后为illumina 测序标识符(选择性部分)；第四行是对应序列的测序质量。


***
#### **<span class="glyphicon glyphicon-check" aria-hidden="true" style="color:#3B9C9C;font-size:20px;" ></span> <span style="color:#3B9C9C">应用范围**

1. 低质量序列过滤。通过对序列质量分数的判定，按照多种标准过滤掉低质量的Reads。同时，还可过滤掉左端或右端测序接头序列。
2.  质控。对测序的序列质量值评估、统计序列的每一个位置ATCG四种碱基的分布、对所有序列的每个位置统计GC含量评估、统计duplication情况。

***

#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　该Task的数据来源于RawDataTask的fq.gz文件，最终生成高质量的fq.gz文件，可用于比对到参考基因组上。
　　如果为双端测序输入左端文件和右端文件，如果为单端测序只拖入左端文件即可。
　　　　左端文件：测序左端reads序列。
　　　　右端文件：测序右端reads序列。
　　输入格式为fq或者fq.gz，输出格式为fq.gz。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='ReadsQuality'>ReadsQuality</label>
　　　Strict：适用于高质量的fastQ序列；
　　　Moderate：适用于高质量的fastQ序列；
　　　Relax：适用于低质量fastQ序列；
　　　Relax 454：适用于454平台测序得到的fastQ序列；
　　　Relax PGM：适用于PGM平台测序得到的的fastQ序列。

| 质控标准   |  参数说明  |适用对象|
| -------- |  :----: | :----:  |
| Strict     |  同时满足质量值小于10低于7%；质量值小于13低于7%；质量值小于20低于15% |适用于高质量的fastQ序列 |
| Moderate     | 同时满足质量值小于10低于10%；质量值小于13低于14%；质量值小于20低于30%   |适用于质量中等的fastQ序列|
| Relax        |  同时满足质量值小于10低于10%；质量值小于13低于15%；质量值小于20低于35%  |适用于低质量fastQ序列|
|Relax_454　|同时满足质量值小于10低于15%；质量值小于15低于30%；|专门适用于454平台测序得到的fastQ序列　　|
|　Relax_PGM　|同时满足质量值小于10低于15%；质量值小于13低于20%|专门适用于PGM平台测序得到的的fastQ序列　|
|Not Filter　　|---　　|　不过滤任何序列，只做质控　|

　<label id='minLenBp'>MinLenBp：</label>最短保留的序列长度，即reads的长度范围。
　<label id='maxLenBP'>MaxLenBP：</label>最长保留的序列长度，即reads的长度范围。默认值为50~500bp，小RNA数据一般为15~33bp。
　<label id='trimEnd'>TrimEnd：</label>两端是否剪切掉reads末端低质量碱基。
　<label id='trimQuality'>TrimQuality：</label>连续出现低质量碱基个数设置，大于设置范围的reads将被过滤。
　<label id='qcBeforeFilter'>QcBeforeFilter：</label>输出过滤前的质控结果。
　<label id='qcAfterFilter'>QcAfterFilter：</label>输出过滤后的质控结果。
　<label id='isJustFastqc'>IsJustFastqc：</label>只质控不进行数据过滤。
　<label id='leftAdaptor'>Left Adaptor：</label>去接头，输入左端接头序列。
　<label id='right Adaptor'>Right Adaptor：</label>去接头，输入右端接头序列。
　<label id='lowCaseAdaptor'>Low Case Adaptor：</label>去PGM测序平台数据接头。
　

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

1.测序质量图
 　　测序的序列的质量评估，quality就是Fred值，-10*log10(p)，p为测错的概率。所以一条reads某位置出错概率为0.01时，其quality就是20。其中横轴为测序reads位置，纵轴为测序质量。红色表示中位数，黄色是25%-75%区间，触须是10%-90%区间，蓝线是平均数。一般我们认为数据Q20质控合格，即可进行进一步的分析。Q20 、Q30 ：分别计算 Phred 数值大于 20、30 的碱基占总体碱基的百分比。

<div style="text-align:center">
<img data-src="1.png" width="300px" ></img>
</div>
2.Reads的GC content

　GC content为计算碱基G和C的数量总和占总的碱基数量的百分比。红线是实际情况，蓝线是理论分布。GC content曲线为正态分布，均值不一定在50%，而是由平均GC含量推断。

<div style="text-align:center">
<img data-src="2.png" width="300px"  ></img>
</div>
3.测序reads长度分布图

<div style="text-align:center">
<img data-src="3.png" width="300px"  ></img>
</div>
4.数据统计表 basicStatsAll.xls 
　　表格统计测序数据量、碱基个数、reads平均长度以及GC含量。
<div style="text-align:center">
<img data-src="4.png" width="850px"  ></img>
</div>