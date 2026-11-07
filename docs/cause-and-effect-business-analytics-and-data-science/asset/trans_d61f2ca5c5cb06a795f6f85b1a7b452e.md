
# 章节阅读概览

建议的书籍章节阅读流程概述于[图 1.8](#chapter1.xhtml#fig1_8)。[第 2 章](#chapter2.xhtml)是对常见统计、计量经济学和机器学习技术的回顾，后续关于因果业务分析和提升建模的章节都建立在这些技术之上。熟悉这些常见技术的读者可以直接跳到其他章节。[第 3 章](#chapter3.xhtml)介绍了因果业务分析（业务中的因果推断），采用更标准的方法如随机实验（也称为 A/B 测试）、潜在结果法和倾向得分匹配。[第 4 章](#chapter4.xhtml)描述了经济学和社会学中广泛使用的额外因果推断技术，包括合成控制法、双重差分和工具变量，但它们也可以用于商业。[第 5 章](#chapter5.xhtml)讨论了一种强大的基于人工智能的方法，即有向无环图或贝叶斯网络，可用于在有或没有可能因果路径的先验知识的情况下发现和量化变量之间的因果关系。

![图 1.8 书籍章节建议阅读流程。⏎](images/fig1_8.jpg)

图 1.8 书籍章节建议阅读流程。 [⏎](#chapter1.xhtml#b1fig1_8)

提升分析在[第 6 章](#chapter6.xhtml)–[第 9 章](#chapter9.xhtml)中讨论。[第 6 章](#chapter6.xhtml)介绍了提升分析的概念以及一种简单的建模方法。[第 7 章](#chapter7.xhtml)讨论了提升的测试与学习流程，包括样本量确定、实验设计和测量指标。[第 8 章](#chapter8.xhtml)提供了提升的规范分析概述，采用数学技术将个人与处理措施进行最优匹配。讨论包括处理模型估计不确定性的技术，基于运筹学、金融和风险管理的方法。[第 9 章](#chapter9.xhtml)讨论了提升分析中的选定高级主题，包括一些最新的提升建模技术，通过将因果推断与提升建模相结合在观察性数据（无随机实验）上开发模型，以及将直接响应数据与实验数据集成用于提升建模。

[第 10 章](#chapter10.xhtml)让我们回到因果业务分析，其中数据以时间序列形式存在，采用市场科学、计量经济学和时间序列分析的方法。[第 10 章](#chapter10.xhtml)讨论了分析时间序列及相关数据的各种高级主题。[第 11 章](#chapter11.xhtml)介绍了结构方程模型（SEM），最初来自心理学和心理测量学，可用于处理商业问题。我们在[第 12 章](#chapter12.xhtml)中以讨论和总结结束本书。实践中的商业问题和数据在全书中用于说明。

## 注释

1. 经济学家通常使用需求自价格弹性来衡量敏感性，其定义为 $\\frac{\\partial lnS}{\\partial lnP}$，具有无量纲的优点。 [⏎](#chapter1.xhtml#en1_11b)

2. 使用来自[图 1.5a](#chapter1.xhtml#fig1_5)的先前拟合销售函数，其中包含混杂因素，价格将为 $6.09，日利润将为 `f(6.09) = (391.5 – 33*6.09) * (6.09 – 2) = $779.27`，导致日利润减少 $23.38。 [⏎](#chapter1.xhtml#en1_21b)

3. 为简单起见，我们假设对照组不接受处理，即保持未接触。在实践中，对照组在营销中可能接受较旧的处理（例如遗留干预方法），或在临床试验中接受“安慰剂”。 [⏎](#chapter1.xhtml#en1_31b)

## 参考文献

* Angrist, Joshua, and Jorn-Steffen Pischke. 2009. 《基本无害的计量经济学：实证主义者的伴侣》. Princeton, NJ: Princeton University Press. [⏎](#chapter1.xhtml#b1ref1_1)

* Angrist, Joshua, and Jorn-Steffen Pischke. 2014. 《精通指标：从原因到效果的路径》. Princeton, NJ: Princeton University Press. [⏎](#chapter1.xhtml#b1ref1_2)

* Athey, S., and G. W. Imbens. 2015. “用于估计异质因果效应的机器学习方法”. 工作论文, Graduate School of Business, Stanford University. [⏎](#chapter1.xhtml#b1ref1_3)

* Cartwright, Nancy. 2007. 《追寻原因并利用它们：哲学与经济学中的方法》. New York, NY: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_4)

* Cartwright, Nancy, and Jeremy Hardie. 2012. 《循证政策：做得更好的实用指南》. New York, NY: Oxford University Press. [⏎](#chapter1.xhtml#b1ref1_5)

* Dunning, Thad. 2016. 《社会科学中的自然实验：一种基于设计的途径》. Cambridge: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_6)

* Gertler, Paul J., Sebastian Martinez, Patrick Premand, Laura B. Rawlings, and Christel M.J. Vermeersch. 2016. 《实践中的影响评估，第二版》. Washington, DC: World Bank Group. [⏎](#chapter1.xhtml#b1ref1_7)

* Glymour, Clark. 2001. 《心灵之箭：心理学中的贝叶斯网络与图形因果模型》. Cambridge, MA: MIT Press. [⏎](#chapter1.xhtml#b1ref1_8)

* Green, Paul E., and V. Srinivasan. 1990. “营销研究中的联合分析：新发展与方向”. 《营销期刊》, 54(4): 3–19. [⏎](#chapter1.xhtml#b1ref1_9)

* Hernan, Miguel A., and James M. Robins. 2020. 《因果推断》. Boca Raton, FL: Taylor & Francis. [⏎](#chapter1.xhtml#b1ref1_10)

* Imbens, Guido W., and Donald B. Rubin. 2015. 《统计、社会和生物医学科学的因果推断：导论》. New York, NY: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_11)

* Jackson, Robert, and Paul Wang. 1996. 《战略数据库营销》. Chicago, IL: NTC Publishing. [⏎](#chapter1.xhtml#b1ref1_12)

* Jordan, Michael I. 2019. “人工智能——革命尚未发生”. *哈佛数据科学评论*, issue 1.1. [https://hdsr.mitpress.mit.edu/pub/wot7mkc1](https://hdsr.mitpress.mit.edu/pub/wot7mkc1) [⏎](#chapter1.xhtml#b1ref1_13)

* Lee, Myoung-Jae. 2005. 《政策、项目和处理效应的微观计量经济学》. New York, NY: Oxford University Press. [⏎](#chapter1.xhtml#b1ref1_14)

* Lee, Myoung-Jae. 2016. 《匹配、回归不连续、双重差分及其以后》. New York, NY: Oxford University Press. [⏎](#chapter1.xhtml#b1ref1_15)

* Lo, Victor S. Y. 2019a. “寻找完美独角兽”. Informs: Analytics, 1(1). [https://doi.org/10.1162/99608f92.ba20f892](https://doi.org/10.1162/99608f92.ba20f892) [⏎](#chapter1.xhtml#b1ref1_16)

* Lo, Victor S. Y. 2019b. “实践中使用的三种分析类型及其联系”. *CIO Review*. [⏎](#chapter1.xhtml#b1ref1_17)

* Meng, Xiao-Li. 2019. “数据科学：一个人工生态系统”. 《哈佛数据科学评论》, 1(1). [https://doi.org/10.1162/99608f92.ba20f892](https://doi.org/10.1162/99608f92.ba20f892) [⏎](#chapter1.xhtml#b1ref1_18)

* Morgan, Stephen, and Christopher Winship. 2015. 《反事实与因果推断：社会研究的方法与原则，第二版》. New York, NY: Cambridge University Press.

* Rosenbaum, P. R. 2002. 《观察性研究》. New York, NY. Springer. [⏎](#chapter1.xhtml#b1ref1_19)

* Rosenbaum, P. R. 2010. 《观察性研究设计》. New York, NY. Springer. [⏎](#chapter1.xhtml#b1ref1_20)

* Rosenbaum, Paul R., and Donald B. Rubin 1983. “倾向得分在因果效应观察性研究中的核心作用”. Biometrika, 70(1): 41–55.

* Rubin, D. B. 2006. 《用于因果效应的匹配抽样》. New York, NY: Cambridge University Press. [⏎](#chapter1.xhtml#b1ref1_22)
