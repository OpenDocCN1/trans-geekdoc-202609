
图 12-7 的可能未来 10 年湖泊水位估计显示，2021 年 8 月的 916.94 m 水位可能是 2017 至 2018 年所有站点的干旱期所致。还显示，1976 至 2019 年观测期间 Eğirdir 湖的平均水位约为 917.30 m，而未来 10 年预计约为 917.50 m。

## 12.4 Conclusions

本研究使用机器学习算法探讨气象干旱与湖泊水位之间的关系。首先，计算了 1976 至 2019 年 Eğirdir、Senirkent、Uluborlu、Yalvaç 和 Isparta 站点的 12 个月 SPI 值。根据计算出的 SPI 值，这五个站点共获得了 127 个月的共同干旱期。随后，将这 127 个月的 SPI 值作为输入，使用 kNN、SVR、AdaBoost、RF、ET、GBR、XGBoost 和 CatBoost 等机器学习模型进行预测，估算 Eğirdir 湖泊水位。模型结果表明，CatBoost 算法表现最佳。为提升 CatBoost 模型的成功率并防止过拟合，采用 Optuna 进行超参数调优，模型性能得到提升。此外，为更好地理解该模型，计算了特征重要性值，并分析输入对模型结果的影响。根据特征重要性，Isparta 站是 Eğirdir 湖泊水位估计 CatBoost 模型中最具影响力的站点，其他站点的影响也值得注意。

其次，利用 LSTM 在各站点估计未来 10 年的 SPI 值，从而预测可能的 Eğirdir 湖泊水位。检查各站点最合适的 LSTM 模型的结果后，发现测试集中计算值与预测值相似。随后，将所有时期的 SPI 值作为各站点最佳 LSTM 模型的输入，预测未来 10 年的 SPI 值。同时，将未来 10 年的 SPI 值作为最佳机器学习模型的输入，预测湖泊水位。将 1976 至 2019 年 Eğirdir 湖泊水位与机器学习模型的未来 10 年预测值进行比较，发现机器学习模型的平均水位预测误差为 0.20 m。本研究表明，机器学习模型能够成功评估气象干旱对湖泊水位的影响，并预测未来的水位变化。结论表明，气象干旱对 Eğirdir 湖泊水位的影响通常在 2 至 4 年之间，这段时间足以建立早期预警系统以防范可能的水文干旱，并开展最优的湖泊管理研究。

## References

