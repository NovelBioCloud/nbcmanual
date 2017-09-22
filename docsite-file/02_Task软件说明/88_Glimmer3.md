Glimmer3
　　Glimmer是一款寻找原核生物基因的免费开源的预测软件，从1.0版本到现在的3.0版本，预测的准确度和速度都已经有了大幅提升。
Glimmer3软件网址: http://cbcb.umd.edu/software/glimmer/
下载网址:http://www.cbcb.umd.edu/software/glimmer/glimmer302.tar.gz

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
inputFile (FASTA)：直接把微生物或病毒的基因组序列，Fasta格式。
chrSeq (FASTA)：参考序列，Fasta格式。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
物种：参考序列物种。
版本：考序列版本。
Gene Length：基因长度。
Maximum Overlap Length：最大overlap长度。
Gene Threshold：基因阈值。
containerNumber：运行时container数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
生成.detail  .predict
<div style="text-align:center"><img data-src="1.png" width="500px" ></img></div>
.predict就是我们最终得到的预测基因文件，以“>"进行分割。
基因的各列信息分别为：
Column 1 预测基因编号，此编号和*.detail文件里编号一致。
Column 2 基因的开始位置。
Column 3 基因的结束位置。为终止密码子的最后一个碱基位置，也就是说包含终止密码子。
Column 4 阅读框。
Column 5 基因的“raw”分值。
