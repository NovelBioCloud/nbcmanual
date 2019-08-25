# **﻿ScBubblePlot**

　 
### **工具介绍**

　  
#### **功能概述**

ScBubblePlot（气泡图），是将CellPhoneDB分析结果进行可视化的工具。导入CellPhoneDB的结果文件可以生成展示细胞类群之间的通讯关系的气泡图。本工具也可手动输入自定义数据，进行定制化分析。

#### **工具特点**

ScBubblePlot利用R语言中的ggplot2绘图包实现图片绘制。
ScBubblePlot通过横纵坐标轴及气泡面积颜色4个变量，对数据进行多角度描述。

　 
### **分析流程**

　  
**上游工具**：CellPhoneDB等
**连接示例**：
 

<div style="text-align:center">
<img data-src="1.png" height="175px" ></img>
</div>
　 
### **输入文件**

　  
#### **输入文件1 ColorData**
气泡颜色数据文件
说明：
本参数用于导入以气泡颜色展示的数据。
需要导入上游工具CellPhoneDB的结果文件BubblePolt/Means_for_Plot.txt。
本输入文件是必传文件。

　  
#### **输入文件2 SizeData**
气泡面积数据文件
说明：
本参数用于导入以气泡面积展示的数据。
需要导入上游工具CellPhoneDB的结果文件BubblePolt/Pvalues_for_Plot.txt。
本输入文件是必传文件。

　  
#### **输入文件3 XlabList**
X轴标签列表文件
说明：
本参数用于导入以X轴表示的细胞类群互作对列表。
可通过规则文件批量导入上游工具CellPhoneDB的结果文件/BubblePolt/XXX.cluster.txt。 
本输入文件是必传文件。

　  
#### **输入文件4 YlabList**
Y轴标签列表文件
说明：
本参数用于导入以Y轴表示的基因互作对列表。
可通过规则文件批量导入上游工具CellPhoneDB的结果文件/BubblePolt/XXX.gene.txt。
本输入文件是必传文件。

　 
### **参数设置**

<label id='attrCol'> </label>
#### **运行参数 AttrCol**
绘图关键数据所在列
参数说明：
根据CellPhoneDB结果文件的规则，默认第2列，即基因互作对名称所在列。必需参数。

<label id='sizeLabel'> </label>
#### **运行参数 SizeLabel**
面积标签
参数说明：
图例中气泡面积的字符串标签

<label id='isSizeNeedLog'> </label>
#### **运行参数 isSizeValueNeedLog**
面积数值是否需要对数变换
参数说明：
气泡面积数值以10为底取负对数，以便绘图。

<label id='minSizeValue'> </label>
#### **运行参数 minSizeValue**
面积数值下限
参数说明：
小于本参数的面积值会被转换成这个值，以便进行对数运算。

<label id='colorLabel'> </label>
#### **运行参数 ColorLabel**
颜色标签
参数说明：
图例中气泡颜色的字符串标签

<label id='plotColor'> </label>
#### **运行参数 plotColor**
绘图颜色
参数说明：
绘图时，非空数值使用的颜色。
默认为darkblue,blue,yellow,red，表示颜色从深蓝到红色渐变。支持自定义颜色。


<label id='naColor'> </label>
#### **运行参数 NAValueColor**
空值颜色
参数说明：
绘图时，空值使用的颜色。默认为gray。设置为white时，实际为透明效果。支持自定义颜色。

<label id='isColorNeedNorm'> </label>
#### **运行参数 isColorValueNeedNorm**
颜色值是否需要标化
参数说明：
气泡颜色值标化处理，以便绘图。

<label id='cut_chara_x'> </label>
#### **运行参数 x轴切割符**
参数说明：
X轴标签列表文件中，分隔细胞互作对的分隔符。

<label id='cut_chara_y'> </label>
#### **运行参数 y轴切割符**
参数说明：
Y轴标签列表文件中，分隔基因互作对的分隔符。

<label id='width'> </label>
#### **运行参数 PlotWidth**
绘图宽度
参数说明：
根据需要设置绘图宽度

<label id='height'> </label>
#### **运行参数 PlotHeight**
绘图高度
参数说明：
根据需要设置绘图高度

<label id='thread'> </label>
#### **运行参数 Threads**
线程数
参数说明：
设置线程数

<label id='memory'> </label>
#### **运行参数 Memory(MB)**
内存（MB）
参数说明：
设置内存大小

　 
### **结果解读**

　  
#### **结果文件结构**
├─ **0_Ligand.BubblePlot.png/pdf/svg **（cluster 0作为配体时，png/pdf/svg格式气泡图）
├─ **0_Receptor.BubblePlot.png/pdf/svg **（cluster 0作为受体时，png/pdf/svg格式气泡图）
├─ ...
1个细胞类群为1组，每组6个文件

#### **BubblePlot气泡图**
<div style="text-align:center">
<img data-src="2.png" height="600px" ></img>
</div>
说明：
横轴表示细胞类群互作对，蓝色表示配体细胞，红色表示受体细胞。
纵轴表示基因互作对，蓝色表示配体基因，红色表示受体基因。
气泡表示对应坐标轴上一对细胞中一对基因的互作关系。
气泡颜色表示互作关系强度，越偏向红色表示作用强度越强，偏向蓝色表示越弱。
气泡大小表示P值以10为底取负对数，越大表示关系越显著。
气泡图可以描述不同细胞类群之间的通讯关系，例如，第1列中蓝色气泡表示Cancer细胞中FAS基因表达的配体蛋白，对CD8效应T细胞中FASLG基因表达的受体蛋白产生影响，这个互作关系的P值小于0.001，相比图中其它关系，作用强度较强。

文档更新：2019.08.25 技术部 李亚当
文档整理：2019.04.30 技术部 李亚当
