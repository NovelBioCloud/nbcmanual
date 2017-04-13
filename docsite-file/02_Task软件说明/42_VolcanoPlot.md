# VolcanoPlot
　　用于显示两组样品数据的显著性差异，RNA-seq中，火山图显示了两个主要的指标：fold change和校正后的p value，利用T检验分析出两样本间显著差异表达的基因后，以log2(fold change)为横坐标，以T检验显著性检验p值的负对数-log10(p)为纵坐标。
　　用火山图推断差异基因的整体分布情况，从差异倍数（Fold change）和显著水平（P-value）两个水平进行评估。
　　软件官网：http://chipster.csc.fi/manual/plot-volcano.html
****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='logFC'>Log2FC所在列：</label>输入数据Log2FC所在的列数。
　<label id='fdr'>FDR所在列：</label>输入数据FDR所在的列数。
　<label id='ylimit'>FY轴limit</label>：Ｙ轴长度

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　Volcano.png：绘制的火山图
　　检验分析出两样本间显著差异表达的基因后，以log2（fold change）为横坐标，以T检验显著性检验P值的负对数-log10（P-value）为纵坐标，利用一定的筛选条件（如大于1.5倍变化且P<0.05）,可以筛选出显著差异表达的基因，进行后续研究。
<div style="text-align:center">
<img data-src="1.png" width="500px" ></img>
</div>