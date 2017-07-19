# VarScan2_Germline
　　VarScan2工具将突变点分为三种突变状态：体细胞突变Somatic突变、基因胚系突变Germline突变、杂合性缺失LOH突变。
　　Germ-line的mutations来自上一代，这种mutation会随着个体整个胚胎发育过程存在，在研究方法上，Germ-line的mutations在家系分析中占有重要角色，对很多遗传病（包括遗传型“肿瘤”）的研究中占有重要地位。在测序过程中，除了个体测序之外，还会加上个体的家属一同测序，病理分析时也会考虑家族背景的影响。
VarScan2官网：http://varscan.sourceforge.net

 ***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>
　**minCoverage：**reads的最小覆盖度，默认值为8。
　**minSupportingReads：**最少支持reads数，默认值为2。
　**minBaseQuality：**最小碱基质量值，默认值为15。
　**minFreq：**最小等位基因变异频率阈值，默认值为0.01。
　**minFreqForHomozygote：**纯合体的最小突变频率，默认值为0.75。
　**p-value：**calling variants 的p值，默认值为0.99。
　**containerNumber：**软件运行时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>
　　vcf文件得到对应的call SNP与InDel的结果。
<div style="text-align:center"><img data-src="1.png" width="500px" ></img></div>
