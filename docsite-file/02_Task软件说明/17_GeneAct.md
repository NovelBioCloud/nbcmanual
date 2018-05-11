# GeneAct
　　GeneAct是基因间信号转导网络关系表格，根据KEGG数据库记载的基因间相互调控关系，可得到我们关注的基因之间的相互关系，进一步锁定信号转导通路中的核心调控基因。
  **功能：**
&nbsp;&nbsp;&nbsp;&nbsp;获取基因与基因之间的相互作用关系。
**使用软件：**
&nbsp;&nbsp;&nbsp;&nbsp;**GeneAct：**该软件由NovelBio研发团队编写java代码开发而成。可根据数据库中的记录，整理出基因之间的相互关系列表。
 **应用范围**
	&nbsp;&nbsp;&nbsp;&nbsp;通常用于对感兴趣基因集（如显著性差异表达基因等）的分析，获取基因与基因之间的相互作用关系，结果文件可作为cytoscape的输入文件，用来绘制基因关系网络图。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是所关注的基因列表。
**inFileName：**基因名称列表，通常输入文件是显著性差异表达基因列表，如caseVScon.diff.txt。输入文件格式如下所示：
<div style="text-align:center">
	<img data-src="input.png" width="100px" ></img>
</div>
注意：
1.	输入文件中必须要有一行title信息，对于title名称无特殊要求。
2.	输入文件中至少要有一列基因名称信息，其他信息可有可无。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
&nbsp;&nbsp;&nbsp;&nbsp;基因之间存在的相互作用关系列表（*Gene_Act_Net.gene.xls），通常作为cytoscape的输入文件来绘制基因关系网络图。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**物种：**选择参考基因组物种。
**AccID列号：**表格中基因名称所在列数。
**isBlast：**如需增加基因间相互调控关系，可在此添加另一个近源物种进行比对从而增加信息。
**blast物种：**选择isBlast的物种。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
 **\*Gene_Act_Net.gene.xls：**基因关系列表，如：
<div style="text-align:center">
	<img data-src="output1.png" width="300px" ></img>
</div>
表中各列信息解释如下：
<div style="text-align:center">
	<img data-src="output2.png" width="300px" ></img>
</div>
其中“relation”表示意义，说明如下：
<div style="text-align:center">
	<img data-src="output3.png" width="300px" ></img>
</div>
基因关系详细解析请见官方文档：http://www.kegg.jp/kegg/xml/docs/
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 详细解释**
&nbsp;&nbsp;&nbsp;&nbsp;在原核生物中，执行相同功能或参与同一生物反应的基因往往连锁在一起，形成操纵子，这些基因在进化到真核生物时易形成融合基因或功能复合体。因此，通过分析基因在基因组序列上的分布信息就可判断出基因间的相互作用，通过比较基因组，可以识别出基因间的转录调控关系，构建基因调控网络。同时，基因调控网络主要是指基因在表达水平上相互调节形成的复杂网络，DNA结合的转录因子以及转录因子识别结合的顺式作用元件在基因调控网络中就起着相当重要的作用。于是，很多研究人员开始研究转录因子和相应的顺式作用元件之间的识别，以此建立基因调控网络。