# Trimmomatic

　　一个针对 Illumina高通量测序的测序数据的修剪工具。即能够针对paired-end 也能够用于single ended。
　
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**<span>
　　尽管已经存在许多NGS片段预处理工具，但是我们不能找到在灵活性、正确处理双端数据和高性能方面满足我们需求的任何工具或工具组合。Trimmomatic作为一种更加灵活和高效的预处理工具，它能够正确地处理双端数据。
　　Trimmomatic用两种策略来去除adapter: Palindrome and Simple。
　　simple trimming是利用每一个adapter序列去跟reads匹配，如果匹配上，就删除read的这部分序列。
　　Palindrome trimming是在adapter序列中reading through一个短的片段。在这个方法中，相应的adapter序列在硅片上的连接被连接到了reads的开始，形成了adapter+read序列，正链和反链比对，如果比对显示read-through，正链剪切掉adapter，反链去掉（由于它没有包含新的数据）。

　　Trimmomatic官网：http://www.usadellab.org/cms/index.php?page=trimmomatic　

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**<span>
　　左端序列文件 (FASTQ) 、右端序列文件 (FASTQ)：single-ended只输入左端序列文件，paired-ended输入分别输入两端的序列。
　　adapterFile ：接头序列文件。
***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**<span>

**线程数：**软件运行时，使用线程数。
**使用内存：**软件运行时，使用内存数。
**切除首端最小质量值：**去除首端低质量的碱基或Ｎ碱基的，默认为３。
**切除末端最小质量值：**去除首端低质量的碱基或Ｎ碱基的质量值，默认为３。
**Windows长度：**滑动窗口扫描阅读的碱基个数，默认为４个碱基。
**windows最小平均质量：**去除最小窗口的平均质量值，默认为15。
**reads最小长度：**reads的最小长度，默认为36。
**保留reads长度：**保留的reads长度。
**剪切长度：**在reads的首端切除指定的长度。
**最低平均质量值：**丢掉质量低于这个值的reads。
**最大mismatch数：**允许的最大mismatch数。
**palindrome匹配碱基数：**palindrome模式下匹配碱基数阈值，默认值为30。
**simple匹配碱基数：**simple模式下的匹配碱基数阈值，默认值为10。
**containerNumber：**软件运行时，使用的container数。

***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**
（1）对于single-ended（单末端）数据
　　　输出修剪和过滤的clean data数据，为单个FASTQ文件。
<div style="text-align:center"><img data-src="1.png" width="600px"  ></img></div>
（2）对于paired-end（双末端）数据，输出四个文件：
　　两个FASTQ文件(R1-paired and R2-paired)，包含read的两端pair（R1和R2）均通过数据质控的结果文件。
　　另两个FASTQ文件(R1-unpaired and R2-unpaired)，包含read，其中一端pair（R1或R2）通过数据质控，另一端无法通过数据质控，仅保留了一端的数据结果。
<div style="text-align:center"><img data-src="2.png" width="600px"  ></img></div>



