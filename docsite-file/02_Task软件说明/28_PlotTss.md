# PlotTss
　　ChIP-Seq分析中的一个常见任务，是获取相对于附近要素的标记的轮廓。当分析组蛋白标记时，通常对转录起始位点（TSS）附近的这种标记的位置和延伸感兴趣。因此，通常计算整个基因组中的片段或片段的覆盖度，然后标记以所有基因的TSS为中心的固定大小的区域，添加区域的大小获取这些区域的覆盖。也可用于allreads、Peak或Gene在Tss区和Tes区的分布统计。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　输入文件格式：.sorted.bam；　输出文件格式： .png、.xls。
官网网址：http://www-huber.embl.de/users/anders/HTSeq/doc/tss.html

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考序列的物种。
　<label id='speciesVersion'>版本：</label>物种的版本。
　<label id='normalizedType'>Normalized type：</label>对all reads/gene做标准化处理或不做标准化处理。
　<label id='extendBP'>Extend BP：</label>reads延长至250bp。
　<label id='invNum'>InvNum：</label>
　<label id='oneSiteOneReads'>One site one Reads：</label>
　<label id='uniqeMapping'>UniqeMapping：</label>统计uniqemapping的reads
　<label id='geneFileType'>GeneFileType：</label>选择做分布统计的区域，一般选择all gene。选择PeakCovered和ReadGene时，需要导入相应的表格。
　<label id='colGene'>ColGene：</label>基因所在列。
　<label id='colValue'>ColValue：</label>
　<label id='colchrld'>Colchrld：</label>染色体ID所在列。
　<label id='colStrat'>ColStrat：</label>染色体起始列。
　<label id='colEnd'>ColEnd：</label>染色体终止列。
　<label id='sortBigToSmall'>SortBigTo Small：</label>是否需要从大到小排序。
　<label id='heatMapSamll'>HeatMapBig：</label>Heatmap的范围。
　<label id='resultBinNum'>ResultBinNum：</label>
　<label id='upStream'>UpStream：</label>tss和tes上游范围。
　<label id='dowmStream'>DowmStream：</label>tss和tes下游范围。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　TSS为Read是在转录起始位置的定位图。 
１）AllGene_pileupInfo_Tss.png是样本Reads在TSS附近的定位图。
<div style="text-align:center">
<img data-src="1.png" width="400px" ></img>
</div>

2).pileupInfo.Tss.xls:
表中Distance to tes：tes位置信息;Normalized reads：标准化后的值reads丰度值。
<div style="text-align:center">
<img data-src="2.png" width="240px"></img>
</div>
