# <font color="#007979">XP-CLR</font>

---

&#160; &#160; &#160; &#160;Selective sweep: reduction or elimination of differences between nucleotides in adjacent DNA at a mutated site due to recent strong positive natural selection.
&#160; &#160; &#160; &#160;The XP-CLR package implements a composite likelihood method for detecting selective sweeps via the differentiation of two populations.

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
> * &#160; &#160;<label id='mode'>mode：</label>Select species classification,Subspecies or species ;
> * &#160; &#160;<label id='subSp'>ObjectPop：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；
> * &#160; &#160;<label id='subSp'>RefPop：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；
> * &#160; &#160;<label id='corrLevel'>corrLevel：</label>the range of its value is on [0 1]. If it is on (0 1], this corrLevel value is used as a criterion in the weighted composite likelihood ratio test. If two SNPs are highly correlated (r2 > corrLevel), their contribution to XPCLR is down-weighted. If corrLevel is set to be 0, XPCLR is estimated un-weightedly.

**<font color="#007979">Result</font>**
&#160; &#160; &#160; &#160;\*.XPCLR.xpclr.txt，The file contains six columns of information:“chr#”、“grid#”、“#ofSNPs_in_window”、“physical_pos”、“genetic_pos”、“XPCLR_score”.    
