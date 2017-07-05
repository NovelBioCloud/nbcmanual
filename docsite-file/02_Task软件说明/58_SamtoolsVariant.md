# SamToolsVariant
　　用Samtools软件Call Variant。
　　官网：Samtools:http://www.htslib.org/
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　refSeq (FASTA)：参考序列fa文件。
　inputBam (BAM)：输入需要分析的样本BAM文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**参考序列物种
　**版本：**物种的版本
　**minBaseQuality：**最小碱基的质量值。碱基质量值过小会影响Variant预测的可信度。
　**minMappingQuality:**最小比对质量值。
　**VCF合并方式：**将样本结果合并
　　　　　　　　none：不排序，输出多条记录。
　　　　　　　　snps：按照SNP记录进行合并。
　　　　　　　　indels:按照indel记录合并。
　　　　　　　　both：按照SNP和indel分别合并。
　　　　　　　　all：都合并在一起。
　　　　　　　　id:按照ID号合并。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center">
<img data-src="1.png" width="600px"  ></img>
</div>
