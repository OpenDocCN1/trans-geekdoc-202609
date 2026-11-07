
一个重要的含义是方法选择很重要。这给研究人员和实践者留下了很大的自由裁量权，因此他们提供的答案将反映他们所做的方法论选择。通往“真理”没有捷径，但最近的实践已远离倾向得分匹配。方法选择的丰富性确实要求我们再次警惕，仅仅报告似乎给出“最合理”结果的方法的结果，因为这会导致潜在的严重偏差，从而削弱我们推断因果关系的能力。

本章描述的技术被广泛使用，尤其是在社会科学中，但并未穷尽所有可能性。在下一章中，我们将讨论断点设计、合成控制的创建以及重要的工具变量方法。

第70页 这里讨论的大多数匹配方法，包括协变量匹配，都可以在 Stata 中使用 `teffects` 命令进行估计。CEM 可以使用 `cem` 命令完成。

## 注释

1. `Z` 也被称为中介变量，因为它位于处理变量 `T` 和结果变量 `Y` 之间。还有一个因果推断的子领域称为中介分析，旨在理解 `T` 对 `Y` 的直接和间接效应，这超出了本书的范围；有关该主题的详细信息请参阅 [Vanderweele (2015)](#chapter3.xhtml#ref3_25)。 [⏎](#chapter3.xhtml#en3_13b)

第71页

## 参考文献

*   Blackwell, Matthew, Stefano Iacus, Gary King, and Giuseppe Porro. 2009. “Cem：Stata 中的粗化精确匹配”. The Stata Journal, 9(4): 524–546. [⏎](#chapter3.xhtml#b3ref3_1)
*   Crump, Richard, Joseph Hotz, Guido Imbens, and Oscar Mitnik. 2009. “处理平均处理效应估计中的有限重叠”. Biometrika, 96(1): 187–199. [⏎](#chapter3.xhtml#b3ref3_2)
*   Dehejia, Rajeev, and Sadek Wahba. 2002. “非实验因果研究的倾向得分匹配方法”. Review of Economics and Statistics, 84(1): 151–161. [⏎](#chapter3.xhtml#b3ref3_3)
*   Diamond, Alexis. 2005. “非实验环境下平均和分位数因果效应的可靠估计”. Working draft. Cambridge, MA: Harvard University. [⏎](#chapter3.xhtml#b3ref3_4)
*   Diamond, Alexis, and Jasjeet Sekhon. 2013. “用于估计因果效应的遗传匹配：实现观察性研究平衡的一般多元匹配方法”. Review of Economics and Statistics, 95(3): 932–945. [⏎](#chapter3.xhtml#b3ref3_5)
*   Drukker, David. 2016. “使用 Teffects、Stteffects 和 Eteffects 从观察数据中估计处理效应”. Presented at UK Stata Users’ Group Meeting 2016. London: Stata Users Group. [⏎](#chapter3.xhtml#b3ref3_6)
*   Glynn, Adam, and Kevin Quinn. 2010. “增广逆倾向加权估计量的介绍”. Political Analysis, 18: 36–56. [⏎](#chapter3.xhtml#b3ref3_7)
*   Haughton, Jonathan, and Alison Kelly. 2014. “入门商业统计课程中的学生表现：授课方式重要吗？”. Journal of Education for Business, 90(1): 31–43. [⏎](#chapter3.xhtml#b3ref3_8)
*   Hernán, Miguel, and James Robins. 2006. “从流行病学数据中估计因果效应”. Journal of Epidemiology and Community Health, 60: 578–596. [⏎](#chapter3.xhtml#b3ref3_9)
*   Hernán, Miguel, and James Robins. 2025. “因果推断：What If”. Boca Raton, FL: CRC Press. [⏎](#chapter3.xhtml#b3ref3_10)
*   Hitchcock, Christopher. 2010. “概率因果”. In *Stanford Encyclopedia of Philosophy*, [https://stanford.library.sydney.edu.au/archives/sum2010/entries/causation-probabilistic/#Int](https://stanford.library.sydney.edu.au/archives/sum2010/entries/causation-probabilistic/#Int) \[Accessed June 11, 2020\] [⏎](#chapter3.xhtml#b3ref3_11)
*   Ho, Daniel, Kosuke Imai, Gary King, and Elizabeth Stewart. 2006. “匹配作为减少参数因果推断中模型依赖性的非参数预处理”. [http://gking.harvard.edu/files/matchp.pdf](http://gking.harvard.edu/files/matchp.pdf) \[An excellent guide for practitioners.\] [⏎](#chapter3.xhtml#b3ref3_12)
*   Holland, Paul W. 1986. “统计学与因果推断”. Journal of the American Statistical Association, 81(396): 945–960. [https://doi.org/10.2307/2289064](http://dx.doi.org/10.1080/01621459.1986.10478354) [⏎](#chapter3.xhtml#b3ref3_13)
*   Iacus, Stefano Maria, Gary King, and Giuseppe Porro. 2008. “无需平衡检验的因果推断匹配”. [https://doi.org/10.2139/ssrn.1152391](http://dx.doi.org/10.2139/ssrn.1152391) [⏎](#chapter3.xhtml#b3ref3_14)
*   Imbens, Guido. 2004. “外生性下平均处理效应的非参数估计：综述”. Review of Economics and Statistics, 86(1): 4–29. [⏎](#chapter3.xhtml#b3ref3_15)
*   Keeter, Scott. 2021. “问答：关于 2020 年美国选举民调问题的对话”. Short Reads, Pew Research Center. [https://www.pewresearch.org/short-reads/2021/07/21/a-conversation-about-u-s-election-polling-problems-in-2020/](https://www.pewresearch.org/short-reads/2021/07/21/a-conversation-about-u-s-election-polling-problems-in-2020/) [⏎](#chapter3.xhtml#b3ref3_16)
*   Kennedy, Courtney, and Hannah Hartig. 2019. “电话调查的响应率已恢复下降趋势”. In Short Reads, Washington, DC: Pew Research Center. [https://www.pewresearch.org/short-reads/2019/02/27/response-rates-in-telephone-surveys-have-resumed-their-decline/](https://www.pewresearch.org/short-reads/2019/02/27/response-rates-in-telephone-surveys-have-resumed-their-decline/) [⏎](#chapter3.xhtml#b3ref3_17)
*   King, Gary, and Richard Nielsen. 2019. “为什么不应将倾向得分用于匹配”. Political Analysis, 27: 4. [https://j.mp/2ovYGsW](https://j.mp/2ovYGsW) [⏎](#chapter3.xhtml#b3ref3_18)

第72页
*   Lee, Brian, Justin Lessler, and Elizabeth Stuart. 2011. “权重修剪与倾向得分加权,” PLOS ONE, 6(3): e18174. [⏎](#chapter3.xhtml#b3ref3_19)
*   Maciel, Fernanda. 2020. “巴西弱势群体的分析”. *PhD dissertation*, Bentley University. [⏎](#chapter3.xhtml#b3ref3_20)
*   Morgan, Stephen, and Christopher Winship. 2015. “反事实与因果推断：社会研究的方法与原则，第二版”. New York, NY: Cambridge University Press. [⏎](#chapter3.xhtml#b3ref3_21)
*   Optimizely. 2020. *实验大书*. [https://www.optimizely.com/resources/experimentation-case-studies/](https://www.optimizely.com/resources/experimentation-case-studies/) \[Accessed June 11, 2020\] [⏎](#chapter3.xhtml#b3ref3_22)
*   Pearl, J. 1995. “用于实证研究的因果图”. Biometrika, 82(4): 669–710. [⏎](#chapter3.xhtml#b3ref3_23)
*   Rosenbaum, P., and D. Rubin. 1983. “倾向得分在因果效应观察性研究中的核心作用”. Biometrika, 70(1): 41–55. [⏎](#chapter3.xhtml#b3ref3_24)
*   Vanderweele, Tyler J. 2015. “因果推断中的解释：中介与交互的方法”. New York, NY: Oxford University Press. [⏎](#chapter3.xhtml#b3ref3_25)

第73页

# 4 因果关系：合成控制、回归不连续性和工具变量

DOI: [10.1201/9780429172588-4](https://doi.org/10.1201/9780429172588-4)

## 4.1 引言

在 [第3章](#chapter3.xhtml) 中，我们讨论了多种估计因果效应的技术。但关于该主题还有更多内容需要说明，在本章中，我们首先讨论双重差分，然后解释合成控制、回归不连续性和工具变量的方法。

