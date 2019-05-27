###  **For CMD users: **
**1.	Download the latest CASH and example data. **
**2.	In console, go to the directory that includes cash, unzip cash and cd the cash directory as follows:**
　unzip cash_v2.1.0-alpha1.zip
　cd cash_v2.1.0-alpha1
　java –jar cash.jar --help 
***
cash version 2.1.0-alpha1
***
Usage: java -jar -Xmx10g cash.jar <options> --Case:prefix1 case.bam --Control:prefix2 Control.bam --GTF genes.gtf --Output outPath
&nbsp;
Example: java -jar -Xmx10g cash.jar --Case:Mutation file1.bam,file2.bam --Control:WildType file3.bam,file4.bam --GTF genes.gtf --Output outPath
&nbsp;
Or you can open GUI interface by run: java -jar -Xmx10g cash.jar --GUI
&nbsp;

Version:
--version print version information and quit
GUI:
--GUI open the GUI interface
&nbsp;
Input:
--Case:prefix1 files
　　Files should be sorted and indexed case bam files, using comma to seperate files. Index file(bai file) can be absent if parameter "--runSepChr" set to False.
　　just like --Case:KO /home/user/ko1.bam,/home/user/ko2.sorted.bam
&nbsp;
--Control:prefix2 files
　　Same as Case:prefix1
　　just like --Control:WT /home/user/wt1.bam,/home/user/wt2.sorted.bam
&nbsp;
--GTF file.gtf
　　CASH needs reference gene annotations (eg. gtf/gff file) and RNA-seq data to construct alternative splicing (AS) model within genes
&nbsp;
Output:
--Output outFilePrefix
	output directory and prefix, example: --Output /home/user/myresult
&nbsp;
Options:
--MergePval A/G, default is G
　　It is recommend to use the default value(G), while the results showed a poor number is more sensitive. Users can switch G to A and get more specific results
　A: arithmetic weighted mean of event-centric strategy and exon-centric strategy Pvalues(more specific)
　G: geometric weighted mean of event-centric strategy and exon-centric strategy Pvalues(more sensitive)
&nbsp;
--Combine True/False, default is False
　False: if here are several replications, CASH treats them as biological replicates as usual
　True: if here are several replications, CASH combines case(control) bam files to be one case(control) big bam file
&nbsp;
--DisplayAllEvent True/False, default is True
　A gene may have several AS events on different exons, CASH can display all events, or just show only one most significantly event
　True: show all splicing event
　False: show only one most significantly splicing event
&nbsp;
--StrandSpecific F/R/NONE, default is NONE
	when the sequence library is strand specific, the parameter is used
　F: first read of the pair-end reads represent the strand of the fragment, just like ion proton
　R: second read of the pair-end reads represent the strand of the fragment
&nbsp;
--SpliceCons True/False, default is True
　　SpliceCons is used to construct AS model based on RNA-seq data and reference gene annotations, leading to detection of novel AS events in the samples
　　True: construct AS model based on RNA-seq data and gtf/gff files. The process needs more time
　　False: employ AS model inferred from gtf/gff file
&nbsp;
--JuncAllSample int, default is 25
　　Doesn't calculate AS event with the sum of all sample junction reads less than JuncAllSample
&nbsp;	
--JuncOneGroup int, default is 10
　　Doesn't calculate AS event with one group of junction reads less than JuncOneGroup
&nbsp;
--minAnchorLen/-A int, default is 5
　　When counting junction reads, exon-exon junctions spanned by reads with at least this many bases on each side
&nbsp;	
--minIntronLen/-I int, default is 25
　　The gaps between RNA-Seq reads with length > 25bp is considered to be intron
&nbsp;	
--minJuncReadsForNewIso/-J int, default is 10
	Min junction reads for reconstructing AS site
&nbsp;	
--runSepChr True/False, default is True
　　Due to some species (e.g. Hordeum vulgare) chromosomes with a huge length of base pairs, the java module 'htsjdk(v2.9.0)' can hardly support the index of the chromosomes and to fix the issue, we added this parameter and users can set this parameter to False, which means CASH run without index files, but it will take more memory and more computing time.
&nbsp;	 
--ChrRegion chrId/chrId:startPos-endPos
　　While runSepChr is True(default), one can set this parameter and CASH will only calculate this region.You can set value as chromosome Id like "--ChrRegion chr1" or set a specific region like "--ChrRegion chr1:1-9527"
&nbsp;
**3.	Example of running CASH. **
Run all chromosome: 
`java -jar cash.jar --Case:KO examples/bamfiles/KO_rep1.bam, examples/bamfiles/KO_rep2.bam --Control:WT examples/bamfiles/WT_rep1.bam, examples/bamfiles/WT_rep2.bam --GTF examples/genes/genes.gtf --Output ./result`
Note: please ensure that the path instance contains the corresponding files. 

