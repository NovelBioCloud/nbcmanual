# <font color="#007979">PiAnalysis</font>


---

&#160; &#160; &#160; &#160;Pi is a parameter to measure the polymorphism of a specific population. It refers to the mean value of nucleotide differences between two randomly selected DNA sequences at each nucleotide site in the same population.The higher the value of PI is, the higher the corresponding subgroup polymorphism.

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160; *Region in chromosome*：select the label, indicating that the analysis is conducted according to the way of input Chromosome region, then the following three parameters need to be filled in, that is, "Chromosome","Start position" and "End position";
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>The chromosome number;
> * &#160; &#160;<label id='start'>Start position：</label>The start position on the chromosome;
> * &#160; &#160;<label id='end'>End position：</label>The end position on the chromosome;
> * &#160; &#160; *Gene locus*：select the label，according to input the Gene location of Upstream and Downstream of the Gene names and distance distance way were analyzed, and the need to fill in the following three parameters, that is: "Gene" , "Upstream" and "Downstream";
> * &#160; &#160;<label id='gene'>Gene：</label>gene name，Such as: Os01g0100100;
> * &#160; &#160;<label id='upstream'>Upstream：</label>The upstream length of the gene(bp);
> * &#160; &#160;<label id='downstream'>Downstream：</label>The downstream length of the gene(bp);
> * &#160; &#160;<label id='dataset'>dataSet：</label>Select the analysis data set,Multiple data sets can be selected;
> * &#160; &#160;<label id='subSp'>subSp：</label>Selective analysis of subspecies,Multiple subspecies can be selected;
> * &#160; &#160;<label id='windowPi'>windowPi：</label> window size,integer；

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;* .windowed.pi，The four columns of information are found in the output file, which are respectively "CHROM", "BIN_START", "BIN_END" and "n_conr".
