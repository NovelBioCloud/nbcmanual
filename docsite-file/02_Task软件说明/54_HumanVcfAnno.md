#HumanVcfAnno
　　GATK里面的vcf文件，进行dbsnp、EXAC、TG、cosmic数据库注释。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
dbsnpVCF (VCF)：dbsnp数据库vcf文件
cosmicVCF (VCF)：cosmic数据库vcf文件
thousandGenomeVCF (VCF)：thousandGenome数据库vcf文件
EXAC-VCF (VCF)：EXAC数据库vcf文件
InputVCF (VCF):输入需要注释的indel、SNP等的vcf文件。


***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

物种：参考序列物种
版本：物种的版本
数据库类型：同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
Unsafe：GATK运行时，输入文件较严格，Unsafe选项为在运行过程中输入文件是否做检查。
(1) SAFE：严格，输入文件格式做检查。
(2) ALLOW_SEQ_DICT_INCOMPATIBILITY：允许fa文件和数据字典不匹配
(3) ALLOW_UNINDEXED_BAM：允许BAM文件没有索引。
(4) ALLOW_UNSET_BAM_SORT_ORDER：允许bam文件sort的时不指定sort方式
(5) LENIENT_VCF_PROCESSING：
(6) NO_READ_ORDER_VERIFICATION：
(7) ALL：以上都允许
线程数：运行时，使用线程数
ContainerNumber：运行时，使用Container数


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
