# <font color="#007979">XP-CLRSimple</font>

---

&#160; &#160; &#160; &#160;Selective clearance: reduction or elimination of differences between nucleotides in adjacent DNA at a mutated site due to recent strong positive natural selection.
&#160; &#160; &#160; &#160;The XP-CLR package implements a composite likelihood method for detecting selective sweeps via the differentiation of two populations.


**<font color="#007979">Input File</font>**

(1) strainInfo.txt：The text file should have at least two columns of information, the first column is species and the second column is species corresponding to subspecies;
(2) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(3) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='snpWin'>snpWin：</label>maximum # of SNPs within a window. XPCLR score depends on the number of SNPs. To make the XP-CLR scores comparable between regions, it is necessary to control the maximum number of SNPs within a single window. The choice of snp # depends on the SNP density of your data;
> * &#160; &#160;<label id='gridSize'>gridSize：</label>he spacing between two grid points. It is in unit of bp;
> * &#160; &#160;<label id='isPhased'>IsPhased：</label>whether data is phased for more precise r2 calculation;
> * &#160; &#160;<label id='corrLevel'>corrLevel：</label>the range of its value is on [0 1]. If it is on (0 1], this corrLevel value is used as a criterion in the weighted composite likelihood ratio test. If two SNPs are highly correlated (r2 > corrLevel), their contribution to XPCLR is down-weighted. If corrLevel is set to be 0, XPCLR is estimated un-weightedly.
> * &#160; &#160;<label id='chrNum'>chrN：</label>Which contig analysis is based on;
> * &#160; &#160;<label id='subSp'>ObjectPop：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；
> * &#160; &#160;<label id='subSp'>RefPop：</label>Select analysis subspecies, you can select multiple subspecies (the value in the drop-down box is from the second column of the input file straininfo.txt, so the parameter value is optional after the input of straininfo.txt)；

**<font color="#007979">Result</font>**
&#160; &#160; &#160; &#160;\*.XPCLR.xpclr.txt，The file contains six columns of information:“chr#”、“grid#”、“#ofSNPs_in_window”、“physical_pos”、“genetic_pos”、“XPCLR_score”.    
