# <font color="#007979">hapAnalysisSimple</font>

---

&#160; &#160; &#160; &#160;Haplotype Network is an important means of genealogical geography research.Through the haplotype network, we can infer the origin and diffusion history of the population.Haplotype refers to a sequence of nucleic acids that is genetically linked in a haplotype network.Different haplotypes, distinguished by mutations in sequences (commonly known as SNPS)。

**<font color="#007979">Input File</font>**

(1) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;
(3) strainInfo.txt：The text file should have at least two columns of information, the first column is species and the second column is species corresponding to subspecies;


**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='isHetFilter'>isHetFilter：</label>Whether to filter heterozygotes in the input data；
> * &#160; &#160;<label id='isAFFilter'>isAFFilter：</label>Whether to filter low frequency sites；
> * &#160; &#160;<label id='isCorrFilter'>isCorrFilter：</label>Whether to filter linkage sites；
> * &#160; &#160;<label id='fastaFilterProp'>fastaFilterProp：</label>Filter out the sites which the variation rate is less than the set value (ped file is a matrix with one column for each loci, and delete the column if the ratio of two alleles of SNP in a column is greater than 0.95 and less than 0.05). The default value is 0.05.；
> * &#160; &#160;<label id='SNPNum'>SNPNum：</label>Select a specified number of mutations for haplotype analysis, such as when set to 10, the input file is divided into 10 equal parts, and then the first row mutation in each small part is presented to generate the filter result file;
> * &#160; &#160;<label id='MaxNodeNum'>MaxNodeNum：</label>Sets the maximum number of nodes in the haplotype network graph;


**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;Haplotype Network：One circle represents a haplotype, the line between the two circles indicates that the two haplotypes are related (one is a mutation of the other), the short vertical line above the line indicates the number of base substitutions required to get from one haplotype to the haplotype with which it is connected, and a vertical line represents a substitution.The colored circles represent the actual haplotypes we sampled, and the circle size represents the number of haplotypes.The gray circles indicate possible intermediate haplotypes that have not been sampled.A color usually represents a group, such as geographical division, breed division, etc.Here's an example of a haplotype that only exists in one population. In fact, a haplotype often occurs in multiple populations.At this point, a haploid circle is filled with multiple colors and presented as a pie chart.
