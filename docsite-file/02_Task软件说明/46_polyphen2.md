# Polyphen2
　　对于SNP以及点突变来进行人类蛋白结构和功能预测。
　　一些点突变改变引起氨基酸的改变从而影响蛋白的折叠，来影响蛋白的的相互作用区间和它的稳定性 。蛋白结构如果改变，蛋白的功能就更可能会发生改变，所以软件整合了序列和蛋白三维结构的一些特征 进行预测。但预测限于错义突变，其他无义突变（突变为终止密码）、碱基缺失、插入所造成的移框突变，以及起始密码子的突 变均不可预测。
　　官方网址：http://genetics.bwh.harvard.edu/pph2/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　在输入文件inputvcf处输入记录突变位点的vcf文件，输出文件为polyphen.result。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='ChrCol'>染色体号：</label>染色体号列
　<label id='posCol'>Position列号：</label>突变位点列。　
　<label id='refCol'>Ref列号：</label>原本的碱基列。
　<label id='altCol'>Alt列号：</label>改变的碱基列。
　
***

#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　　MutationTaste分值越高越显著， PolyPhen2越接近于1，对蛋白质的影响越大。
<div style="text-align:center">
<img data-src="1.png" width="700px" ></img>
</div>
　　**acc:** UniProtKB accession if known protein, otherwise same as o_acc.
　　**pos:** substitution position in UniProtKB protein sequence, otherwise same as o_pos.
　　**prediction:** qualitative ternary classification appraised at 5%/10% (HumDiv) or 10%/20% (HumVar) FPR thresholds (“benign”, “possibly damaging”, “probably damaging”).
　　**based_on:** prediction basis.
　　**effect:** predicted substitution effect on the protein structure or function.
　　**site:** substitution SITE annotation.
　　**region:** substitution REGION annotation.


