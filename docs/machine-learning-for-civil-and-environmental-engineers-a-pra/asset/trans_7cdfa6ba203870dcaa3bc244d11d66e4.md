

表 5.1 常用回归指标列表。

| No. | Metric | Definition/remarks | Formula | Notes |
|---|---|---|---|---|
| 1 | Error (E) | 预测值与其实际值之间的差异量。 | \( E = A - P \) | 直观。易于应用。 |
| 2 | Mean error (ME) | 一组中所有误差的平均值。 | \( ME = \frac{\sum_{i=1}^n E_i}{n} \) | 在正负预测相互抵消的情况下可能无济于事。倾向于高估。 |
| 3 | Mean Normalized Bias (MNB) | 与基于观测的最小阈值相关。 | \( MNB = \frac{\sum_{i=1}^n E_i / A_i}{n} \) | 当任何实际值为零时未定义。 |
| 4 | Mean Percentage Error (MPE) | 百分误差的计算平均值。 | \( MPE = \frac{\sum_{i=1}^n E_i / A_i}{n / 100} \) | 与输入数据使用相似的比例 [7]。可比较不同尺度。 |
| 5 | Mean Absolute Error (MAE)* | 测量两个连续变量之间的差异。 | \( MAE = \frac{\sum_{i=1}^n |E_i|}{n} \) | 常用作损失函数 [8]。如果存在零值，则无法使用。对于小预测，百分误差不能超过 1.0。无上限。非对称（如果预测值大于或小于相应实际值，则会受到不利影响）[8]。\( E_i \) 从零（理想）到无穷大。 |
| 6 | Mean Absolute Percentage Error (MAPE)* | 以百分比形式衡量误差程度。 | \( MAPE = \frac{100}{n} \sum_{i=1}^n |E_i| / |A_i| \) | 对异常值敏感。除以零时未定义。对于完美拟合，分子等于零 [9]。 |
| 7 | Relative Absolute Error (RAE) | 以比率形式表示，将平均误差与平凡模型产生的误差进行比较。 | \( RAE = \sum_{i=1}^n |E_i| / |A_i - A_{mean}| \) | |
| 8 | Mean Absolute Relative Error (MARE) | 测量绝对误差与随机误差之比的平均值。 | \( MARE = \frac{1}{n} \sum_{i=1}^n |E_i| / |A_i| \) | |
| 9 | Mean Relative Absolute Error (MRAE) | 误差累积与随机误差累积之比。 | \( MRAE = \frac{\sum_{i=1}^n |E_i| / |A_i - A_{mean}|}{n} \) | |

- 对于平均相对量相比算术平均值可能更合适 [10]。
- 可能会被大异常值和小误差主导。
- 适用于数值数据。
- 依赖于尺度 [11]。
- 值越接近零，状态越充分。
- 异常值权重大。
- 高度依赖所用数据比例（可靠性低）[12]。
- 倾向于过度预测 [13]。
- MSE 的扩展。
- 依赖于尺度。
- RMSE 值越低越有利。
- 对异常值敏感。
- 高度依赖所用数据比例 [12]。
- MSE 的扩展。
- 与尺度无关。
- 可用于比较不同数据集的预测。
- 非对称 [8]。
- RMSE 的扩展。
- 可用于比较不同数据集的预测 [14]。
- 适用于数值数据。
- RMSE 的扩展。

### 10 几何平均绝对误差 (GMAE)*

定义为误差值乘积的 n 次方根。

\[ GMAE = \sqrt[n]{\prod_{i=1}^n |E_i|} \]

### 11 分数绝对误差 (FAE)

评估绝对分数误差。

\[ FAE = \frac{1}{n} \sum_{i=1}^n \frac{2 \times |E_i|}{|A_i| + |P_i|} \]

### 12 均方误差 (MSE)

测量误差平方的平均值。

\[ MSE = \frac{\sum_{i=1}^n E_i^2}{n} \]

