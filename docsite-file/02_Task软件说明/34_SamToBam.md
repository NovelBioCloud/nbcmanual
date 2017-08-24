## SamToBam
　　SAM和BAM是序列比对之后常用的输出格式，比如tophat输出BAM格式，bowtie和bwa等都采用了SAM格式。SAM的全称是sequence alignment/map format。而BAM就是SAM的二进制文件(B取自binary)，占用存储空间更小，利用bam二进制文件的运算速度快。Sam to Bam是将方便迅速将Sam格式转换为Bam格式。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　vcfInputData (BAM,SAM)：输入vcf格式文件。
　mappingToFile (FASTA)：输入基因组文件，FASTA格式文件。
　samInputData (SAM,BAM)：输入SAM或BAM格式文件。
　输入格式：Sam，bam；输出格式：bam，gz。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='mappingTo'>MappingTo：</label>Chromosome：比对到基因组序列。
　　　　　　　refSeq_All_Iso：比对到转录组序列。
　　　　　　　refSeq_One_Iso：比对到转录本中最长的一条序列。
　<label id='tread'>Tread：</label>软件所用线程数。
　<label id='sortBam'>SortBam：</label>Bam文件排序。
　<label id='index'>Index：</label>构建索引。
　<label id='mergeByPrefix'>MergeByPrefix：</label>多个bam合并。
　<label id='generatePileUpFile'>GeneratePileUpFile：</label>生成pileup文件。
　<label id='toBed'>To Bed：</label>生成bed文件。
　<label id='toBedOptionNoneUnique'>ToBedOptionNoneUnique：</label>用于Sam to bed 中，对于非unique mapping的数据，如果选择此选项只输出一条mapping结果，如不选择的则将所有的mapping结果都输出。
　<label id='MappingToFile'>MappingToFile：</label>当没有参考序列时（物种选为UnKnown Species），可上传参考序列。
　<label id='unsafe'>Unsafe：</label>
　　　　　　SAFE：严格，输入文件格式做检查
　　　　　　ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　　　　　　ALLOW_UNINDEXED_BAM:允许输入的Bam文件没有排序
　　　　　　ALLOW_UNSET_BAM_SORT_ORDER：允许输入的Bam文件没有建索引
　　　　　　LENIENT_VCF_PROCESSING
　　　　　　NO_READ_ORDER_VERIFICATION
　　　　　　ALL
**高级设置：**
　<label id='addUniqMapFlag'>AddUniqMapFlag(UnSortedSam)：</label>添加UniqMap的标签。
　<label id='addGroupInfo'>AddGroupInfo：</label>往sam文件中添加group信息。
　<label id='removeDuplicate'>RemoveDuplicate：</label>去除Duplicate序列。
　<label id='realign'>Realign：</label>重比对。
　<label id='recalibrate'>Recalibrate：</label>重估计。
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　sorted.bam：排序好的bam文件。
<div style="text-align:center">
<img data-src="1.png" width="600px" ></img>
</div>