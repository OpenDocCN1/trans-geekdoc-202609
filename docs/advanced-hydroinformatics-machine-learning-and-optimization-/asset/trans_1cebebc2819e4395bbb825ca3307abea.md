
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_157_0.png)

图 5.3 在校准和验证期间显示模拟和观测径流值与其相对超额时间的流量历时曲线。FDC（a、c）表示流量被超过的时间百分比。x 轴上的零值代表观测到的最高流量，1 代表随时间推移被超过的最低观测流量。流量超额概率还使用对数尺度（b、d）呈现，以更好地可视化低流量和高流量的变异性。

中等至低降雨事件。因此，降雨与径流之间的关系可能与降雨量及其分布的动态和时机有关。总体而言，在本研究中使用的各种模型中，贝叶斯 Lasso 为 NE-CFB 降雨-径流模拟提供了有前景的结果。在贝叶斯框架下，Lasso 估计可以解释为具有独立同分布拉普拉斯先验的系数后验模式估计，适用于建模顺序发生的时序数据。

## 5.4. 结论与未来工作

基于回归的机器学习模型可以用作概念性和物理性水文模拟模型的补充。然而，人们仍然担心其提供熟练预测性能的能力，部分原因在于它们需要更多训练数据来生成水文过程、数据中不同程度的噪声以及过拟合，这些都可能转化为建模结果中大量的误差和不确定性。我们认为，机器学习模型在沿海平原排水系统日径流模拟方面的潜在益处只能通过制定稳健而严格的贝叶斯 Lasso 接口来实现，该接口作为后验模式估计，非常适合评估顺序径流时间序列数据的输入-输出行为（行为一致性）。

一个明显的方法来减少障碍并提高机器学习保真度是使用预处理方法（例如，奇异谱和小波分析；参见 Vautard et al., 1992），在大量数据中寻找复杂模式，改进序列到序列学习，并计算噪声方差，然后通过监测噪声分量来捕捉异常值。增强机器学习对时间序列记录中极端观测的建模能力也很重要，需要进一步关注。此外，物理参数（和过程相互作用）可以数学地公式化并纳入机器学习模型，以确保模型输入-输出行为与可用数据和流域特性之间保持适当的一致性。因此，我们的研究小组致力于开发与流域尺度水文模拟模型相当的适当机器学习模型。然而，我们提出的机器学习方法的局限性在于其庞大的计算时间和成本，以及过拟合，使其成为某种程度上较差的预测器。我们正在进行的工作探索开发更先进且计算成本更有效的机器学习算法，例如循环神经网络（RNN），以整合可从网络的循环/结构和数学公式中提取的信息与流域物理属性和观测。始终如一地，我们邀请对这些和相关机器学习模型模拟主题感兴趣的其他人进行对话。

## 致谢

本工作部分得到美国国家科学基金会（NSF）工程局在资助号 CBET 1901646 下的支持。

本研究中表达的任何意见、发现和讨论均为作者本人，并不一定反映 NSF 的观点。感谢克莱姆森大学在 Palmetto 集群上慷慨分配的计算时间。

## 参考文献

