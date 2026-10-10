
| C1 | 1 | 0 | 0.793519 | 0.206481 | 0.247645 | 0.752355 |

| C2 | 0 | 1 | 0.206481 | 0.793519 | 0.752355 | 0.247645 |

| C3 | 0.793519 | 0.206481 | 1 | 0 | 0.046994 | 0.953006 |

| C4 | 0.206481 | 0.793519 | 0 | 1 | 0.953006 | 0.046994 |

| C5 | 0.247645 | 0.752355 | 0.046994 | 0.953006 | 1 | 0 |

| C6 | 0.752355 | 0.247645 | 0.953006 | 0.046994 | 0 | 1 |

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_139_0.png)

(a) 2016 年散点图

(b) 2017 年散点图

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_139_1.png)

(c) 2018 年散点图

# 图 6.8 AQI 参数集成聚类的散点图

## 算法 6.1: 加权集成图聚类算法

1. 输入：`K*`, `METIS`, 基础聚类划分 `C`
2. 输出：`C*`，即最终的集成聚类
3. 开始
4. 使用公式 6.1 将 `C` 聚类划分转换为二值向量。
5. 使用公式 6.2 给出的单次权重分配，对对象分配权重。
6. 使用公式 6.6 计算聚类类对之间的聚类权重。
7. 构建元图 `G = (V, E)`，其中使用公式 6.6 计算与边相关的权重。
8. `*元聚类 (MetaClusters)* = METIS(G, k*)` [将元图划分为 `k*` 个元聚类]
9. `C* = Assign(metaClusters)` [每个对象被分配到其参与度最强的元聚类中]
10. 返回 `C*`
11. 结束

## 6.5 实验结果

聚类过程完成后，必须对聚类技术的性能进行量化。可以使用某些指标来实现，这些指标根据聚类间的最大距离和类内最小距离来表征理想聚类。这些指标分为两种：

- 外在指标，如 V-度量、完整性、同质性、Fowlkes-Mallows 分、基于互信息的评分以及调整兰德指数，它们需要真实标签（ground truth labels）来评估聚类性能。
- 内禀指标，如 Davies-Bouldin-Harabasz 指数和轮廓系数（Silhouette Coefficient）。这些指标不需要真实标签，而是基于原始数据和聚类结果来评估聚类性能。

### 6.5.1 轮廓系数 (SILHOUETTE COEFFICIENT)

在未知真实标签时使用生成的模型进行评估。这种评估方法之一是轮廓系数。它针对每个样本定义，聚类更好的模型由较高的轮廓系数得分表示。轮廓系数由两部分组成：

- 样本与同一类中其他点之间的平均距离。
- 样本与最近邻聚类中其他点之间的平均距离。

# 印度空气质量预测

## 表格 6.10

基础聚类模型按年份划分的轮廓系数指标

| 年份 | 层次聚类 (Hierarchical clustering) | 模糊均值 (Fuzzy C means) | K均值 (K means) |
|---|---|---|---|
| 2016 | 0.657571268 | 0.723436528 | 0.684701362 |
| 2017 | 0.602559157 | 0.707689134 | 0.598002859 |
| 2018 | 0.632259157 | 0.658438986 | 0.52142568 |

对于单个样本，轮廓系数 `s` 由下式给出：

$$s(x) = \frac{b(x) - a(x)}{\max[a(x), b(x)]}$$

该值范围在 -1 到 +1 之间；-1 表示聚类效果差或错误；接近 +1 的值表示聚类密集且分离良好。表6.10 中的基础聚类结果包含了 2016、2017 和 2018 年的轮廓系数。与基础聚类相比，最终 `METIS` 输出的轮廓系数更高，证明了集成方法的有效性。基础聚类结果的轮廓系数值在 0.52142568 到 0.72343628 之间。然而，集成技术的最高轮廓系数计算为 0.75174527。

### 6.5.2 CALINSKI-HARABAS 指数

另一个评估指标是 Calinski-Harabasz 指数，也称为方差比例。它是所有聚类间方差和与类内方差的比率。Calinski-Harabasz 分定义为 `$n_E$` 已划分为 `$k$` 个聚类时的类间方差与类内方差的比：

$$s = \frac{tr(B_k)}{tr(W_k)} \times \frac{n_E - k}{k - 1}$$

类内矩阵的迹由 `tr(W_k)` 表示，类间矩阵的迹定义为：

$$B_k = \sum_{q \in C_k} (x - c_q)(x - c_q)^T$$

## 表格 6.11

基础聚类按年份划分的 Calinski-Harabasz 指数

| 年份 | HC | FCM | KM |
|---|---|---|---|
| 2016 | 1542.598346 | 2285.12543 | 1302.02493 |
| 2017 | 1953.759845 | 2016.330664 | 1763.26297 |
| 2018 | 1682.570628 | 1945.748552 | 823.395102 |

