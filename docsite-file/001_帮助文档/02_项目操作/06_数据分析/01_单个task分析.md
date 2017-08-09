### **单个task分析**
<div style="text-align:center"><img data-src="单个task分析.gif"width="650px"></img>
</div>

**1.建立新的工作流**
　　在工作流处点击“添加工作流”，填写工作流基本信息，保存。双击新建的工作流，进入。
<div style="text-align:center"><img data-src="1.png" width="650px" ></img>
</div>

**2.添加RawData task**
　　无论是运行工作流还是task，添加RawData task都是必不可少的第一步。在页面左侧工具库中选择RawDataTask，拖入右侧运行界面，在跳出弹框中，填写“任务名称”并选择“输入类型”来选择数据文件类型。注意，“输入类型”需要选择对应的数据类型，否则在Rawdata添加数据中不能显示。
<div style="text-align:center"><img data-src="2.png" width="600px" ></img>
</div>

　　添加RawData完成后，点击第一个task中的“编辑参数信息”。

<div style="text-align:center"><img data-src="3.png" width="600px" ></img>
</div>

　　点击“编辑”，选择需要分析的数据。
<div style="text-align:center"><img data-src="3_1.png" width="600px" ></img>
</div>

　　选择本项目中的原始数据文件。
<div style="text-align:center"><img data-src="4.png" width="450px" ></img>
</div>

　　从右端中找到选择分析数据。
<div style="text-align:center"><img data-src="5.png" width="450px" ></img>
</div>

　　选择完成。
<div style="text-align:center"><img data-src="6.png" width="450px" ></img>
</div>
**3.添加第二个task**
　　完成RawData设置后，从左侧工具栏选择下一个task拖入运行界面（这里以fastQC为例）。
<div style="text-align:center"><img data-src="7.png" width="600px" ></img>
</div>

　　将两个task相连后，弹出数据选择弹出框，从弹框左侧选择数据拖入右侧。如果为单端测序数据，数据都添加到左端，如果为双端测序，数据分别对应拖入左端和右端。
<div style="text-align:center"><img data-src="8.png" width="600px" ></img>
</div>
　　文件选择完毕后，需要设置fastQC task参数，点击“编辑参数按钮”跳出弹框，设置该task参数。

<div style="text-align:center">
	<img data-src="9.png" width="600px" ></img>
</div>

　　以此类推在流程中可添加多个工具task，也可单个task设置完成后，点击“开始运行”按钮，选择“提交选中任务”运行当前选中单个task，或选择“提交全部任务”可选择运行全部task。
<div style="text-align:center"><img data-src="10.png" width="600px" ></img>
</div>



