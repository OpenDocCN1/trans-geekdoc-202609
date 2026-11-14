

## 用于建模时间依赖性的深度学习框架

### 表 4. Spearman 等级相关

| | 小时 | 天 | 周 | 月 | 季度 | 半年 | 年 |
|---|---|---|---|---|---|---|---|
| Hour | 1.00 | | | | | | |
| Day | 0.00 | 1.00 | | | | | |
| Week | 0.00 | 0.06 | 1.00 | | | | |
| Month | 0.00 | 0.00 | 0.97 | 1.00 | | | |
| Quarter | 0.00 | 0.00 | 0.94 | 0.97 | 1.00 | | |
| Half_year | 0.00 | -0.01 | -0.84 | -0.86 | -0.89 | 1.00 | |
| Year | 0.00 | -0.01 | -0.20 | -0.20 | -0.20 | 0.14 | 1.00 |

轮廓系数为 0.7284（高），表明聚类分离良好。然而，Davies-Bouldin 指数为 1.0289（中等），表明聚类分离适中，Mini-Batch K-Means 的轮廓系数确定为 0.3805（中等），同样表明聚类分离适中。

最后，通过 Fuzzy C-Means 发现轮廓系数为 0.3734（中等），表明聚类分离适中，而 Davies-Boulden 指数为 1.0554（中等），暗示聚类分离适中。总的来说，K-Means 在三种算法中表现似乎最好，具有更高的轮廓系数和更低的 Davies-Boulden 指数值。基于这些指标，Mini-Batch K-Means 和 Fuzzy C-Means 表现出相似的中等性能。最后，使用 k-means 对每个簇中的层次结构时间依赖性如图 10 所示。

### 结论与未来方向

尽管对电力/能源消耗进行准确可靠的估计至关重要，但该领域令人沮丧地吸引的关注度却低于其他领域。但在过去几年中，研究人员取得了一些重大进展，利用深度学习（DL）和人工智能（AI）开发出了可靠、准确且有效的预测模型。由于其特性和重要性，这些技术——人工智能和深度学习——在处理时间序列数据的非线性问题时表现良好且高效。在本章中，我们介绍了一种深度学习集成方法，它利用时间依赖性来预测和预估电力需求的每小时负载。为确保模型性能，我们的系统首先处理数据清洗、归一化和转换。

此外，预处理后的数据被输入到集成模型中，通过使用 RNN、LSTM、CNN 和堆叠集成架构来提取混合判别特征。这将使公用事业公司能够规划资源并平衡供需，从而确保电网的稳定性和安全性以及服务提供的可靠性。使用每小时电力需求负载，我们评估了所提系统并比较了结果，结果显示于表 3。针对未来工作，可以研究各种非线性外源数据结构，例如变量、货币特征以及天气/气候条件或变化，用于电力负载模式的趋势分析。此外，可以构思并开发许多优化技术，以提高推荐系统的预测准确性。

### 表 5. 聚类算法性能

| | 轮廓系数 | Davies-Bouldin 指数 |
|---|---|---|
| K-means | 0.728393737 | 0.501091441 |
| Mini-Batch K-Means | 0.380461786 | 1.028941784 |
| Fuzzy C-Means | 0.373376881 | 1.055433432 |

### 图 10. 电力需求层次结构聚类

![](img/2e8f3dfd000fbfaa074ac5bc7a8b2717_78_0.png)

### 参考文献

