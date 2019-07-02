# <font color="#007979">GWASPCASimple</font>

---

&#160; &#160; &#160; &#160;The full name of PCA is Principal Component Analysis, it is a common method for analyzing and simplifying data sets. Principal component analysis (pca) is often used to reduce the dimensionality of a dataset, and to preserve the features of the dataset that contribute the most to the variance. For example, when a population is resequenced, the SNP sites obtained are at the level of one million. The PCA analysis process is to extract key information from the information at the level of one million, so that we can effectively distinguish samples with fewer variables (indicators).These extracted information, according to its effect from large to small, we call principal component1 (component1), principal component 2, principal component 3........From the perspective of biology, the process of PCA analysis is the process of information concentration. Similar information will be extracted from the original SNP site information and condensed into new variables PC1, PC2, PC3...The output.Therefore, different principal components may correspond to different biological meanings and produce different clustering and classification effects.

**<font color="#007979">Input File</font>**

(1) strainInfo.txt：The text file should have at least two columns of information, the first column is species and the second column is species corresponding to subspecies;
(2) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(3) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='maf'>Maf: </label>exclude SNPs with minor allele frequency(MAF) less than a specified value, e.g. 0.01。
> * &#160; &#160;<label id='pca'>pca：</label>output the first n (n = 20, by default) eigenvectors (saved as *.eigenvec, plain text file) and all the eigenvalues (saved as *.eigenval, plain text file), which are equivalent to those calculated by the program EIGENSTRAT. The only purpose of this option is to calculate the first m eigenvectors, and subsequently include them as covariates in the model when estimating the variance explained by all the SNPs (see below for the option of estimating the variance explained by genome-wide SNPs). Please find the EIGENSTRAT software if you need more sophisticated principal component analysis of the population structure.
> * &#160; &#160;<label id='subSp'>subsp：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;(a)	*.pca.eigenval，sample name file (no header line; the first m eigenvalues) 
&#160; &#160; &#160; &#160;(b)	*.pca.eigenvec pca result file (no header line; the first m eigenvectors; columns are family ID, individual ID and the first m eigenvectors)

