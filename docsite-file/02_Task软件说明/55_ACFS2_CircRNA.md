## ACFS CicRNA
　　基于de novo的方法，以准确和快速鉴定和丰度定量来自单端和双端序列，来预测CicRNA的软件。
　　官网：https://github.com/arthuryxt/acfs

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　LeftFastq添加左端序列文件，RightFastq 添加右端序列文件，组名可修改填写，组名为为输出结果显示的文件名称。
　　GTF文件为参考序列的注释文件。
　
***

#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考序列的版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传gtf文件。
　<label id='filter'>FilterReadsWithN：</label>过滤掉含N的reads。
　<label id='seq_len'>SeqLength：</label>序列长度。
　<label id='thread'>Threads：</label>线程数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**

　　1. 正反义链统计图
<div style="text-align:center"><img data-src="1.png" width="200px"  ></img>
</div>
　　
　　2. BlockCounts统计图：cicRNA的外显子数量统计
　　<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>
　　3. CircRNA染色体分布图
　　<div style="text-align:center"><img data-src="3.png" width="350px"  ></img>
</div>
　　4. CircRNA_AllCounts.txt：circRNA的表达量统计
<div style="text-align:center"><img data-src="4.png" width="780px" ></img>
</div>