- Adhikari, R. J. N. (2015). 基于神经网络的时间序列预测线性集成框架. Academic Press.
- Ahmadi, A., Daccache, A., Sadegh, M., & Snyder, R. L. (2023). 参考蒸散量时间序列预测的统计学和深度学习模型：准确性、复杂性和数据效率比较. Computers and Electronics in Agriculture, 215. doi:10.1016/j.compag.2023.108424
- Aldhsan, S. R. S., Abdul Maulud, K. N., Wan Mohd Jaafar, W. S. Karim, O. A., & Pradhan, B. (2021). 马来西亚可再生能源渗透率和建筑能效的能源消耗与空间评估：综述. Sustainability (Basel), 13(16), 9244. doi:10.3390/su13169244
- Bagnall, A., Lines, J., Hills, J., & Bostrom, A. (2015). 基于 COTE 的时间序列分类：基于变换的集合. IEEE Transactions on Knowledge and Data Engineering, 27(9), 2522–2535. doi:10.1109/TKDE.2015.2416723
- Bandara, K., Bergmeir, C., & Smyl, S. (2020). 基于相似系列组的循环神经网络跨时间序列数据库预测：一种聚类方法. Expert Systems with Applications, 140, 112896. doi:10.1016/j.eswa.2019.112896
- Cordeiro-Costas, M., Villanueva, D., Eguía-Oller, P., Martínez-Comesaña, M., & Ramos, S. (2023). 基于机器学习和深度学习方法的负载预测. Applied Sciences (Basel, Switzerland), 13(13), 7933. doi:10.3390/app13137933
- Ensafi, Y., Amin, S. H., Zhang, G., & Shah, B. (2022). 季节性商品销售的机器学习时间序列预测——比较分析. International Journal of Information Management Data Insights, 2(1), 100058. doi:10.1016/j.jjimei.2022.100058
- Hagenau, M., Liebmann, M., & Neumann, D. (2013). 自动化新闻阅读：基于捕捉上下文特征的财务新闻股票价格预测. Decision Support Systems, 55(3), 685–697. doi:10.1016/j.dss.2013.02.006
- Hamed, M. M., Ali, H., & Abdelal, Q. (2022). 使用均值和方差异质的随机参数模型预测年度电力消耗. Energy, 255, 124510. doi:10.1016/j.energy.2022.124510
- Hochreiter S, & Schmidhuber J (1997). 长短期记忆网络. Neural Comput, 9(8), 1735–1780. doi:10.1162/neco.1997.9.8.1735
- Huang, S.-H., & Pan, Y.-C. (2014). 基于自动化 RGB-D 人体测量系统的人体工学工作轮换策略. Journal of Manufacturing Systems, 33(4), 699–710. doi:10.1016/j.jmsy.2014.02.005
- Huang, S.-H., & Pan, Y.-C. (2015). 半导体行业自动化视觉检测：综述. Computers in Industry, 66, 1–10. doi:10.1016/j.compind.2014.10.006
- Jin, L., & Dong, J. (2016). 生物医学时间序列分类的集成深度学习. Computational Intelligence and Neuroscience. doi:10.1155/2016/6212684 PMID:27725828
- Jogonula, O., Adebisi, B., Hoang, K. V., Tsado, Y., Popoola, S. I., Hammoudeh, M., & Nawaz, R. (2022). CBLSTM-AE：一种用于预测能源消耗的混合深度学习框架. Energies, 15(3), 810. doi:10.3390/en15030810
- Kamal-Chaoui, L., & Robert, A. (2009). 竞争城市与气候变化. Academic Press.
- Kohzadi, N., Boyd, M. S., Kermanshahi, B., & Kaastra, I. (1996). 人工神经网络与时间序列模型预测商品价格的比较. Neurocomputing, 10(2), 169–181. doi:10.1016/0925-2312(95)00020-8
- Kranjc, J., Smailović, J., Podpečan, V., Grčar, M., Žnidaršič, M., & Lavrač, N. (2015). 数据流情感分析的主动学习：CloudFlows 平台中的方法论与工作流实现. Information Processing & Management, 51(2), 187–203. doi:10.1016/j.ipm.2014.04.001
- Le, T., Vo, M. T., Vo, B., Hwang, E., Rho, S., & Baik, S. W. (2019). 使用 CNN 和 Bi-LSTM 改善电能消耗预测. Applied Sciences (Basel, Switzerland), 9(20), 4237. doi:10.3390/app9204237
- Liu, T., Tan, Z., Xu, C., Chen, H., & Li, Z. (2020). 建筑能耗预测深度强化学习技术研究. Energy and Building, 208, 109675. doi:10.1016/j.enbuild.2019.109675
- Lotfipoor, A., Patidar, S., & Jenkins, D. P. (2024). 用于住宅负载预测的带经验模态分解和贝叶斯优化的深度神经网络. Expert Systems with Applications, vol. 237, 121355. 先行在线发表. doi:10.1016/j.eswa.2023.121355
- Mariano-Hernández, D., Hernández-Callejo, L., García, F. S., Duque-Perez, O., & Zorita-Lanandrid, A. L. (2020). 智能建筑能耗预测综述：方法、输入变量、预测时域与指标. Applied Sciences (Basel, Switzerland), 10(23), 8323. doi:10.3390/app10238323
- Rahman, M. M., Shakeri, M., Tiong, S. K., Khatun, F., Amin, N., Pasupuleti, J., & Hasan, M. K. (2021). 基于人工神经网络混合可再生能源系统能源预测的前瞻性方法. Sustainability (Basel), 13(4), 2393. doi:10.3390/su13042393
- Razavi, R., Gharipour, A., Fleury, M., & Akpan, I. J. (2019). 基于智能电表数据的住宅建筑人员占用检测：大规模研究. Energy and Building, 183, 195–208. doi:10.1016/j.enbuild.2018.11.025
- Sharma, N., Jain, V., & Mishra, A. (2018). 图像分类卷积神经网络分析. Procedia Computer Science, 132, 377–384. doi:10.1016/j.procs.2018.05.198
- Shiri, Perumal, Mustapha, & Mohamed. (n.d.). 深度学习模型综合概述与比较分析：CNN, RNN, LSTM, GRU. https://arxiv.org/ftp/arxiv/papers/2305/2305.17473.pdf
- Singaravel, S., Suykens, J., & Geyer, P. (2018). 深度学习神经网络架构与方法：用于建筑设计能耗预测的基于组件的模型. Advanced Engineering Informatics, 38, 81–90. doi:10.1016/j.aei.2018.06.004
- Slater, L. J., Arnal, L., Boucher, M., Chang, A., Moulds, S., Murphy, C., Nearing, G., Shalev, G., Shen, C., Speight, L., Villarrini, G., Wilby, R. L., Wood, A., & Zappa, M. (2022). 混合预测：使用统计学和机器学习集成动态模型预测. Hydrology and Earth System Sciences. 先行在线发表. doi:10.5194/hess-2022-334
- Somu, N., Raman, M. R. G., & Ramamritham, K. (2021). 建筑能耗预测深度学习框架. Renewable & Sustainable Energy Reviews, 137, 110591. doi:10.1016/j.rser.2020.110591
- Wang, Z., & Oates, T. (2015). 通过成像时间序列改进分类和插补. arXiv 预印本 arXiv:00327.

