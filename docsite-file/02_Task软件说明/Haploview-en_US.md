# <font color="#007979">hapAnalysis</font>

---

&#160; &#160; &#160; &#160;Haplotype Network is an important means of genealogical geography research.Through the haplotype network, we can infer the origin and diffusion history of the population.Haplotype refers to a sequence of nucleic acids that is genetically linked in a haplotype network.Different haplotypes, distinguished by mutations in sequences (commonly known as SNPS)。

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160; Region in chromosome：select the label, indicating that the analysis is conducted according to the way of input Chromosome region, then the following three parameters need to be filled in, that is, "Chromosome","Start position" and "End position";
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>The chromosome number;
> * &#160; &#160;<label id='start'>Start position：</label>The start position on the chromosome;
> * &#160; &#160;<label id='end'>End position：</label>The end position on the chromosome;
> * &#160; &#160;选择IRGSPID：select the label，according to input the Gene location of Upstream and Downstream of the Gene names and distance distance way were analyzed, and the need to fill in the following three parameters, that is: "Gene" , "Upstream" and "Downstream";
> * &#160; &#160;<label id='gene'>Gene：</label>gene name，Such as: Os01g0100100;
> * &#160; &#160;<label id='upstream'>Upstream：</label>The upstream length of the gene(bp);
> * &#160; &#160;<label id='downstream'>Downstream：</label>The downstream length of the gene(bp);
> * &#160; &#160;<label id='dataset'>dataSet：</label>Select the analysis data set,Multiple data sets can be selected;
> * &#160; &#160;<label id='subSp'>subSp：</label>Selective analysis of subspecies,Multiple subspecies can be selected;


**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;Haplotype Network：One circle represents a haplotype, the line between the two circles indicates that the two haplotypes are related (one is a mutation of the other), the short vertical line above the line indicates the number of base substitutions required to get from one haplotype to the haplotype with which it is connected, and a vertical line represents a substitution.The colored circles represent the actual haplotypes we sampled, and the circle size represents the number of haplotypes.The gray circles indicate possible intermediate haplotypes that have not been sampled.A color usually represents a group, such as geographical division, breed division, etc.Here's an example of a haplotype that only exists in one population. In fact, a haplotype often occurs in multiple populations.At this point, a haploid circle is filled with multiple colors and presented as a pie chart.
