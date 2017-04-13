# GeneAnno
　　烈冰云平台基因注释是利用生物信息学方法和工具，对所测基因的生物学功能进行高通量注释。 
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　　注释进行可视化选择基因注释（Annotation）、基因功能注释（GO）、信号通路注释（KEGGpath）、人类遗传疾病数据库（OMIM）。
　　为了更准确得到基因物种基因注释、GO和Pathway等注释结果，平台已经尽可能多地收录了人类、模式动植物种以及常见物种的基因组及多个版本的数据库，并且完成了数据库间基因ID的相互转换，对多个数据库进行合并去冗余。
　　Go类别: 有三种类别 Biological Process、Cellular Component、Molecular Function。

| GO结构        | GO结构   |  说明 |
| :----:   | :----:  | :----:  |
| Biological Process    | 生物学途径 |   生物学途径是由分子功能有序地组成的，具有多个步骤的一个过程。    |
| Cellular Component        |   细胞组分、定位   |   细胞中的位置指基因产物位于何种细胞器或基因产物组中（如糙面内质网，核或核糖体，蛋白酶体等）   |
| Molecular Function       |    分子功能    |  分子功能描述在分子生物学上的活性，如催化活性或结合活性 |
|All       |    --    |  前三种都输出 |

相关网站：　　
　  http://asia.ensembl.org/info/genome/genebuild/genome_annotation.html
　  https://en.wikipedia.org/wiki/DNA_annotation
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**

　　输入包含基因列的表格即可，通常我们将Expression及DifGene模块的结果文件进行注释。在inFileArray中拖入添加需要注释的文件，输入文件格式：.txt 或.xls; .xlsx　输出文件格式：.txt。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='species'>物种：</label>注释比对物种选择。
　<label id='speciesVersion'>版本：</label>基因组数据库版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　<label id='isBlast'>IsBlast：</label>如需增加物种的注释信息，除了“物种”选项中，还可在此多添加另一个近源物种进行比对从而增加注释信息。
　<label id='blastSpecies'>BlastSpecies：</label>勾选IsBlast时，选择所需比对物种。
　<label id='accIDColumn'>GeneColNum：</label>为表格中需要注释的基因名称列。
　<label id='annoType'>AnnoType：</label>Annotation ：整合了多个数据库信息，及多个版本的数据库 ，在Loc_GeneType中可以进行选择。
　　　　　　　GO：基因功能注释；
　　　　　　　KEGGpath：信号通路注释；
　　　　　　　OMIM：人类遗传疾病数据库注释。
　<label id='goType'>GoType：</label>Biological Process：生物学途径；
　　　　　　Cellular Component：细胞组分、定位；
　　　　　　Molecular Function：分子功能；
　　　　　　All：前三种都输出，推荐使用。
　<label id='isAddLocAndGeneType'>Loc_GeneType：</label>添加选择数据库版本。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1.基因注释列表.anno.gene.xls
　　第一列为id，第二列为基因类型，其余为样品counts或FPKM值， 剩下的AccID,Symbol，KeggID，Description列为序列在数据库的比对结果。
<div style="text-align:center">
<img data-src="1.png" width="780px" ></img>
</div>
