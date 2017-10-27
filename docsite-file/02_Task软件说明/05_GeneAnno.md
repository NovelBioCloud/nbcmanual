# GeneAnno
　　基因注释是利用生物信息学方法和工具，对所输入的基因进行生物学功能注释。
**功能：**
　　对基因多方面的注释，其中包括添加基因的accession number（即Genbank的收录号，也是查询号）、Gene Symbol（基因名称）、Gene description（基因描述）、GO功能注释、KEGG代谢通路注释以及OMIM注释（仅用于人类）。
**使用软件：**
　1.Blast2Go：Blast2GO是一套集成的比较成熟的序列功能注释和分析平台， 可以整合NR， Swiss-prot 以及Interproscan的结果对序列进行功能Gene Ontology（GO）的功能分类。
　　软件官网：https://www.blast2go.com/
　2.TopGO：topGO是一个Bioconductor的包，用于GO term富集分析以及结果展示。
　　软件官网：https://bioconductor.org/packages/release/bioc/html/topGO.html
 **应用范围：**
　　需要了解更多功能信息的基因，仅需要提供基因名称即可。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于SamAndRPKM的基因表达值列表文件，也可以是外源基因列表文件。
　　inputData：基因列表，仅含有基因名称一列信息即可，该输入文件的格式为：
<div style="text-align:center"><img data-src="2.png" width="100px" ></img></div>

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　注释后的结果文件（txt），该task会在原输入文件列表后添加一列或者多列注释信息，如果某基因行没有添加注释信息，则表示该基因没有相应（所选类型，即GO、KEGGpath、OMIM）的注释。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**

　<label id='species'>物种：</label>选择参考基因组物种。
　<label id='speciesVersion'>版本：</label>参考基因组的版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
　<label id='accIDColumn'>GeneColNum：</label>为表格中需要注释的基因名称列。
　<label id='annoType'>AnnoType：</label>Annotation ：基因AccID（accession number），基因名称（Gene symbol）、KeggID和基因描述（Gene description）信息。
　　　　　　　GO：基因功能注释；
　　　　　　　KEGGpath：信号通路注释；
　　　　　　　OMIM：人类遗传疾病数据库注释，仅用于人的基因注释。
　<label id='goType'>GoType：</label>GO注释结构分为三大类，该选项用于选择注释GO的哪一大类，其选项有如下四个：
 　　　　　　Biological Process：生物学途径；
　　　　　　Cellular Component：细胞组分、定位；
　　　　　　Molecular Function：分子功能；
　　　　　　All：前三种都输出，推荐使用。
　<label id='isAddLocAndGeneType'>Loc_GeneType：</label>添加选择数据库版本。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1)“.anno.gene.txt”：
 　　当参数“AnnoType”选中“Annotation”时，会产生该类结果文件。此结果文件会在原输入文件的之后添加如下信息：基因AccID（accession number），基因名称（Gene symbol）、KeggID和基因描述（Gene description）信息。
　2)“.go_Biological Process.gene.txt”:
 　　当参数“AnnoType”选中“GO”并且参数“GoType”选中“Biological Process”时，task会在GO的生物学途径（Biological Process）层面对基因进行GO注释。最终结果文件会在原输入文件的之后添加如下信息：基因AccID（accession number）或者基因名称（Gene symbol），(当该基因名称注释到的话显示基因名称，否则显示基因AccID)、GO ID和GOTerm（GO 条目）的信息。
　3)“.go_Cellular Component.gene.txt”：
 　　当参数“AnnoType”选中“GO”并且参数“GoType”选中“Cellular Component”时，task会在GO的细胞组分（Cellular Component）层面对基因进行GO注释。最终结果文件会在原输入文件的之后添加如下信息：基因AccID（accession number）或者基因名称（Gene symbol），(当该基因名称注释到的话显示基因名称，否则显示基因AccID)、GO ID和GOTerm（GO 条目）的信息。
　4)“.go_Molecular Function.gene.txt”:
 　　当参数“AnnoType”选中“GO”并且参数“GoType”选中“Molecular Function”时，task会在GO的分子功能（Molecular Function）层面对基因进行GO注释。最终结果文件会在原输入文件的之后添加如下信息：基因AccID（accession number）或者基因名称（Gene symbol），(当该基因名称注释到的话显示基因名称，否则显示基因AccID)、GO ID和GOTerm（GO 条目）的信息。
　5)“.go_All.gene.txt”：
 　　当参数“AnnoType”选中“GO”并且参数“GoType”选中“All”时，task会在GO的三个层面（BP、CC、MF）对基因进行GO注释。最终结果文件会在原输入文件的之后添加如下信息：基因AccID（accession number）或者基因名称（Gene symbol），(当该基因名称注释到的话显示基因名称，否则显示基因AccID)、GO ID和GOTerm（GO 条目）的信息。
　6)“.path.gene.txt”：
 　　当参数“AnnoType”选中“KEGGpath”时，会产生该类结果文件。此结果文件会在原输入文件的之后添加如下信息：基因名称（Gene symbol）、KeggID和Kegg Term。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　注释进行可视化选择基因注释（Annotation）、基因功能注释（GO）、信号通路注释（KEGGpath）、人类遗传疾病数据库（OMIM）。
　　为了更准确得到基因物种基因注释、GO和Pathway等注释结果，平台已经尽可能多地收录了人类、模式动植物种以及常见物种的基因组及多个版本的数据库，并且完成了数据库间基因ID的相互转换，对多个数据库进行合并去冗余。
　　Go类别: 有三种类别 Biological Process、Cellular Component、Molecular Function。

| GO结构        | GO结构   |  说明 |
| :----:   | :----:  | :----:  |
| Biological Process    | 生物学途径 |   生物学途径是由分子功能有序地组成的，具有多个步骤的一个过程。    |
| Cellular Component        |   细胞组分、定位   |   细胞中的位置指基因产物位于何种细胞器或基因产物组中（如糙面内质网，核或核糖体，蛋白酶体等）   |
| Molecular Function       |    分子功能    |  分子功能描述在分子生物学上的活性，如催化活性或结合活性 |
|All       |    --    |  前三种都输出 |

相关网站：　http://asia.ensembl.org/info/genome/genebuild/genome_annotation.html
　　　　　　https://en.wikipedia.org/wiki/DNA_annotation