$$B_k = \sum_{q=1}^k n_q(c_q - c_E)(c_q - c_E)^T$$

其中 `$C_q$` 是聚类 `$q$` 中的点集，`$c_q$` 是聚类 `$q$` 的中心，`$c_E$` 是全局中心，`$n_q$` 是点数。Calinski-Harabasz 指数的较高值表明聚类大小是合适的，意味着恰当划分。集成技术的评估指标给出最大值 2369.598641。表 13 中的值表明，集成技术比基础技术更有效，范围从 823.395102 到 2285.12543。2016、2017 和 2018 年的 Calinski-Harabasz 指数值见表 6.11。

### 6.5.3 DAVIES-BOULDIN 指数

第三个评估指标是 Davies-Bouldin 指数，它通过比较聚类之间的距离与其大小来表示聚类间的平均相似性（表 6.12）。较低的 Davies-Bouldin 指数表示聚类分离得更好。最低分为零，越接近零的值表示划分越好。该指标定义为平均相似性

## 表格 6.12

基础聚类模型按年份划分的 Davies-Bouldin 指数

| 年份 | HC | FCM | KM |
|---|---|---|---|
| 2016 | 0.846300725 | 0.608585734 | 0.834993702 |
| 2017 | 0.775144086 | 0.565130431 | 0.664321735 |
| 2018 | 1.097000041 | 0.895981891 | 0.776500993 |

# 印度空气质量预测

## 表格 6.13

集成聚类的性能矩阵

| 轮廓系数 | Calinski-Harabasz 指数 | Davies-Bouldin 指数 |
|---|---|---|
| 2016 | 0.713306312 | 2369.598641 | 0.55407292 |
| 2017 | 0.716547345 | 2234.848156 | 0.422597204 |
| 2018 | 0.751745327 | 1965.403228 | 0.559457489 |

对于每个聚类 `$C_i$` (`$i=1, \dots,$`) 与其最相似的 `$C_j$`。在该指标背景下，`$R_{ij}$` 是权衡相似性

- 聚类直径定义为聚类中心与聚类内其他所有点的平均距离，聚类 `$i$` 和 `$j$` 的聚类直径被取为 `$s_i$`。
- 聚类中心之间的距离被取 `$d_{ij}$`。

`$R_{ij}$` 是非负且对称的，定义为：

$$R_{ij} = \frac{s_i + s_j}{d_{ij}}$$

Davies-Bouldin 指数可以定义为：

$$DB = \frac{1}{k} \sum_{i=1}^k \max_{j \neq i} R_{ij}$$

基础聚类技术的 Davies-Bouldin 值从层次聚类的 0.846300725 到模糊均值聚类的 0.565130431，再到 K 均值聚类的 0.776500993。而在具有三个最终聚类的集成技术中，Davies-Bouldin 指数值在 0.422597204 到 0.559457489 之间。

## 6.6 结论

本章的重点是寻找一种解决方案来解决根据在不同地点不同时段记录的趋势来预测空气质量的挑战性任务。这是一个计算复杂的问题，因为模型需要管理大量数据并分析模式。该方法的第一步涉及处理原始数据集，并对 AQI 参数（如 `CO`、`$PM_{2.5}$`）的知识。

## 机器学习中的应用智能决策

`SO2`，以及 `O3`。生成了基于 `HC`、`FCM` 和 `K-means` 聚类（`KM`）基学习器的结果，用于集成学习。对于这些结果，确定了对象权重和聚类权重。然后，将这些值用于 `METIS` 图划分的结果中，通过聚合这些结果来获得最终的集成聚类。轮廓系数（Silhouette Coefficient）和卡林斯-哈拉巴兹指数（Calinski-Harabaz Index）越高，表明聚类技术对所使用的污染数据集越有效。因此，每种聚类技术的值以及这些值的比较表明，加权集成聚类算法相比其他方法提供了更好的结果。该算法在三个指标上均具有更好的聚类质量，轮廓方法、卡林斯-哈拉巴兹指数和 DB 指数分别为 0.75、2369.59 和 0.56。它优于传统的聚类质量。印度地理图谱的可视化结果揭示了不同地点空气污染的严重性。这有助于分析各地的污染程度，以采取正确的措施。该模型的一个局限性是结果没有覆盖该国家的每一个地区，因为偏远地区没有空气质量数据。可以通过外推周围地区的结果克服这一局限性。总之，加权集成聚类算法是预测任何选位置空气质量的一种非常有效的技术。

## 参考文献

