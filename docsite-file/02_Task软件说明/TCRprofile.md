# **TCRprofile**

　 
### **工具介绍**

　  
#### **功能概述**

TCRprofile（TCR基本信息），是烈冰生物开发的对TCR测序结果进行数据可视化的工具。主要功能包括：VDJC基因使用频率分析，VJ基因组合频率分析，CDR3序列长度分布统计，Clonotype数量占比统计，以及Clonotype扩增分析。

　 
### **流程搭建**

　  
**上游工具**：CellRangerVDJ
**连接示例**：
<div style="text-align:center">
<img data-src="1.png" width="150px" ></img>
</div>


　 
### **文件传入**

　  
#### **输入文件 ContigAnnotationFilePath(required)**
重叠群注释文件路径（csv文件）（必传文件）
参数说明：
重叠群注释文件filtered_contig_annotations.csv来自上游工具CellRangerVDJ。
注：
此处不仅支持传入文件，同时支持传入文件所在以样本名命名的文件夹（推荐操作）。

　 
### **参数设置**

<label id='HeatmapColors'> </label>
#### **运行参数 HeatmapColors**
热图颜色
参数说明：
本参数为VJ基因组合频率分析结果热图使用颜色。默认颜色lightyellow,#3399BB,#2255AA，由浅到深表示数值由小增大。

<label id='StackPlotColors'> </label>
#### **运行参数 StackPlotColors**
堆叠图颜色
参数说明：
本参数为CDR3序列长度分布统计结果堆叠图使用颜色。默认颜色orange,gold,green3,lightgreen,blue,lightblue,purple,lavender,red,pink,darkblue,cyan4,grey表示CDR3序列上频率由高到底的V基因。
注：
此处颜色数量要比参数StackPlotVGeneNum的值多出一个。其中，最后的灰色表示其它所有基因。

<label id='RingPlotColors'> </label>
#### **运行参数 RingPlotColors**
环形图颜色
参数说明：
本参数为Clonotype扩增分析结果环形图使用颜色。默认颜色white,#FC8237,#5456A3,red表示扩增程度由低到高的Clonotype。

<label id='StackPlotVGeneNum'> </label>
#### **运行参数 StackPlotVGeneNum**
堆叠图V基因数量
参数说明：
本参数为CDR3序列长度分布统计结果堆叠图中被展示V基因的数量。默认值12表示显示出现频率最高的12个V基因。

<label id='ClonotypeNum'> </label>
#### **运行参数 ClonotypeNum**
Clonotype数量
参数说明：
本参数为Clonotype数量占比统计结果柱形图中显示的高频Clonotype数量上限，默认50。

<label id='ClonotypeCutoff'> </label>
#### **运行参数 ClonotypeCutoff**
Clonotype截断值
参数说明：
本参数为Clonotype扩增分析结果环形图中Clonotype按照频率高低分组的截断值。默认1,2,5,30表示Clonotype扩增程度按照出现频率由低到高分成四组（Unique，2-4,5-29,≥30）。

<label id='ThreadNum'> </label>
#### **运行参数 ThreadNum**
线程数
参数说明：
设置线程数，默认1线程

<label id='memory'> </label>
#### **运行参数 Memory(MB)**
内存（MB）
参数说明：
设置内存大小，默认1000MB

　 
### **结果解读**

　  
#### **结果文件结构**
├─ <font color=#00BFFF>**AllSample **</font>(多样本合并分析结果文件路径)
┊　 ├─ **Clonotype_frequency.BarPlot.png/pdf **(Clonotype数量占比柱形图) 
┊　 ├─ **Clonotype_frequency.BubblePlot.png/pdf **(Clonotype数量占比气泡图) 
┊　 ├─ **Clonotype_Expansion.png/pdf **(Clonotype扩增分析环形图)
┊　 ├─ ...
├─ <font color=#00BFFF>**SampleName1 **</font>(样本1分析结果路径)
┊　 ├─ **CellNum_of_V/JGene.tsv **(V/J基因使用频率表)
┊　 ├─ **V/JGene_usage.png/pdf **(V/J基因使用频率柱形图)
┊　 ├─ **Combination_of_VJgene.tsv **(VJ基因组合频率矩阵表)
┊　 ├─ **Combination_of_VJgene.png/pdf **(VJ基因组合频率热图)
┊　 ├─ **CDR3_Length_Info.tsv **(CDR3序列长度信息表)
┊　 ├─ **CDR3_length_TRA/TRB.png/pdf **(序列长度分布统计堆叠图)
┊　 ├─ **CellNum_of_clonotype.tsv **(Clonotype数量占比统计表)
┊　 ├─ **Clonotype_frequency.png/pdf **(Clonotype数量占比柱形图)
┊　 ├─ **Clonotype_Expansion_Analysis.tsv **(Clonotype扩增分析统计表)
┊　 ├─ **Clonotype_Expansion.png/pdf **(Clonotype扩增分析环形图)
┊　 ├─ ...
├─ <font color=#00BFFF>**SampleName2**</font>
┊　 ├─ ...

　  
#### **V/J基因使用频率柱形图**
<div style="text-align:center">
<img data-src="2.png" width="600px" ></img>
</div>
说明： 
横轴标签表示V/J基因名称。
纵轴标签表示CellBarcode频率。
本图描述V/J基因在样本中的频率分布。

