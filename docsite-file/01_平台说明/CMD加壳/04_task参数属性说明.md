Task结果文件编写说明
**更新记录：**

| 日期        | 姓名   |  事宜  |
| --------   | -----:  | :----:  |:----:  |:----:  |
| 2016-7-25     | 樊小龙| 做成     |
|2017-3-6      |   樊小龙  |   添加task参数，动态表格，echarts图的配置说  |
| 2017-3-30        |   樊小龙   |  添加cytoscape配置说明	  |


**1. 基本用法：**												
　　我们V1.0版的结果报告主要使用markdown语法.具体语法可见https://www.zybuluo.com/mdeditor#429720
　表格:表格直接使用下面的标签就可以.将data-url参数的值改为您要显示的表格数据文件就可以。
注意路径前缀一般都是以resultReport_getFileContent?fileId=Task@@project_@projectId@/task_@taskId@/开头,后面就是在结果文件夹里能看到的文件夹路径和文件名.
　　th页签中data-field标签值必须和后台数据标题对应.th标签本身的值是表格显示名称.可以不对应。
```
<table id=table1
       data-toggle=table
       data-height=460
       data-pagination=true
       data-search=false
       data-url=resultReport_getFileContent?fileId=Task@@project_@projectId@/task_@taskId@/QualityControl_result/basicStatsAll.xls >
    <thead>
    <tr>
        <th data-field="SampleName">SampleName</th>
        <th data-field="Encoding">Encoding</th>
        <th data-field="TotalReads_Before">TotalReads_Before</th>
        <th data-field="TotalBase_Before">TotalBase_Before</th>
        <th data-field="TotalReads_After">TotalReads_After</th>
        <th data-field="TotalBase_After">TotalBase_After</th>
        <th data-field="ReadsFilter%">ReadsFilter%</th>
        <th data-field="BaseFilter%">BaseFilter%</th>
        <th data-field="GC%_Before">GC%_Before</th>
        <th data-field="GC%_After">GC%_After</th>
    </tr>
    </thead>
</table>
```
　　动态表格。有些表格的列名无法直接确定，需要使用动态表格。动态表格无需添加具体列信息等。只需添加class=dynamic
```
<table class=dynamic  fileId=Task@@project_@projectId@/task_@taskId@/QualityControl_result/basicStatsAll.xls >
</table>
```
　　图片:图片类似表格.只要替换src参数值就行.需要注意的一点是.如果图片(或表格)文件名中有组名等动态字段.需使用@prefix@来代替.src参数的最后面加上&outPrefix=@outPrefix@. 在标签中再加入一个outPrefix="@outPrefix@"标签就可以.
```
<p><image id="image1" class="res-image" src="resultReport_viewImg?fileId=Task@@project_@projectId@/task_@taskId@/QualityControl_result/QCResults/QualityScore_@prefix@_BeforeFilter.png&outPrefix=@outPrefix@" outPrefix="@outPrefix@" /></p>
```
task运行时参数。
　　要显示task运行时设置的参数。比如FastQC要在结果报告显示readsQuality参数的值，使用如下方式填写 @taskData.readsQuality@


**2. echarts图**
　　结果报告中,为了使得展示的效果更绚丽,我们有时需要使用echarts进行动态画图.
基本语法如下:
```
<div class="echarts" type=""  fileId="" xaxis="" yaxis="" eventRow="" filter=“” style="width: 803px;height: 800px;"></div>
```
其中: 
　class 指当前类型,这里画图必须是echarts				
　type 指图的类型.如柱装图,散点图等等.具体如:bar,scatter,heatmap				
　fileId 文件路径,基本语法介绍中已经说明,这里不赘述.				
　xaxis 指图的横坐标取数从哪个列取,这里是列名				
　yaxis 指图的纵坐标取数从哪个列取,这里是列名				
　filter 指图的数据和哪个表格有联动效果				
　eventRow eventRow和filter必须同时使用,eventRow是指fileId中哪一列的数据和表格的数据联动		
　style 这里的宽和高

