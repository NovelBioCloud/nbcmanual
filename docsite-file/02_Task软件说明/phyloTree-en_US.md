# <font color="#007979">phyloTree</font>

---

&#160; &#160; &#160; &#160;Phylogenetic tree Is also called evolutionary tree ，it is a branch graph or tree that describes the order of differentiation among groups and is used to represent the evolutionary relationship between groups.According to the physical or genetic characteristics of a population, the similarities or differences between them can be inferred.
&#160; &#160; &#160; &#160;PHYLIP is a comprehensive package of programs for inferring phylogenies. Methods that are available in the package include parsimony, distance matrix, and likelihood methods, including bootstrapping and consensus trees. Data types that can be handled include molecular sequences, gene frequencies, restriction sites and fragments, distance matrices, and discrete characters.

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
> * &#160; &#160;<label id='treeType'>TreeType：</label>build tree methods，The options are NJ, MP, and ML;NJ represents the method based on distance matrix (adjacency method);MP (maximum minimalism);ML maximum likelihood method;
> * &#160; &#160;<label id='seqType'>SeqType：</label>input sequence type, The options are DNA and AA，DNA stands for nucleic acid sequence;AA stands for protein sequence；
> * &#160; &#160;<label id='BootstrapDup'>BootstrapDup：</label>Set the value of bootstrap, which is the number of replicate, to use generally 1000 or 100

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;*.tre: constree file,It can be opened in treeview.
&#160; &#160; &#160; &#160;*.png/pdf: The evolution tree is stored graphically in PNG/PDF format.
