###  **Task规则文件编写说明**
**更新记录**
2016-7-22 樊小龙 做成														
2017-3-30 樊小龙 (1)增加对结果文件没有文件夹的支持。
 　　　　　　　　　(2)增加对文件夹名称带prefix的支持。	
&nbsp;
#### **１.规则文件说明**
　　我们在task选择文件时,如果task还未运行,是无法选择实际文件的.这时我们可以通过选择规则文件。让上级task成功运行后,自动运行下级task。
　　规则文件的制定,我们是通过配置xml文件来进行的.通过指定文件夹.文件别名.文件名对应的正则表达式等一系列规则。最终生成规则文件。
　　以是FastQC的规则文件样式：
<div style="text-align:center"><img data-src="1.png" width="500px" ></img>
</div>


  包括几个基本部分:
　　OutAllFileNameModel(规则文件整体结构)。
　　lsTaskFilepath(该task下的文件夹名称,因为可能存在多个文件夹.所以需挨个列出)。
　　lsOutFileNameModel(所有规则文件的模型列表,里面可能有多个文件夹中的规则文件)。
　　OutFileNameModel(每一个文件夹下的规则文件)。
　　filepathStr(文件夹名)。
　　mapRuleModelFiles(规则文件显示名和对应的正则表达式)。

**针对FastQC的规则文件,具体说明如下:**
```
<?xml version="1.0" encoding="UTF-8"?>	　
<OutAllFileNameModel>	　	规则文件整体结构
　	<lsTaskFilepath>	　	文件夹	　	　
　	　	<string>QualityControl_result</string>
　	</lsTaskFilepath>	　	　	　	　	　	　
　	<lsOutFileNameModel>	　	所有规则文件的模型列表,里面可能有多个文件夹中的规则文件
　	　	<OutFileNameModel>	　	具体的文件夹对应的模型
　	　	　	<filepathStr>QualityControl_result</filepathStr>
　	　	　	<mapRuleModelFiles>	　	该文件夹中的多个规则文件用map结构存储.key是别名,value是正则表达式
　	　	　	　	<entry>	　	　	　	　	　	　
　	　	　	　	　	<string>left_resultFile_1.fq.gz</string>
　	　	　	　	　	<string>${prefix}\w*_1\.fq\.gz$#${prefix}\w*\.fq\.gz$</string>
　	　	　	　	</entry>	　	　	　	　	　
　	　	　	　	<entry>	　	　	　	　	　	　
　	　	　	　	　	<string>right_resultFile_2.fq.gz</string>
　	　	　	　	　	<string>${prefix}\w*_2\.fq\.gz$</string>
　	　	　	　	</entry>	　	　	　	　	　
　	　	　	</mapRuleModelFiles>	　	　	　
　	　	</OutFileNameModel>	　	　	　	　
　	</lsOutFileNameModel>	　	　	　	　
</OutAllFileNameModel>	　	　	　	　	　
```
**注意：**在上面左端文件的规则文件的正则表达式中有两个特殊符号。
　　其中${prefix}是代指组名(或者叫输出文件前缀)。在执行前,会自动用组名替换；
　　第二、#代表切分正则表达式.即下面的正则表达式实际上是两个正则表达式。#前是一个,#后是一个，实际执行时,先执行前边的,如果前边的未匹配到文件。会再执行后边的，但如果使用前边的正则表达式匹配到文件了。就不会再执行后面的。

<div style="text-align:center"><img data-src="2.png" width="500px" ></img>
</div>

**3.几种特殊的规则文件**
　　现在新做的task结果文件默认没有文件夹，配置时就不需要配置lsTaskFilepath和filepathStr两个属性的配置。具体如下图
<div style="text-align:center"><img data-src="3.png" width="350px" ></img>
</div>

　　对于有些task，结果文件可能放在不同前缀的文件夹中，这时文件夹名称可以配置为${prefix}格式。
<div style="text-align:center"><img data-src="4.png" width="350px" ></img>
</div>
**4.具体样例**
　FastQC
```
<?xml version="1.0" encoding="UTF-8"?>
<OutAllFileNameModel>
 <lsTaskFilepath>
  <string>QualityControl_result</string>
 </lsTaskFilepath>
 <lsOutFileNameModel>
  <OutFileNameModel>
   <filepathStr>QualityControl_result</filepathStr>
   <mapRuleModelFiles>
    <entry>
     <string>left_resultFile_1.fq.gz</string>
     <string>${prefix}\w*_1\.fq\.gz$#${prefix}\w*\.fq\.gz$</string>
    </entry>
    <entry>
     <string>right_resultFile_2.fq.gz</string>
     <string>${prefix}\w*_2\.fq\.gz$</string>
    </entry>
   </mapRuleModelFiles>
  </OutFileNameModel>
 </lsOutFileNameModel>
</OutAllFileNameModel>
```
SamAndRPKM
```
<?xml version="1.0" encoding="UTF-8"?>
<OutAllFileNameModel>
 <lsTaskFilepath>
  <string>GeneExpression_result</string>
  <string>GeneStructure_result</string>
  <string>SamStatistic_result</string>
 </lsTaskFilepath>
 <lsOutFileNameModel>
  <OutFileNameModel>
   <filepathStr>GeneExpression_result</filepathStr>
   <mapRuleModelFiles>
    <entry>
     <string>All_Counts.exp.txt</string>
     <string>^All_Counts\.exp\.txt$#^All_Fragments\.exp\.txt$</string>
    </entry>
    <entry>
     <string>All_RPKM.exp.txt</string>
     <string>^All_RPKM\.exp\.txt$#^All_FPKM\.exp\.txt$</string>
    </entry>
    <entry>
     <string>All_TPM.exp.txt</string>
     <string>All_TPM\.exp\.txt</string>
    </entry>
    <entry>
     <string>All_UQ.exp.txt</string>
     <string>All_UQ\.exp\.txt</string>
    </entry>
   </mapRuleModelFiles>
  </OutFileNameModel>
  <OutFileNameModel>
   <filepathStr>GeneStructure_result</filepathStr>
   <mapRuleModelFiles>
    <entry>
     <string>GeneStructure.txt</string>
     <string>[a-zA-Z0-9_]+_GeneStructure\.txt</string>
    </entry>
    <entry>
     <string>SamLibraryInfo.txt</string>
     <string>SamLibraryInfo\.txt</string>
    </entry>
   </mapRuleModelFiles>
  </OutFileNameModel>
  <OutFileNameModel>
   <filepathStr>SamStatistic_result</filepathStr>
   <mapRuleModelFiles>
    <entry>
     <string>MappingStatistic.xls</string>
     <string>MappingStatistic_[a-zA-Z0-9_]+\.xls</string>
    </entry>
   </mapRuleModelFiles>
  </OutFileNameModel>
 </lsOutFileNameModel>
</OutAllFileNameModel>
```