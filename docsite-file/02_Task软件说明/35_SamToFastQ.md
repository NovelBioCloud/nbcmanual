# SamToFastQ
　　根据比对结果提取指定序列提取的软件。
**功能：**
　　从Bam格式文件中提取指定序列，并以FastQ格式文件输出。
**使用软件：**
　　Samtools： samtools是目前广泛使用的处理bam/sam文件的工具。软件官网： http://www.htslib.org/doc/samtools.html
**应用范围：**
　　可从测序得到的reads比对到从参考序列上以后得到的bam文件中，根据不同需求，提取可用于后续不同分析内容的reads序列，如mapped reads或者unmapped reads。
  
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该task的输入数据通常是来源于RnaSeqMap的比对结果Bam文件，也可以是外源的Bam文件。
　　**inFileArray：**sam/bam格式文件，该输入文件的格式为：
```  
  VN	1.5SO	unsorted
software: PN	hisat2software: VN	2.0.1-beta
chr1	248956422
chr2	242193529
E00591:53:hkkvgalxx:8:1220:20364:46824 153 chr1 14646 255 129M = 14646 0 AGAGCAATGGCCCAAGTCTGGGTCTGGGGGGGAAGGTGTCATGGAGCCCCCTACGATTCCCAGTCGTCCTCGTCCTCCTCTGCCTGTGGCTGCTGCGGTGGCGGCAGAGGAGGGATGGAGTCTGACACG FAAAA-<aajajfjffafjja<<jjjjjjjjjjjjfja7j<ajjfjjjjjjjjjjjjfjj<fjjjjfjjajjffjjjjjfjjjjfjfjjjjjjjjjjjjjjjfjjjjjjfjjfjjjjjjjjfjjjjjaj md:z:7c121 xg:i:0 nh:i:1 nm:i:1 xm:i:1 xn:i:0 xo:i:0 as:i:-5 zs:i:-8 yt:z:up
E00591:53:hkkvgalxx:8:1220:20364:46824 69 chr1 14646 0 * = 14646 0 AAGCTGGTCTCCGCACAGTGCTGGTTCCATCACCCCCACCCAGGGAAGCAGGTCTGAGCAGCTTGTCCTGGCTGTGTCCATGTCAGAGCAATGGCCCAAGTCTGGGTCTGGGGGGGAAGGTGTCATGGAG JJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJJFJJJJJJJJJJJJJJJJJJ<fjjjjjjjjjjjj yt:z:up
E00591:53:hkkvgalxx:8:1204:25784:42288 153 chr1 14648 255 128M = 14648 0 AGCAATGGCCCAAGTCTGGGTCTGGGGGGGAAGGTGTCATGGAGCCCCCTACGATTCCCAGTCGTCCTCGTCCTCCTCTGCCTGTGGCTGCTGCGGTGGCGGCAGAGGAGGGATGGAGTCTGACACGC JJFA7-AJJJJAFFFAAJFF<jjjjjfjffjjffjjjjjfjjfjjjajjfjjjjjjjjjjjjjj-jj<jjjjjjjjjjjjjf<jfjjjjjjjjjjjjjjjjjjjjjjjfjjjjjjjjjjjjjjjjjjj md:z:5c122 xg:i:0 nh:i:1 nm:i:1 xm:i:1 xn:i:0 xo:i:0 as:i:-3 zs:i:-6 yt:z:up
``` 
　　Sam文件详细说明请见官方说明文档：http://samtools.github.io/hts-specs/SAMv1.pdf

#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　提取出来的reads序列文件，以FastQ格式存储。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='samToFastQType'>samToFastQType：</label>选择提取Bam中哪种类型的序列，其值有如下选项：
　　　AllReads：提取出所有的reads。
　　　MappedReads：提取出所有的比对上参考序列reads。
　　　MappedReadsPairend：提取出双端都比对上参考序列reads。
　　　OneMappedOneNot：提取出一端比对上参考序列，另一端没比对到参考序列的reads。
　　　UnmappedReadsToOneFile：提取出一端没有比对上的reads，并将reads序列输出到一个结果文件中。
　　　UnmappedReads：提取出所有未比对上参考序列reads，包括一端没比对和双端都没比对上。
　　　UnmappedBothReads：提取都没比对到的参考序列reads。

****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　fq.gz：是提取出来的reads序列文件，以FastQ文件格式存储。如：
<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
</div>
