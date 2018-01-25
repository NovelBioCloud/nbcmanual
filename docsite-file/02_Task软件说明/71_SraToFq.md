# SraToFq
　　SRA是NCBI在2007年底推出的用于存储、显示、提取和分析高通量测序数据的数据库。SRA数据库，最初的命名为Short Read Archive，现已改为Sequence Read Archive。在该数据库中，高通量数据的存储格式为sra，而大多数数据分析软件不支持该类型文件格式，此时就需要将文件格式进行转换。
**功能：**
　　将sra格式文件转换成fastq格式文件。
**使用软件：**
　　SRA数据库提供的实现sra格式转化为fastq格式的工具。
**软件官网：**https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=toolkit_doc&f=fastq-dump

 **应用范围**
　　从NCBI 的SRA数据库中下载的高通量测序数据，进过转化后可进行后续的数据分析，如数据过滤等。
***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>  
　　**inputFile：**sra格式文件，详细信息请见官方说明：
https://trace.ncbi.nlm.nih.gov/Traces/sra/sra.cgi?view=announcement
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**<span>  
　　转化后的Fastq格式文件（\*.fastq.gz）。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>  
　**containerNumber：**软件运行时，使用的container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**<span>  
　　\*.fastq.gz：转化后的Fastq格式文件。