- Addor, N., Newman, A. J., Mizukami, N., Clark, M. P. (2017). CAMELS 数据集：大样本研究的流域属性和气象学. Hydrology and Earth System Sciences, 21, 5293–5313.
- Amatya, D. M., & Jha, M. K. (2011). 评估南卡罗来纳州沿海低梯度森林流域的 SWAT 模型. Transactions of the ASABE, 54(6), 2151–2163.
- Asadieh, B., & Krakauer, N. Y. (2017). 21 世纪气候变化下径流极值的全球变化. Hydrology and Earth System Sciences, 21, 5863.
- Box, G. E. P., & Cox, D. R. (1964). 变换分析. Journal of the Royal Statistical Society, Series B, 26, 211–243.
- Breiman, L. (2001). 随机森林. Machine Learning, 45, 5–32.
- Bui, D. T., Pradhan, B., Nampak, H., Bui, Q.-T., Tran, Q.-A., & Nguyen, Q.-P. (2016). 基于神经模糊推理模型和元启发式优化的混合人工智能方法，用于利用 GIS 在高频热带气旋区域进行洪水易发性建模. Journal of Hydrology, 540, 317–330.
- Burnash, R. J. C. (1995). NWS 河流预报系统-流域建模. In V. Singh (Ed.), 流域水文的计算机模型. Water Resources Publications, Colorado, 311–366.
- Campbell, J. L., Driscoll, C. T., Pourmokhtarian, A., & Hayhoe, K. (2011). 美国新罕布什尔州哈伯德布鲁克实验林气候过去和预测未来变化的径流响应. Water Resources Research, 47.
- Corzo, G., Solomatine, D., Hidayat, H., Werner, M., Uhlenbrook, S., et al. (2009). 流量模拟中半分布式过程模型与数据驱动模型的结合：默兹河流域案例研究. Hydrology and Earth System Sciences, 13, 1619–1634.
- Das Bhowmik, R., Seo, S., & Sahoo, S. (2018). 使用多元线性样条的贝叶斯回归进行径流模拟以估计未来变化. Water, 10(7), 875. https://doi.org/10.3390/w10070875
- Deka, P. C. (2014). 水文领域支持向量机应用：综述. Applied Soft Computing, 19, 372–386.
- Efron, B., Hastie, T., Johnstone, I., & Tibshirani, R. (2004). 最小角回归. The Annals of Statistics, 32, 407–499.
- Fang, K., Shen, C., Kifer, D., & Yang, X. (2017). 使用深度学习神经网络将 SMAP 延长至美国大陆时空无缝覆盖. Geophysical Research Letters, 44, 11–30.
- Fotovatikhah, F., Herrera, M., Shamshirband, S., Chau, K., Faizollahzadeh Ardabili, S., & Piran, M. J. (2018). 计算智能作为大洪水管理基础的综述：挑战、研究方向和未来工作. Engineering Applications of Computational Fluid Mechanics, 12, 411–437.
- Gupta, H. V., Kling, H., Yilmaz, K. K., & Martinez, G. F. (2009). 均方误差和 NSE 性能标准的分解：改进水文建模的意义. Journal of Hydrology, 377, 80–91.
- Helgøy, I. M., & Li, Y. (2019). 一种抗噪快速稀疏贝叶斯学习模型. arXiv preprint arXiv:1908.07220.
- Hidalgo, H. G., Das, T., Dettinger, M. D., Cayan, D. R., Pierce, D. W., Barnett, T. P., et al. (2009). 美国西部径流时机变化对气候变化的检测和归因. Journal of Climate, 22, 3838–3855.
- Kratzert, F., Klotz, D., Brenner, C., Schulz, K., & Herrnegger, M. (2018). 使用长短期记忆（LSTM）网络的降雨-径流建模. Hydrology and Earth System Sciences, 22, 6005–6022.
- Kumar, D., Pandey, A., Sharma, N., & Flügel, W.-A. (2016). 使用机器学习方法的日悬移质模拟. Catena, 138, 77–90.
- Loos, M., & Elsenbeer, H. (2011). 森林中地表径流生成的地形控制：集成树方法. Journal of Hydrology, 409, 94–103.
- Maurer, E. P., Wood, A. W., Adam, J. C., Lettenmaier, D. P., & Nijssen, B. (2002). 美国本土长期水文基础的地表通量和状态数据集. Journal of Climate, 26(23), 9384–9392. https://doi.org/10.1175/JCLI-D-12-250508.1
- Murphy, K. P. (2012). 机器学习：概率视角. MIT Press.
- Naghibi, S. A., Ahmadi, K., & Daneshi, A. (2017). 支持向量机、随机森林和遗传算法优化随机森林模型在地下水潜力制图中的应用. Water Resources Management, 31, 2761–2775.
- Nash, J. E., & Sutcliffe, J. V. (1970). 通过概念模型进行河流流量预测 第一部分：原理讨论. Journal of Hydrology, 10(3), 282–290. https://doi.org/10.1016/0022-1694(70)90255-6
- Newman, A. J., Clark, M. P., Sampson, K., Wood, A., Hay, L. E., Bock, A., et al. (2015). 美国本土大样本流域尺度水文气象数据集的开发：数据集特征和水文模型性能区域变异性评估. Hydrology and Earth System Sciences, 19, 209–223. https://doi.org/10.5194/hess-19-209-2015
- Park, T., & Casella, G. (2008). 贝叶斯 Lasso. Journal of the American Statistical Association, 103, 681–686.
- Sadler, J. M., Goodall, J. L., Morsy, M. M., Spencer, K. (2018). 使用泊松回归和随机森林从众包洪水报告建模城市沿海洪水严重程度. Journal of Hydrology, 559, 43–55.
- Samadi, S., Pourreza-Bilondi, M., Wilson, C., & Hitchcock, D. B. (2020). 具有固定和灵活先验的贝叶斯模型平均：降雨-径流建模的理论、概念和校准实验. Journal of Advances in Modeling Earth Systems, 12, e2019MS001924.
- Samadi, S., Tufford, D. L., & Carbone, G. J. (2017). 评估浅层含水层主导的半分布式水文模型的参数不确定性
