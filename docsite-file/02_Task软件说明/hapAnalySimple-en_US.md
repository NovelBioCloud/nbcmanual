# <font color="#007979">hapAnalysisSimple</font>

---

&#160; &#160; &#160; &#160;Haplotype Network is an important means of genealogical geography research.Through the haplotype network, we can infer the origin and diffusion history of the population.Haplotype refers to a sequence of nucleic acids that is genetically linked in a haplotype network.Different haplotypes, distinguished by mutations in sequences (commonly known as SNPS)。

**<font color="#007979">Input File</font>**

(1) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;
(3) strainInfo.txt：The text file should have at least three columns of information, the first column is species and the second column is species corresponding to subspecies,the third column is the country of the species;


**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='SNPNum'>SNPNum：</label>Select a specified number of mutations for haplotype analysis, such as when set to 10, the input file is divided into 10 equal parts, and then the first row mutation in each small part is presented to generate the filter result file;
> * &#160; &#160;<label id='MaxNodeNum'>MaxNodeNum：</label>Sets the maximum number of nodes in the haplotype network graph;


**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;Haplotype Network：One circle represents a haplotype, the line between the two circles indicates that the two haplotypes are related (one is a mutation of the other), the short vertical line above the line indicates the number of base substitutions required to get from one haplotype to the haplotype with which it is connected, and a vertical line represents a substitution.The colored circles represent the actual haplotypes we sampled, and the circle size represents the number of haplotypes.The gray circles indicate possible intermediate haplotypes that have not been sampled.A color usually represents a group, such as geographical division, breed division, etc.Here's an example of a haplotype that only exists in one population. In fact, a haplotype often occurs in multiple populations.At this point, a haploid circle is filled with multiple colors and presented as a pie chart.
