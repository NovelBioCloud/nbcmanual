# PICRUSt
　　PICRUSt为基于16s rRNA 序列可以预测功能的软件。原理基于已测细菌基因组的16S rRNA全长序列，推断它们的共同祖先的基因功能谱，对Greengenes数据库中其它未测物种的基因功能谱进行推断，构建古菌和细菌域全谱系的基因功能预测谱，最后，将测序得到的菌群组成“映射”到数据库中，对菌群代谢功能进行预测。
　　软件官网：http://picrust.github.io/picrust/
**** 
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
InputBiom：输入BIOM格式的OTU文件，.biom。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
Prediction_Type：ko  cog  rfam,可以多选。
containerNumber：软件运行时，所使用container数。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**