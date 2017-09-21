# Prokka
　　Prokka，是用Perl实现，一款快速的原核生物基因组注释软件，它产生标准兼容的输出文件以进行进一步分析或者在基因组浏览器中查看。Prokka由澳大利亚莫纳什大学生物信息学平台开发。
　　prokka软件链接：http://www.vicbioinformatics.com/software.prokka.shtml
　　参考文献：Seemann T. Prokka: rapid prokaryotic genome annotation. Bioinformatics. 2014 Jul 15;30(14):2068-9. PMID:24642063

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
inputFile (FASTA):输入序列，fasta格式。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**threadNum:**软件使用时使用线程数。
**Add Genes:**添加Gene注释信息。
**Add mRNA:**添加mRNA注释信息。
**Kingdom:**参考序列界。
**Genus:**参考序列属。
**Species:**参考序列种。
**No rRNA:**不注释rRNA。
**No trna:**不注释tRNA。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　.gff注释结果文件，.txt注释统计结果文件。
　.fna:FASTA file of original input contigs (nucleotide) 
　.faa:FASTA file of translated coding genes (protein) 
　.ffn:FASTA file of all genomic features (nucleotide) 
　.fsa:Contig sequences for submission (nucleotide) 
　.tbl:Feature table for submission 
　.sqn:Sequin editable file for submission 
　.gbk:Genbank file containing sequences and annotations 
　.gff:GFF v3 file containing sequences and annotations 
　.log:Log file of Prokka processing output 
　.txt:Annotation summary statistics 



