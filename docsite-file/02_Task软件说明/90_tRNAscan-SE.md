# tRNAscan-SE
　　tRNAscan-SE 能在基因组水平上进行tRNA扫描。该软件实际上是一个perl 脚本，整合了tRNAscan、EufindRNA 和Cove 这3个独立的tRNA检测软件。tRNAscan-SE 首先调用 tRNAscan和EufindRNA鉴定基因组序列中 tRNA区域，然后调用Cove进行验证。这样既保证了前者的sensitivities， 又保证了后者较低的假阳性概率，同时在搜索速度上提升了很多。
　　tRNAscan-SE 的网页版：http://lowelab.ucsc.edu/tRNAscan-SE/。

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　inputFile (FASTA)：输入FASTA格式文件。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　Type：需要分析的物种类型。
　containerNumber：软件运行时所使用的container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>
　　结果中可以看到会输出三个文件，分别是tRNA.out、tRNA.stats、tRNA.ss。tRNA.out文件里面会输出我们的测试序列中tRNA的位置信息。
  
  
