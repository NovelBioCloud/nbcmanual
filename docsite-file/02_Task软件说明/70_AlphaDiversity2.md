AlphaDiversity2
　　多样性指数有3类，分别是alpha、beta和gamma指数。针对alpha diversity，是用于测量群落内生物种类数量以及生物种类间相对丰度的一种测量。它反映了群落内物种间通过竞争资源或利用同种生境而产生的共存结果，可分为物种丰富度指数、物种均匀度指数、物种多样性指数三类。
　　Qiime官网：  http://qiime.org/
***
#### **<span class="glyphicon glyphicon-tags" aria-hidden="true" style="color:#3090C7"></span></i><span style="color:#3090C7"> 详细说明**

　　Alpha多样性是指一个特定区域或者生态系统内的多样性，常用的度量指标有丰富度估计量Chao1（Chao1 richness estimator）、香农-威纳多样性指数（Shannon-wiener diversity index）、辛普森多样性指数（Simpson diversity index）等。
　　计算菌群丰度：Chao、ace；  
　　计算菌群多样性：Shannon、Simpson。Simpson指数值越大，说明群落多样性越高；Shannon指数越大，说明群落多样性越高。

**Chao1：**是用chao1 算法估计群落中含OTU 数目的指数，chao1 在生态学中常用来估计物种总数，由Chao (1984) 最早提出。Chao1值越大代表物种总数越多。
Schao1=Sobs+n1(n1-1)/2(n2+1)
其中Schao1为估计的OTU数，Sobs为观测到的OTU数，n1为只有一条序列的OTU数目，n2为只有两条序列的OTU数目。
**Shannon：**用来估算样品中微生物的多样性指数之一。它与 Simpson 多样性指数均为常用的反映 alpha 多样性的指数。Shannon值越大，说明群落多样性越高。
**Ace：**用来估计群落中含有OTU 数目的指数，由Chao 提出，是生态学中估计物种总数的常用指数之一，与Chao1 的算法不同。
**Simpson：**用来估算样品中微生物的多样性指数之一，由Edward Hugh Simpson ( 1949) 提出，在生态学中常用来定量的描述一个区域的生物多样性。Simpson 指数值越大，说明群落多样性越高。
辛普森多样性指数=随机取样的两个个体属于不同种的概率
=1-随机取样的两个个体属于同种的概率

***
#### **<i class="fa fa-dot-circle-o" aria-hidden="true" style="color:#3090C7"></i><span style="color:#3090C7"> 输入文件**
InputBiom：输入biom文件
MapFile：mapping文件
InputTree：

***
#### **<i class="fa fa-cog" aria-hidden="true" style="color:#F88158"></i> <span style="color:#F88158">参数设置**
MinSeqNumber：最小序列/样本数量
MaxSeqNumber：最大序列/样本数量
StepSize：每个稀释区间的取样长度
containerNumber：软件运行时，使用container数。


***
#### **<i class="fa fa-file-text" aria-hidden="true" style="color:#848b79"></i><span style="color:#848b79"> 结果说明**


alpha:富集度--Reads分析结果
alpha_div_collated:Alpha多样性结果指数文件
alpha_rarefaction_plots:指数结果绘图
