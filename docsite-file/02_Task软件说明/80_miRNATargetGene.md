# miRNATargetGene
　　circRNA、lncRNA、ncRNA与miRNA进行靶向调控进行预测，应用靶基因预测算法miranda和RNAhybrid来进行负相关调控关系预测。
　　成熟的miRNA是由较长的初级转录物经过一系列核酸酶的剪切加工而产生的，随后组装进RNA诱导的沉默复合体，通过碱基互补配对的方式识别靶基因，并根据互补程度的不同指导沉默复合体降解靶mRNA或者阻遏靶mRNA的翻译。
　**官网：**Miranda：http://www.microrna.org/microrna/home.do
　　　　RNAhybird：https://bibiserv.cebitec.uni-bielefeld.de/rnahybrid/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　miRNASeq：输入miRNA序列。
　　3'UTRSeq：输入负调控关系fasta序列文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**software：**选择所使用软件，Miranda和RNAhybird可以同时选择。
**Seed_Strict：**选中参数。对于miranda软件表示，添加这个参数-strict；添加这个参数的意思是要求miRNA的第2到第8个碱基必须是完全比对上的；对于RNAhybrid软件表示添加-f的参数，且其值为 2,7 ；-f 2,7 表示要求miRNA的第2到第7个碱基必须是完全比对上的。
**Miranda_Score：**miRNA和靶基因结合的效率水平。
**Miranda_Energy：**miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
**RNAhybrid_Model：**参考基因组的物种。
**RNAhybrid_MaxTargetLen：**RNAhybrid 中3`UTR序列最大长度。
**RNAhybrid_MaxQueryLen：**RNAhybrid 中miRNA序列最大长度。
**RNAhybrid_Energy：**miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
**RNAhybrid_Pvalue：**关系的结合显著性值，统计学根据显著性检验方法所得到的P值。
**RNAhybrid_HitsPerTarget：**一个小RNA和一个靶基因的某一段序列匹配情况最多列出几次，比如一个小RNA和一个靶基因的某一段序列匹配存在多种情况，则为1的话只列出最优的匹配情况，一般选1就比较好。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center"><img data-src="1.png" width="700px" ></img>
</div>
　　ubjectID：靶基因预测结果。
　　Energy：miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
　　Score：miRNA和靶基因结合的效率水平。
　　StartSubject：miRNA和靶基因结合的起始位点。
　　EndSubject：miRNA和靶基因结合的终止位点。


