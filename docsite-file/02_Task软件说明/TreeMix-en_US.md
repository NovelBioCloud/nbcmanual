# <font color="#007979">TreeMix</font>

---

&#160; &#160; &#160; &#160;Gene flow, also known as migration pressure or gene migration, refers to the introduction of new genetic material from one population of one species to another, thus changing the composition of the "gene pool" of the population.Introducing new alleles into the population through gene exchange is a very important source of genetic variation, which affects the genetic diversity of the population and produces new character combinations.That is, for some reason, a part of a population with a certain gene frequency will migrate to another population with a different gene frequency, and hybridize and settle down, which will cause the gene frequency of the population to change.
TreeMix is a program for the inference of patterns of population splitting and mixing from genome-wide allele frequency data. If given a set of allele frequencies from a number of populations, it will return the maximum likelihood tree for the set of populations, and optionally attempt to infer a number of admixture events.

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160; Region in chromosome：select the label, indicating that the analysis is conducted according to the way of input Chromosome region, then the following three parameters need to be filled in, that is, "Chromosome","Start position" and "End position";
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>The chromosome number;
> * &#160; &#160;<label id='start'>Start position：</label>The start position on the chromosome;
> * &#160; &#160;<label id='end'>End position：</label>The end position on the chromosome;
> * &#160; &#160;选择IRGSPID：select the label，according to input the Gene location of Upstream and Downstream of the Gene names and distance distance way were analyzed, and the need to fill in the following three parameters, that is: "Gene" , "Upstream" and "Downstream";
> * &#160; &#160;<label id='gene'>Gene：</label>gene name,Such as: Os01g0100100;
> * &#160; &#160;<label id='upstream'>Upstream：</label>The upstream length of the gene(bp);
> * &#160; &#160;<label id='downstream'>Downstream：</label>The downstream length of the gene(bp);
> * &#160; &#160;<label id='dataset'>dataSet：</label>Select the analysis data set,Multiple data sets can be selected;
> * &#160; &#160;<label id='subSp'>subSp：</label>Selective analysis of subspecies,Multiple subspecies can be selected;
> * &#160; &#160;<label id='disequilibrium'>Disequilibrium：</label>To account for the fact that nearby SNPs are not independent, group them together in windows of size n SNPs by using the -k flag. The order of SNPs in the input file is assumed to be their order 3 in the genome. We recommend using a value of n that far exceeds the known extent of LD in the organism in question (this will depend, of course, on the SNP density).。
> * &#160; &#160;<label id='migration'>Migration：</label>If you wish to allow for a number of migration events in the tree, use the -m flag, followed by the number of allowed migration events.


**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;1. *.stem.cov.gz. The covariance matrix  between populations estimated from the data
&#160; &#160; &#160; &#160;2. *.stem.covse.gz. The standard errors for each entry in the covariance matrix.
&#160; &#160; &#160; &#160;3. *.stem.modelcov.gz. The fitted covariance according to the model
&#160; &#160; &#160; &#160;4. *.stem.treeout.gz. The fitted tree model and migration events
&#160; &#160; &#160; &#160;5. *.stem.vertices.gz.This and the following file (outstem.edges.gz) contain the internal structure of the inferred graph. Modifying these files will cause issues if you try to read the graph back in, so we recommend against this.
&#160; &#160; &#160; &#160;6. *.stem.edges.gz. The tree inferred from the data is in outstem.treeout.gz. The first line of this file is the Newick format ML tree, and the remaining lines contain the migration edges. The first column for these lines is the weight on the edge, followed (optionally) by the jackknife estimate of the weight, the jackknife estimate of the standard error, and the p-values. Then come the subtree below the origin of the migration edge, and the subtree below the destination of the migration edge.
&#160; &#160; &#160; &#160;7. * .treemix.png，The phylogenetic tree is shown as a PNG file
&#160; &#160; &#160; &#160;8. * .treemix.pdf，The phylogenetic tree is shown as a PDF file
