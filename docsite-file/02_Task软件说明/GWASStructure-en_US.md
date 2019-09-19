# <font color="#007979">GWASStructure</font>


---

&#160; &#160; &#160; &#160;Population genetic Structure refers to a non-random distribution of genetic variation within a species or population.According to geographical distribution or other criteria, a population can be divided into several subgroups. Different individuals within the same subgroup are highly related, while subgroups are slightly distant from each other.Population structure analysis helps to understand the evolutionary process and to determine the subgroups to which individuals belong through association studies of genotypes and phenotypes.

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160; Region in chromosome：select the label, indicating that the analysis is conducted according to the way of input Chromosome region, then the following three parameters need to be filled in, that is, "Chromosome","Start position" and "End position";
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>The chromosome number;
> * &#160; &#160;<label id='start'>Start position：</label>The start position on the chromosome;
> * &#160; &#160;<label id='end'>End position：</label>The end position on the chromosome;
> * &#160; &#160;Gene locus：select the label，according to input the Gene location of Upstream and Downstream of the Gene names and distance distance way were analyzed, and the need to fill in the following three parameters, that is: "Gene" , "Upstream" and "Downstream";
> * &#160; &#160;<label id='gene'>Gene：</label>gene name，Such as: Os01g0100100;
> * &#160; &#160;<label id='upstream'>Upstream：</label>The upstream length of the gene(bp);
> * &#160; &#160;<label id='downstream'>Downstream：</label>The downstream length of the gene(bp);
> * &#160; &#160;<label id='dataset'>dataSet：</label>Select the analysis data set,Multiple data sets can be selected;
> * &#160; &#160;<label id='subSp'>subSp：</label>Selective analysis of subspecies,Multiple subspecies can be selected;
> * &#160; &#160;<label id='minMAF'>MinMAF：</label>Exclude variants with minor allele frequency lower than a threshold (default 0.01).
> * &#160; &#160;<label id='hwe'>hwe：</label>Exclude variants with Hardy-Weinberg equilibrium exact test p-values below a threshold.
> * &#160; &#160;<label id='geno'>geno：</label>Exclude variants with missing call frequencies greater than a threshold (default 0.1).  (Note that the default threshold is only applied if --geno is invoked without a parameter; when --geno is not invoked, no per-variant missing call frequency ceiling is enforced at all.  Other inclusion/exclusion default thresholds work the same way).
> * &#160; &#160;<label id='maxK'>maxK：</label>Maximum K，K is the number of populations


**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;The proportion of each component in each sample
&#160; &#160; &#160; &#160;*.qc.*.Q:Ancestral score
&#160; &#160; &#160; &#160;*.qc.*.P:The estimated allele frequency of an ancestral population