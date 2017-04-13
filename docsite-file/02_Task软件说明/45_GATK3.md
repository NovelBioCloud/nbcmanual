# GATK3
　　基于Illumina数据格式的人类全基因组和外显子组的测序数据，主要进行variant calling，包括SNP、INDEL，一般通过BWA+GATK进行数据分析。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　bamFile输入排好序的bam文件，vcfFile输入vcf注释文件，例如dbsnp注释文件，输入文件格式：sort.bam  输出文件格式：vcf。
　　选择建好bai索引的sorted.bam文件，根据需求设定参数，生成记录突变位点的vcf文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>参考序列物种。
　<label id='speciesVersion'>版本：</label>物种的版本。　
　<label id='thread'>线程数：</label>运行时，使用线程数。
　<label id='memory'>Memory：</label>运行时，使用内存。
　<label id='gvcf'>outGVCF：</label>勾选时，输出文件是vcf格式。
**高级选项：**
　<label id='standCallConf'>stand Call Conf：</label>可信度阈值的设定，Set the minimum phred-scaled confidence threshold at which variants should be call，默认值30.0。
　<label id='standEmitConf'>stand Emit Conf：</label>在变异检测过程中，所容许的最小质量值。只有大于等于这个设定值的变异位点会被输出到结果中，默认值为10.0。
　<label id='mmq'>MapQuality：</label>在变异检测过程中，每条reads所容许的最小mapping质量值，默认值为20。
　<label id='mbq'>BaseQuality：</label>在变异检测过程中，每个碱基所容许的最小质量值，默认值为10。
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　　记录突变位点的vcf文件：
<div style="text-align:center">
<img data-src="1.png" width="700px" ></img>
</div>