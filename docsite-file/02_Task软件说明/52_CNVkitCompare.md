# CNVkitCompare
　　全基因组测序中，基于基因组比对结果，进行了拷贝数变异分析，得到了不同的患者的癌症组织相对于癌旁组织的拷贝数变异情况。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
InputBam (BAM)：需要分析的样品bam文件
TargetBed (BED)：基因组位置文件

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**参考序列物种
**版本：**物种的版本
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
**BedSpelit：**最小gap的碱基数，默认为5000
**Thread：**运行时，使用线程数
**ContainerNumber：**运行时，使用Container数



***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

