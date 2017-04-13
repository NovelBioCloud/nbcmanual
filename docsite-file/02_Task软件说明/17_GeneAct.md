# GeneAct
　　GeneAct是基因间信号转导网络关系表格，根据KEGG数据库记载基因间相互调控关系，可得到客户关注基因与基因之间的相互关系，进一步锁定基因信息号转导的核心调控基因。
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　　在原核生物中，执行相同功能或参与同一生物反应的基因往往连锁在一起，形成操纵子，这些基因在进化到真核生物时易形成融合基因或功能复合体。因此，通过分析基因在基因组序列上的分布信息就可判断出基因间的相互作用，通过比较基因组，可以识别出基因间的转录调控关系，构建基因调控网络。同时，基因调控网络主要是指基因在表达水平上相互调节形成的复杂网络，DNA结合的转录因子以及转录因子识别结合的顺式作用元件在基因调控网络中就起着相当重要的作用。于是，很多研究人员开始研究转录因子和相应的顺式作用元件对的识别，以此建立基因调控网络。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　选取关注的基因表格，即可得到基因间信号转导关系表格。将需要做基因间信号转导的关系表拖入右侧inFileName栏中，输入文件格式：.txt 或.xls; .xlsx 输出文件格式：. xls。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='accIDColNum'>AccID列号：</label>基因列所在表格列数。
　<label id='isBlast'>isBlast：</label>如需增加物种基因间相互调控关系，除了“物种”选项中，还可在此多添加另一个近源物种进行比对从而增加信息。
　<label id='blastSpecies'>blast物种：</label>选择isBlast的物种。
***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　GeneActRelation.Gene_Act_Net.gene.xls
<div style="text-align:center"><img data-src="1.png" width="500px"  ></img>
</div>
　说明：
　　source:上游基因。
　　target:下游基因。
　　detail Relation:上下游基因之间的关系。
　　Pathway:基因间pathway描述。