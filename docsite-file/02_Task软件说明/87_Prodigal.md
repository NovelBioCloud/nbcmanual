# Prodigal
　　prodigal（Prokaryotic Dynamic Programming Genefinding Algorithm），原核的动态编程基因查找算法，prodigal主要应用于细菌和古生菌的基因预测，不能用于真核生物。如果要对meta样品做基因预测，prodigal还专门提供了meta的版本。prodigal软件可以直接输出基因的核酸序列并翻译出的相应的氨基酸序列。
　　Prodigal软件官网：http://prodigal.ornl.gov/
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　inputFile (FASTA)：assembly.fa

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
Output Format：选择输出文件格式，有gbk,gff,和sco格式可供选择
Exclude Run off Edges Gene：基因预测时考虑终止密码子的因素
Translation Table：核糖体结合位点表代码，默认11。
Treat N as masked Seq：屏蔽基因组中含N碱基序列。
containerNumber：软件运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　生成基因预测文件：assembly.gbk或assembly.gff或assembly.sco。