### 13 归一化均方误差 (NMSE)

估计测量值与预测值之间的总体偏差。

\[ NMSE = \frac{\sum_{i=1}^n E_i^2}{n} \]

### 14 均方根误差 (RMSE)

平均平方误差的平方根。

\[ RMSE = \sqrt{\frac{\sum_{i=1}^n E_i^2}{n}} \]

### 15 根平均平方百分误差 (RMSPE)

以百分比形式评估平方误差的平均值。

\[ RMSPE = \sqrt{\frac{\sum_{i=1}^n (|E_i|/|A_i|)^2}{n/100}} \]

### 16 归一化均方根误差 (NRMSE)*

归一化均方根误差。

\[ NRMSE = \frac{\sqrt{\frac{\sum_{i=1}^n E_i^2}{n}}}{A_{mean}} \]

| No. | Metric | Definition/remarks | Formula | Notes |
|:---|:---|:---|:---|:---|
| 17 | 几何均方根误差 (GRMSE) | 评估几何平方根误差。 | $GRMSE = 2n \sqrt[n]{\prod_{i=1}^n E_i^2}$ | 依赖于尺度。比 RMSE 对异常值的敏感度低 [11]。RMSE 的扩展。较低的 RRMSE 值更有利。 |
| 18 | 相对均方根误差 (RRMSE) [15] | 呈现准确性的百分比变化。 | $RRMSE = \sqrt{\frac{1}{n} \sum (A - P)^2}$ | |
| 19 | 平方误差和 (SSE) | 对每个观测值与其均值之间的平方差求和。 | $SSE = \sum_{i=1}^n E_i^2$ | 较小的 SSE 表示良好的拟合 [16]。 |
| 20 | 相对平方误差 (RSE) | 通过除以总平方误差来归一化总平方误差。 | $RSE = \frac{\sum_{i=1}^n E_i^2}{(A_i - A_{mean})^2}$ | 当分子等于零时实现完美拟合 [9]。 |
| 21 | 根相对平方误差 (RRSE) | 评估两个向量之间的根相对平方误差。 | $RRSE = \sqrt{\frac{\sum_{i=1}^n E_i^2}{\sum (A_i - A_{mean})^2}}$ | 在 0 到 1.0 之间，0 为理想值 [9]。 |
| 22 | 平均平方百分误差 (MSPE)* | 评估平方百分误差的平均值。 | $MSPE = \frac{\sum_{i=1}^n (|E_i|/|A_i|)^2}{n/100}$ | 非对称 [8]。 |
| 23 | 相关系数 (R) | 测量变量之间关联的强度。 | $R = \frac{\sum_{i=1}^n (A_i - \bar{A})(P_i - \bar{P})}{\sqrt{\sum_{i=1}^n (A_i - \bar{A})^2 \sum_{i=1}^n (P_i - \bar{P})^2}}$ | R > 0.8 意味着强相关 [17]。等比例缩放不改变。无法区分自变量和因变量。 |
| 24 | 决定系数 ($R^2$) | 相关系数的平方。 | $R^2 = 1 - \frac{\sum_{i=1}^n (P_i - A_i)^2}{\sum_{i=1}^n (A_i - A_{mean})^2}$ | 接近 1.0 的 $R^2$ 值表明强相关。与 R 相关。添加预测因子会增加 R^2（即使仅由于偶然因素）。与尺度无关。在零附近稳定 [11]。 |
| 25 | 平均绝对缩放误差 (MASE) | 平均绝对误差除以平均绝对误差。 | $\frac{\sum_{i=1}^n E_i}{n/100 \cdot \frac{1}{A_i} |\sum_{i=1}^n A_i - A_{i-1}|}$ | |

### 26 Golbraikh 和 Tropsha 的标准 [18]

实际值 (Ay) 对预测输出 (Pj) 或 Pj 对 Ay 通过原点的回归线之间至少有一个回归斜率（k 或 k'），即 Ay = k × Pj 和 Pj = k' Ay。