- Alquarski, T. and W. Wang. 集类集成方法.International Journal of Machine Learning and Cycles, 10(6):1227–1246, 2019.
- Asgari, M., M. Faraghi, and G. Zhahemi. 使用臭氧峰值进行空气污染预测建模.Proceedings of the 2017 International Conference on Cloud and Big Data Computing, pp. 89–93. ACM, New York, 2017.
- Avogadri, R. and G. Valentini. 基于随机投影的 DNA 微列数据分析模糊聚类.Artificial Intelligence in Medicine, 45(2–3):183, 2009.
- Ayad, H. and M. Kamel. 基于共享邻居的多聚类组合器寻找自然聚类.International Workshop on Multiple Classifiers Systems, pp. 166–175. Springer, Berlin, 2013.
- Ben Ishak, A., M. Ben Dao, and A. Trabelsi. 使用统计学习方法预测臭氧浓度.Journal of Materials and Environmental Science, 8(12):4522–4543, 2017.
- Brazier, L. 通过自适应加权构建 LSTM 网络集成，以改进时间序列预测.Mathematical Models in Engineering, Article ID 2470712, 2018. doi:10.1155/2018/2470712/2018.
- CPCB. 中央污染控制委员会，空气质量管理中央控制室 — 全印度, 2019. [https://pccb.nic.in/caaqm-dashboard-all/caaqm-landing](https://pccb.nic.in/caaqm-dashboard-all/caaqm-landing).
- Dai, C., H. Y., P. Lu, S. Luo, P. Qin, and H. Peng. 长安城市大气 PM2.5 和 NO2 浓度的相关分析.Advanced Materials Research, 998, pp. 1414–1418. Tech Press Publ, 2014.
- Esposito, E. S. T. M. Salvato, V. Bright, R. L. Jones, and O. Popoola. 用于低成本空气质量传感系统现场随机校准的动态神经网络架构.Sensors and Actuators B: Chemical, 231:701–713, 2016.
- Fred, A. L. N. and A. K. Jain. 使用证据证据进行数据聚类.Object Recognition Supported by User Interaction for Service Robots, Vol. 4, pp. 276–280. IEEE, 2002.

# 印度空气质量预测

- Ghomeim, O. A., B. R. Manjunatha, et al. 深度学习在智慧城市臭氧浓度预测的应用.2017 International Conference on Advances in Computing, Communications and Informatics (ICACCI), pp. 1320–1326. IEEE, Piscataway, NJ, 2017.
- Ghosh, J. and A. Acharya. 聚类集成.Interdisciplinary Reviews: Data Mining and Knowledge Discovery, 1(4):305–315, 2011.
- Gore, W. D. and D. S. Deshpande. 基于空气质量水平的健康风险分类方法.2017 International Conference on Intelligent Systems and Information Management (ICISM), pp. 58–61. IEEE, 2016.
- Greene, D., N. Bolakova, and P. Cunningham. 医学诊断中的集成聚类.Medical diagnostics, Vol. 4, pp. 276–280. IEEE, 2002.
- Han, G. and C. 结合多种聚类结果的集成聚类方法.Eleventh Conference on Information Management, pp. 600–607, 2012.
- Hu, X. and M. 共享邻居的的聚类组合.IEEE of on Systems, Vol. 2, pp. 251–258, 2008.
- Ishak, A., M. Ben, and A. Trabelsi. 使用统计学习方法预测臭氧浓度.Journal of Materials and Environmental Science, 8(12):4522–4543, 2017.
- Karypis, G. and V. METIS 图划分算法.Journal of Parallel and Distributed Systems, 48:96–129, 1998.
- Kings, R., M. Manigali, and S. 2016 加权集成聚类预测空气质量.2016 IEEE International Conference (TENCON), pp. 1945–1949. IEEE, Piscataway, NJ.
- Kune, L. and P. 一种自适应元聚类方法：结合不同聚类结果.IEEE, Vol. 2, pp. 121–129, 2004.
- Li, C., D. Huang, and Y. Z. 使用矩阵分解的集成聚类.Seventh IEEE International Conference on Data Mining, pp. 577–582, 2007.
- Martínez-Espuzuela, R., F. Alias, and J. 深度学习的智慧城市空气质量预测.Big Data and Cognitive Computing, 2(1):5, 2018.
- Nock, R. and G. 加权聚类.IEEE Transactions on Pattern Analysis and Machine Intelligence, 28(8):1223–1235, 2006.
- Pura, K. and J. 基于提升的共识模糊聚类.Artificial Intelligence, 22(7):780–810, 1998.
- Schapire, R. E. 提升算法简要介绍.IJCAI, Vol. 9, pp. 1401–1406, 1999.
- Sevillaano, X., F. Soft, and J. 基于位置投票的共识模糊聚类.Fuzzy Sets and Systems, 19(3):1–32, 2002.
- Strehl, A. and J. 聚类集成——一种知识框架.Journal of Machine Research, 3(3):583–617, 2002.
- Topchy, A., A. SIAM, and J. Puchi. 聚类集成的一种混合模型.SIAM International Conference on Data Mining, pp. 379–390, 2004.
- Vandhana, S. and J. Design. 使用层次聚类方法预测登革热.International Conference on Design Research in Information Systems and Technology, pp. 157–168. Springer, Berlin, 2018.
