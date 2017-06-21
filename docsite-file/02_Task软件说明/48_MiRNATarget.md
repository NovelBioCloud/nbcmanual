# MiRNATarget
　　circRNA、lncRNA、ncRNA与miRNA进行靶向调控进行预测，应用靶基因预测算法miranda和RNAhybrid来进行负相关调控关系预测。
　　成熟的miRNA是由较长的初级转录物经过一系列核酸酶的剪切加工而产生的，随后组装进RNA诱导的沉默复合体，通过碱基互补配对的方式识别靶基因，并根据互补程度的不同指导沉默复合体降解靶mRNA或者阻遏靶mRNA的翻译。
　**官网：**Miranda：http://www.microrna.org/microrna/home.do
　　　　RNAhybird：https://bibiserv.cebitec.uni-bielefeld.de/rnahybrid/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　在utrseq处输入负调控关系fasta序列文件，在miRNASeq处输入miRNA序列。
　　
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>参考基因组的物种。
　<label id='speciesVersion'>speciesClass：</label>增加参考基因组的物种。　
　<label id='score'>score：</label>miRNA和靶基因结合的效率水平。
　<label id='pValue'>pValue：</label>关系的结合显著性值，统计学根据显著性检验方法所得到的P值。
　<label id='energy'>energy：</label>miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
　
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center"><img data-src="1.png" width="700px" ></img>
</div>
　　ubjectID：靶基因预测结果。
　　Energy：miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
　　Score：miRNA和靶基因结合的效率水平。
　　StartSubject：miRNA和靶基因结合的起始位点。
　　EndSubject：miRNA和靶基因结合的终止位点。