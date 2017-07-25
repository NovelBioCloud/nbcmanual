Mutect2
　　Mutect2是GATK下的一个子模块，采用突变热点局部重比对和贝叶斯统计的方法，可以针对成对的正常-肿瘤样本进行体细胞变异分析，并对分析的结果进行校正过滤，去除正常样本和dbSNP库中的突变位点，最终得到高可信度的体细胞变异信息。
　　官网：https://hpc.nih.gov/apps/muTect.html

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件<span>**
　InputBam：输入需要分析的Bam文件。
　Interval_bed：基因组位置文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。
**unsafe：**运行时，输入文件较严格，Unsafe选项为在运行过程中输入文件是否做检查。
　　(1) SAFE：严格，输入文件格式做检查。
　　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许bam文件sort的时不指定sort方式。
　　(5) LENIENT_VCF_PROCESSING：
　　(6) NO_READ_ORDER_VERIFICATION：
　　(7) ALL：以上都允许。
**AltFreqCutOff：**突变频率的阈值，默认值为0.08。
**文件对比：**加入对比两个组份。选择实验组与对照组比较。
　　　　　group1Array：选择对比组1；
　　　　　group2Array：选择对比组2；
　　　　　outFileArray：输出文件名称。
**containerNumber：**软件运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
