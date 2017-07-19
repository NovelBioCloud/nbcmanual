# vcf2maf
　　vcf2maf将VCF文件注释，生成MAF格式，相当于将VCF格式转换成MAF格式。
　　MAF格式Mutation Annotation Format (MAF) ，是对突变进行注释的格式。一些和癌症分析相关的软件，要求MAF格式文件作为输入。经过GATK或samtools检测出突变的格式一般为VCF格式
　　官网：https://github.com/ckandoth/vcf2maf
　　

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
　　**inputVCF (VCF)：**输入VCF文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**选择参考基因组物种。
　**版本：**参考序列的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**BinSize:**每次计算的突变位点数量。
　**线程：**软件运行时，使用线程数。
　**内存：**软件运行时，使用内存数。
　**containerNumber：**软件运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>

　　生成maf文件。
<div style="text-align:center"><img data-src="1.png" width="600px"  ></img></div>
