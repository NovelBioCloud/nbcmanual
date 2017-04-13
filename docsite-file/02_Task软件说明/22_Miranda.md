#  Miranda
　　查找基因组中潜在的RNA位点软件, miRNA的靶点预测。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　InputFile中添加mRNA、miRNA、lncRNA等序列，输入格式： .fa；输出格式：.targetPredict.miranda.gz。
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　　miRanda是John等在2003年5月开发的第一个miRNA靶基因预测软件。miRanda适用范围广泛，不受物种限制，同时提供了 windows,linux,和macintosh多平台版本，可以下载到本地运行。碱基互补方面，miRanda算法和Smith-Waterman算 法相似，但它以碱基互补(如A=U,G&equiv;C等)代替Smith-Waterman算法中的碱基匹配(如A-A,U-U等)来构建打分矩阵，允许G=U错 配，为了体现miRNA3’端和5’端和靶基因作用过程中的不对称性，软件给出了scale参数(5’端11个碱基得分值乘以该值，然后和3’端11个碱 基得分值相加作为碱基互补得分)。同时强调miRNA第2到4位碱基和靶基因精确互补，第3到12位碱基和靶基因错配不得多于5个，9到L-5(L为 miRNA总长)位碱基至少一个错配，最后5个碱基错配不得多于两个。
　　软件官网：http://www.microrna.org/microrna/home.do

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='score'>Score：</label>miRNA和靶基因结合的效率水平。
　<label id='energy'>Energy：</label>miRNA和靶基因结合的吉布斯自由能，其绝对值越大，说明两者结合的越稳定。
　<label id='添加组合'>添加组合：</label>添加mRNA和miRNA。
　　　如图为miRNA和lncRNA、miRNA和mRNA做靶基因调控。
<div style="text-align:center">
<img data-src="1.png" width="370px" height="115px" ></img>
</div>

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　targetPredict.miranda.gz：做靶基因调控信息。
<div style="text-align:center">
<img data-src="2.png" width="600px"  ></img>
</div>