\[ k = \frac{\sum_{i=1}^n (A_i \times P_i)}{A_i^2} \]

\[ k' = \frac{\sum_{i=1}^n (A_i \times P_i)}{P_i^2} \]

\[ m = \frac{R^2 - R_0^2}{R^2} \]

\[ n = \frac{R^2 - R_{0^\prime}^2}{R^2} \]

- k 和 k' 需要接近 1.0，或者至少在 0.85 到 1.15 的范围内。
- m 和 n 是性能指数，其绝对值应低于 0.1。

### 27 Roy 和 Roy 的 Q.S.A.R. 模型 [19]

\[ R_m = R^2 \times \left(1 - \sqrt{|R^2 - R_0^2|}\right) \]

其中

\[ \frac{\sum_{i=1}^n (P_i - A_i^o)^2}{\sum_{i=1}^n (P_i - P_{mean})^2}, A_i^o = k \times P_i^o \]

\[ = 1 - \frac{\sum_{i=1}^n (A_i - P_i^o)^2}{\sum_{i=1}^n (A_i - A_{mean})^2}, P_i^o = k' \times A_i \]

- \(R_m\) 是外部可预测性指标。\(R_m > 0.5\) 意味着良好的拟合。

### 28 Frank 和 Todeschini [20]

建议观测数量与输入参数之间保持 3-5 的比率。

表 5.1（续）

| No. | Metric | Definition/remarks | Formula | Notes |
|:---|:---|:---|:---|:---|
| 29 | Gandomi 等人提出的目标函数 [21] | 多准则指标。 | \( Function = \frac{(N_{O-Training} - N_{O-Validation})}{N_{O-Training} + N_{O-Validation}} \frac{RMSE_{Training} + MAE_{Learning}}{R_{Learning} + 1} + \frac{2N_{O-Validation}}{N_{O-Training} + N_{O-Validation}} \frac{RMSE_{Validation} + MAE_{Validation}}{R_{Training} + 1} \) 其中，No. Training 和 No. Validation 分别是训练和验证数据的数量。 | 需要最小化该函数以获得最高适应度。 |
| 30 | Cheng 等人提出的参考索引 (RI) [22] | 一种统一考虑 RMSE、MAE 和 MAPE 的多准则指标。 | \( RI = \frac{RMSE + MAE + MAPE}{3} \) | 每个性能指标都归一化以达到最佳性能。RMSE、MAE 和 MAPE 的扩展。 |
| 31 | 散射指数 (SI) [23] | 用于检验 RMSE 是否良好。 | \( SI = \frac{\sqrt{\sum_{i=1}^n (P_{max}(A) - P_{max}(p))^2 / n}}{P_{max}(p)} \) 其中 n = 训练阶段使用的数据集数量。P_max(p) = 实际观测数据的平均值 | SI 是相对于测量数据平均值归一化的 RMSE。如果 SI 小于 1，则估计是可接受的。当 SI < 0.1 时为“优异性能”，当 0.1 < SI < 0.2 时为“良好性能”，当 0.2 < SI < 0.3 时为“中等性能”，当 SI > 0.3 时为“较差性能”。 |
| 32 | 综合指数 (SyI) [24] | 基于 MAE、RMSE 和 MAPE 的综合性能度量。 | \( SyI = \frac{1}{n} \sum_{i=1}^n \left( \frac{P_i - P_{min,i}}{P_{max,i} - P_{min,i}} \right) \) 其中，n = 性能指标数量；P_i = 第 i 个性能指标。 | SI 值范围在 0.0 到 1.0 之间；SI 值接近 0 表示高精度预测模型。 |
| 33 | 性能指数 (PI) [15] | 用于评估模型预测能力的性能指数。 | \( PI = \frac{RMSE}{1+R} \) | 较低的 PI 值会产生更准确的模型预测。 |