**4.	Output files:** Two output files are generated in the current output directory with prefix <span style="color:blue">result</span>, that is, <span style="color:blue">result.KOvsWT.alldiff.statistics.txt </span>presents the summary of AS splicing types in the samples, and <span style="color:blue">result.KOvsWT.alldiff.txt </span> presents details for all of the AS events in the samples.

**5.	Details for output file:**

| AccID       | gene name   |  
|:  ----------:  |: -----: | 
| Location     | the location of splicing exon in genome  |  
| Exon_Number    | the number of splicing exon in gene  |  
|A_2_Skip::Others     | The numbers in sample_Skip::Others indicate the number of exclusion reads and the number of inclusion reads for sample A_2  |  
| A_1_Skip::Others   | The numbers in sample_Skip::Others indicate the number of exclusion reads and the number of inclusion reads for sample A_1  |  
|A_2Exp   |The numbers in sampleExp indicate the sequencing coverage of the splicing region relative to the whole gene for sample A_2  |  
| A_1Exp     | The numbers in sampleExp indicate the sequencing coverage of the splicing region relative to the whole gene for sample A_1; |  
|P-Value     | adjusted Pvalue based on arithmetic/geometric weighted mean of event-centric strategy and exon-centric strategy;Pvalues.(Depends on param --MergePval, Default is arithmetic weighted mean) |  
| FDR     | False Discovery Rate using Benjamini-Hochberg method based on "P-Value "  |  
| SplicingType     | Types of AS event  |  

###  **For windows users: **
**6.	Download the latest CASH and example data and unzip it into the directory that the users want. **
<div style="text-align:center"><img data-src="image1.png" width="550px" ></img>
</div>

**7.	Go to the directory that includes CASH, directly double click CASH.jar or cd the CASH directory that you set and type java -jar CASH.jar in CMD command. **
<div style="text-align:center"><img data-src="image2.png" width="550px" ></img>
</div>


**8.	An interface exhibits as follows:**
<div style="text-align:center"><img data-src="image3.png" width="550px" ></img>
</div>
&nbsp;
**9.	A) Load RNA-seq bam files: **Click button AddBam to load .bam format files from your system. If the experiments have RNA-seq replications, do some edits in group column to make the control files classified into Control group (e.g. Untreated) and the test files into Test group (e.g. RNAi). 
　**B) Load GTF or GFF3 file:** Click OpenGFF3/GTF to load the file of reference gene annotations.
About GTF format: the GTF file format should follow two rules:
　　1). No matter the strand of a gene, the location of the exon should be sorted from low to high;
　　2). If there is a CDS, it should be wroten after all the exons involved in.
　just like the table below:
<div style="text-align:center"><img data-src="image4.png" width="550px" ></img>
</div>

　**C) Construction of Alternative Splicing (AS) sites: **Tick off SpliceCons to construct AS sites based on RNA-seq data and reference gene annotations, leading to detection of novel AS events in the samples. Otherwise, detection of AS events relies on reference gene annotations. 
　**D) Groups comparison:** Click AddCmp to set the two compared groups. 
　**E) The samples with replications: **Tick off Consider replications indicates CASH will treat the samples in the same group as biological replicates. However, when the sequencing depth is too low to detect AS events, we suggest the users not to tick off Consider replications, and in that way, CASH will integrate the bam files in the same group into one bam file to enhance the detection of AS events. 
　**F) Save the results: **Click SaveTo to store the analysis results. 

**10.	An example of loading files and setting parameters. **
<div style="text-align:center"><img data-src="image5.png" width="550px" ></img>
</div>

**11.runCASH: **When all required files are loaded, start running CASH. 
**12.Output files:** Two output files are generated in the output directory, that is, for example, result.WtvsKO.statistics.txt presents the summary of AS splicing types in the samples, and result.WTvsKO.alldiff.txt presents details for all of the AS events in the samples.


