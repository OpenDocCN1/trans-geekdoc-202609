
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_138_0.png)

图 4.12 来自委员会模型 Lumped-MF-A 的流量过程线结果。

NSE(LF)，最高值位于图表底部，分别为 0.71 和 0.77，最低值位于图的上部，分别为 0.55 和 0.62。所有单模型（集总式和分布式）出现在图的上部（RMSE 最高、NSE 最低），而委员会模型出现在图表底部（RMSE 最低、NSE 最高），这表明委员会模型在所有性能指标上均优于所有单模型。图 4.13 与图 4.11 显示，分布式模型中单元尺寸的影响非常微弱，这表明有必要对概念性分布式模型进行更多研究。

NSGA-II 找到的最佳 70 种模型参数化在图 4.15 中以最优非支配解的 Pareto 前沿形式呈现。它还说明了所选目标之间的权衡，并表明单模型无法同时匹配流域响应的全部变异性。校准数据集的最优参数集并不优于验证数据集，因此针对校准数据集获得的高低流量最佳专业化模型在验证数据集中并非最佳（在其他 Pareto 最优集中）。

图 4.15 显示，委员会模型比单模型和 Pareto 前沿的所有成员更接近理想点。这确保了委员会模型的性能优于任何其他单模型。校准中的最优模型不一定在验证中也是最好的。然而，校准和验证中的版本必须非常接近。所有委员会模型的组合在校准和验证数据集中均优于所有 Pareto 成员。

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_139_0.png)

图 4.13 校准期最大洪水事件期间委员会模型的性能。

很容易注意到 RMSE_LF 的值始终高于 RMSE_HF 的值。其原因在于低流量期远长于高流量期，因此可以预期较长时期的误差高于较短时期（低流量值数量多于高流量值），并且加权均方根误差求和公式中的误差除以相同的观测总数，见（图 4.15）。

为再现水文响应特定方面（高低流量模型）而开发的专业化模型委员会，使用模糊隶属函数组合，成功利用了各模型的优势来提高委员会的性能。这使其性能比所有单模型和所有 Pareto 前沿成员更接近理想点，从而确保委员会模型的性能优于任何其他单模型。

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_140_0.png)

图 4.14 所有模型归一化性能指标用于视觉比较，呈现了每个误差的最大值和最小值。底部的委员会模型具有更低的 RMSE、RMSE(LF) 和 RMSE(HF)，以及更高的 NSE(LF) 和 NSE(HF)；因此，在所有指标上性能均更好。

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_140_1.png)

图 4.15 多目标优化和不同模型得到的专业化模型的 Pareto 最优集。

## 致谢

我们感谢萨尔瓦多环境和自然资源部（MARN）提供本研究使用的数据。我们还感谢 Rotary 基金会（TRF）在 Rotary 奖学金框架内提供的资金支持。

## 参考文献

