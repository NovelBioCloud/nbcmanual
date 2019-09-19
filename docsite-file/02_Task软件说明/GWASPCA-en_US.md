# <font color="#007979">GWASPCA</font>


---

&#160; &#160; &#160; &#160;The full name of PCA is Principal Component Analysis, it is a common method for analyzing and simplifying data sets. Principal component analysis (pca) is often used to reduce the dimensionality of a dataset, and to preserve the features of the dataset that contribute the most to the variance. For example, when a population is resequenced, the SNP sites obtained are at the level of one million. The PCA analysis process is to extract key information from the information at the level of one million, so that we can effectively distinguish samples with fewer variables (indicators).These extracted information, according to its effect from large to small, we call principal component1 (component1), principal component 2, principal component 3........From the perspective of biology, the process of PCA analysis is the process of information concentration. Similar information will be extracted from the original SNP site information and condensed into new variables PC1, PC2, PC3...The output.Therefore, different principal components may correspond to different biological meanings and produce different clustering and classification effects.


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
> * &#160; &#160;<label id='maf'>Maf: </label>exclude SNPs with minor allele frequency(MAF) less than a specified value, e.g. 0.01。
> * &#160; &#160;<label id='pca'>pca：</label>output the first n (n = 20, by default) eigenvectors (saved as *.eigenvec, plain text file) and all the eigenvalues (saved as *.eigenval, plain text file), which are equivalent to those calculated by the program EIGENSTRAT. The only purpose of this option is to calculate the first m eigenvectors, and subsequently include them as covariates in the model when estimating the variance explained by all the SNPs (see below for the option of estimating the variance explained by genome-wide SNPs). Please find the EIGENSTRAT software if you need more sophisticated principal component analysis of the population structure.

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;(a)	*.pca.eigenval，sample name file (no header line; the first m eigenvalues) 
&#160; &#160; &#160; &#160;(b)	*.pca.eigenvec pca result file (no header line; the first m eigenvectors; columns are family ID, individual ID and the first m eigenvectors)
