# <font color="#007979">TajimaDAnalysisSimple</font>

---

&#160; &#160; &#160; &#160;The purpose of Tajima's D test is to distinguish randomly evolving DNA sequences (" neutral ") from those that evolve in non-random processes, including directional selection or balanced selection, population statistics expansion or contraction. Randomly evolving DNA sequences contain mutations that have no effect on fitness or survival.Mutations that evolve randomly are called "neutral," while mutations under selection are "non-neutral."For example, you may find that mutations that cause prenatal death or serious illness are being selected.When looking at the population as a whole, we say that the population frequency of neutral mutations fluctuates randomly through genetic drift (that is, the population percentage in a mutant population changes from one generation to the next, and this percentage may also change to increase or decrease).

**<font color="#007979">Input File</font>**

(1) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='tajimaD'>TajimaD：</label> Outputs Tajima’s D statistic in bins with size of the specified number.

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;The output file has the suffix ".Tajima.D", There are four columns in the file“CHROM、BIN_START、N_SNPS、TajimaD”


Tajima’s D
D | Mathematical explanation |  meaning |  biology interpretation  
-|-|-
D=0 | Theta-Pi=Theta-k(Observed=Expected)，Mean heterozygosity = number of polymorphic sites | Observed variation is similar to expected variation | The population evolves according to the mutation - drift equilibrium.There is no evidence of choice |
D<0 | Theta-Pi<Theta-k(Observed<Expected)，Mean heterozygosity < number of polymorphic sites | Rare alleles are present at high frequencies (in excess of rare alleles) | The most recent selective clearance, the most recent population expansion behind the bottleneck, is linked to the clearance gene |
D>0 | Theta-Pi>Theta-k(Observed>Expected)，Mean heterozygosity > number of polymorphic sites | Rare alleles are present at low frequencies (absence of rare alleles) |Balanced selection, sudden population contraction |

