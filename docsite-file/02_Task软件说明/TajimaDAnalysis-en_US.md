# <font color="#007979">TajimaDAnalysis</font>

---

&#160; &#160; &#160; &#160;The purpose of Tajima's D test is to distinguish randomly evolving DNA sequences (" neutral ") from those that evolve in non-random processes, including directional selection or balanced selection, population statistics expansion or contraction. Randomly evolving DNA sequences contain mutations that have no effect on fitness or survival.Mutations that evolve randomly are called "neutral," while mutations under selection are "non-neutral."For example, you may find that mutations that cause prenatal death or serious illness are being selected.When looking at the population as a whole, we say that the population frequency of neutral mutations fluctuates randomly through genetic drift (that is, the population percentage in a mutant population changes from one generation to the next, and this percentage may also change to increase or decrease).

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
> * &#160; &#160;<label id='tajimaD'>TajimaD：</label> Outputs Tajima’s D statistic in bins with size of the specified number.

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;The output file has the suffix ".Tajima.D", There are four columns in the file“CHROM、BIN_START、N_SNPS、TajimaD”


Tajima’s D
D | Mathematical explanation |  meaning |  biology interpretation  
-|-|-
D=0 | Theta-Pi=Theta-k(Observed=Expected)，Mean heterozygosity = number of polymorphic sites | Observed variation is similar to expected variation | The population evolves according to the mutation - drift equilibrium.There is no evidence of choice |
D<0 | Theta-Pi<Theta-k(Observed<Expected)，Mean heterozygosity < number of polymorphic sites | Rare alleles are present at high frequencies (in excess of rare alleles) | The most recent selective clearance, the most recent population expansion behind the bottleneck, is linked to the clearance gene |
D>0 | Theta-Pi>Theta-k(Observed>Expected)，Mean heterozygosity > number of polymorphic sites | Rare alleles are present at low frequencies (absence of rare alleles) |Balanced selection, sudden population contraction |

