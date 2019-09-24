# <font color="#007979">FstAnalysis</font>

---

&#160; &#160; &#160; &#160;inter-population Fixation index(FST)，A indicatrix of whether a population's median gene frequency deviates from the ratio of genetic balance theory, to study the degree of differentiation between different groups. Its value is from 0 to 1,0 means that the two groups are undifferentiated, Its members are completely random; 1 represents the complete differentiation of the two groups, which forms species isolation and has no common diversity.
&#160; &#160; &#160; &#160;VCFtools can also calculate Fst statistics between individuals of different populations. It is an estimate calculated in accordance to Weir and Cockerham’s 1984 paper. The user must supply text files that contain lists of individuals (one per line) that are members of each population. The function will work with multiple populations if multiple --weir-fst-pop arguments are used.

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160; *Region in chromosome*：select the label, indicating that the analysis is conducted according to the way of input Chromosome region, then the following three parameters need to be filled in, that is, "Chromosome","Start position" and "End position";
> * &#160; &#160;<label id='chromsome'>Chromosome：</label>The chromosome number;
> * &#160; &#160;<label id='start'>Start position：</label>The start position on the chromosome;
> * &#160; &#160;<label id='end'>End position：</label>The end position on the chromosome;
> * &#160; &#160;*Gene locus*：select the label，according to input the Gene location of Upstream and Downstream of the Gene names and distance distance way were analyzed, and the need to fill in the following three parameters, that is: "Gene" , "Upstream" and "Downstream";
> * &#160; &#160;<label id='gene'>Gene：</label>gene name，Such as: Os01g0100100;
> * &#160; &#160;<label id='upstream'>Upstream：</label>The upstream length of the gene(bp);
> * &#160; &#160;<label id='downstream'>Downstream：</label>The downstream length of the gene(bp);
> * &#160; &#160;<label id='dataset'>dataSet：</label>Select the analysis data set,Multiple data sets can be selected;
> * &#160; &#160;<label id='subSp'>subSp：</label>Selective analysis of subspecies,Multiple subspecies can be selected;
> * &#160; &#160;<label id='subSp'>subSpA：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；
> * &#160; &#160;<label id='subSp'>subSpB：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt);
> * &#160; &#160;<label id='winSize'>winSize:</label> (--fst-window-size)  window size，integer;
> * &#160; &#160;<label id='winStep'>winStep:</label>  (--fst-window-step)   window step，integer
These options can be used with "--weir-fst-pop" to do the Fst calculations on a windowed basis instead of a per-site basis. These arguments specify the desired window size and the desired step size between windows;

**<font color="#007979">Result</font>**

*.windowed.weir.fst：the result file contains six columns, respectively, chromosome number, Bin starting position, Bin ending position, variance, WEIGHTED_FST, MEAN_FST
