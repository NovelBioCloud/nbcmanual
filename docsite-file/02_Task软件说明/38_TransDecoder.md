# TransDecoder
　　TransDecoder识别转录本序列中候选的编码区域，诸如那些将RNA-Seq数据用Trinity从头组装或者使用Tophat和Cufflinks将RNA-Seq比对到基因组中构建的转录本。

****
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**
　TransDecoder 基于以下标准识别可能的编码序列：
　　•	在转录本序列中需要能够找到一个（满足）最小（限定）长度的ORF。
　　•	对数似然数得分大于0。（与GeneID软件计算得到的得分相类似）。
　　•	第一阅读框的对数似然数打分同其它5个阅读框比较为最大值时。
　　•	如果候选的ORF完全被包含在其它候选ORF的框架内，那么报告最长的ORF。否则，一个单独的转录本会得到多个ORF的报告。（考虑到有操纵子、嵌合体等情况）。
　　•	作为可选项，预测出的多肽在Pfam domain库中存在比对分值高于得分阈值之上的。
该软件主要由Broad Institute的Brian Haas和Commonwealth Scientific and Industrial Research Organisation的Alexie Papanicolaou维护。
　　软件官网：https://transdecoder.github.io

****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　inputFile：将左侧FASTA格式文件拖入到inputFile中，输入文件格式为FASTA。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='isBlastToUniprot'>isBlastToUniprot：</label>是否通过blast到Uniprot数据库来识别共同的蛋白质结构域。
　<label id='isBlastToPfam'>isBlastToPfam：</label>是否通过blast到pfam来搜索已知蛋白的同源序列来识别ORF。
　<label id='minProteinLen'>minProteinLen：</label>最小的蛋白质长度。
　<label id='minOrfLen'>minOrfLen：</label>最小的ORF长度。
　<label id='cpuNum'>cpu数量：</label>分析时使用的CPU数量。
　<label id='retainBestORF'>retainBestORF：</label>是否保留最好的ORF。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　(1) **transdecoder.pep**：最终候选ORF的蛋白质序列；所有较长ORF中的较短的候选序列已被移除。
　(2) **transdecoder.cds **：最终候选ORF的编码区的核酸序列。
　(3) **transdecoder.gff3**：最终被选中的ORF在目的转录本中的位置
　(4) **transdecoder.bed**：用来描述ORF位置的bed格式文件，最好用GenomeView或IGV来查看。
