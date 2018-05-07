### **CMD详细步骤说明**
　Cmd加壳主要分为建立task、设置task参数、以及部署到服务器，这几步，以下进行详细说明。
#### **1.系统中建立task**
　　登录阿里云平台系统，用管理用户进入：　
　　选择“分析平台”中“task Module管理”<div style="text-align:center"><img data-src="1.png" width="600px" height="300px" ></img>
</div>
　　点击“新增”，新增task后，在“tasktype”列中填写task名称，“enable”列填写“1”后，保存，即可。
<div style="text-align:center"><img data-src="2.png" width="600px" height="300px" ></img>
</div>

&nbsp; &nbsp; &nbsp; 设置task使用镜像，在“dockerImageName”一列中，点击下拉框，选择task使用的镜像。
<div style="text-align:center"><img data-src="20.png" width="900px" height="200px" ></img>
</div>

#### **2.task参数设置**
　（1）在“分析平台”中找到“task ModuleParam管理”进入。
 <div style="text-align:center"><img data-src="3.png" width="600px" height="300px" ></img>
</div>

　（2）在搜索框中搜索task名称。输入刚才新建的task名称，找到task。
<div style="text-align:center"><img data-src="4.png" width="600px" height="300px" ></img>
</div> 
　（3）添加task参数。点击“新增”，填写需要增加task参数。
<div style="text-align:center"><img data-src="5.png" width="600px" height="300px" ></img>
</div>

　（4）填写参数列
<div style="text-align:center"><img data-src="6.png" width="600px" height="300px" ></img>
</div>
 
TaskType ：需要与第一步添加task 名称相一致
名称：后台显示名称，字段在后台的名称,必须小写字母开头,按驼峰法则命名
显示名称：前台的显示名称，可以为汉字
顺序：需为整数
参数类型：PageParam：前台页面的参数
　　　　　Compare：是否为比较参数，如group1, group2，或者treat, control 
　　　　　InputFile：输入文件
　　　　　Prefix：输入文件的前缀，在读取规则文件的时候会用这个来进行替换
　　　　　OutPrefix：输出路径的参数，用该参数来做输出文件的名字
　　　注意：参数类型可多选，通常Prefix和OutPrefix需同时选择；（主要用参数框选择标黄）
控件类型：  nbcChkbo: 单选框
　　　　　　validationInput:文本输入框
　　　　　　nbcCombobox:下拉单选
　　　　　　multiCombobox:下拉多选,现只用于blastSpecies
　　　　　　slider:滑动器

 **几种比较特殊的参数型：**
 **A．下拉框型 ** 当控件类型为下拉框选择时，需要填写URL地址，步骤如下：
　　a．在“基础数据管理”中选择“数据字典管理”
<div style="text-align:center">
<img data-src="7.png" width="600px" height="300px" ></img>
</div>
　　b.如建有选项可直接进行选择，如没有需要选择“新增”；
参数名称：左侧“编码”与后台参数名称相一致，“显示名称”为前台显示参数名称，保存。
参数下拉选项：右侧填写参数下拉选项。 “编码”填写后台参数名称，“显示名称”为前台显示参数名称，顺序为参数显示顺序，保存。
 <div style="text-align:center">
<img data-src="8.png" width="600px" height="300px" ></img>
</div>
　　c. 拷贝“编码”列内容到datadict_getlsDataValues/编码后，粘贴到“task ModuleParam”的url中。
　例如：datadict_getlsDataValues/species1，将“datadict_getlsDataValues/species1”粘贴到“task ModuleParam”的url中。
 
<div style="text-align:center">
<img data-src="9.png" width="600px" height="300px" ></img>
</div>
 <div style="text-align:center">
<img data-src="10.png" width="600px" height="150px" ></img>
</div>
 **B.参数类型为Inputfile时，为输入文件参数。 **
　　当数据为SE测序，“选择文件形式”填写SINGLE，并填写“可输入文件类型”;
 <div style="text-align:center">
<img data-src="11.png" width="600px" height="150px" ></img>
</div>
　　当数据为PE测序，填写设置左端、右端、组名文件。左端文件的“选择文件形式”左端填写“LEFT”，“关联字段名称”填写关联右端的文件“名称”，“对应的组名”填写关联组名“名称”。只需进行左端文件关联右端即可。
 <div style="text-align:center">
<img data-src="12.png" width="600px" height="300px" ></img>
</div>
 <div style="text-align:center">
<img data-src="13.png" width="600px" height="300px" ></img>
</div>
　　可输入文件类型 ：SAM, BAM, SORTED_BAM, UNMAPPED_BAM,BED, BLAST,FASTA,FASTQ, LEFT_FASTQ, RIGTH_FASTQ, FASTQINTERLEVE,GENEXPTABLE,GENELOCTABLE, DIFGENE,GENETABLE,TABLE,VCF, BCF,GFF3, GTF,MRD,PILEUP,PIC, SRC2TRG,WIG;

