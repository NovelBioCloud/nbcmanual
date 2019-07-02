# <font color="#007979">phyloTreeSimple</font>

---

&#160; &#160; &#160; &#160;Phylogenetic tree Is also called evolutionary tree ，it is a branch graph or tree that describes the order of differentiation among groups and is used to represent the evolutionary relationship between groups.According to the physical or genetic characteristics of a population, the similarities or differences between them can be inferred.
&#160; &#160; &#160; &#160;PHYLIP is a comprehensive package of programs for inferring phylogenies. Methods that are available in the package include parsimony, distance matrix, and likelihood methods, including bootstrapping and consensus trees. Data types that can be handled include molecular sequences, gene frequencies, restriction sites and fragments, distance matrices, and discrete characters.

**<font color="#007979">Input File</font>**

(1) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='treeType'>TreeType：</label>build tree methods，The options are NJ, MP, and ML;NJ represents the method based on distance matrix (adjacency method);MP (maximum minimalism);ML maximum likelihood method;
> * &#160; &#160;<label id='seqType'>SeqType：</label>input sequence type, The options are DNA and AA，DNA stands for nucleic acid sequence;AA stands for protein sequence；
> * &#160; &#160;<label id='BootstrapDup'>BootstrapDup：</label>Set the value of bootstrap, which is the number of replicate, to use generally 1000 or 100

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;*.tre: constree file,It can be opened in treeview.
&#160; &#160; &#160; &#160;*.png/pdf: The evolution tree is stored graphically in PNG/PDF format.
