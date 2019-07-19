# <font color="#007979">GWASStructure</font>


---

&#160; &#160; &#160; &#160;群体遗传结构(Structure)指遗传变异在物种或群体中的一种非随机分布。按照地理分布或其他标准可将一个群体分为若干亚群，处于同一亚群内的不同个体亲缘关系较高，而亚群与亚群之间则亲缘关系稍远。群体结构分析有助于理解进化过程，并且可以通过基因型和表型的关联研究确定个体所属的亚群。

**<font color="#007979">输入参数</font>**

> * &#160; &#160; Region in chromosome：选中该标签，表示按照输入染色体区域的方式进行分析，此时需要填写以下三个参数，即：“Chromosome”、“Start position”、“End position”；
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>染色体号；
> * &#160; &#160;<label id='start'>Start position：</label>起始位置；
> * &#160; &#160;<label id='end'>End position：</label>终止位置；
> * &#160; &#160;Gene locus：：选中该标签，表示按照输入基因名称以及距离该基因上下游位置距离的方式进行分析，此时需要填写以下三个参数，即：“Gene”、“Upstream”、“Downstream”；
> * &#160; &#160;<label id='gene'>Gene：</label>基因名称，如：Os01g0100100；
> * &#160; &#160;<label id='upstream'>Upstream：</label>基因上游长度；
> * &#160; &#160;<label id='downstream'>Downstream：</label>基因下游长度；
> * &#160; &#160;<label id='dataset'>dataSet：</label>选择分析数据集，可选择多个数据集；
> * &#160; &#160;<label id='subSp'>subSp：</label>选择分析亚种，可以选择多个亚种；
> * &#160; &#160;<label id='minMAF'>MinMAF：</label>排除等位基因频率小于该阈值的位点，默认为0.01
> * &#160; &#160;<label id='hwe'>hwe：</label>排除哈迪-温伯格平衡准确检验p-value值小于该设置阈值的位点；
> * &#160; &#160;<label id='geno'>geno：</label>排除缺失率大于该设定阈值的位点，默认为0.1，（注意只有在—geno没有参数的情况下才应用该默认的阈值；当—geno没有调用时，将不强制限制使用每个突变缺失率上限，其他inclusion/exclusion默认阈值的工作方式也是一样的）
maxK：最大K值，K指群体数量

**<font color="#007979">结果文件</font>**

&#160; &#160; &#160; &#160;每种成分在每个样本所占的比例
&#160; &#160; &#160; &#160;*.qc.*.Q   祖先的分数
&#160; &#160; &#160; &#160;*.qc.*.P推断出的祖先群体的等位基因频率