**各种图所需要的数据文件格式要求**
（1）柱形图（bar）
文件格式要求：文件是类excel格式的txt文本.第一行的列名必须存在x,y轴的列名,eventRow可选非必须
格式示例：
　　cola　　colb	
　　a1　　　b1	
　　a2　　　b2	
　　a3　　　b3	
（2）散点图（scatter）						
文件格式要求：文件是类excel格式的txt文本.第一行的列名必须存在x,y轴的列名,eventRow可选非必须						
格式示例							
　　cola　　colb				
　　a1　　　b1				
　　a2　　　b2				
　　a3　　　b3				
（3）热力图（heatmap）																						
文件格式要求：文件是类excel格式的txt文本.这个图不用指定x,y轴坐标,默认第一行就是横坐标,第一列就是纵坐标.中间就是数值.eventRow无效。																						
																						
格式示例																							
　　　　a1　a2　　a3																			
　　b1　1　　2　　3																			
　　b2　2　　3　　4																			
　　b3　1　　2　　3																			

**3.Demo**
```
# FastQC
# 3.2.1 质量控制（Quality Control）
---
&#160; &#160; &#160; &#160;由于现阶段的技术原因，送样序列在测序前一般会添加上接头，部分测序结果中会包含有接头序列信息。此外一次测序常常产生数亿的结果序列，不可避免的会出现低质量的测序结果，有些序列质量很差，有些会有接头污染，有些甚至会出现其他物种的污染。因此对于序列的过滤以及序列质量的评估就会变得极为重要。
## 3.2.1.1方法
&#160; &#160; &#160; &#160;我们运用Fast-QC (http://www.bioinformatics.babraham.ac.uk/projects/fastqc/) 软件对测序数据的质量进行整体评估。这些图表可以使我们在变异检测之前对测序数据本身有更深入的认识。
## 3.2.1.2 结果
&#160; &#160; &#160; &#160;质量控制分析具体结果获取路径如下：
>* /NovelBio Result/1.QCResults

&#160; &#160; &#160; &#160;表3.2.1-1是所有样本的转录组序列质控统计的结果.图3.2.1-1、图3.2.1-2是样本转录组序列质控统计的结果

<table id=table1
       data-toggle=table
       data-height=460
       data-pagination=true
       data-search=false outPrefix=@outPrefix@
       data-url=resultReport_getFileContent?fileId=Task@@project_@projectId@/task_@taskId@/QualityControl_result/basicStatsAll.xls&outPrefix=@outPrefix@ >
    <thead>
    <tr>
        <th data-field="SampleName">SampleName</th>
        <th data-field="Encoding">Encoding</th>
        <th data-field="TotalReads_Before">TotalReads_Before</th>
        <th data-field="TotalBase_Before">TotalBase_Before</th>
        <th data-field="TotalReads_After">TotalReads_After</th>
        <th data-field="TotalBase_After">TotalBase_After</th>
        <th data-field="ReadsFilter%">ReadsFilter%</th>
        <th data-field="BaseFilter%">BaseFilter%</th>
        <th data-field="GC%_Before">GC%_Before</th>
        <th data-field="GC%_After">GC%_After</th>
    </tr>
    </thead>
</table>
 表3.2.1-1 BasicStatsAll
 <div id="sample">
  <p><image id="image1" class="res-image" src="resultReport_viewImg?fileId=Task@@project_@projectId@/task_@taskId@/QualityControl_result/QCResults/QualityScore_@prefix@_BeforeFilter.png&outPrefix=@outPrefix@" outPrefix="@outPrefix@" /></p>
  <pre><code>图3.2.1-1 QualityScore BeforeFilter<br/>注：横轴表示碱基数或碱基的范围，纵轴表示质量分数值，其中Quality scores大于20表示mapping准确度大于80%。</code></pre>
  <p><image id="image2" class="res-image" src="resultReport_viewImg?fileId=Task@@project_@projectId@/task_@taskId@/QualityControl_result/QCResults/SequenceGCContent_@prefix@_BeforeFilter.png&outPrefix=@outPrefix@" outPrefix="@outPrefix@" /></p>
  <pre><code>图3.2.1-2 SequenceGCContent BeforeFilter<br/>注：横轴表示平均Quality scores，纵轴表示reads.蓝线是理论GC含量分布情况，红线是实际GC含量分布情况，图中实际线条分布跟正态分布接近，结果较好，可以用于下面分析。</code></pre>
 </div>
```
**4.cytoscape**
　　结果报告中,为了更好的展示基因之间的关联关系,我们有时需要使用cytoscape进行结果展示.
基本语法如下:
```
<div class="cytoscape"   fileId="Task@@project_@projectId@/task_@taskId@/QualityControl_result/abc"  style="width: 803px;height: 800px;"></div>
```
其中: 
Class  指当前类型,这里必须是cytoscape
fileId 文件路径,基本语法介绍中已经说明.
　　注意: 1.这里的文件不带文件后缀名.
　　　　　2.后台需要生成两个文件.分别是.node文件描述点信息和.edge描述连线信息.
**数据格式**
　(1)node的数据格式，如下