- Abrahart, R. J., & See, L. (2000). 比较神经网络和自回归移动平均技术在两个对比流域提供连续河流流量预报中的应用。 Hydrological Processes, 14(11–12), 2157–2172. https://doi.org/10.1002/1099-1085(20000815/30)14:11/12<2157::AID-HYP57>3.0.CO;2-S
- Agawa, T., & Takeuchi, O. (2016). 重新审视日本 EFL 学习者的心理需求和二语动机：一项访谈研究。 Asian EFL Journal, 89(89), 74–98.
- Ajami, N. K., Duan, Q., Gao, X., & Sorooshian, S. (2006). 水文模拟分析的多模型组合技术：应用于分布式模型互对比项目结果。 Journal of Hydrometeorology, 7(4), 755–768. https://doi.org/10.1175/jhm519.1
- Beven, K. (1996). 地貌建模中的等效性与不确定性。 The Scientific Nature of Geomorphology. Proceeding of the 27th Binghamton Symposium in Geomorphology, September 1996, 289–314.
- Clemen, R. T. (1989). 组合预测：综述与注释书目。 International Journal of Forecasting, 5(4), 559–583. https://doi.org/10.1016/0169-2070(89)90012-5
- Corzo, G., & Solomatine, D. (2007). 用于流量预报模块化人工神经网络建模的基流分离技术。 Hydrological Sciences Journal, 52(3), 491–507. https://doi.org/10.1623/hysj.52.3.491
- Deb, K., Pratap, A., Agarwal, S., & Meyarivan, T. (2002). 一种快速且精英的多目标遗传算法：NSGA-II。 IEEE Transactions on Evolutionary Computation, 6(2), 182–197. https://doi.org/10.1109/4235.996017
- Dehotin, J., & Braud, I. (2008). 分布式水文模型采用何种空间离散化？针对中大型流域的方法论建议及示例。 Hydrology and Earth System Sciences, 12(3), 769–796. https://doi.org/10.5194/hess-12-769-2008
- Duan, Q., Ajami, N. K., Gao, X., & Sorooshian, S. (2007). 使用贝叶斯模型平均的多模型集合水文预测。 Advances in Water Resources, 30(5), 1371–1386. https://doi.org/10.1016/j.advwatres.2006.11.014
- Fenicia, F., Solomatine, D. P., Savenije, H. H. G., & Matgen, P. (2007). 多目标框架下局部模型的软组合。 Hydrology and Earth System Sciences, 11(6), 1797–1809. https://doi.org/10.5194/hess-11-1797-2007
- Fernando, D. A. K., Shamseldin, A. Y., & Abrahart, R. J. (2009). 使用基因表达式编程从常规降雨径流模型输出开发组合径流估算模型。 18th World IMACS Congress and MODSIM09 International Congress on Modeling and Simulation: Interfacing Modeling and Simulation with Mathematical and Computational Sciences, Proceedings, July, 748–754. https://www.scopus.com/inward/record.uri?eid=2-s2.0-80052983135&partnerID=40&md5=73dcd5eba92b4c026dcff2b6bf128f02
- Gupta, H. V., & Sorooshian, S. (1998). 改进水文模型校准：多重且不可通约的信息度量。 Water Resources Research, 34(4), 751–763.
- Gupta, H. V., Kling, H., Yilmaz, K. K., & Martinez, G. F. (2009). 均方误差和 NSE 性能指标的分解：改进水文建模的意义。 Journal of Hydrology, 377(1–2), 80–91. https://doi.org/10.1016/j.jhydrol.2009.08.003
- Jain, A., & Srinivasulu, S. (2006). 使用人工神经网络和概念技术建模分解流量过程线的综合方法。 Journal of Hydrology, 317(3–4), 291–306. https://doi.org/10.1016/j.jhydrol.2005.05.022
- Kayastha, N., Ye, J., Fenicia, F., Kuzmin, V., & Solomatine, D. P. (2013). 专业化降雨径流模型的模糊委员会：进一步改进与测试。 Hydrology and Earth System Sciences, 17(11), 4441–4451. https://doi.org/10.5194/hess-17-4441-2013
- Krause, P., Boyle, D. P., & Bäse, F. (2005). 水文模型评估不同效率标准的比较。 Advances in Geosciences, 5(89), 89–97. https://doi.org/10.5194/adgeo-5-89-2005
- Lindström, G., Johansson, B., Persson, M., Gardelin, M., & Bergström, S. (1997). 分布式 HBV-96 水文模型的开发与测试。 Journal of Hydrology, 201(1–4), 272–288. https://doi.org/10.1016/S0022-1694(97)00041-3
- Oudin, L., Andréassian, V., Mathevet, T., Perrin, C., & Michel, C. (2006). 基于互补模型参数化的降雨径流模型模拟的动态平均。 Water Resources Research, 42(7), 1–10. https://doi.org/10.1029/2005WR004636
- Schumann, A. H. (1993). 概念半分布式水文模型的发展及其参数的 GIS 辅助估计。 Hydrological Sciences Journal, 38(6), 519–528. https://doi.org/10.1080/026266693094926702
- Shamseldin, A. Y., O’Connor, K. M., & Liang, G. C. (1997). 组合不同降雨径流模型输出的方法。 Journal of Hydrology, 197(1–4), 203–229. https://doi.org/10.1016/S0022-1694(96)03259-3
- SNET (2005). 萨尔瓦多的综合动态水量平衡, 109. https://unesdoc.unesco.org/ark:/48223/pf0000228142
- Solomatine, D. P. (2006). 预测环境变量中学习模型的最佳模块化。 Proceedings of the IEMSs 3rd Biennial Meeting, Summit on Environmental Modeling and Software, July. http://www.scopus.com/inward/record.url?eid=2-s2.0-84858682542&partnerID=tZOtx3y1
- Takagi, T., & Sugeno, M. (1985). 系统的模糊辨识及其在建模与控制中的应用。 IEEE Transactions on Systems, Man, and Cybernetics, SMC-15 (1), 116–132. https://doi.org/10.1109/TSMC.1985.6313399
- Xiong, L., Shamseldin, A. Y., & O’Connor, K. M. (2001). 一阶 Takagi-Sugeno 模糊系统对降雨径流模型预报的非线性组合。 Journal of Hydrology, 245(1–4), 196–217. https://doi.org/10.1016/S0022-1694(01)00349-3
