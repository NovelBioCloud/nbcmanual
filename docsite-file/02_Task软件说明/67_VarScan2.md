# Varscan2
　　Varscan2由华盛顿大学基因组研究所开发，是一个基于Java，用于检测插入/缺失的(SNPs and InDels)变异预测软件工具。Varscan2特别针对肿瘤外显子测序检测体细胞突变和CNV。
　　官网：http://dkoboldt.github.io/varscan/

****
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　通常文件来源于SamToBam模块的PileUp结果文件。分别选取好Case组与Control组的PileUp文件，输入文件格式：pileup.gz；输出文件格式：vcf。

****
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
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
 
****
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　recal_indel.vcf、recal_snp.vcf为得到对应的SNP与InDel的txt、vcf结果。
　　somatic_all.vcf、somatic_indel.vcf、somatic_snp.vcf为针对肿瘤外显子测序检测体细胞突变。
<div style="text-align:center"><img data-src="1.png" width="５00px"  ></img></div>
 