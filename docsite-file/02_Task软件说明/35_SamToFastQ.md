# SamToFastQ
　　根据比对结果提取指定序列提取的软件。
****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　在inFileArry处添加bam文件，为比对后的序列文件，输入格式：SAM、BAM；输出格式：fq.gz。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='samToFastQType'>samToFastQType：</label>
　　　AllReads：提取出所有的reads。
　　　MappedReads：提取出所有的比对上参考序列reads。
　　　MappedReadsPairend：提取出双端都比对上参考序列reads。
　　　OneMappedOneNot：提取出一端比对上参考序列，另一端没比对到参考序列的reads。
　　　UnmappedReadsToOneFile：提取出一端没有比对上的reads。
　　　UnmappedReads：提取出所有未比对上参考序列reads，包括一端没比对和双端都没比对上。
　　　UnmappedBothReads：提取都没比对到的参考序列reads。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　结果为提取出所需要的序列文件。
<div style="text-align:center">
<img data-src="1.png" width="550px"  ></img>
</div>
<div style="text-align:center">
<img data-src="2.png" width="600px" ></img>
</div>
