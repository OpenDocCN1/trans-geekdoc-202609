

**表52.5：对数贝叶斯因子摘要。**

| | **SVJ vs. SV** | **SVIJ vs. SV** | **SVIJ vs. SVJ** | **SVCJ vs. SV** | **SVIJ vs. SVCJ** |
|---|---|---|---|---|
| 贝叶斯因子 | 19.90 | 34.71 | 10.13 | 21.18 | 13.53 |

对数贝叶斯因子为1表明竞争模型优于基础模型；因子为3到5表明存在强烈证据反对基础模型；大于5则是支持竞争模型的可靠证据。此外，贝叶斯因子可以转换为常规的t值。在样本量为1,000的情况下，对数贝叶斯因子为1相当于2.63；为2相当于3.59；为3相当于4.11。

表52.5汇总了所选模型之间的贝叶斯因子。SVJ、SVIJ和SVCJ的解释能力均优于SV模型。SVCJ明显优于SVJ模型，但又不如SVIJ模型。因此，在四个竞争模型中，SVIJ模型的解释能力最强。

### 52.5 事件匹配与估计结果

泰铢的历史价格可以解释为泰国政府、市场投机者以及外汇市场其他各方之间相互作用的结果。尽管外汇市场参与者显然有不同的目标，我们的估计结果可用于更好地理解不同市场参与者如何影响泰铢的行为。我们以Nouriel Roubini¹整理的亚洲金融危机年表和Ito（1999）对泰国货币危机的总结作为事件描述的主要来源。由于SVIJ和SVCJ结果相似，且SVIJ是更好的解释模型，本节将重点关注SVIJ的结果。图52.11展示了1997年4月至1998年12月SVIJ估计结果的详细图。

![](img/31ee7e6fa5107b22bbf7960ec96106a1_2049_0.png)

**图52.11：** SV和SVIJ模型估计的波动率，以及SVIJ模型观测方程中的跳跃，时间范围为1997年4月1日至1998年12月31日。

#### 52.5.1 1997年5月之前及期间

由于泰国GDP增长率缓慢且金融机构不稳定，泰铢在1997年引起了投机者的关注。1997年1月、2月和5月发生了数波投机性攻击。然而，SV族模型的估计结果显示泰铢未受这些攻击影响。5月，情况发生了急剧变化。从5月12日开始的一波波攻击使SVIJ模型的估计波动率从0.04大幅上升至2.24。模型识别出特定时期内的波动率跳跃，这表明泰国政府未能维持其外汇市场的稳定。

#### 52.5.2 1997年6月至7月

6月11日识别出另一次波动率跳跃，当时投机者继续攻击泰铢。幅度为8.873，推动估计波动率升至10.05。这一跳跃标志着更加动荡阶段的开始。在此期间，日变动超过3%变得常见。例如，泰铢于6月17日升值4.15%，6月19日贬值6.19%，6月27日升值4.54%，最终于7月2日贬值17%。SVIJ模型估计7月2日观测方程存在11.3%的跳跃，并将这35%变动中的剩余部分归因于条件波动率。

虽然7月2日之后泰铢继续下滑，但估计波动率逐渐下降，除少数零星时刻外。下一次主要波动率跳跃发生在10月6日，当日泰铢贬值3.43%，次日升值3.15%。SVIJ模型将其识别为波动率跳跃，幅度为4.9。

Kass, R. E. and Raftery, A. E. (1995). Bayesian Factors. *Journal of the American Statistical Association*, 90, 773–795.

Kim, S., Shephard, N., and Chib, S. (1998). Stochastic Volatility: Likelihood Inference and Comparison with ARCH Models. *The Review of Economic Studies*, 65(3), 361–393.

Kou, Steven, Yu, C. and Zhong, H. (2017). Jumps in Equity Index Returns Before and During the Recent Financial Crisis: A Bayesian Analysis. *Management Science*, 63(4), 988–1010.

Li, Haitao, Wells, M. T. and Yu, C. L. (2008). A Bayesian Analysis of Return Dynamics with Levy Jumps. *The Review of Financial Studies*, 21(5), 2345–2378.

