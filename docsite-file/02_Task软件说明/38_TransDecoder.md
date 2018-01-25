# TransDecoder
　　某些情况下，需要对转录本序列中候选的编码区域进行识别，诸如将RNA-Seq数据用Trinity从头组装或者使用Tophat和Cufflinks将RNA-Seq数据比对到基因组中所构建的转录本。
**功能：**
　　识别转录本序列中候选的编码区域。
**使用软件：**
　　TransDecoder：是Trinity下游分析的重要组件。
　　软件官网： https://transdecoder.github.io/

 **应用范围**
　　通常是对RNA denovo组装得到的序列文件进行编码区域预测分析。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据来源于Trinity组装结果\*.fasta文件。对于多个样本的组装，通常是将组装后的结果进行聚类，然后对聚类后的序列文件，再进行编码区域的预测分析。
　　**inputFile：**基因序列文件，文件格式为fasta。对于输入多个文件，task会首先将多个文件进行合并，合并成一个文件后，再进行预测。 
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　编码区域的cds序列和蛋白序列，以及对编码区域进行注释的gff3格式文件。

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
　1) \*. transdecoder.pep：最终候选ORF的蛋白质序列。
　2) \*. transdecoder.cds：最终候选ORF的编码区的核酸序列。
　3) \*. transdecoder.gff3：编码区域注释的gff3格式文件。
　4) \*. transdecoder.bed：用来描述ORF位置的bed格式文件，可用GenomeView或IGV来查看。