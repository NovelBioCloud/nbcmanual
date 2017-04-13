# FreeBayes
　　FreeBayes是一个Bayesian 基因变异检测软件，可以检测到小多态性，如SNP（single-nucleotide polymorphisms）、Indel（insertions and deletions）、MNPs（multi-nucleotide polymorphisms）和complex events（composite insertion and substitution events）。

　　官网：https://github.com/ekg/freebayes

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
　<label id='species'>物种：</label>注释比对物种选择。
　<label id='speciesVersion'>版本：</label>基因组数据库版本。
　<label id='dbType'>数据库类型：</label>同一版本的基因组数据，在不同数据库中记录的信息不同，选择不同数据库gtf文件，也可以选择为我们上传的gtf文件。
　<label id='pvar'>polymorphism probability：</label>该位点存在polymorphism 可能性阈值。
　<label id='theta'>mutation rate：</label>突变率。
　<label id='ploidy'>ploidy：</label>需要分析的物种是几倍体，默认为：2。
　<label id='nosnps'>Ignore SNP alleles：</label>是否忽略SNP alleles。
　<label id='noindel'>Ignore indel alleles：</label>是否忽略 indel alleles。
　<label id='nocomplex'>Ignore comples events：</label>是否忽略 comples events(composite insertion and substitution events即复杂的插入和置换事件)。

**高级设置：**
　<label id='maxComGap'>max complex gap：</label>最大的complex gap。
　<label id='minRepeatSize'>min repeat size：</label>最小重复序列的长度大小。
　<label id='usedupreads'>use duplicate reads：</label>是否使用重复reads。
　<label id='minMapQua'>min mapping quality：</label>检测变异过程中使用的reads的最小mapping 质量值。
　<label id='minCoverage'>minCoverage：</label>位点的最小覆盖数。
　<label id='repGenoLikeMax'>report genotype likelihood max：</label>是否在基因分型过程中使用最大似然估计。
　<label id='genotypeMaxIter'>genotypeing max iterations：</label>在基因分型过程中迭代的次数不超过该阈值，默认为：25。
　<label id='postInteLimit'>posterior integration limits：</label>整合所有包括比多余N个样品第M个最好的数据可能值的基因型组合，默认值：1,3。
　<label id='exclUnobserGeno'>exclude unobserved genotypes：</label>是否跳过没有reads支持的样品。
　<label id='useMapQua'>use mapping quality：</label>是否在计算data likelihoods的时候使用等位基因的比对质量值。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
　　.vcf ： 输出的结果文件，以VCF格式存储。
<div style="text-align:center">
<img data-src="1.png" width="800px"  ></img>
</div>

<div style="text-align:center">
<img data-src="2.png" width="600px" ></img>
</div>
