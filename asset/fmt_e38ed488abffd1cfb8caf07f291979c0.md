
## 公式与模型评价指标

决定系数（$R^2$）和均方根误差（RMSE）的计算公式如下：

$$R^{2} = 1 - \frac{\sum_{i = 1}^{N}(X_{i(\text{measured})} - X_{i(\text{model})})^{2}}{\sum_{i = 1}^{N}(X_{i(\text{measured})} - X_{i(\text{mean})})^{2}} \tag{12.3}$$

![Equation](img/F000055si4.png)

$$RMSE = \sqrt{\frac{1}{N}\sum_{i = 1}^{N}(X_{i(\text{measured})} - X_{i(\text{model})})^{2}} \tag{12.4}$$

![Equation](img/F000055si5.png)

其中，$N$ 表示数据总数，$X_{i(\text{measured})}$ 为实测湖水位值，$X_{i(\text{model})}$ 为机器学习模型预测结果，$X_{\text{mean}}$ 为实测湖水位均值。

## 机器学习模型结果对比

**表 12-1** 展示了各机器学习（ML）模型在训练集和测试集上的 $R^2$ 与 RMSE 结果。

| ML algorithms | Training set | | Testing set | |
| :--- | :---: | :---: | :---: | :---: |
| | $R^2$ | RMSE | $R^2$ | RMSE |
| kNN | 0.67 | 0.37 | 0.62 | 0.44 |
| SVR | 0.71 | 0.34 | 0.55 | 0.48 |
| AdaBoost | 0.81 | 0.28 | 0.61 | 0.45 |
| RF | 0.92 | 0.18 | 0.63 | 0.44 |
| ET | 1.00 | $0.1\times10^{-10}$ | 0.70 | 0.39 |
| GBR | 0.99 | 0.08 | 0.54 | 0.49 |
| XGBoost | 1.00 | 0.0008 | 0.70 | 0.39 |
| CatBoost | 1.00 | 0.02 | 0.71 | 0.39 |

为提升模型性能并防止过拟合，对基于 CatBoost 算法开发的模型进行了超参数调优。采用 Akiba 等人（2019）推荐的 Optuna 框架，因其在不同领域具有良好的可扩展性和易用性。调优后，改进的 CatBoost 模型在测试集上的 $R^2$ 和 RMSE 分别为 0.75 和 0.37；训练集上分别为 1 和 0.000025。测试集 $R^2$ 值有所提升。超参数取值见 **表 12-2**。

**表 12-2** CatBoost 模型超参数调优取值。

| Parameters | Value |
| :--- | :--- |
| Iterations | 926 |
| Depth | 5 |
| `Learning_rate` | 0.093 |
| `l2_leaf_reg` | $1.73\times10^{-7}$ |
| `Border_count` | 84 |

训练集与测试集的散点图见 **图 12-3**。散点显示，预测值与实测值分布在 45 度线附近，无显著偏离。

![Figure 12–3 Scatter diagrams of CatBoost model for training and testing sets.](img/F000055f12-03-9780443219054.jpg)

**图 12-3** CatBoost 模型训练集与测试集散点图。

此外，计算了特征重要性以理解输入参数对 CatBoost 模型的影响（**图 12-4**）。分析表明，伊斯帕尔塔（Isparta）气象站的 SPI 值对埃伊尔迪尔湖水位预测影响最大，而乌卢博尔卢（Uluborlu）站的 SPI 值影响最小。

![Figure 12–4 Feature importance chart for CatBoost model.](img/F000055f12-04-9780443219054.jpg)

**图 12-4** CatBoost 模型特征重要性图。

## LSTM 模型构建与未来预测

随后，利用埃伊尔迪尔（Eğirdir）、塞尼尔肯特（Senirkent）、乌卢博尔卢（Uluborlu）、亚尔瓦奇（Yalvaç）和伊斯帕尔塔（Isparta）五个气象站的 SPI 值，采用 LSTM 模型预测未来 10 年湖水位。数据集为 1976–2019 年共 517 个月数据，按 8:2 比例划分：训练集 409 个月（80%），测试集 108 个月（20%）。通过对比不同单元数、激活函数和优化器下的 $R^2$ 值，确定各站点最优 LSTM 模型，其超参数与 $R^2$ 见 **表 12-3**，时序预测图见 **图 12-5**。

**表 12-3** 长短期记忆（LSTM）模型最优超参数与 $R^2$ 值。

| Station | Units | Activation | Optimizer | $R^2$ |
| :--- | :---: | :---: | :---: | :---: |
| Eğirdir | 396 | tanh | adam | 0.82 |
| Senirkent | 460 | relu | adam | 0.80 |
| Uluborlu | 12 | tanh | rmsprop | 0.80 |
| Yalvaç | 364 | relu | rmsprop | 0.75 |
| Isparta | 460 | relu | adam | 0.74 |

![Figure 12–5 Time series of long short-term memory models for each station.](img/F000055f12-05a-9780443219054.jpg)

**图 12-5** 各站点 LSTM 模型时间序列预测图。

由 **表 12-3** 可知，埃伊尔迪尔站 $R^2$ 最高（0.82），伊斯帕尔塔站最低（0.74）；塞尼尔肯特站与乌卢博尔卢站均为 0.80，亚尔瓦奇站为 0.75。

**图 12-5** 显示，LSTM 模型在所有站点均能正确预测 SPI 值的增减趋势。基于上一步得到的最佳机器学习模型（CatBoost），将 LSTM 预测的未来 10 年 SPI 值作为输入，进而预测未来 10 年湖水位。1976–2019 年埃伊尔迪尔湖水位变化见 **图 12-6**，未来 10 年预测水位变化见 **图 12-7**。

![Figure 12–6 Eğirdir Lake water level change between 1976 and 2019.](img/F000055f12-06-9780443219054.jpg)

**图 12-6** 1976–2019 年埃伊尔迪尔湖水位变化。

![Figure 12–7 Eğirdir Lake water level change for the next 10 years.](img/F000055f12-07-9780443219054.jpg)

**图 12-7** 未来 10 年埃伊尔迪尔湖水位变化预测。

检查 **图 12-6** 发现，最小湖水位分别出现在 1994 年 10 月（915.81 m）、2008 年 12 月（916.25 m）和 2018 年 12 月（916.20 m）。将这些最小水位与 1990 年 11 月塞尼尔肯特、乌卢博尔卢和伊斯帕尔塔站记录的最干旱 SPI 值（**图 12-2**）对比，显示湖水位在约 48 个月后出现显著下降。同时，埃伊尔迪尔站和亚尔瓦奇站 2007 年 10 月的最干旱值与 2008 年 12 月 916.25 m 湖水位之间存在约 12 个月的滞后响应。
