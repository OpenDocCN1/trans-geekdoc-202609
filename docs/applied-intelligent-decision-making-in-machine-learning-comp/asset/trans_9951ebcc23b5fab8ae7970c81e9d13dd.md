

# 表 10.13

LSTM 和 GRU 五天后预测性能

| 货币 | MAPE | RMSE | R² | ARV | Theil's | DA | MAPE | RMSE | R² | ARV | Theil's | DA |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AUD | 0.9351 | 0.0092 | 0.7297 | 0.2667 | 0.0060 | 58 | 0.9847 | 0.0097 | 0.7005 | 0.2977 | 0.0063 | 59 |
| CAD | 0.8515 | 0.0136 | 0.8856 | 0.1311 | 0.0053 | 56 | 0.8814 | 0.0141 | 0.8780 | 0.1023 | 0.0054 | 56 |
| GBP | 0.9469 | 0.0158 | 0.9131 | 0.0889 | 0.0060 | 57 | 0.9548 | 0.0160 | 0.9109 | 0.1023 | 0.0061 | 59 |
| INR | 0.4223 | 0.0381 | 0.8888 | 0.1109 | 0.0028 | 54 | 0.5241 | 0.0369 | 0.8871 | 0.1097 | 0.0028 | 53 |
| JPY | 0.9701 | 0.1348 | 0.6851 | 0.2609 | 0.0060 | 55 | 0.9111 | 0.1293 | 0.7373 | 0.2681 | 0.0055 | 54 |

# 表 10.14

LSTM 和 GRU 七天后预测性能

| 货币 | MAPE | RMSE | R² | ARV | Theil's | DA | MAPE | RMSE | R² | ARV | Theil's | DA |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AUD | 1.2148 | 0.0118 | 0.5485 | 0.4285 | 0.0077 | 57 | 1.1356 | 0.0112 | 0.5996 | 0.3994 | 0.0073 | 56 |
| CAD | 1.0414 | 0.0167 | 0.8291 | 0.2027 | 0.0064 | 55 | 1.0168 | 0.0163 | 0.8367 | 0.1843 | 0.0063 | 55 |
| GBP | 1.2382 | 0.0221 | 0.8446 | 0.1721 | 0.0081 | 52 | 1.1744 | 0.0198 | 0.8629 | 0.1608 | 0.0076 | 52 |
| INR | 0.5220 | 0.4323 | 0.8332 | 0.1601 | 0.0033 | 55 | 0.5243 | 0.0472 | 0.8294 | 0.1546 | 0.0034 | 52 |
| JPY | 1.1153 | 1.5197 | 0.5950 | 0.3998 | 0.0068 | 50 | 1.1595 | 0.1735 | 0.5659 | 0.4233 | 0.0071 | 49 |

# 表 10.15

LSTM 和 GRU 十天后预测性能

| | LSTM 模型: MAPE | RMSE | R² | ARV | Theil's | DA | GRU 模型: MAPE | RMSE | R² | ARV | Theil's | DA |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AUD | 1.3755 | 0.0134 | 0.4225 | 0.5294 | 0.0087 | 56 | 1.3174 | 0.0127 | 0.4779 | 0.5009 | 0.0083 | 55 |
| CAD | 1.4074 | 0.0225 | 0.6885 | 0.3523 | 0.0087 | 55 | 1.2811 | 0.0203 | 0.7465 | 0.3009 | 0.0078 | 55 |
| GBP | 1.8596 | 0.0307 | 0.6697 | 0.3690 | 0.0118 | 57 | 1.3180 | 0.0224 | 0.8241 | 0.1977 | 0.0086 | 57 |
| INR | 0.6131 | 0.5077 | 0.7699 | 0.2139 | 0.0039 | 48 | 0.5707 | 0.4841 | 0.7909 | 0.1868 | 0.0037 | 51 |
| JPY | 1.2529 | 1.7016 | 0.4923 | 0.5359 | 0.0076 | 49 | 1.2719 | 1.7172 | 0.4829 | 0.5405 | 0.0077 | 50 |

# 机器学习中的应用智能决策

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_218_0.png (a)

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_218_1.png (b)

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_218_2.png (c)

