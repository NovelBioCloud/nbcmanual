# <font color="#007979">FstAnalysisSimple</font>

---

&#160; &#160; &#160; &#160;inter-population Fixation index(FST)，A indicatrix of whether a population's median gene frequency deviates from the ratio of genetic balance theory, to study the degree of differentiation between different groups. Its value is from 0 to 1,0 means that the two groups are undifferentiated, Its members are completely random; 1 represents the complete differentiation of the two groups, which forms species isolation and has no common diversity.
&#160; &#160; &#160; &#160;VCFtools can also calculate Fst statistics between individuals of different populations. It is an estimate calculated in accordance to Weir and Cockerham’s 1984 paper. The user must supply text files that contain lists of individuals (one per line) that are members of each population. The function will work with multiple populations if multiple --weir-fst-pop arguments are used.

**<font color="#007979">Input File</font>**

(1) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;
(3) strainInfo.txt：The text file should have at least two columns of information, the first column is species and the second column is species corresponding to subspecies;

**<font color="#007979">Input Parameters</font>**


These options can be used with "--weir-fst-pop" to do the Fst calculations on a windowed basis instead of a per-site basis. These arguments specify the desired window size and the desired step size between windows;
> * &#160; &#160;<label id='subSp'>subSpA：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；
> * &#160; &#160;<label id='subSp'>subSpB：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt);
> * &#160; &#160;<label id='winSize'>winSize:</label> (--fst-window-size)  window size，integer;
> * &#160; &#160;<label id='winStep'>winStep:</label>  (--fst-window-step)   window step，integer;

**<font color="#007979">Result</font>**

*.windowed.weir.fst：the result file contains six columns, respectively, chromosome number, Bin starting position, Bin ending position, variance, WEIGHTED_FST, MEAN_FST
