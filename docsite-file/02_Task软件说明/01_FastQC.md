# FastQC
　　用于去除低质量数据和有偏差的数据，进行数据过滤和质控。高通量测序得到海量的数据，我们在对数据进行分析之前，首先确保原始数据的可用性，低质量数据和偏差的数据会影响数据的有效性及分析的可信度，因此首先要采用FastQC软件进行数据过滤和质控。
　**功能包括：**
　(1) 去接头。输入左端和右端接头序列，去除接头序列。
　(2) 低质量序列过滤。通过对序列质量分数的判定，按照多种标准过滤掉低质量的Reads。同时，可过滤掉左端或右端测序接头序列。
　(3) 质控。对测序的序列质量值评估、统计序列的每一个位置ATCG四种碱基的分布、对所有序列的每个位置进行GC含量评估、统计重复reads (即，reads duplication)情况。
　**过滤标准：**针对于Hiseq、454、Proton三个平台，设有strict、moderate、relax三个等级的过滤标准，供用户选择。
&nbsp; &nbsp;**过滤步骤：**
1.如果参数Left Adaptor或Right Adaptor设置了接头，则去除接头序列。
2.如果参数TrimEnd为True，则剪切掉reads末端质量值低的碱基。
3.根据参数MinLenBp和MaxLenBp，对reads进行长度过滤。
4.根据参数ReadsQuality，对reads进行质量过滤。
　**使用软件：**
　FastQC由剑桥巴布拉汉研究所开发，可进行数据质控，并生成质控报告。NovelBrain在此基础上添加了过滤序列的功能。 
　　软件官网：http://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/


***
#### **<span class="glyphicon glyphicon-check" aria-hidden="true" style="color:#3B9C9C;font-size:20px;" ></span> <span style="color:#3B9C9C">应用范围**
　1.低质量序列过滤。通过对序列质量分数的判定，按照多种标准过滤掉低质量的Reads。同时，还可过滤掉左端或右端测序接头序列。
　2.质控。对测序的序列质量值评估、统计序列的每一个位置ATCG四种碱基的分布、对所有序列的每个位置进行GC含量评估、统计重复reads (即，reads duplication)情况。

***

#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　该Task的数据来源于 fastq格式文件，最终生成高质量的fastq文件，可用于比对到参考基因组上。
　　如果为双端测序，输入左端文件和右端文件，如果为单端测序只拖入左端文件即可。
　　　　左端文件：测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。文件可以为gz压缩后fastq格式，如 filename.1.fq.gz
　　　　右端文件：测序右端reads序列，单端不需要输入该文件，双端要求输入右端文件，如filename.2.fq.gz
　　

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　输出为经过gz压缩的fastq文件，如filename.1.fq.gz和filename.2.fq.gz。本文件可以用于做序列比对等后续工作，如作为DnaSeqMap的输入文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='ReadsQuality'>ReadsQuality</label>
　　　Strict：适用于高质量的fastQ序列；
　　　Moderate：适用于高质量的fastQ序列；
　　　Relax：适用于低质量fastQ序列；
　　　Relax 454：适用于454平台测序得到的fastQ序列；
　　　Relax PGM：适用于PGM平台测序得到的的fastQ序列。
   具体解释见下表：

| 质控标准   |  参数说明  |适用对象|
| -------- |  :----: | :----:  |
| Strict     |  同时满足质量值小于10低于7%；质量值小于13低于7%；质量值小于20低于15% |适用于高质量的fastQ序列 |
| Moderate     | 同时满足质量值小于10低于10%；质量值小于13低于14%；质量值小于20低于30%   |适用于质量中等的fastQ序列|
| Relax        |  同时满足质量值小于10低于10%；质量值小于13低于15%；质量值小于20低于35%  |适用于低质量fastQ序列|
|Relax_454　|同时满足质量值小于10低于15%；质量值小于15低于30%；|专门适用于454平台测序得到的fastQ序列　　|
|　Relax_PGM　|同时满足质量值小于10低于15%；质量值小于13低于20%|专门适用于PGM平台测序得到的的fastQ序列　|
|Not Filter　　|---　　|　不过滤任何序列，只做质控　|


