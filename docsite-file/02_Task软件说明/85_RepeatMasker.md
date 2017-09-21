# RepeatMasker
　　RepeatMasker是一款广泛应用于基因鉴定、分类和mask repetitive elements,包括低复杂度序列和散布重复序列。RepeatMasker通过将数据库，如Repbase中已知的重复序列与输入的基因组序列比对来搜素重复序列。一款专门用于基因组重复序列识别的软件，适用于所有物种。是做基因组、非编码RNA的必备软件。
　　软件官网：http://www.repeatmasker.org/

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
inputFile (FASTA)：输入序列，fasta格式。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
ThreadNum：软件使用时，使用线程数。
Species：参考序列物种。
Slow Search：快速检索，低于默认5%到10%敏感度，默认速度的3倍到4倍。
Quick Search：急速检索，低于默认10%的敏感度。
No simple repeats mark：不标记简单重复序列。
Olny mask simple repeats：指标记简单重复序列。
Not mask small RNA：不标记小RNA或者假基因。
Skips Bacterial Insertion：跳过细菌插入的序列。
Complete Lower Case：把序列改为小写。
Repetitive Lowercase：把重复序列改为小写。
Masked Repeat with Xs：重复区域用X代替。
containerNumber：软件使用时，使用container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
assembly.fa.masked：用N代替的分析序列。
assembly.fa.out.html：统计信息。
<div style="text-align:center"><img data-src="1.png" width="500px" ></img></div>
