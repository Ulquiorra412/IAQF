***
### 2.5 会议大纲
### 上周工作总结
- Guangyu Wang: 
1. 画了机器学习结果和价格的对应图
2. 做了一个双栏的Latex模板（实装计划待定）
- Nicole Zhao:
1. 低频数据以环比增长合并
2. 事件驱动研究
3. Vthr技术指标（alphas）
4. 解决一致预期的用法
- Chang Liu:
1. Fourier Transformation 改进
2. 新的检验结果
3. 两个三角函数叠加新的处理方式
- Thomas Tan:
1. PS 算法未能识别covid-19带来的短熊市
2. LT能识别
3. 可能在标签中手动加入
		
### 下周工作概要
- Tan & Liu：
继续完成HMM和其他第一部分的内容
- Wang & Zhao：
数据形式改为月频；label改为使用PS识别的结果
完成机器学习部分的初稿


***
### 1.30 会议大纲 【PS：大家的新年快乐！】
- 各成员讨论工作进度、文章结构，以及一些后续工作
- 下次会议 **与老师讨论后后，再行分工**

### 讨论内容  
- **文章结构（暂定）**
1. 开头：傅立叶（亮点），证明美股有42个月周期（有周期性，42个月主导）
2. 识别：42个月作为一个结果/参数，放到识别LT和PS算法里，得到市场状态label
3. 计量：feature的分布、检验、差分、回归等（通过计量方法确定所用因子，而后传给机器学习）
4. 机器学习：运用label和features进行训练和预测（可参考：2018之前作为训练数据；2018-2021作为测试集并执行策略）
5. 策略：单个复合/复杂的高收益策略（例如，信号叠加）OR每个模型后面跟一个简单的、用于对比模型之间收益差别的策略


- **整理数据**
1. 宏观指标相关数据：GDP（nominal和real，也有GDP明细）；利率（联邦，2y，5y，10y，还有3m未下载）；住房价格指数，可考虑；附加数据，石油、黄金；PMI（制造业和服务业）；等等
2. 罗素指数相关数据：10年季度、25年年度；三大表（以及相关的市场、流动性、盈利、估值数据）；一致预期、pb、pe等；都是美元计价
3. 国际指数相关数据：以当地货币为单位，附有加权原理文件
4. 文件夹中有对应的word简介

5. 后续：数据时间统一（日度月度季度）；整合、清洗、处理异常数据
6. 建议：是否需要合并git上面的两个数据文件夹？


- **机器学习**
1. 用罗素指数价格数据，从1987年开始，计算return；正态分布不好，t分布好；
2. Label来源：每22天为一个周期，计算接下来5天的平均收益（反应市场信息）
3. Feature来源：罗素指数收益率
4. RNN模型，multi RNN模型，过拟合
5. CNN+GRU模型，40%准确率，有一定意义

6. 后续：加入其他feature和优化模型；或许可以参考老师发的技术指标链接？？
7. 建议：可考虑合成数据的手段？？

- **HMM模型和傅立叶**
1. 加入AIC、BIC：用于证明状态个数的选择；状态2、4不好，状态3好
2. 傅立叶：尝试滤波，应用梯度下降法、最小二乘法；42个月的周期占主导

3. 后续：测试对比状态2、3的策略收益
4. 建议：报告可以放图表，证明各个市场的指数都存在周期

- **计量检验**
1. 月度宏观指标及其同比：画图，失业率突出；正态性检验大部分因子的QQ图不好，但不一定要放报告（PPI比较符合正态）；平稳性检验（部分平稳，因子需改进）
2. Causality：宏观指标对1-12个月后的指数收益都有影响，但p值逐渐变大

3. 后续：测试和检验环比、差分和其他数据；尝试计量logistics预测模型；进行回归，推出有效的feature传递给ML模型

- **牛熊识别**
1. LT识别：简单一点，拐点多些（原理：波峰后，收益率开始下降。。。）
2. PS or BB算法：复杂一点，效果好些（原理：抛弃前后5个月数据，涨跌阈值，持续涨跌。。。）

3. 后续：两个算法互相验证，选一个作为结果，传递给ML模型


- **其他想法**
1. HMM是否可以作为x放到ml里面？（神经网络）
2. 不同state用不同的model？复合模型？
3. 如果变的频繁：损失函数，不仅损失小，同时变化少（平滑处理），是否会更好？
4. Baseline模型，对比的是各个模型的01预测准确率，还是各个模型的策略收益率？


### 1.31-2.1工作
1. 队员24h内把自己目前的工作在git上备份（ML和计量目录下，每人一个文件夹）
2. 队长与指导老师沟通目前的文章结构、模型运用、思路验证等；**询问老师：是要做单一的复合策略，还是多个模型各自一个简单策略**



***
### 1.27 会议大纲
- 各成员讨论行文思路，模型选取 
- 下次会议 **(1.30)** 之前任务及分工
### 讨论内容  
- **行文思路（暂定）**
1. 傅里叶变换分析Russell频谱，得到周期和相位，从而证明指数存在周期性，周期决定了宏观上的牛熊状态。
2. 计量模型。验证模型假设，分布，平稳性，因果检验，把有影响的筛出来做correlation matrix。线性回归，分析残差，是否符合正态分布，共线性检验，通过vif检测，异方差，自相关，引入广义模型。
3. 基于识别模型确定历史上的牛熊状态 / 借鉴高盛研究结果。
4. 预测部分，结合多个ml模型比较斟酌，制定最终的交易策略。

