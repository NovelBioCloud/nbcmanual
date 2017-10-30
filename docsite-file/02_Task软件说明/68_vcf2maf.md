# vcf2maf
　　vcf2maf将VCF格式突变数据进一步注释成MAF格式。MAF格式Mutation Annotation Format (MAF) ，是对突变进行注释的格式。
**功能：**
　　利用十几个常见的已知数据库来注释得到的vcf变异检测结果。
**使用软件：**
　　Vcf2maf：是将VCF格式突变数据进一步注释成MAF格式的软件。软件官网：https://github.com/mskcc/vcf2maf
**应用范围：**
　　通常情况下是对somatic的突变才注释成maf格式。一些和癌症分析相关的软件，要求MAF格式文件作为输入。经过GATK或samtools检测出突变的格式一般为VCF格式。

***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是GATK3中的结果VCF文件。
　　**InputVCF：**GATK检测变异结果VCF文件，VCF的详细说明请见官方文档：http://samtools.github.io/hts-specs/VCFv4.2.pdf


#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　变异注释结果文件，以maf文件格式存储。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**物种：**选择参考基因组物种。
　**版本：**参考序列的版本。
　**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**BinSize:**每次计算的突变位点数量，设置同时读入内存的变异数量，如果设置值较低，则会有较长的运行时间为带来换来较少的内存使用，设置值较高，则运行时间短但使用内存大。
　**线程：**软件运行时，使用线程数。
　**内存：**分析过程中使用的最大内存，以Mb为单位。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>

　　maf：结构变异注释maf结果文件，maf文件格式说明，请见官方文档：https://wiki.nci.nih.gov/display/TCGA/Mutation+Annotation+Format+(MAF)+Specification