　<label id='minLenBp'>MinLenBp：</label>最短保留的序列长度，即reads的长度范围。小于该长度的reads会被过滤掉。默认为50。
　<label id='maxLenBP'>MaxLenBP：</label>最长保留的序列长度，即reads的长度范围。默认值位500。
　　MinLenBp和MaxLenBp用于过滤过长或过短的序列，根据不同的测序需要选择不同的参数。如mRNA一般最短reads不能短于50bp，而miRNA数据一般为长度设置区间为15~33bp。即MinLenBp设为15，MaxLenBp设为33。
　<label id='trimEnd'>TrimEnd：</label>两端是否剪切掉reads末端低质量碱基。Illumina测序的序列越长质量越差，那么我们会考虑将头部和尾部低质量的序列切除。
　<label id='trimQuality'>TrimQuality：</label>在切除末端低质量序列时，如果末尾处的碱基质量小于（不包含）该值，则会被剪切掉。
　　以上两个参数，在当TrimEnd设置为True，并且TrimQuality设置为15时，则软件会从头部和尾部开始，把连续质量小于15的碱基删除，直到遇到的碱基质量大于15为止。
 例如考虑序列以Phred 33格式展示：
```
@fastqreads
ATCGATCGAATTCCGG
+
,..AB.A,BCABC.,.
```
　　其中“，”和”.”所代表的质量分别为11和13，其他值大于15。
过滤后得到序列
```
@fastqreads
GATCGAATTC
+
AB.A,BCABC
```
　　本结果之后再会去进行参数ReadsQuality所涉及到的过滤。

 
　<label id='qcBeforeFilter'>QcBeforeFilter：</label>输出过滤前的质控结果。
　<label id='qcAfterFilter'>QcAfterFilter：</label>输出过滤后的质控结果。
 　　FastQC可以在过滤前和过滤后都进行质控。
　<label id='isJustFastqc'>IsJustFastqc：</label>只质控不进行数据过滤。部分场景可能仅需要得到质控数据，并不需要真正的过滤数据，这时候可以选择本选框，注意仅输出QcBeforeFilter的结果。
　<label id='leftAdaptor'>Left Adaptor：</label>去接头，输入左端接头序列。
　<label id='right Adaptor'>Right Adaptor：</label>去接头，输入右端接头序列。
　部分测序比如16s测序等，会包含接头，可以通过这两个参数进行去接头处理。
　

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

1.测序质量图
 　　测序的序列的质量评估，quality就是Fred值，-10*log10(p)，p为测错的概率。所以一条reads某位置出错概率为0.01时，其quality就是20。其中横轴为测序reads位置，纵轴为测序质量。红色表示中位数，黄色是25%-75%区间，触须是10%-90%区间，蓝线是平均数。一般我们认为数据Q20质控合格，即可进行进一步的分析。Q20、Q30：分别计算 Phred 数值大于20、30的碱基占总体碱基的百分比。

<div style="text-align:center">
<img data-src="1.png" width="300px" ></img>
</div>
2.Reads的GC content
　GC content（GC含量）为序列中碱基G和C的数量总和占总的碱基数量的百分比。红线是实际情况，蓝线是理论分布。GC content曲线为正态分布，均值不一定在50%，而是由平均GC含量推断。
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

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  详细说明**
　**Q20：**指测序数据碱基识别（Base Calling）过程中，对所识别的碱基给出的错误概率。如果质量值是Q20，则错误识别的概率是1%，即错误率1%，或者正确率是99%；
　**Q30：**指错误识别的概率是0.1%，即错误率0.1%，或者正确率是99.9%。
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

