# <font color="#007979">PiAnalysisSimple</font>


---

&#160; &#160; &#160; &#160;Pi is a parameter to measure the polymorphism of a specific population. It refers to the mean value of nucleotide differences between two randomly selected DNA sequences at each nucleotide site in the same population.The higher the value of PI is, the higher the corresponding subgroup polymorphism.

**<font color="#007979">InputFile</font>**

(1) ped file: A ped file is a plain text file that requires at least six columns, it‘s be separated by “\t”.These are the 6 columns：“Family ID”、“Individual ID”、“Paternal ID”、“Maternal ID”、“Sex”、“Phenotype”；
(2) bim file: PLINK extended MAP file，Bim file is an extension of the map file, which has six lines in total and contains the specific information of SNP (conconder). The six columns are: "chromosome information", "SNP name", "mole distance", "physical distance", "required alleles" and "main alleles" respectively;

**<font color="#007979">Input Parameters</font>**

> * &#160; &#160;<label id='windowPi'>windowPi：</label> window size,integer；

**<font color="#007979">Result</font>**

&#160; &#160; &#160; &#160;* .windowed.pi，The four columns of information are found in the output file, which are respectively "CHROM", "BIN_START", "BIN_END" and "n_conr".
