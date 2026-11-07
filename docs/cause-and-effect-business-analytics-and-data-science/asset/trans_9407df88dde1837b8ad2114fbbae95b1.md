
## 脚注

7. 敏感性分析有意义的常见适当情况是可控参数。例如，人们可能有兴趣评估额外预算或更低预算对最优解的影响。第249页 [⏎](#chapter8.xhtml#en8_78b)

8. Lo 和 Pachamanova (2015) 概述了使用均值和方差作为目标函数的另一种 `MVO` 形式化方法。 [⏎](#chapter8.xhtml#en8_88b)

9. 这里在 `Excel` 中使用多功能函数进行 `Eqn. (8.9)` 的矩阵计算；请参阅 [Jackson 和 Staunton (2003)](#chapter8.xhtml#ref8_18) 以了解示例。 [⏎](#chapter8.xhtml#en8_98b)

10. 从 [示例 8.1](#chapter8.xhtml#sec8_3_1) 获得的确定性解被用作每个预设最小均值值的起始解。 [⏎](#chapter8.xhtml#en8_108b)

11. 我们只讨论可实际应用于提升优化的随机规划 (`SP`) 的一个子集。例如，`SP` 的一个分支称为场景优化，要求为所有可能的模拟场景找到一个共同解（参见 [Wallace 和 Ziemba (2005)](#chapter8.xhtml#ref8_36)、Zenios (2007) 或 [King 和 Wallace (2012)](#chapter8.xhtml#ref8_20)），并且特别适合多阶段优化问题。由于其在提升情况下的复杂性以及大多数提升问题都是单阶段的事实，这里不讨论场景优化。 [⏎](#chapter8.xhtml#en8_118b)

12. 例如，请参阅 [Jorion (2006)](#chapter8.xhtml#ref8_19) 了解 `VaR` 以及其他风险度量（如条件风险价值，`CVaR`）的详细信息。 [⏎](#chapter8.xhtml#en8_128b)

13. `CB` 中的随机优化基于一种称为 `Simulation Optimization` 的启发式方法；请参阅 [附录 8.2](#chapter8.xhtml#app8_2) 简要介绍，或 EPM Information Development Team (2009) 或 Better et al. (2008) 了解更多详细信息。其他 `Excel` 插件软件如 `@Risk` 和 Frontline Systems 也具有 `Simulation Optimization` 功能。在 [示例 8.3c](#chapter8.xhtml#sec8_5_3_1) 中的所有解中，使用以下设置：模拟次数 = 1,000，试验次数 = 1,000。 [⏎](#chapter8.xhtml#en8_138b)

14. [示例 8.3c](#chapter8.xhtml#sec8_5_3_1) 中随机优化的所有解均使用 [示例 8.1](#chapter8.xhtml#sec8_3_1) 中 [表 8.2](#chapter8.xhtml#tbl8_2) 的最优解作为初始解。 [⏎](#chapter8.xhtml#en8_148b)

15. [示例 8.2](#chapter8.xhtml#sec8_4_1) 的自助法结果在 `Crystal Ball` 中用于每个不确定（随机）变量的“自定义”分布（即离散均匀分布，每个自助法观测值概率相等）。此外，[表 8.4](#chapter8.xhtml#tbl8_4) 中的相关性被作为输入，因此随机数生成机制将以多元方式模拟值——默认情况下在 `Crystal Ball` 中，多元模拟使用一种称为 `Gaussian copula` 的常见依赖结构；例如参见 [Trivedi 和 Zimmer (2005)](#chapter8.xhtml#ref8_33) 或 [Meissner (2014)](#chapter8.xhtml#ref8_25)。 [⏎](#chapter8.xhtml#en8_158b)

16. `Crystal Ball` 在 [图 8.7](#chapter8.xhtml#fig8_7) 中选择对数正态分布作为最佳拟合分布。同样，`Crystal Ball` 为 [图 8.8](#chapter8.xhtml#fig8_8) 和 [8.9](#chapter8.xhtml#fig8_9) 中的其他解选择最佳拟合分布。 [⏎](#chapter8.xhtml#en8_168b)

17. 严格来说，只有总体方差-协方差矩阵保证是半正定的，但样本方差-协方差矩阵不一定都具有此性质。 [⏎](#chapter8.xhtml#en8_178b)

## 参考文献

* Bertsimas, Dimitris, and John N. Tsitsiklis. 1997. 线性规划导论. Belmont, MA: Athena Scientific. [⏎](#chapter8.xhtml#b8ref8_1)
* Bertsimas, Dimitris, David B. Brown, and Constantine Caramanis. 2011. “鲁棒优化的理论与应用”. SIAM Review, 53(3): 464–501. [⏎](#chapter8.xhtml#b8ref8_2)
* 第250页 Better, Marco, Fred Glover, Gary Kochenberger, and Haibo Wang. 2008. “仿真优化：风险管理中的应用”. International Journal of Information Technology & Decision Making, 7(4): 571–587. [⏎](#chapter8.xhtml#b8ref8_3)
* Birge, John R., and Francois Louveaux. 1997. 随机规划导论. New York, NY: Springer. [⏎](#chapter8.xhtml#b8ref8_4)
* Cook, William J. 2012. 追寻旅行商问题：计算极限的数学. Princeton, NJ. Princeton University Press. [⏎](#chapter8.xhtml#b8ref8_5)
* Cormen, Thomas H. 2013. 算法揭秘. Cambridge, MA: MIT Press. [⏎](#chapter8.xhtml#b8ref8_6)
* Cornuejols, Gerard, and Reha Tutuncu. 2007. 金融中的优化方法, Cambridge, England: Cambridge University Press. [⏎](#chapter8.xhtml#b8ref8_7)
* Dantzig, George B. 1955. “不确定性下的线性规划”. Management Science, 1, 3 & 4: 197–206. [⏎](#chapter8.xhtml#b8ref8_8)
* Dantzig, George B. 1957. “离散变量极值问题”. Operations Research, 5: 266–277. [⏎](#chapter8.xhtml#b8ref8_9)
* Dasgupta, Sanjoy, Christos H. Papadimitriou, and Umesh V. Vazirani. 2006. 算法. New York, NY: McGraw-Hill. [⏎](#chapter8.xhtml#b8ref8_10)
* Davison, A. C., and D. V. Hinkley. 1997. 自助法及其应用. Cambridge, England: Cambridge University Press. [⏎](#chapter8.xhtml#b8ref8_11)
* Efron, Bradley, and Robert J. Tibshirani. 1993. 自助法导论. Boca Raton, FL: Chapman & Hall/CRC. [⏎](#chapter8.xhtml#b8ref8_12)
* EPM Information Development Team. 2009. Oracle Crystal Ball 决策优化，Fusion 版：发布 11.1.1.3.00. [http://docs.oracle.com/cd/E12825_01/epm.111/cb_oq_user.pdf](http://docs.oracle.com/cd/E12825_01/epm.111/cb_oq_user.pdf) [⏎](#chapter8.xhtml#b8ref8_13)
* Fabozzi, Frank J., Petter N. Kolm, Dessislava A. Pachamanova, and Sergio M. Focardi. 2007. 鲁棒投资组合优化与管理. Hoboken, NJ: Willey. [⏎](#chapter8.xhtml#b8ref8_14)
* Fortnow, Lance. 2013. 金色门票：P、NP 与不可能的探索. Princeton, NJ: Princeton University Press. [⏎](#chapter8.xhtml#b8ref8_15)
* Goldberg, D. E. 1989. 遗传算法在搜索、优化和机器学习中的应用. Boston, MA: Addison-Wesley. [⏎](#chapter8.xhtml#b8ref8_16)
* Higle, Julia L., and Stein W. Wallace. 2003. “线性规划中的敏感性分析与不确定性”. Interfaces, 33(4): 53–60. [⏎](#chapter8.xhtml#b8ref8_17)
* Jackson, Mary, and Mike Staunton. 2003. 使用 Excel 和 VBA 进行金融高级建模. Hoboken, NJ: Wiley. [⏎](#chapter8.xhtml#b8ref8_18)
* Jorion, Philippe. 2006. 风险价值：管理金融风险的新基准，第3版. New York, NY: McGraw-Hill. [⏎](#chapter8.xhtml#b8ref8_19)
* King, Alan J., and Stein W. Wallace. 2012. 随机规划建模. New York NY: Springer. [⏎](#chapter8.xhtml#b8ref8_20)
* Lo, Victor S. Y. 2002. “真实提升模型——数据库营销中响应建模的一种新颖数据挖掘方法”. ACM SIGKDD Explorations, 4(2): 78–86. [⏎](#chapter8.xhtml#b8ref8_21)
* Lo, Victor S. Y., and Dessislava Pachamanova. 2015. “规范性提升分析：解决营销处理优化问题并考虑估计误差风险的实用方法”. Journal of Marketing Analytics, 3(2): 79–95. [⏎](#chapter8.xhtml#b8ref8_22)
* Lo, Victor S. Y., Dessislava Pachamanova, and Nalan Gulpinar. 2017. “分段营销中规范性提升分析的不确定性表示与数据驱动启发式方法”. Technical Paper. [⏎](#chapter8.xhtml#b8ref8_23)
* Markowqitz, Harry. 1952. “投资组合选择”. Journal of Finance, 7(1): 77–91.
* Meissner, Gunter. 2014. 相关风险建模与管理. Hoboken, NJ: Wiley. [⏎](#chapter8.xhtml#b8ref8_25)
