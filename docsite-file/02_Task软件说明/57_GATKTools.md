# GATKTools
　　GATKTools包含recalibtate和 realign两个工具。
（１）realign：这一步是样本层次的一个本地重排，因为在indel周围出现mapping错误的概率很高，而通过在indel周围进行一些重排可以大大减少由于indel而导致的很多SNP的假阳性。如果已经有一些可靠位点的信息的话 (例如dbsnp的数据)，这一步可以只在一些已知的可靠位点周围进行，这样得到的结果比较可靠也比较节省时间；而缺少这些数据的情况下则需要对所有位点都进行这样一个操作。
　　如果已经有可靠的INDEL位点(如dbsnp数据等），需要是VCF格式的信息，让realign操作主要集中在这些位点附近，实际情况下可能很多物种并没有这样的参考数据，所以需要对所有INDEL位点进行这样的一个操作。
（２）recalibtate
　　这一步是对bam文件里reads的碱基质量值进行重新校正，使最后输出的bam文件中reads中碱基的质量值能够更加接近真实的与参考基因组之间错配的概率。这一步适用于多种数据类型，包括illunima、solid、454、CG等数据格式。在GATK2.0以上版本中还可以对indel的质量值进行校正，这一步对indel calling非常有帮助。
　　例如，在reads碱基质量值被校正之前，我们要保留质量值在Q25以上的碱基，但是实际上质量值在Q25的这些碱基的错误率在1%，也就是说质量值只有Q20，这样就会对后续的变异检测的可信度造成影响。还有，在Hiseq测序数据中，在reads末端碱基的错误率往往要比起始部位更高。碱基AC的质量值往往要低于TG。recalibtate就是要对这些质量值进行校正。


***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
InputBam (BAM)：需要分析的样品bam数据文件。
InputVCF(dbSNP) (VCF)：dbsnp EXAC TG cosmic数据库VCF。
interval_Bed (BED)：基因组位置文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**参考序列物种
**版本：**物种的版本
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
**ToolsType：**选择则需要用的工具recalibtate或者realign。               
**Unsafe：**GATK运行时，输入文件较严格，Unsafe选项为在运行过程中输入文件是否做检查。
　(1) SAFE：严格，输入文件格式做检查。
　(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配。
　(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
　(4) ALLOW_UNSET_BAM_SORT_ORDER：允许bam文件sort的时不指定sort方式。
　(5) LENIENT_VCF_PROCESSING：
　(6) NO_READ_ORDER_VERIFICATION：
　(7) ALL：以上都允许。
**线程：**运行时，使用线程数。
**Memory：**运行时，使用Container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
(1).realign.bam:realign后的bam文件。
(2).recal.bam：recalibtate后的bam文件。