色块从蓝到红渐变表示基因集合在不同的细胞类群中激活程度从低到高。

　  
#### **V/J基因使用频率表**
<div style="text-align:center">
<img data-src="3.png" height="px" ></img>
</div>
说明：
表中两列的含义分别是：V/J基因名称和表达这个基因的细胞数量。


　  
#### **VJ基因组合频率热图**
<div style="text-align:center">
<img data-src="4.png" width="600px" ></img>
</div>
说明：
横轴标签表示V基因。
纵轴标签表示J基因。
色块从黄到蓝渐变表示不同VJ基因组合在群体中的出现频率由低到高。

　  
#### **VJ基因组合频率矩阵表**
<div style="text-align:center">
<img data-src="5.png" height="px" ></img>
</div>
说明：
表中首行和首列分别是V基因名称和J基因名称，矩阵中数值表示表达对应V基因J基因组合的细胞数量。


　  
#### **CDR3序列长度分布统计堆叠图**
<div style="text-align:center">
<img data-src="6.png" width="600px" ></img>
</div>
说明：
图中，横轴表示TCRα/β链的CDR3碱基序列的长度。纵轴表示不同长度的CDR3序列在样本中的占比。堆叠图中不同的颜色自上至下表示样本中出现频率最高的12个V基因，最下方灰色表示其它所有V基因。

　  
#### **CDR3序列长度信息表**
<div style="text-align:center">
<img data-src="7.png" height="px" ></img>
</div>
说明：
表头含义分别是：TCR链名称，V基因名称，CDR3序列长度，以及细胞数量。每一行表示α/β链中，含有特定V基因，并且有特定长度的CDR3序列，对应的细胞数量。


　  
#### **Clonotype数量占比柱形图**
<div style="text-align:center">
<img data-src="8.png" width="600px" ></img>
</div>
说明：
横轴标签表示ClonotypeID。
纵轴标签表示CellBarcode频率。
本图描述Clonotype在样本中的频率分布。

　  
#### **Clonotype数量占比气泡图**
<div style="text-align:center">
<img data-src="9.png" width="600px" ></img>
</div>
说明：
横轴标签表示样本名。
纵轴标签表示ClonotypeID。
气泡大小与颜色表示频率的高低，气泡越大颜色越深表示频率越高，反之越低。

　  
#### **Clonotype数量占比统计表**
<div style="text-align:center">
<img data-src="10.png" height="px" ></img>
</div>
说明：
表头含义分别是：Clonotype名称，细胞数量。每一行表示一个Clonotype对应的细胞数量。

　  
#### **Clonotype扩增分析环形图**
<div style="text-align:center">
<img data-src="11.png" width="600px" ></img>
</div>
说明：
图中，不同颜色的扇区对应不同扩增程度的Clonotype，扇区的大小取决于组成这个扇区的Clonotype的对应的细胞数量的总和。

　  
#### **Clonotype扩增分析统计表**
<div style="text-align:center">
<img data-src="12.png" height="px" ></img>
</div>
说明：
表头含义分别是：Clonotype扩增程度，Clonotype数量。
　  
文档更新 2020.04.14 技术部 李亚当
文档整理 2020.04.14 技术部 李亚当
