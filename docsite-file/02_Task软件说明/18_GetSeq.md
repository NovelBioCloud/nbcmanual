# GetSeq
　　通过基因名称、序列位置、基金结构等提取序列的软件。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　从左侧文件中选择拖入 右侧相应位置。
　　chrFile:序列文件。
　　inFileName:输入基因名称表格文件。
　　gtfFile:序列注释信息。

***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='chrIdCol'>染色体所在列号：</label>Region提取，基因染色体列Gene提取，为基因名称列。
　<label id='getAllIso'>获取所有的ISO：</label>获取所有转录本序列。
　<label id='getmiRNA'>获取miRNA：</label>获取miRNA序列。
　<label id='seqtype：'>Seqtype：</label>Region：按照区域提取序列，需要填写“开始”“结束”；
　　　　　　Site：按照位置提取序列，需要填写表格中“site列号”，例如：chr1:8-90；
　　　　　　Gene：按照基因提取序列。
　<label id='startCol'>开始：</label>开始位置列。
　<label id='endCol'>结束：</label>结束位置列。
　<label id='siteCol'>Site列号：</label>选择site，需填写site号。
　<label id='genomwide'>Genomwide：</label>提取该物种的整个基因序列。
　<label id='geneStructure'>基因结构：</label>按基因结构选择需要提取部分。
　<label id='tssUp'>转录组起始位点-上游：</label>获取基因结构的上游bp序列，例如，基因结构选择Atg，转录组起始位点-上游填写：2000bp，即提取起始密码子上游2000bp序列。
　<label id='tssDown'>转录组起始位点-下游：</label>获取基因结构的下游bp序列。
　<label id='getAminoacid'>获取Aminoacid：</label>获取氨基酸序列。
　
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　Sequence.fa：提取出.fa结果。
<div style="text-align:center">
<img data-src="1.png" width="500px" ></img>
</div>
