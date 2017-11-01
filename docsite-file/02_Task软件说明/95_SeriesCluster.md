# SeriesCluster
　　趋势分析(STC, Series Test of Cluster)就是发现基因表达的趋势特征，将相同变化特征的基因集中在一种变化趋势中，从而找到实验变化过程中最具有代表性的基因群，揭示生物样本在变化过程中所特有的规律。
**功能：**
　　可以根据对相似表达谱的基因进行聚类，从聚类中已知功能的基因去推断同类中其他基因的功能。
**使用软件：**
　　STEM：一个短时间序列基因表达数据分析工具，由java语言编写而成，主要是用于对短时间序列的基因表达数据(少于或等于8个时间点)进行聚类、比较和可视化。
	软件官网： http://www.cs.cmu.edu/~jernst/stem/

**应用范围：**
　　STEM可以识别显著性的时间表达谱，精确、直观地筛选出与这些表达谱相关的基因，并比较不同条件下这些基因的表达趋势。通过评价基因表达趋势与样本性状变化的关联程度，分离出与样本变化无关的基因群，提取并醒目标记出主流基因表达趋势，按照由显著性水平由小到大顺序对重要的、主流的基因表达趋势进行排列。
  
  ***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据来通常来源于认为筛选的感兴趣的基因集。 
　　**InputFile：**基因表达值列表，包含基因名称和基因在各个样本中的counts数即可，输入文件一般是感兴趣的基因集，基因集的筛选方法通常为，如果三个时间点的话，就是两两比较，得到三组差异基因，三组差异基因去取并集，并集基因进行趋势分析。如：
  <div style="text-align:center"><img data-src="1.png" width="300px" ></img>
</div>
  
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　趋势分析结果图(png)以及每个基因所在的趋势列表。
  
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**NormalizedType：** 标准化数据的方式，在基因表达时间序列与模型表达趋势匹配之前，需要将时间序列转换为从0开始，这种转换有三种方法：
　　1. Log normalize data 将向量转化为<div style="text-align:center"><img data-src="2.png" width="250px" </img></div>
　　2. Normalize data将向量转化为<div style="text-align:center"><img data-src="3.png" width="250px" </img></div>
　　3. No normalization/add 0 ，不标准化，直接加0（0，v0，v1，v2，…vn）
  
　**Change_based_on：**选择基因过滤的方法，其选项有：
　　　Maximum-Minimum：两点差值的最大绝对值的基因会被过滤掉。
　　　Difference From 0：如果基因从时间点0到任意时间点的表达变化值小于最小绝对表达变化值参数所设定的值，则会被过滤掉。
　**MaxProfile：**可被选择的最大的趋势模型数。
　**Maximum_Unit_Change_between_Time_Points：**用来指定时间点之间趋势模型可以改变的一个单位的最大数量。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　	1) ProfilePlot：每个趋势图都存放在这个文件夹中，如：
  <div style="text-align:center"><img data-src="4.png" width="350px" </img></div>
　　2) all_genetable.txt：基因所在趋势的列表
　　3) all_profiletable.txt：每个趋势以及趋势模型信息
　　4) Non.png：表明趋势中基因数量的趋势总表，如：
<div style="text-align:center"><img data-src="5.png" width="350px" </img></div>
　　5) Number.png：表明趋势中基因数量的趋势总表，用红色和绿色表示有显著变化的趋势，筛选标准默认为p-value<0.05，其中红色表示显著向上的趋势，绿色表示显著向下的趋势，如：
<div style="text-align:center"><img data-src="6.png" width="350px" </img></div>
　　6) Sig.png：表明趋势中p-value的趋势总表，用红色和绿色表示有显著变化的趋势，筛选标准默认为p-value<0.05，其中红色表示显著向上的趋势，绿色表示显著向下的趋势，如：
<div style="text-align:center"><img data-src="7.png" width="350px" </img></div>

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**趋势分析：**在实验的设计中，我们经常需要了解基因随时间，温度，药物浓度等变化的表达趋势。当生物体按照一定顺序发生变化或者受到外界环境刺激（如受到不同浓度的化学药物诱导）时，基因表达变化也会呈现趋势特征。从生物学的角度，表达模式相似的基因可能具有共同的特征，比如同时被某种基因调控，或者具有相似的生物功能，或者有共同的细胞起源等。尽管有许多意外的情况存在，大量功能相关的基因的确在相关的一组条件下有非常相似的表达谱，特别是被共同的转录因子调控的基因，或者产物构成同一蛋白复合体，或者参与相同的调控路径。

参考文献：
Ernst J, Bar-Joseph Z. STEM: a tool for the analysis of short time series gene expression data. BMC Bioinformatics. 2006;7:191. 