*   Abeysingha and Rajapaksha, 2020 Abeysingha NS, Rajapaksha URLN. SPI-based spatiotemporal drought over Sri Lanka. *Advances in Meteorology*. 2020;2020 [`https://doi.org/10.1155/2020/9753279`](https://doi.org/10.1155/2020/9753279).

*   Akiba et al., 2019 Akiba, T., Sano, S., Yanase, T., Ohta, T., & Koyama, M. (2019). Optuna: A next-generation hyperparameter optimization framework. In *Proceedings of the 25th ACM SIGKDD international conference on knowledge discovery & data mining* (pp. 2623–2631). [`https://doi.org/10.1145/3292500.3330701`](https://doi.org/10.1145/3292500.3330701).

*   Alvarez et al., 2024 Alvarez I, Pereira H, Lorenzo MN, et al. Drought projections for the NW Iberian Peninsula under climate change. *Climate Dynamics* 2024;:1–17 [`https://doi.org/10.1007/s00382-023-07084-z`](https://doi.org/10.1007/s00382-023-07084-z).

*   Angelidis et al., 2012 Angelidis P, Maris F, Kotsovinos N, Hrissanthou V. Computation of drought index SPI with alternative distribution functions. *Water Resources Management*. 2012;26:2453–2473 [`https://doi.org/10.1007/s11269-012-0026-0`](https://doi.org/10.1007/s11269-012-0026-0).

*   Awad et al., 2015 Awad M, Khanna R, Awad M, Khanna R. *Support vector regression*. *Efficient learning machines: Theories, concepts, and applications for engineers and system designers* Apress Berkeley 2015;67–80 [`https://doi.org/10.1007/978-1-4302-5990-9_4`](https://doi.org/10.1007/978-1-4302-5990-9_4).

*   Baykal et al., 2023 Baykal T, Taylan D, Terzi Ö. Assessment of future possible meteorological drought for Isparta Province. *Journal of Natural Hazards and Environment*. 2023;9(1):90–100 [`https://doi.org/10.21324/dacd.1165500`](https://doi.org/10.21324/dacd.1165500).

*   Belayneh and Adamowski, 2013 Belayneh A, Adamowski J. Drought forecasting using new machine learning methods. *Journal of Water and Land Development*. 2013;18(9):3–12 [`https://doi.org/10.2478/jwld-2013-0001`](https://doi.org/10.2478/jwld-2013-0001).

*   Bhunia et al., 2020 Bhunia P, Das P, Maiti R. Meteorological drought study through SPI in three drought prone districts of West Bengal, India. *Earth Systems and Environment*. 2020;4(1):43–55 [`https://doi.org/10.1007/s41748-019-00137-6`](https://doi.org/10.1007/s41748-019-00137-6).

*   Chen and Guestrin, 2016 Chen, T., & Guestrin, C. (2016, August). XGBoost: A scalable tree boosting system. In *Proceedings of the 22nd ACM SIGKDD international conference on knowledge discovery and data mining* (pp. 785–794). [`https://doi.org/10.1145/2939672.2939785`](https://doi.org/10.1145/2939672.2939785).

*   Citakoglu and Coşkun, 2022 Citakoglu H, Coşkun Ö. 混合机器学习方法用于预测土耳其萨卡里亚气象站的短期气象干旱。 *Environmental Science and Pollution Research*. 2022;29(50):75487–75511 [`https://doi.org/10.1007/s11356-022-21083-3`](https://doi.org/10.1007/s11356-022-21083-3).

*   Cortes and Vapnik, 1995 Cortes C, Vapnik V. 支持向量网络。 *Machine Learning*. 1995;20:273–297 [`https://doi.org/10.1007/BF00994018`](https://doi.org/10.1007/BF00994018).

*   Dai et al., 2020 Dai M, Huang S, Huang Q, 等. 农业干旱风险评估及其动态演变特征。 *Agricultural Water Management*. 2020;231106003 [`https://doi.org/10.1016/j.agwat.2020.106003`](https://doi.org/10.1016/j.agwat.2020.106003).

*   Dai et al., 2024 Dai R, Wang W, Zhang R, Yu L. 多模态深度学习水位预测模型用于费伊云河流域的多尺度干旱警报。 *Expert Systems with Applications*. 2024;244122951 [`https://doi.org/10.1016/j.eswa.2023.122951`](https://doi.org/10.1016/j.eswa.2023.122951).

*   Dash and Jaiswal, 2024 Dash S, Jaiswal A. 基于机器学习的降雨预测模型。 *World Journal of Advanced Research and Reviews*. 2024;21(1):1678–1686 [`https://doi.org/10.30574/wjarr.2024.21.1.0180`](https://doi.org/10.30574/wjarr.2024.21.1.0180).

*   Drucker, 1997 Drucker, H. (1997, July). 使用增强技术改进回归器。在 *ICML’97: Proceedings of the fourteenth international conference on machine learning* (第 107–115 页)。

*   Du et al., 2023 Du Y, Liu Y, Yan Y, Fang J, Jiang X. 基于可解释额外树的电力系统天气相关故障风险管理。 *Journal of Modern Power Systems and Clean Energy* 2023; [`https://doi.org/10.35833/MPCE.2022.000430`](https://doi.org/10.35833/MPCE.2022.000430).

*   Erkoç, 2023 Erkoç M. 对拜谢湖水位及当地干旱条件的科学分析。 *Bulletin of Geophysics and Oceanography*. 2023;64 [`https://doi.org/10.4430/bgo00426`](https://doi.org/10.4430/bgo00426).

*   Fang et al., 2024 Fang L, Yin J, Wang Y, 等. 机器学习和共轭分析全球干旱及社会暴露过去变化的研究。 *Journal of Hydrology*. 2024;628130536 [`https://doi.org/10.1016/j.jhydrol.2023.130536`](https://doi.org/10.1016/j.jhydrol.2023.130536).

*   Friedman, 2001 Friedman JH. 贪婪函数逼近：梯度提升机。 *Annals of Statistics* 2001;:1189–1232 [`https://www.jstor.org/stable/2699986`](https://www.jstor.org/stable/2699986).

*   Geurts et al., 2006 Geurts P, Ernst D, Wehenkel L. 极端随机树。 *Machine Learning*. 2006;63:3–42 [`https://doi.org/10.1007/s10994-006-6226-1`](https://doi.org/10.1007/s10994-006-6226-1).

*   Gumus, 2017 Gumus V. 利用流量干旱指数对阿西河流域的水文干旱进行分析。 *Gazi University Journal of Science Part C*. 2017;5:65–73.

*   Hancock and Khoshgoftaar, 2020 Hancock JT, Khoshgoftaar TM. CatBoost 用于大数据：跨学科综述。 *Journal of Big Data*. 2020;7(1):1–45 [`https://doi.org/10.1186/s40537-020-00369-8`](https://doi.org/10.1186/s40537-020-00369-8).

*   Huang et al., 2019 Huang G, Wu L, Ma X, 等. 评估 CatBoost 方法在湿润地区预测参考蒸发量的效果。 *Journal of Hydrology*. 2019;574:1029–1041 [`https://doi.org/10.1016/j.jhydrol.2019.04.085`](https://doi.org/10.1016/j.jhydrol.2019.04.085).

*   Ibrahim et al., 2020 Ibrahim AA, Ridwan RL, Muhammed MM, Abdulaziz RO, Saheed GA. 与其他机器学习方法比较 CatBoost 分类器。 *International Journal of Advanced Computer Science and Applications*. 2020;11 [`https://doi.org/10.14569/ijacsa.2020.0111190`](https://doi.org/10.14569/ijacsa.2020.0111190).

*   Kadam et al., 2024 Kadam CM, Bhosle UV, Holambe RS. 深度学习驱动的区域干旱评估：优化视角。 *Earth Science Informatics* 2024;:1–15 [`https://doi.org/10.1007/s12145-024-01244-3`](https://doi.org/10.1007/s12145-024-01244-3).

*   Kumar et al., 2022 Kumar P, Singh SN, Dawra S. 使用额外树分类器和增强胡氏鹰优化算法对软件组件可重用性进行预测。 *International Journal of System Assurance Engineering and Management*. 2022;13(2):892–903 [`https://doi.org/10.1007/s13198-021-01359-6`](https://doi.org/10.1007/s13198-021-01359-6).

*   Kumar et al., 2023 Kumar V, Kedam N, Sharma KV, Mehta DJ, Caloiero T. 先进机器学习技术提升水文预测：对流量预测模型的比较分析。 *Water*. 2023;15(14):2572 [`https://doi.org/10.3390/w15142572`](https://doi.org/10.3390/w15142572).

*   Latifoğlu and Nuralan, 2020 Latifoğlu L, Nuralan KB. 使用 singular spectrum analysis 和长短期记忆网络预测流量。 *European Journal of Science and Technology* 2020;:376–381 [`https://doi.org/10.31590/ejosat.araconf49`](https://doi.org/10.31590/ejosat.araconf49).

*   Latifoğlu and Özger, 2023 Latifoğlu L, Özger M. 高性能 SPI 数据估计在干旱预测中的新方法。 *Sustainability*. 2023;15(19):14046 [`https://doi.org/10.3390/su151914046`](https://doi.org/10.3390/su151914046).

*   Lee et al., 2021 Lee J, Lee S, Hong J, 等. 使用机器学习和深度学习模型评估降雨侵蚀性因子估计。 *Water*. 2021;13(3):382 [`https://doi.org/10.3390/w13030382`](https://doi.org/10.3390/w13030382).

*   Li et al., 2024 Li G, Liu Z, Zhang J, Han H, Shu Z. 将深度学习模型组合的贝叶斯模型平均法提高湖泊水位预测。 *Science of The Total Environment*. 2024;906167718 [`https://doi.org/10.1016/j.scitotenv.2023.167718`](https://doi.org/10.1016/j.scitotenv.2023.167718).
