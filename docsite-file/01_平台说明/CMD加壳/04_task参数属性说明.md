###  **Task参数属性说明**

| 日期        | 姓名   |  事宜  |
| --------   |:-----:  | :----:  |
| 2016-7-22    | 樊小龙| 做成    |
|2016-11-8     |   樊小龙  |   对类似DifGene这种需要两个表格联动形式的参数配置说明  |
| 2017-2-22    |   任耀祥  |  修改联动字段配置说明  |

&nbsp;

1.name 名称
　说明：字段在后台的名称,必须小写字母开头,按驼峰法则命名
2.displayName 显示名称 
　说明：字段在前台的显示名称.可以是汉字
3.paramOrder 顺序 
　说明：正整数
4.setParamTypeStr 参数类型 
　4.1 Normal普通类型
　4.2 PageParam前台页面的参数
　4.3 Compare是否为比较，如group1, group2，或者treat, control 这种
　4.4 InputFile是否为输入文件
　4.5 Prefix是否为文件前缀，在读取规则文件的时候会用这个来进行替换
　4.6OutPrefix是否为输出路径相关的参数，会用该参数来做输出文件的名字
5.valueType值类型
　5.1 None
　5.2String
　5.3Integer
　5.4Double
　5.5Boolean
　5.6Path如果该字段是选择的文件,就选Path类型
6.defaultValue默认值 
7.widgetType 控件类型 (当参数类型是PageParam时,该字段必填)
　7.1 nbcChkbox单选框
　7.2 validationInput文本输入框,带验证效果
　7.3 nbcCombobox下拉单选
　7.4 multiCombobox下拉多选,现只用于blastSpecies
　7.5 slider滑动器
8.valueUrl请求值的URL
　说明： 只有控件类型是nbcCombobox或multiCombobox时需要设置，请求值的url地址。
9.required 是否必需
　说明： true/false
10.dataOption 数据格式要求 
　说明：当控件类型是validationInput时,可选设置该参数.具体设置可参考http://www.runoob.com/jquery/jquery-plugin-validate.html
当控件类型是slider时,必填.至少设置min和max参数."
11.fileSelectType选择文件形式(当参数类型是InputFile时,该字段必填,代表输入文件的选择形式)
　11.1 SINGLE单选文件
　11.2 LEFT左端文件
　11.3 RIGHT右端文件
　11.4 MULTIPLE多选文件
　11.5 MULTIPLEPREFIX带组名的多选文件
　11.6 INTERSECTION带组名和需合并列的多选文件
12.setEnumFileTypeStr可输入文件类型 
　参数：SAM, BAM, SORTED_BAM, UNMAPPED_BAM,BED, BLAST,FASTA,FASTQ, LEFT_FASTQ, RIGTH_FASTQ, FASTQINTERLEVE,GENEXPTABLE,GENELOCTABLE,DIFGENE,GENETABLE,TABLE,VCF, BCF,GFF3, GTF,MRD,PILEUP,PIC,SRC2TRG,WIG;
　说明：当参数类型是InputFile时,该字段必填,代表输入文件的选择形式,可填写多个,用逗号分割
13.setUnacceptableFileTypeStr 不可输入文件类型 
　参数：SAM, BAM, SORTED_BAM, UNMAPPED_BAM,BED, BLAST,FASTA,FASTQ, LEFT_FASTQ, RIGTH_FASTQ, FASTQINTERLEVE,GENEXPTABLE,GENELOCTABLE,DIFGENE,GENETABLE,TABLE,VCF, BCF,GFF3, GTF,MRD,PILEUP,PIC,SRC2TRG,WIG;
　说明：当参数类型是InputFile时,该字段选填,代表输入文件的选择形式,可填写多个,用逗号分割
14.combineColumn关联字段名称 
　说明：主要用于双端选文件时,当选择文件形式是LEFT时,这里填写右端的名称,右端时,填写左端名称
15.isNeedSplit是否根据本字段进行切分 
　说明：是否根据本字段进行切分，就是把本task的数据切分成多份在不同的container中运行
16.prefixAssociated对应的组名
　说明：当选择文件形式是LEFT,MULTIPLEPREFIX,INTERSECTION时,设置组名字段名称到该字段.
17.colComb需合并列的列名
　说明：需合并列的列名称，目前仅用在intersection中
18.advanced是否是高级设置
　18.1 参数：true,false
　说明：设在该字段是否在高级属性列表中展示。
　18.2 task受影响字段[名称、值]的列表组合 [名称、值]分别对应依赖的字段名称和字段应该填写的值，
　说明：[名称，值]的列表组合可以填写多个，只要满足其中的一个条件，该字段就会在前台显示。

　　DifGene的参数中需要单选输入一个文件,根据这个文件头信息,参数中有两个联动的表格参数需要设置。
　　类似DifGene的两级联动表格参数设置,只需将参数名称和类型设置和DifGene的两级表格所需参数和类型相同即可。
&nbsp;
具体如下:

| 名称(参数名称必须完全相同)       | 参数类型   | 
| --------   |:-----:  | :----:  |
| colSampleArray Compare    | Compare	| 
|sampleNameArray	   |   Compare	  |  
| groupNameArray    |   Compare	  |  
| group1Array    |   Compare	  |  
|group2Array  |  Compare	  |  
| outFileArray    | OutPrefix  |  
|inFileName    |   InputFile  |  
##文件类型参数所需设置的其他参数....
<div style="text-align:center"><img data-src="1.png" width="250px" ></img>
</div>
														

