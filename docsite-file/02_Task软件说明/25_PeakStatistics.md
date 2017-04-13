# PeakStatistics
　　差异peak比对到参考基因组上的结构组成。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　在inFileArray处，输入Peakcalling的结果表格文件，确定summit对应的列数。
输入文件格式：peak.loc.xls；输出文件格式：gene_structure.txt。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='tssUp'>转录起始位点-上游：</label>选定参考基因组转录起始范围上游。
　<label id='tesUp'>转录起始位点-下游：</label>选定参考基因组转录起始范围下游。
　<label id='tesDown'>转录终止位点-上游：</label>选定参考基因组转录终止范围上游。
　<label id='cutoff'>转录终止位点-下游：</label>选定参考基因组转录终止范围下游。
　<label id='chrIdCol'>染色体列号：</label>表格中染色体号对应列数。
　<label id='peakStartCol'>Peaksummit位点：</label>表格中Peaksummit对应列数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　运行后，得到peak区域在参考基因组上的结构组成。
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>
