# snpEff
　　SnpEff是一个variant注释和预测软件。
　　SnpEff官网：http://snpeff.sourceforge.net/SnpEff_manual.html

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
**chrSeq：**参考序列.fa
**inputFile (VCF)：**输入样本的vcf文件，variant call format (VCF)
**gtfFile (GTF,GFF3)：**参考序列的注释文件.gtf

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**物种版本：**参考序列的版本。
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
**containerNumber：**软件运行，使用container数量。



***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

<div style="text-align:center"><img data-src="1.png" width="600px"  ></img></div>
summary.genes.txt：从基因层面的注释信息
summary.html：用浏览器打开，很多统计信息。
snpEff.txt：vcf的注释信息

