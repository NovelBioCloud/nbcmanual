# GetCircSeq

　　根据circRNA位置信息从参考基因组序列中提取circRNA序列信息，可用于后续实验验证。
**功能：**
　		提取circRNA序列。
**使用软件**
　　	**GetSequence：**NovelBio编写java代码实现根据不同需求提取指定序列的功能。

 **应用范围**
根据circRNA位置信息，提取circRNA序列，用于后续实验验证。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件<span>**
该Task的输入数据是circRNA位置信息列表，文件格式为txt。 
**Circ Table：**circRNA信息列表，如下表所示：

| AccID  |  CHROM  |start|end|strand|GeneName|
| -------- |  :----: | :----:  |  :----: | :----: | :----: |
| chr10_18872995\_18843501_-29494-MYO9A | chr10 |18843500 |18872995|-|MYO9A|
| chr10_3255970\_3255552_+418-KCNN2   | chr10   |3255551|3255970|+|KCNN2|
| chr14_26985681_26966261_-19420-TOX   | chr14   |26966260|26985681|-|TOX|
| chr24_33072771_33061241_-11530-TTC39C   | chr24   |33061240|33072771|-|TTC39C|
| chr24_43500238_43498192_-2046-SPIRE1   | chr24   |43498191|43500238|-|SPIRE1|
| chr3_90418916_90401663_-17253-PRKAA2   | chr3  |90401662|90418916|-|PRKAA2|
| chr3_94280136_94255871_-24265-SCP2   | chr3   |94255870|94280136|-|SCP2|
**注意：**
1.表格中必须要有一行title ,对于title名称无特殊要求；
2.输入表格中这六列信息，即circRNA名称、circRNA所在的染色体信息、circRNA在染色体上的起始位置、circRNA在染色体上的终止位置是必须要有的。
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件<span>**
提取到的circRNA序列文件，以fasta格式存储。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置<span>**
**物种：**选择参考基因组物种。
**版本：**参考序列的版本。
**数据库类型：**同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件。
**CircNameCol：**在输入文件中，Circ Id所在的列数。
**ChrCol：**在输入文件中，染色体所在列数。
**StartCol：**在输入文件中，circRNA起始位点的所在列数。
**EndCol：**在输入文件中，circRNA终止位点的所在列数。
**StrandCol：**在输入文件中，链特异性正反链所在列数。
**HostGeneCol：**在输入文件中，HostGene所在列数。
**containerNumber：**软件运行使用容器（container）数量。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件<span>**
　\*.circRNA.fa：提取到的序列文件，以fasta文件格式存储。
　\*.type.xls：在输入文件表格中添加“CircType”和“SeqLength”两列信息。

