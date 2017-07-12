# SamtoolsVCFCombine
　　Samtools软件Call Variant生成的vcf进行合并。
　　官网：Samtools:http://www.htslib.org/
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　InputVCF(.gz) (VCF)：输入CallVariant生成的vcf文件。

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
**VCF合并方式：**将样本结果合并。
　　　　　　　none：不排序，输出多条记录。
　　　　　　　snps：按照SNP记录进行合并。
　　　　　　　indels:按照indel记录合并。
　　　　　　　both：按照SNP和indel分别合并。
　　　　　　　all：都合并在一起。
　　　　　　　id:按照ID号合并。
**Memory（Mb）：**运行时，使用线程数。
**ContainerNumber：**运行时，使用Container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center">
<img data-src="1.png" width="700px"  ></img>
</div>
