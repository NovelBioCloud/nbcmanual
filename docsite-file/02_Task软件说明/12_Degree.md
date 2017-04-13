## **Degree**
　　Degree表示基因的核心度。在基因代谢通路中，一个基因往往参与多个信号通路，并且上下游的基因在不同的信号通路中也各不相同，degree表示每一个基因的与其他基因的互作程度，Degree越高，说明这个基因在信号通路中出于核心地位，也越为重要。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　只需要输入基因间互作关系表格，即可得到包含每个基因的Degree值的表格。在inFileName处，只需要输入基因间互作关系表格，输入文件格式：txt 或xls; xlsx；输出文件格式：xls。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
<label id='species'>物种：</label>选择参考序列物种
<label id='threshold'>阈值：</label>默认值为0.05


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center"><img data-src="1.png" width="650px"  ></img>
</div>

　AccID：基因名称。
　Symbol：NCBI的标准命名，accid的矫正。
　Description：基因的描述。
　Indegree：输入基因节点的度。
　Outdegree：输出基因节点的度。
　Degree：基因节点的度。