|﻿id|shape|width	|height	|content|fontSize|	fontWeight|	backgroundColor|textOutlineColor|textBorderWidth|textBorderStyle|textBorderColor|borderColor|borderWidth|color|
| --------   | -----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  | :----:  |
|1|ellipse|40px	|40px| |20px|normal|#ea8a31|blue|1px|solid	|blue|#ea8a31	|2px|#333333|		
|2|ellipse|40px	|40px|  |20px|normal|#ea8a31|blue|1px|solid|blue|#ea8a31|2px	|#333333|		
|3|ellipse|40px	|40px| |20px|normal|#ea8a31|blue|1px|solid|blue	|#ea8a31|2px|	#333333	|	
|4|ellipse|40px	|40px| ddd|20px	|normal	|#ea8a31|blue|1px|solid	|blue|#ea8a31|2px|#333333|		
|5|ellipse|40px	|40px|	ddd|	20px|normal|#ea8a31|blue|1px|solid|blue|#ea8a31	|2px|#333333|

　　第一行是表头，表头下面的是内容，字段直接的分隔符是制表符\t，每一行的列数必须相同，id是必须填写的属性的)
表头字段说明：
　　id:节点的id，每个节点的id都必须不同
　　shape:节点的形状，可以填写的内容有(rectangle|roundrectangle|ellipse|triangle|pentagon|hexagon|heptagon|octagon|star|diamond|vee|rhomboid)
　　width:节点的宽度，例：30px
　　height:节点的高度，例：40px
　　content:节点label的内容
　　fontSize:label的文字大小，例：20px
　　fontWeight:label的文字粗细，例：normal
　　backgroundColor:节点的背景颜色，例：red，blue，#eeffdd，#000000
　　textOutlineColor:label外边框颜色，例：red，blue，#eeffdd，#000000
　　textBorderWidth:文字边框宽度，例：1px
　　textBorderStyle:文字边框样式，例：solid，dotted,dashed
　　textBorderColor:label外边框颜色，例：red，blue，#eeffdd，#000000
　　borderColor:边框颜色	　	　
　　borderWidth:边框宽度	　	　
　　color:label的颜色

(2)edge的数据格式，如下

| ﻿id        | source   | target  |content  |color  |width  |fontSize  |lineColor  |lineStyle  |curveSty  |targetArrowShape  |
| --------   | -----:  | :----:  |:----:  |:----:  |:----:  |:----:  |:----:  |:----:  |:----:  |:----:  |:----:  |:----:  |
| 1     | 1|   2  |    | #333333   | 4px   | 20px   | #fcc694  | solid   | bezier   | triangle  |   
| 2  | 2   |   3 |  | #333333   | 4px   | 20px   | #fcc694  | solid   | bezier   | triangle  |   
|3      |  1   | 3   |  | #333333   | 4px   | 20px   | #fcc694  | solid   | bezier   | triangle  |   

　　第一行是表头，表头下面的是内容，字段直接的分隔符是制表符\t，每一行的列数必须相同，source、target是必须填写的属性，并且必须在点存在的情况下才会创建该连线，如果连线已经存在，新连线不会创建)
表头字段说明：																					
　id:连线id		
　source:起始节点id
　target:终止节点id		
　content:连线label内容	
　color:连线label内容的颜色，例：solid，dotted,dashed		
　width:连线的宽度，例：20px		
　fontSize:label的大小，例：20px		
　lineColor:连线的颜色，例：red，blue，#eeffdd，#000000
　lineStyle:连线的连续类型，例：solid，dotted,dashed	
　curveStyle:连线的形状：bezier		
　targetArrowShape:终止节点处的箭头：triangle													


																						




