# SplitFile
　　当需要处理的Fastq文件太大时，处理过程会占用太长时间，把Fastq文件进行等量切分后，就可以并行处理切分后文件，从而大大缩短处理时间。
　**功能：**
　		等量切分Fastq数据。
　**使用软件　**
　　	SplitFile：NovelBio编写java代码实现Fastq的切分功能。

　**应用范围　**
一般用于输入的Fastq文件很大，而且后续需要处理时间特别长的数据。
***
#### **<i class="glyphicon glyphicon-log-in" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
　　该Task的输入数据是测序reads数据，文件格式为Fastq。 
**leftInputData：**测序左端reads序列。要求输入单端fastq文件或双端测序的左端文件。
**rightInputData：**测序右端reads序列，单端不需要输入该文件，双端要求输入右端文件。
#### **<i class="glyphicon glyphicon-log-out" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输出文件**
　　	切分后Fastq文件（\*.part.1.fq.gz/\*.part.2.fq.gz）。
 **参数设置**
**part：**输入文件需要切分成几等份。
 ***
**<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果文件**
\*.part.1.fq.gz 切分后Fastq文件。
　　