**图 10.2** 不同滑动窗口（WS）下 LSTM 模型和 GRU 模型五种货币的训练和测试阶段预测：**(a)** WS 10 的 AUD 五天后预测；**(b)** WS 7 的 CAD 三天后预测；**(c)** WS 10 的 GBP 七天后预测；**(d)** WS 13 的 INR 十天后预测；以及**(e)** WS 7 的 JPY 一天后预测。

## 10.2 对于滑动窗口大小 10

表 10.6-10 显示了滑动窗口大小为10 的结果。对于 AUD、CAD 和 JPY 外汇，GRU 提供了更好的结果；对于 INR 数据集，LSTM 提供了更好的结果。当样本存在长期依赖问题时，LSTM 模型优于 GRU，因为它具有更多的特征和更复杂的架构。

# 汇率预测分析

## 10.3.3 滑动窗口大小 13

从表 10.11–15 可以观察到 LSTM 和 GRU 的结果各不相同。当预测天数较少时，LSTM 在 AUD、CAD、JPY 上表现更好。当预测天数较多时，GRU 模型在 INR、AUD 和 CAD 上表现更好。

使用 LSTM 和 GRU 模型进行五种不同货币汇率预测的模拟以及两种模型的收敛特性见图 10.2 和 10.3。

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_219_0.png

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_219_1.png

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_219_2.png

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_219_3.png

img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_219_4.png

## **图 10.3** 使用 LSTM 和 GRU 模型在不同滑动窗口大小（WS）下的 MSE 收敛图：**(a)** WS 10 的 AUD 五天后预测；**(b)** WS 7 的 CAD 三天后预测；**(c)** WS 10 的 GBP 七天后预测；**(d)** WS 13 的 INR 十天后预测；以及**(e)** WS 7 的 JPY 一天后预测。

## 10.4 结论

本章描述了一种特殊类型循环神经网络（RNN）——GRU 网络在五种货币（AUD、CAD、GBP、INR 和 JPY）汇率预测中的实现。GRU 模型将 LSTM 复杂的结构简化为具有更新门（update gates）和重置门（reset gates）的两个门控架构，并减少了执行所需的迭代次数。这导致了计算减少，使得提出的模型比 LSTM更快。LSTM 和 GRU 的性能衡量通过应用不同的窗口大小来实现。对于滑动窗口 7，GRU 模型为所有五种货币提供了最佳结果；对于滑动窗口 10 和 13，LSTM 在某些情况下表现更好。总体而言，GRU 的性能优于 LSTM。

## 参考文献

1. Taylor, S. 基于遗传算法优化的混合神经网络预测汇率 *International Journal of Forecasting*, 20:159–170.
2. Kamruzzaman, J. 使用人工神经网络进行货币汇率预测：一个案例研究 *International Conference on Emerging Trends in Engineering, Sciences and Technology (ICEEST)*, IEEE, Karachi, Pakistan, 2018.
3. Yu, L. 外汇预测中的自适应平滑神经网络 *International Conference on Computational Science*, Springer, Heidelberg, 2005.
4. Hussain, A. 受免疫算法启发的动态自组织神经网络用于金融时间序列预测 *Neurocomputing*, 188:23–30.
5. Nada, S. 基于模糊系统的神经汇率预测 *International Conference on Control and Automation*, 2006.
6. Huang, W. 使用深度神经网络预测汇率 *Saud University*, 27:4–5.
7. Rajajan, N. 基于深度学习的汇率预测 *International Conference on Neural Networks*, Springer, India, 2018.
8. He, K. 基于深度学习的汇率预测 *Physicsia Science*, 114:239–244.
9. Das, S. 基于特征提取的汇率预测 *International Conference on Knowledge*, 2019:31–32.
10. Young, Y. 基于深度学习的汇率预测 *Procedia Computer Science*, 147:647–652.
11. Andreou, A. 基于共轭方法的深度神经网络预测汇率 *Computational Economics*, 72:191–220.
12. Jena, P. 一种知识引导人工神经网络（KGANN）汇率预测模型 *Saud University-Computer and Information Sciences*, 27:450–457.
13. Rehman, M. 使用 LSTM 和循环网络预测外汇率 *IERI Procedia*, 10:239–244.
14. Ni, L. 基于深度学习的外汇时间序列预测 *Procedia Computer Science*, 2019.