Merton, R. (1976a). Option Pricing when the Underlying Stock Returns are Discontinuous, *Journal of Financial Economics*, 3, 125–144.

Merton, R. (1976b). The Impact on Option Pricing of Specification Error in the Underlying Stock Price Returns. *Journal of Finance*, 31, 333–350.

Ito, T. (1999). The Development of the Thailand Currency Crisis: A Chronological Review, NBER Session on Thailand, April 22.

Venkataraman, S. (1997). Value at risk for a mixture of normal distributions: The use of quasi-Bayesian techniques, *Federal Reserve Bank of Chicago Economic Perspectives*, 21(2), 2–13.

Zangari, P. (1996). An Improved Methodology for Measuring VAR, Risk Metrics Monitor.

## 第53章：条件异方差下盈余公告的系统性风险修正

Chin-Chen Chien、Cheng Few Lee、She-Chih Chiu

### 目录

- 53.1 引言 ........................................ 1970
- 53.2 模型开发 .................................. 1973
- 53.3 研究设计 ...................................... 1975
  - 53.3.1 标准化未预期盈余（SUEs）的估计 ..... 1975
  - 53.3.2 研究方法 ........................ 1976
- 53.4 数据与实证结果 ........................ 1977
  - 53.4.1 数据 ............................................. 1977
  - 53.4.2 日股票收益的ARCH效应检验 ... 1977
  - 53.4.3 实证结果 ............................... 1978
- 53.5 结论 ............................................ 1985
- 参考文献 ................................................ 1986
- 附录53A ................................................ 1988

Chin-Chen Chien  
国立成功大学  
e-mail: chien442001@yahoo.com.tw

Cheng Few Lee  
罗格斯大学  
e-mail: cflee@business.rutgers.edu

She-Chih Chiu  
国立台北大学  
e-mail: scchiu@mail.ntpu.edu.tw

### 摘要

本章旨在通过关注盈余信息发布后系统性风险的修正，来探索盈余公告后漂移之谜。本章将ARCH纳入CAPM，提出一个具有时变系统性风险的市场模型。然后采用卡尔曼滤波估计市场如何在盈余公告后修正其风险评估。本章还基于2010–2014五个会计年度期间美国上市公司的样本进行了实证分析。在控制风险修正并隔离潜在混杂效应后，本章发现会计文献中充分记载的盈余公告后漂移现象不再存在。

### 关键词

ARCH（自回归条件异方差）• CAPM • 卡尔曼滤波 • 盈余公告后漂移。

### 53.1 引言

Ball和Brown（1968）首次观察到的盈余公告后漂移（PEAD）现象已被现代会计研究广泛调查（Cartwright and Lee, 1987; Bernard and Thomas, 1989; Bhushan, 1994; Ke and Ramalingegowda, 2005; Garfinkel and Sokobin, 2006; Sadka, 2006; Francis et al., 2007; Ng et al., 2008; Ayers et al., 2011; Chung and Hrazdil, 2011; Louis and Sun, 2011; Shin and Park, 2018; Wang et al., 2018）。然而，这一现象是由于研究设计不当还是市场无效的标志，尚无定论。

在那些难以主张股票市场无效的人中，Ball（1978）、Foster等人（1984）（以下简称FOS）和Ball等人（1993）（以下简称BKW）将这一现象归因于系统性风险的非平稳性。他们认为，系统性风险可能未被完全调整，因为用于计算异常收益的资本资产定价模型（CAPM）要么不完整，要么设定错误。因此，所谓的异常收益代表了对已定价但未被CAPM捕捉的风险承担的公平补偿。Ball和Bartov（1996）进一步认为，盈余公告后的可预测股票收益仍然是异常的，可能源于样本选择或异常收益测量的偏差。另一方面，Bernard和Thomas（1989、1990，以下简称BT）认为资产定价模型设定错误的推论是没有根据的。在调查了盈余公告后漂移的几个可能来源后，BT简洁地总结道，这种漂移是对市场效率信念的不利证据。更具体地说，漂移是由于价格对充分

