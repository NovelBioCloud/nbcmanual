# <font color="#007979">GWASStructure</font>


---

&#160; &#160; &#160; &#160;Population genetic Structure refers to a non-random distribution of genetic variation within a species or population.According to geographical distribution or other criteria, a population can be divided into several subgroups. Different individuals within the same subgroup are highly related, while subgroups are slightly distant from each other.Population structure analysis helps to understand the evolutionary process and to determine the subgroups to which individuals belong through association studies of genotypes and phenotypes.

**<font color="#007979">Input File</font>**

(2) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(3) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='minMAF'>MinMAF：</label>Exclude variants with minor allele frequency lower than a threshold (default 0.01).
> * &#160; &#160;<label id='hwe'>hwe：</label>Exclude variants with Hardy-Weinberg equilibrium exact test p-values below a threshold.
> * &#160; &#160;<label id='geno'>geno：</label>Exclude variants with missing call frequencies greater than a threshold (default 0.1).  (Note that the default threshold is only applied if --geno is invoked without a parameter; when --geno is not invoked, no per-variant missing call frequency ceiling is enforced at all.  Other inclusion/exclusion default thresholds work the same way).
> * &#160; &#160;<label id='maxK'>maxK：</label>Maximum K，K is the number of populations

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;The proportion of each component in each sample
&#160; &#160; &#160; &#160;*.qc.*.Q:Ancestral score
&#160; &#160; &#160; &#160;*.qc.*.P:The estimated allele frequency of an ancestral population