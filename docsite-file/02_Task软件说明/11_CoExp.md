## **CoExp**
　　共表达网络图（Coexpression Network），根据基因在样本中的信号表达值，计算每两个基因之间的Pearson correlation，并设立阈值。当两基因之间Pearson correlation 超过阈值时，则认为该两基因之间存在共表达关系。
　　基因共表达网络多是以基因间数据的相关性为基础而实现构建的。在基因共表达网络的表示中，经常使用图模型来描述基因之间的关系。节点代表基因，线表示两个基因之间的共表达相互作用关系。共表达网络构建主要分两个步骤，一是对所有基因进行相似性度量；二是通过阈值的选择确定共表达网络的边界。
　　官网：https://en.wikipedia.org/wiki/Gene_co-expression_network
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　将基因表达量的表格拖入右侧inFileName中。输入文件格式：.txt 或.xls; .xlsx；输出文件格式：.txt。输入为关注基因及该组所有样本表达量的txt文件，即可获得基因间共表达关系表格。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　　<label id='threshold'>阈值：</label>p值和FDR值,，默认值为0.05。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　相关系数（correlation coefficient）代表两个基因间表达谱的相似程度，值越高表明相似性越高。相关关系（relationship）表明两个基因表达是正相关还是负相关。
　　
　　共表达网络图：
<div style="text-align:center"><img data-src="coExp1.png" width="650px"  ></img>
</div>
<div style="text-align:center">
<img data-src="coExp2.png" width="500px" height="400px" ></img>
</div>
