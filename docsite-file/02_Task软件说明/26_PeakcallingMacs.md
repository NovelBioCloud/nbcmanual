
# PeakcallingMacs
　　差异peak的统计，是一种用于鉴定chip-seq或MeDIP-seq后所得到的比对读段富集在基因组哪些区域中的一种计算方法。
　　官方网站：https://en.wikipedia.org/wiki/Peak_calling
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　inFileArray和inFileCtrlArray输入Bam或bed文件。左边case，右边input来进行两组比较。chromsomeFile输入参考序列文件。
　　输入文件格式：.sorted.bam；输出文件格式：.xls 、.bed。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='mFoldMin'>mFoldMin：</label>实验组比对照组最小reads堆叠倍数。
　<label id='pvalue'>pvalue：</label>统计学根据显著性检验方法所得到的P 值，一般以P < 0.05 为显著， P <0.01 为非常显著。

　<label id='mFoldMax'>mFoldMax：</label>实验组比对照组最大reads堆叠倍数。
　<label id='nolambda'>nolambda：</label>
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　peaks.xls ：Peak结果统计说明
<div style="text-align:center">
<img data-src="1.png" width="600px" ></img>
</div>
　chr	Peak：所在的染色体编号
　Start：Peak起始位点
　end	Peak：终止位点
　length：Peak长度
　summit：峰最高点的位点
　tags：	峰中的标准化Reads数
　(-10log10(pvalue))：峰的Pvalue以10为底取对数的10倍的相反数，(-10log10(pvalue))越大表示峰越可信
　fold_enrichment：峰中富集的Tag数与计算机模拟的背景Tag之间的比值
　FDR(%)：多重假设检验错误误判率。FDR越小，误判率越低。
　Symbol：Peak所对基因的名称
　Location：Peak所对基因的位置
　Strand：正义链反义链信息
　KeggID：基因的KeggID
　Description：Peak所对基因的描述