- **模型**
1. 傅里叶频谱分析已经初步达到效果。
2. HMM初步得到简单的稳定结果。
3. 优化HMM，选取合适features以及状态数。
《基于特征选择和HMM的股票价格行为研究》
4. 有监督学习如何使用label，待商议。
方案1：使用识别模型生成labels，用于训练。
《中国股票市场的牛熊市的识别与预测_叶露》
方案2：直接使用收益率序列的正负形用于训练，提取网络隐藏层的信息。
方案3：使用高盛研报的牛熊判定。
5. 模型之间如何过渡，待商议。
方案1：并行，制定标准比较模型优劣，做图表。
方案2：部分串联，以识别模型的结果为rnn的labels，hmm与识别模型对比交叉验证。
方案3：构建复合信号。

### 1.27-1.30工作
各成员汇总可用因子，梳理可行的论文逻辑线  
- 魏泽伦：找数据，优先网站，如找不到，则使用bbg。
- 赵翔宇：初步尝试计量模型部分。
- 刘昶、谭浩喆、黄思扬：实现识别模型，优化完善hmm，fourier。
- 王光宇：尝试以收益率为label的dl模型。

***
### 1.23 会议大纲
- 各成员汇总信息、讨论思路  
- 下次会议 **(1.27)** 之前任务及分工
### 讨论内容  
- **量价指标**
1. 情绪指标/恐怖指数：VIX   
[ref: 中金 | 海外：从情绪和流动性指标看美股当前波动 ](https://mp.weixin.qq.com/s/Y7LfBzoImKyXoAyYxktP2w)
3. 牛熊指标: 波动率/换手率    
ref:《波动率与换手率构造牛熊指标》  
5. 全球统一择时信号：对全球11个指数利用同比指标择时,超过5个看多后得到   
ref:《全球多市场择时配置初探》  
5. RSRS    
ref:《基于阻力支撑相对强度(RSRS)的市场择时》   
6. 景气指标：加权统计过去6个月机构预测行业板块对未来一年盈利预测上调的百分比（需Bloomberg找机构一致预期）  
ref: 《中观行业配臵系列一:分析师行业景气指数构建与应用》
- **经济指标**  
CPI、PPT、GDP、PMI、国债收益率  
用市盈率、美国ISM及PMI数据、美国失业率、美国国债期限利差和美国核心通胀率等宏观指标数据构建“牛/熊市风险指标”

- **模型**
1. 基于规则识别和预测中国股票市场牛熊市状态  
2. hmm模型：单纯用收益率序列做预测也能跑赢基准    
[HMM隐马尔可夫模型详解](https://blog.csdn.net/weixin_41923961/article/details/82750687)  
[利用隐马尔可夫模型预测股票价格（附代码）](https://zhuanlan.zhihu.com/p/51418002)  
[隐马尔可夫模型|股票预测](https://zhuanlan.zhihu.com/p/108992049)  
《High-order Hidden Markov Model for trend prediction in financial time series》
4. 奇异谱分析：比ma能更快预测到市场变化  
[基于奇异谱分析的均线择时研究](https://uqer.datayes.com/v3/community/share/577cbae4228e5b8a02931e1a)
6. 傅里叶变换：暂时达不到华泰研报中的效果，但做好了会增加亮点，考虑与hmm相结合  
7. 神经网络：RNN、lstm等

- **其他**
熊市分类问题：结构性熊市S,事件驱动型熊市E，周期性熊市C  
[高盛美股熊市指南](https://m.sohu.com/a/197597545_313170)  
《Predicting bear and bull stock markets with dynamic binary time series models》

### 1.23-1.27工作
各成员汇总可用因子，梳理可行的论文逻辑线  
- 魏泽伦：找数据，确定时间段、频率、插补方式等
- 黄思扬、赵翔宇：总结计量模型中因子检验的流程方法
- 刘昶、谭浩喆、王光宇：研究要用的机器学习模型


***
### 1.20 会议大纲

1. 时间线

2. 下次会议前工作安排

### 时间线

1.20 - 1.30 查阅文献，咨询教授，选定方法

1.31 - 2.6 获取数据，模型搭建，数据分析

2.7 - 2.13 依据分析结果进行回测验证，得到conclusion

2.14 - 2.20 汇编前期工作，得到初稿

2.21 - 2.27 咨询教授，最终定稿

### 下次会议前工作安排

下次会议时间：1.23 上午

下次会议前完成：每位成员阅读历史获奖文章，理清获奖文章结构；阅读研报和论文，为小组研究方向和模型提供意见

#### 附录：一些有用的链接

0. 历史获奖文章：https://www.dropbox.com/sh/wl11t0ty7yan7s9/AACTlz04KtzKblZlgc74ZdB8a?dl=0 
1. 研报库(思杨)：https://drive.google.com/drive/folders/1xaXMDSs_EISwhddeO7SQ0f66HDmHZCTD?usp=sharing
3. 【华泰金工林晓明团队】市场拐点的判断方法：https://mp.weixin.qq.com/s/Kejku8IYgIYYcOsVxydiDA
4. AI算法技能包 | 牛市熊市怎么预测：https://mp.weixin.qq.com/s/u3fKXi8qVLCXljIl8HtDxg
