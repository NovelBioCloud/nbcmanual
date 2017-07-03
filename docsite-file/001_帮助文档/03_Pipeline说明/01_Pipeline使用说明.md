## **Pipline流程使用说明**
　　NovelBrain数据分析平台，可进行标准流程分析和定制化流程分析。标准流程分析可以实现一键式生成结果；定制化流程分析功能可以根据不同的研究需要自定义参数及分析任务，简单高效地满足您的科研需求。平台内设有多条配套整合的工作流，如基因组测序、转录组测序、miRNA测序、甲基化测序、ChIP-Seq以及芯片数据，都有对应的配套整合工作流便于分析。
　　下面以circRNA分析为实例，来演示平台流程使用：
#### **1.新建项目**
　　点击“新建项目”，填写项目名称、项目描述后，点击“保存”。
<div style="text-align:center"><img data-src="1.png" width="600px" height="300px" ></img>
</div>

&nbsp;
#### **2.添加实验信息**
　　点击“添加实验”，填写实验名称、数据类型、实验描述后，保存。
<div style="text-align:center"><img data-src="2.png" width="600px" height="250px" ></img>
</div>

&nbsp;
#### **3.添加样本信息**
　　点击“点击添加样本”，填写样本名称和分组信息。可以任意增加行和删除样本。
<div style="text-align:center"><img data-src="3.png" width="600px" height="300px" ></img>
</div>

&nbsp;
#### **4.上传数据**
　　上传数据有两种方式，如果数据量较小时，用户可以通过平台直接上传。数据量较大时，客户可以选择通过云端上传，云端上传使用多线程，上传速度较快，并且支持断点续传，可参考NBCClient使用说明。平台直接上传，点击“点击上传数据”。选择上传数据后，上传。
<div style="text-align:center"><img data-src="4.png" width="600px" height="300px" ></img>
</div>

&nbsp;
#### **5.样本匹配**
　　将上传的分析数据名称和样品名称匹配起来。点击匹配样本，选择样本名后勾选相应的数据。
<div style="text-align:center"><img data-src="5.png" width="600px" height="300px" ></img>
</div>

&nbsp;
#### **6.新建工作流**
　　建好实验、样本信息和项目数据后，点击“新建工作流”可以新建工作流。选择所需分析流程，填写“工作流名称”和“工作流描述”等信息，保存。
<div style="text-align:center"><img data-src="6.png" width="600px" height="550px" ></img>
</div>
<div style="text-align:center"><img data-src="7.png" width="600px" height="250px" ></img>
</div>

&nbsp;
#### **7.项目数据分析**
　　上一步完成后，自动进入工作流页面。点击“切换到参数输入页面”。
<div style="text-align:center"><img data-src="8.png" width="600px" height="250px" ></img>
</div>

**7.1 输入文件**
（1）输入分析数据文件，点击“编辑”。选择pipline中需要分析的数据。
<div style="text-align:center"><img data-src="9.png" width="600px" height="300px" ></img>
</div>

（2）选择文件
　公共文件：平台中共有文件，大多项目需要用到的文件，共享文件。
　全部项目：可以进入到有权限的全部项目。
　所属项目：本项目中所有文件。
　此处选择本项目中的原始数据文件：
<div style="text-align:center"><img data-src="10.png" width="500px" ></img>
</div>

从右端中找到选择分析数据；在左端显示已选文件，可以进行删除修改。
<div style="text-align:center"><img data-src="11.png" width="500px" ></img>
</div>

（3）选择完成。
<div style="text-align:center"><img data-src="12.png" width="600px" ></img>
</div>


**7.2 参数设置**
　　在参数输入页面，点击“编辑”即可修改task参数。
　　需要修改某个task参数时，可在左侧框下拉，查找需要更改task，也可点击右侧pipline预览图中，点击相应的task，参数页面会自动滚动到相应task参数页面，进行修改。

<div style="text-align:center"><img data-src="13.png" width="600px" height="250px" ></img>
</div>
　　参数修改完成后，点击参数保存。将所有需要修改task参数修改完成后，点击“cicRNA”进入项目流程页面。
<div style="text-align:center"><img data-src="14.png" width="600px" height="250px" ></img>
</div>
　　进入cicRNA页面后，点击“开始任务”，选择“提交全部任务”，就可以运行了。
<div style="text-align:center"><img data-src="15.png" width="600px" height="250px" ></img>
</div>

&nbsp;
#### **8.项目结果**
　　项目结束后点击“结果信息”，或者双击任何一个task，进入结果页面。
<div style="text-align:center"><img data-src="16.png" width="600px" height="250px" ></img>
</div>

**8.1结果页面**
　　系统自动生成每一个task分析结果。简洁、高效、可视化的在线预览分析结果，并可勾选一个或多个项目结果进行下载。
<div style="text-align:center"><img data-src="17.png" width="600px" height="250px" ></img>
</div>

**8.2监控页面**
　　任务监控帮助用户实时监控硬盘损坏情况、CPU的使用率以及内存使用量、网络是否畅通。可以清晰知道各个程序所占用CPU、内存，实时对进程进行监控，方便对项目的暂停和恢复、杀掉等操作的进行判断。并设有硬件监控报警，如某一硬盘有坏道时，就会报警提示更换硬盘。
<div style="text-align:center"><img data-src="18.png" width="600px" height="250px" ></img>
</div>

**8.3 一键式结果报告**
　　全面整合代码托管的功能，针对项目数据分析开发定制的一站式工具，系统自动生成结果报告。结果报告生成的测序分析图表文章化，只需下载就可用于文章发表，零生物信息学基础也可快速理解、分析测序结果。

<div style="text-align:center"><img data-src="19.png" width="600px" height="250px" ></img>
</div>




