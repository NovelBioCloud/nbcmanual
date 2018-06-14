## Cuffdif
　　Cuffdif为RNA-seq差异基因表达的分析软件，衡量两个或多个样本间差异表达的基因。是Cufflinks软件的一部分，Cufflinks包括四个部分为：cufflinks、cuffcompare、cuffmerge及cuffdiff，它可以利用tophat/bowtie比对结果（bam格式）及参考基因组构建转录本，最终的转录本是以gtf格式保存。
　　Cufflinks可以进行转录本组装，估计转录本的丰度，并且检测样本间的差异表达及可变剪接。由加利福尼亚大学伯克利分校数学和计算机生物实验室，伯克利分校的LiorPachter团队，和美国约翰霍普金斯大学遗传医学研究所的Steven Salzberg，以及加利福尼亚理工学院的Barbara Wold实验室联合作用的结果。

　官网：http://cole-trapnell-lab.github.io/cufflinks/
　输入格式：.sam，.bam；输出格式：.gtf

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择参考基因组物种。
<label id='speciesVersion'>物种版本：</label>参考基因组的版本
<label id='dbType'>物种类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　**选择gif文件：**添加注释文件。
***
