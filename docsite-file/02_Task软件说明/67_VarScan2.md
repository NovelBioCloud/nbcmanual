# Varscan2
　　Varscan2可用来检测来自肿瘤-正常对的外显子组数据中的体细胞突变和拷贝数改变（copy number alterations，CNAs）。该算法同时从两个样品中读取数据；一种启发式和统计算法检测序列变异，并通过体细胞状态（生殖细胞系、体细胞或杂合性丢失）分类它们；标准化read深度的一项比较阐明了相对拷贝数变化。
**功能：**
　1） 单个样本/多个样本（群体样本、如体细胞变异）共有或独有的种系变异；
　2） 识别肿瘤-正常样品对中的体细胞突变、拷贝数变异可LOH（Loss of Heterozygosity，杂合性缺失）；
　3） 鉴定家庭三人组中的生殖细胞系变异，denovo突变和孟德尔遗传错误；
**使用软件：**
　　Varscan2：由华盛顿大学基因组研究所开发，是一个基于Java，用于检测插入/缺失的(SNPs and InDels)变异预测软件工具。Varscan2特别针对肿瘤外显子测序检测体细胞突变和CNV。
　　软件官网： http://varscan.sourceforge.net/index.html

**应用范围:**
　　适用于靶向测序、外显子和全基因重测序数据。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
该Task的输入数据来源于Samtools模块的PileUp结果文件。
　  InputData：PileUp文件，使用Samtools的mpileup命令，生成的bcf文件。该文件每一行代表了参考序列中某一个碱基位点的比对结果，如：
<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>
各列信息解释如下：
　　1	参考序列名
　　2	位置
　　3	参考碱基
　　4	比对上的reads数
　　5	比对情况
　　6	比对上的碱基的质量
其中第5列比较复杂，解释为：
　　 ‘.’代表与参考序列正链匹配
　　 ‘,’代表与参考序列负链匹配
　　 ‘ATCGN’代表在正链上的不匹配
　　 ‘atcgn’代表在负链上的不匹配
　　 ‘`*`’代表模糊碱基
　　 ‘^’代表匹配的碱基是一个read的开始；’^'后面紧跟的ascii码减去33代表比对质量；这两个符号修饰的是后面的碱基，其后紧跟的碱基(.,ATCGatcgNn)代表该read的第一个碱基
　　 ‘$’代表一个read的结束，该符号修饰的是其前面的碱基
　　　正则式’\+[0-9]+[ACGTNacgtn]+’代表在该位点后插入的碱基；比如上例中在scaffold_1的2847后插入了9个长度的碱基acggtgaag。表明此处极可能是indel
　　 　正则式’-[0-9]+[ACGTNacgtn]+’代表在该位点后缺失的碱基
　**Pileup 文件详细说明**，请见官方文档： http://samtools.sourceforge.net/pileup.shtml

**<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　检测的SNP和indel结果文件，以VCF文件格式存储。
<hr/>**<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　**物种：**选择参考基因组物种。
　**版本：**参考序列的版本。
　<label id='minCoverage'>minCoverage：</label>reads的最小覆盖度，默认值为8。
　<label id='minCovNor'>minCovNor：</label>正常组（对照组）的最小覆盖度，默认值为8。
　<label id='minCovTum'>minCovTum：</label>患病组（实验组）的最小覆盖度，默认值为6。
　<label id='minVarFreq'>minVarFeq：</label>杂合子的最小变异频率，默认值为0.01。
　<label id='minFreForHom'>minFreForHom：</label>纯合子的最小变异率，默认值为0.75。
　<label id='pValue'>pValue：</label>杂合子检测突变的最低p阈值，0.99。
　<label id='pValueSom'>pValueSom：</label>检测突变的p阈值，默认值为0.05。
　**文件对比：**加入对比两个组份。选择实验组与对照组比较。
　　　　　group1Array：选择对比组1；
　　　　　group2Array：选择对比组2；
　　　　　outFileArray：输出名称。
 <hr/> **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　1) indel.vcf：检测到的所有indels结果VCF文件，如：
<div style="text-align:center"><img data-src="3.png" width="600px" ></img>
</div>
 表中各列信息解释如下：
 <div style="text-align:center"><img data-src="4.png" width="500px" ></img>
</div>
VCF的详细说明请见官方文档：
　　　　　http://samtools.github.io/hts-specs/VCFv4.2.pdf
　　　　　https://en.wikipedia.org/wiki/Variant_Call_Format
　2) snp.vcf：检测到的所有snp结果VCF文件，文件格式详情同上。
　3) somatic_all.vcf：检测到的所有的体细胞突变VCF文件，文件格式详情同上。
　4) somatic_indel.vcf：检测到的所有的somatic indel文件，文件格式详情同上。
　5) somatic_snp.vcf：检测到的所有的somatic snp文件，文件格式详情同上。

***
#### **<span class="glyphicon glyphicon-paperclip" aria-hidden="true" style="color:#C47451"></span></i><span style="color:#C47451">  补充说明**
　　**SNP：**全称Single Nucleotide Polymorphisms，单核苷酸多态性，主要是指在基因组水平上由单个核苷酸的变异所引起的DNA序列多态性。包括转换、颠换、缺失和插入，形成的遗传标记，其数量很多，多态性丰富。它是人类可遗传的变异中最常见的一种。占所有已知多态性的90%以上。SNP在人类基因组中广泛存在，平均每500～1000个碱基对中就有1个，估计其总数可达300万个甚至更多。 
　　**Indel：**insertion-deletion，插入缺失标记，指的是两种样本中在全基因组中的差异，相对另一个样本而言（通常是参考基因组序列），有一定数量的核苷酸插入或缺失(Jander et al., 2002)。
&nbsp;
参考文献：
Koboldt DC, Zhang Q, Larson DE, Shen D, McLellan MD, Lin L, Miller CA, Mardis ER, Ding L, Wilson RK. VarScan 2: somatic mutation and copy number alteration discovery in cancer by exome sequencing. Genome Res. 2012;22:568–576. [PMC free article] [PubMed]


 
 
 
 