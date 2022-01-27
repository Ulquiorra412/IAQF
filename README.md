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
1. 傅里叶频谱分析已经初步达到效果
2. HMM初步得到简单的稳定结果
3. 优化HMM，选取合适features以及状态数。
《基于特征选择和HMM的股票价格行为研究》
4. 有监督学习如何使用label，待商议。
方案1：使用识别模型生成labels，用于训练。
《中国股票市场的牛熊市的识别与预测_叶露》
方案2：直接使用收益率序列的正负形用于训练，提取网络隐藏层的信息。
方案3：使用高盛研报的牛熊判定
5. 模型之间如何过短，待商议。
方案1：并行，制定标准比较模型优劣，做图表。
方案2：部分串联，以识别模型的结果为rnn的labels，hmm与识别模型对比交叉验证。
方案3：构建复合信号。

### 1.23-1.27工作
各成员汇总可用因子，梳理可行的论文逻辑线  
- 魏泽伦：找数据，优先网站，如找不到，则使用bbg。
- 赵翔宇：初步尝试计量模型部分。
- 刘昶、谭浩喆：实现识别模型，优化完善hmm，fourier。
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
