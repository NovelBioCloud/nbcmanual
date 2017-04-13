# PlotChromosome
　　测序Reads在染色体区域上的分布图。每条染色体上minP的分布，横坐标为染色体上位置，纵坐标为-log10（minP）,每个点代表一个通过筛选的SNP。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　在 InputBam输入已排序的bam文件，输入文件格式：.sorted.bam；输出文件格式：png。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='invNum'>InvNum：</label>取样区段，默认以10bp取样。
　<label id='normalizedType'>Normalized type：</label>取样内的标准化方式。
　<label id='containerNumber'>ContainerNumber：</label>运行时使用的container数。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　sorted_chrome_distribution_chr1.png：测序Reads在染色体区域上的分布图。
<div style="text-align:center">
<img data-src="1.png" width="900px"  ></img>
</div>