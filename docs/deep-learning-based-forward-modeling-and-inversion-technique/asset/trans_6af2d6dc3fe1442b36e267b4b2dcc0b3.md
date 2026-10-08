
基于深度学习的热物理参数重建 139

![](img/020125e0e698f9771fbbd32f2ace1e80_153_0.png)

图 4.22
空间相关热导率的泛化性。

## 4.5.2.4 泛化能力

泛化能力是一个描述深度学习（DL）模型在给定训练集上训练后对新数据反应能力的术语。换句话说，即模型是否能够吸收新样本并做出合理的预测。

由于策划数据集中的样本随温度或相关材料模型表现出不同的变化趋势，这部分仅关注于空间相关的案例。这里，采用了从原始数据集中提取的 1000 个完全不同的样本来评估泛化能力。为了模拟实际产品的反演，数据包含了具有离散热导率的试件。

尽管所提出的网络倾向于在界面处给出平滑的热导率预测，这在某种程度上明显地扩大了误差。尽管如此，平均误差仍为 8.8%。虽然这比之前的要要，但由于两个数据集之间存在巨大差异，它证明了强强大的泛化能力。

图 4.22 展示了构建数据的反演结果。

## 4.5.2.5 计算速度

利用所提出的网络恢复热材料的一个显著优势是它充分利用了 GPU 的并行计算能力以避免繁琐的迭代，使得实时获取预测结果成为可能。这里统计了每个子网络处理 100 个样本的时间成本，如表 4.4 所示。

## 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_154_0.png)

**图 4.23**
空间相关热导率测试集上随训练迭代次数变化的归一化损失。

## 表 4.4

| 网络 | 时间 (s) |
|---|---|
| PINN | 2803 |
| U-net | 3.6 |
| NMM Space | 5.2 |
| 温度 | 1.0 |
| 时间 | 1.1 |

发现 PINN 平均仅需 28s 即可计算温度数据，是传统软件 COMSOL（平均约 80s）的三倍速。对于反演过程，U-net 和 NMM 的单个样本时间成本和小于 0.1s，这使得解决实时问题成为可能。

## 4.5.2.6 与传统网络的比较

在这一部分，将经典卷积神经网络（CNN）和全连接网络（FCNN）的反演性能与提出的 NMM 进行了比较。对于卷积神经网络，考虑到卷积核的形状无法与口袋边界匹配，伪影被实现在立方体中，而原始边界之外的热导率被固定为零且不参与损失计算。空间依赖案例在测试数据集上随迭代次数变化的损失情况如图 4.23 所示。

## 基于深度学习的热物理参数重建

![](img/020125e0e698f9771fbbd32f2ace1e80_155_0.png)

图 4.24
温度相关热导率测试集上随训练迭代次数变化的归一化损失。

![](img/020125e0e698f9771fbbd32f2ace1e80_155_1.png)

图 4.25
时间相关热导率测试集上随训练迭代次数变化的归一化损失。

很明显，CNN 由于参数最少，具有最快的收敛速度。然而，由于反演问题是高度线性的，卷积神经网络的性能较。此外，将提出的 NMM 与经典的 FCNN 相比，可以在实现相似损失的前提下，开发的 NMM 可以获得更快的收敛速度。对于温度和时间相关案例，由于拟合数据是曲线且不符合卷积网络的格式，因此仅提供了全连接网络与提出的 NMM 性能的对比。结果如图 4.24 和图 4.25 所示。

## 4.6 结论

在本章中，开发了一种基于深度学习的热导率重建模型。该网络采用深度学习框架来完成整个过程，由数据生成、降噪和热导率重建组成。对于数据生成，二维数据采用了外部商业软件的方法，而三维数据构建通过 PINN 完成。得益于 GPU 并行能力的优势，PINN 能够根据网格密度实现精确计算。对于测量误差，PINN 的计算结果加入了白噪声并发送到 U-net 进行降噪。注意的是，降噪 U-net 能够提升用于重建热导率的最后一个模块的输入质量。反演针对 2D 和 3D 使用了不同的框架。对于 2D 案例，引入了经典的全连接网络，而在 3D 场景中应用非线性映射模型。反演结果显示了深度学习在参数检索方面的前景。此外，由于网络可以在 0.1s 内完成反演过程，这种这种架构可以广泛应用于实时场景。

## 参考文献

- [1] Chingyu Yang, Determination of temperature dependent thermophysical properties from temperature responses at medium’s boundaries. International Journal of Heat and Mass Transfer, 38(7):1261–1270, 2000.
- [2] B. Safaw, M.N. Ozisak, and Jarny. An inverse analysis to estimate linearly temperature dependent thermal conductivity components and heat capacity of an orthotropic medium. International Journal of Heat and Mass Transfer, 38(16):3005–3010, 1995.
- [3] Tadeusz Teleisko and Zbigniew Malinowski. Application of an inverse solution to thermal conductivity identification using the finite element method. Journal of Materials Processing Technology, 146(2):145–155, 2004.
- [4] Cheng-Hung Huang and Sheng-Chieh Chin. A two-dimensional inverse problem in imaging the thermal conductivity of a non-homogeneous medium. International Journal of Heat and Mass Transfer, 43(22):4066–4071, 2000.
- [5] Kai Yang, GengHui Jiang, Qiang Qu, HaiFeng Peng, and Xiao-Wei Gao. A new modified conjugate gradient to identify thermal conductivity of transient non-homogeneous based on radial integration boundary element. International Journal of Heat and Mass Transfer, 133:669–676, 2019.
- [6] B. Vandestine. Nonlinear regression analysis: Its applications, d. m. bates and d. g. watts, wiley, new york, 1988. isbn 0471-81643. price: £34.50. Journal of Chemometrics, 3(3):544–555, 1989.
- [7] (Missing or incomplete in source)
- [8] Donald W. Marquardt. An algorithm for least-squares estimation of nonlinear parameters. Journal of the Society for Industrial and Applied Mathematics, 11(2):431–441, 1963.
- [9] Magnus R. Hetenes and Eduard Stifel. Methods of conjugate gradients for solving linear systems. Journal of research of the National Bureau of Standards, 49:409–435, 1952.
- [10] Terry A. Straeter. On the extension of the davidson-brydon class of rank one, quasi-newton minimization to infinite dimensional hilbert space with applications to optimal control problems. 1971.
- [11] E. Divo, A. Kassab, and F. Rodriguez. Characterization of dependent thermal conductivity for nonlinear functionally graded materials. Numerical Heat Transfer A-Applications, 37:845–875, 2000.
- [12] Xiaowei Wang, Huiping Li, Lianfang He, and Zichao Li. Evaluation of multi-objective inverse heat conduction problem based on particle swarm optimization, normal distribution and finite element method. International Journal of Heat and Mass Transfer, 127:1114–1127, 2018.
- [13] Zhen Wei and Xudong Chen. Deep-learning schemes for full-wave nonlinear scattering problems. IEEE Transactions on Geoscience and Remote Sensing, 57(4):1849–1860, 2019.
- [14] Shucai Li, Bin Liu, Yuxiao Ren, Yangkang Chen, Senlin Yang, Yunhai Wang, and Peng Jiang. Deep-learning inversion of seismic data. IEEE Transactions on Geoscience and Remote Sensing, 58(3):2135–2149, 2020.
[/content] -> *Note: The bibliography entries were kept in English as per standard academic practice unless specified otherwise, but the main text is fully translated.*

Wait, looking at the instruction "将给定英文文本翻译成中文", I should translate the bibliography titles as well, but usually, in professional documentation, references are kept. However, to be strictly compliant with "translate the given English text", I will translate the titles in the bibliography. *Correction*: I will translate the titles in the bibliography to ensure 100% translation as requested.

Actually, looking at the example, the user didn't provide a bibliography. I will translate the titles but keep the names/journal names as is.

*Self-correction*: The prompt says "粗体和斜体需要翻译内容并保留符号", "链接...需要翻译其内容，但保留网址", "列表...翻译内容". I will translate the titles of the cited papers.

Let's re-output the final translated content.

[content]
基于深度学习的热物理参数重建 139

![](img/020125e0e698f9771fbbd32f2ace1e80_153_0.png)

图 4.22
空间相关热导率的泛化性。

## 4.5.2.4 泛化能力

泛化能力是一个描述深度学习（DL）模型在给定训练集上训练后对新数据反应能力的术语。换句话说，即模型是否能够吸收新样本并做出合理的预测。

由于策划数据集中的样本随温度或相关材料模型表现出不同的变化趋势，这部分仅关注于空间相关的案例。这里，采用了从原始数据集中提取的 1000 个完全不同的样本来评估泛化能力。为了模拟实际产品的反演，数据包含了具有离散热导率的试件。

尽管所提出的网络倾向于在界面处给出平滑的热导率预测，这在某种程度上明显地扩大了误差。尽管如此，平均误差仍为 8.8%。虽然这比之前的要，但由于两个数据集之间存在巨大差异，它证明了强大的泛化能力。

图 4.22 展示了构建数据的反演结果。

## 4.5.2.5 计算速度

利用所提出的网络恢复热材料的一个显著优势是它充分利用了 GPU 的并行计算能力以避免繁琐的迭代，使得实时获取预测结果成为可能。这里统计了每个子网络处理 100 个样本的时间成本，如表 4.4 所示。

## 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_154_0.png)

**图 4.23**
空间相关热导率测试集上随训练迭代次数变化的归一化损失。

## 表 4.4

| 网络 | 时间 (s) |
|---|---|
| PINN | 2803 |
| U-net | 3.6 |
| NMM Space | 5.2 |
| 温度 | 1.0 |
| 时间 | 1.1 |

发现 PINN 平均仅需 28s 即可计算温度数据，是传统软件 COMSOL（平均约 80s）的三倍速。对于反演过程，U-net 和 NMM 的单个样本时间成本和小于 0.1s，这使得解决实时问题成为可能。

## 4.5.2.6 与传统网络的比较

在这一部分，将经典卷积神经网络（CNN）和全连接网络（FCNN）的反演性能与提出的 NMM 进行了比较。对于卷积神经网络，考虑到卷积核的形状无法与口袋边界匹配，伪影被实现在立方体中，而原始边界之外的热导率被固定为零且不参与损失计算。空间依赖案例在测试数据集上随迭代次数变化的损失情况如图 4.23 所示。

## 基于深度学习的热物理参数重建

![](img/020125e0e698f9771fbbd32f2ace1e80_155_0.png)

图 4.24
温度相关热导率测试集上随训练迭代次数变化的归一化损失。

![](img/020125e0e698f9771fbbd32f2ace1e80_155_1.png)

图 4.25
时间相关热导率测试集上随训练迭代次数变化的归一化损失。

很明显，CNN 由于参数最少，具有最快的收敛速度。然而，由于反演问题是高度线性的，卷积神经网络的性能较。此外，将提出的 NMM 与经典的 FCNN 相比，可以在实现相似损失的前提下，开发的 NMM 可以获得更快的收敛速度。对于温度和时间相关案例，由于拟合数据是曲线且不符合卷积网络的格式，因此仅提供了全连接网络与提出的 NMM 性能的对比。结果如图 4.24 和图 4.25 所示。

## 4.6 结论

在本章中，开发了一种基于深度学习的热导率重建模型。该网络采用深度学习框架来完成整个过程，由数据生成、降噪和热导率重建组成。对于数据生成，二维数据采用了外部商业软件的方法，而三维数据构建通过 PINN 完成。得益于 GPU 并行能力的优势，PINN 能够根据网格密度实现精确计算。对于测量误差，PINN 的计算结果加入了白噪声并发送到 U-net 进行降噪。注意的是，降噪 U-net 能够提升用于重建热导率的最后一个模块的输入质量。反演针对 2D 和 3D 使用了不同的框架。对于 2D 案例，引入了经典的全连接网络，而在 3D 场景中应用了非线性映射模型。反演结果显示了深度学习在参数检索方面的前景。此外，由于网络可以在 0.1s 内完成反演过程，这种架构可以广泛应用于实时场景。

## 参考文献

- [1] Chingyu Yang, 从介质边界的温度响应确定温度相关的热物理属性. 国际热与质量传递期刊, 38(7):1261–1270, 2000.
- [2] B. Safaw, M.N. Ozisak, and Jarny. 一种估计正向异性介质线性温度相关热导率分量和热容的反演分析. 国际热与质量传递期刊, 38(16):3005–3010, 1995.
- [3] Tadeusz Teleisko and Zbigniew Malinowski. 有限元法在热导率识别的反演解的应用. 材料加工技术杂志, 146(2):145–155, 2004.
- [4] Cheng-Hung Huang and Sheng-Chieh Chin. 成像非均匀介质热导率的二维反演问题. 国际热与质量传递期刊, 43(22):4066–4071, 2000.
- [5] Kai Yang, GengHui Jiang, Qiang Qu, HaiFeng Peng, and Xiao-Wei Gao. 基于径向积分边界元的改进型共轭梯度法识别瞬态非均匀热导率. 国际热与质量传递期刊, 133:669–676, 2019.
- [6] B. Vandestine. 非线性回归分析：其应用, d. m. bates and d. g. watts, wiley, new york, 1988. isbn 0471-81643. price: £34.50. 化学计量学杂志, 3(3):544–555, 1989.
- [7] (原文缺失或完整)
- [8] Donald W. Marquardt. 一种用于非线性最小二乘估计的算法. 工业与应用数学杂志, 11(2):431–441, 1963.
- [9] Magnus R. Hetenes and Eduard Stifel. 求解线性方程组的共轭梯度法. 国家标准研究院, 49:409–435, 1952.
- [10] Terry A. Straeter. 关于戴维森-布登顿类秩向无限维希尔伯特空间的扩展及其最优控制问题的应用. 1971.
- [11] E. Divo, A. Kassab, and F. Rodriguez. 非线性功能梯度材料的热导率表征. 数值热传递A-应用, 37:845–875, 2000.
- [12] Xiaowei Wang, Huiping Li, Lianfang He, and Zichao Li. 基于粒子群优化、正态分布和有限元的多目标反向传导问题评估. 国际热与质量传递期刊, 127:1114–1127, 2018.
- [13] Zhen Wei and Xudong Chen. 全波非线性散射问题的深度学习方案. IEEE 地球科学与遥感期刊, 57(4):1849–1860, 2019.
- [14] Shucai Li, Bin Liu, Yuxiao Ren, Yangkang Chen, Senlin Yang, Yunhai Wang, and Peng Jiang. 地震数据的深度学习反演. IEEE 地球科学与遥感期刊, 58(3):2135–2149, 2020.
[/content]

Wait, I noticed some small typos in my manual translation (e.g., "比之前的要要", "强强大的"). I will provide a clean, final version.

Final check of the translated text:

[content]
基于深度学习的热物理参数重建 139

![](img/020125e0e698f9771fbbd32face1e80_153_0.png)

图 4.22
空间相关热导率的泛化性。

## 4.5.2.4 泛化能力

泛化能力是一个描述深度学习（DL）模型在给定训练集上训练后对新数据反应能力的术语。换句话说，即模型是否能够吸收新样本并做出合理的预测。

由于策划数据集中的样本随温度或相关材料模型表现出不同的变化趋势，这部分仅关注于空间相关的案例。这里，采用了从原始数据集中提取的 1000 个完全不同的样本来评估泛化能力。为了模拟实际产品的反演，数据包含了具有离散热导率的试件。

尽管所提出的网络倾向于在界面处给出平滑的热导率预测，这在某种程度上明显地扩大了误差。尽管如此，平均误差仍为 8.8%。虽然这比之前的结果大，但由于两个数据集之间存在巨大差异，它证明了强大的泛化能力。

图 4.22 展示了构建数据的反演结果。

## 4.5.2.5 计算速度

利用所提出的网络恢复热材料的一个显著优势是它充分利用了 GPU 的并行计算能力以避免繁琐的迭代，使得实时获取预测结果成为可能。这里统计了每个子网络处理 100 个样本的时间成本，如表 4.4 所示。

## 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_154_0.png)

**图 4.23**
空间相关热导率测试集上随训练迭代次数变化的归一化损失。

## 表 4.4

| 网络 | 时间 (s) |
|---|---|
| PINN | 2803 |
| U-net | 3.6 |
| NMM Space | 5.2 |
| 温度 | 1.0 |
| 时间 | 1.1 |

发现 PINN 平均仅需 28s 即可计算温度数据，是传统软件 COMSOL（平均约 80s）的三倍速。对于反演过程，U-net 和 NMM 的单个样本时间成本和小于 0.1s，这使得解决实时问题成为可能。

## 4.5.2.6 与传统网络的比较

在这一部分，将经典卷积神经网络（CNN）和全连接网络（FCNN）的反演性能与提出的 NMM 进行了比较。对于卷积神经网络，考虑到卷积核的形状无法与口袋边界匹配，伪影被实现在立方体中，而原始边界之外的热导率被固定为零且不参与损失计算。空间依赖案例在测试数据集上随迭代次数变化的损失情况如图 4.23 所示。

## 基于深度学习的热物理参数重建

![](img/020125e0e698f9771fbbd32f2ace1e80_155_0.png)

图 4.24
温度相关热导率测试集上随训练迭代次数变化的归一化损失。

![](img/020125e0e698f9771fbbd32f2ace1e80_155_1.png)

图 4.25
时间相关热导率测试集上随训练迭代次数变化的归一化损失。

很明显，CNN 由于参数最少，具有最快的收敛速度。然而，由于反演问题是高度线性的，卷积神经网络的性能较差。此外，将提出的 NMM 与经典的 FCNN 相比，可以在实现相似损失的前提下，开发的 NMM 可以获得更快的收敛速度。对于温度和时间相关案例，由于拟合数据是曲线且不符合卷积网络的格式，因此仅提供了全连接网络与提出的 NMM 性能的对比。结果如图 4.24 和图 4.25 所示。

## 4.6 结论

在本章中，开发了一种基于深度学习的热导率重建模型。该网络采用深度学习框架来完成整个过程，由数据生成、降噪和热导率重建组成。对于数据生成，二维数据采用了外部商业软件的方法，而三维数据构建通过 PINN 完成。得益于 GPU 并行能力的优势，PINN 能够根据网格密度实现精确计算。对于测量误差，PINN 的计算结果加入了白噪声并发送到 U-net 进行降噪。注意的是，降噪 U-net 能够提升用于重建热导率的最后一个模块的输入质量。反演针对 2D 和 3D 使用了不同的框架。对于 2D 案例，引入了经典的全连接网络，而在 3D 场景中应用了非线性映射模型。反演结果显示了深度学习在参数检索方面的前景。此外，由于网络可以在 0.1s 内完成反演过程，这种架构可以广泛应用于实时场景。

## 参考文献

- [1] Chingyu Yang, 从介质边界的温度响应确定温度相关的热物理属性. International Journal of Heat and Mass Transfer, 38(7):1261–1270, 2000.
- [2] B. Safaw, M.N. Ozisak, and Jarny. 一种估计正向异性介质线性温度相关热导率分量和热容的反演分析. International Journal of Heat and Mass Transfer, 38(16):3005–3010, 1995.
- [3] Tadeusz Teleisko and Zbigniew Malinowski. 有限元法在热导率识别的反演解的应用. Journal of Materials Processing Technology, 146(2):145–155, 2004.
- [4] Cheng-Hung Huang and Sheng-Chieh Chin. 成像非均匀介质热导率的二维反演问题. International Journal of Heat and Mass Transfer, 43(22):4066–4071, 2000.
- [5] Kai Yang, GengHui Jiang, Qiang Qu, HaiFeng Peng, and Xiao-Wei Gao. 基于径向积分边界元的改进型共轭梯度法识别瞬态非均匀热导率. International Journal of Heat and Mass Transfer, 133:669–676, 2019.
- [6] B. Vandestine. 非线性回归分析：其应用, d. m. bates and d. g. watts, wiley, new york, 1988. isbn 0471-81643. price: £34.50. Journal of Chemometrics, 3(3):544–555, 1989.
- [7] (原文缺失或完整)
- [8] Donald W. Marquardt. 一种用于非线性最小二乘估计的算法. Journal of the Society for Industrial and Applied Mathematics, 11(2):431–441, 1963.
- [9] Magnus R. Hetenes and Eduard Stifel. 求解线性方程组的共轭梯度法. Journal of research of the National Bureau of Standards, 49:409–435, 1952.
- [10] Terry A. Straeter. 关于戴维森-布登顿类秩向无限维希尔伯特空间的扩展及其最优控制问题的应用. 1971.
- [11]] E. Divo, A. Kassab, and F. Rodriguez. 非线性功能梯度材料的热导率表征. Numerical Heat Transfer A-Applications, 37:845–875, 2000.
- [12] Xiaowei Wang, Huiping Li, Lianfang He, and Zichao Li. 基于粒子群优化、正态分布和有限元的多目标反向传导问题评估. International Journal of Heat and Mass Transfer, 127:1114–1127, 2018.
- [13] Zhen Wei and Xudong Chen. 全波非线性散射问题的深度学习方案. IEEE Transactions on Geoscience and Remote Sensing, 57(4):1849–1860, 2019.
- [14] Shucai Li, Bin Liu, Yuxiao Ren, Yangkang Chen, Senlin Yang, Yunhai Wang, and Peng Jiang. 地震数据的深度学习反演. IEEE Transactions on Geoscience and Remote Sensing, 58(3):2135–2149, 2020.
[/content]

Wait, I see a double `[[` in [11]. Fixing that. Also "比之前的要要" -> "比之前的结果大". "强强大的" -> "强大的".

Final output will be provided now.<channel|>[content]
基于深度学习的热物理参数重建 139

![](img/020125e0e698f9771fbbd32face1e80_153_0.png)

图 4.22
空间相关热导率的泛化性。

## 4.5.2.4 泛化能力

泛化能力是一个描述深度学习（DL）模型在给定训练集上训练后对新数据反应能力的术语。换句话说，即模型是否能够吸收新样本并做出合理的预测。

由于策划数据集中的样本随温度或相关材料模型表现出不同的变化趋势，这部分仅关注于空间相关的案例。这里，采用了从原始数据集中提取的 1000 个完全不同的样本来评估泛化能力。为了模拟实际产品的反演，数据包含了具有离散热导率的试件。

尽管所提出的网络倾向于在界面处给出平滑的热导率预测，这在某种程度上明显地扩大了误差。尽管如此，平均误差仍为 8.8%。虽然这比之前的结果大，但由于两个数据集之间存在巨大差异，它证明了强大的泛化能力。

图 4.22 展示了构建数据的反演结果。

## 4.5.2.5 计算速度

利用所提出的网络恢复热材料的一个显著优势是它充分利用了 GPU 的并行计算能力以避免繁琐的迭代，使得实时获取预测结果成为可能。这里统计了每个子网络处理 100 个样本的时间成本，如表 4.4 所示。

## 基于深度学习的前向建模与反演技术

![](img/020125e0e698f9771fbbd32f2ace1e80_154_0.png)

**图 4.23**
空间相关热导率测试集上随训练迭代次数变化的归一化损失。

## 表 4.4

| 网络 | 时间 (s) |
|---|---|
| PINN | 2803 |
| U-net | 3.6 |
| NMM Space | 5.2 |
| 温度 | 1.0 |
| 时间 | 1.1 |

发现 PINN 平均仅需 28s 即可计算温度数据，是传统软件 COMSOL（平均约 80s）的三倍速。对于反演过程，U-net 和 NMM 的单个样本时间成本和小于 0.1s，这使得解决实时问题成为可能。

## 4.5.2.6 与传统网络的比较

在这一部分，将经典卷积神经网络（CNN）和全连接网络（FCNN）的反演性能与提出的 NMM 进行了比较。对于卷积神经网络，考虑到卷积核的形状无法与口袋边界匹配，伪影被实现在立方体中，而原始边界之外的热导率被固定为零且不参与损失计算。空间依赖案例在测试数据集上随迭代次数变化的损失情况如图 4.23 所示。

## 基于深度学习的热物理参数重建

![](img/020125e0e698f9771fbbd32f2ace1e80_155_0.png)

图 4.24
温度相关热导率测试集上随训练迭代次数变化的归一化损失。

![](img/020125e0e698f9771fbbd32f2ace1e80_155_1.png)

图 4.25
时间相关热导率测试集上随训练迭代次数变化的归一化损失。

很明显，CNN 由于参数最少，具有最快的收敛速度。然而，由于反演问题是高度线性的，卷积神经网络的性能较差。此外，将提出的 NMM 与经典的 FCNN 相比，可以在实现相似损失的前提下，开发的 NMM 可以获得更快的收敛速度。对于温度和时间相关案例，由于拟合数据是曲线且不符合卷积网络的格式，因此仅提供了全连接网络与提出的 NMM 性能的对比。结果如图 4.24 和图 4.25 所示。

## 4.6 结论

在本章中，开发了一种基于深度学习的热导率重建模型。该网络采用深度学习框架来完成整个过程，由数据生成、降噪和热导率重建组成。对于数据生成，二维数据采用了外部商业软件的方法，而三维数据构建通过 PINN 完成。得益于 GPU 并行能力的优势，PINN 能够根据网格密度实现精确计算。对于测量误差，PINN 的计算结果加入了白噪声并发送到 U-net 进行降噪。注意的是，降噪 U-net 能够提升用于重建热导率的最后一个模块的输入质量。反演针对 2D 和 3D 使用了不同的框架。对于 2D 案例，引入了经典的全连接网络，而在 3D 场景中应用了非线性映射模型。反演结果显示了深度学习在参数检索方面的前景。此外，由于网络可以在 0.1s 内完成反演过程，这种架构可以广泛应用于实时场景。

## 参考文献

- [1] Chingyu Yang, 从介质边界的温度响应确定温度相关的热物理属性. International Journal of Heat and Mass Transfer, 38(7):1261–1270, 2000.
- [2] B. Safaw, M.N. Ozisak, and Jarny. 一种估计正向异性介质线性温度相关热导率分量和热容的反演分析. International Journal of Heat and Mass Transfer, 38(16):3005–3010, 1995.
- [3] Tadeusz Teleisko and Zbigniew Malinowski. 有限元法在热导率识别的反演解的应用. Journal of Materials Processing Technology, 146(2):145–155, 2004.
- [4] Cheng-Hung Huang and Sheng-Chieh Chin. 成像非均匀介质热导率的二维反演问题. International Journal of Heat and Mass Transfer, 43(22):4066–4071, 2000.
- [5] Kai Yang, GengHui Jiang, Qiang Qu, HaiFeng Peng, and Xiao-Wei Gao. 基于径向积分边界元的改进型共轭梯度法识别瞬态非均匀热导率. International Journal of Heat and Mass Transfer, 133:669–676, 2019.
- [6] B. Vandestine. 非线性回归分析：其应用, d. m. bates and d. g. watts, wiley, new york, 1988. isbn 0471-81643. price: £34.50. Journal of Chemometrics, 3(3):544–555, 1989.
- [7] (原文缺失或完整)
- [8] Donald W. Marquardt. 一种用于非线性最小二乘估计的算法. Journal of the Society for Industrial and Applied Mathematics, 11(2):431–441, 1963.
- [9] Magnus R. Hetenes and Eduard Stifel. 求解线性方程组的共轭梯度法. Journal of research of the National Bureau of Standards, 49:409–435, 1952.
- [10] Terry A. Straeter. 关于戴维森-布登顿类秩向无限维希尔伯特空间的扩展及其最优控制问题的应用. 1971.
- [11] E. Divo, A. Kassab, and F. Rodriguez. 非线性功能梯度材料的热导率表征. Numerical Heat Transfer A-Applications, 37:845–875, 2000.
- [12] Xiaowei Wang, Huiping Li, Lianfang He, and Zichao Li. 基于粒子群优化、正态分布和有限元的多目标反向传导问题评估. International Journal of Heat and Mass Transfer, 127:1114–1127, 2018.
- [13] Zhen Wei and Xudong Chen. 全波非线性散射问题的深度学习方案. IEEE Transactions on Geoscience and Remote Sensing, 57(4):1849–1860, 2019.
- [14] Shucai Li, Bin Liu, Yuxiao Ren, Yangkang Chen, Senlin Yang, Yunhai Wang, and Peng Jiang. 地震数据的深度学习反演. IEEE Transactions on Geoscience and Remote Sensing, 58(3):2135–2149, 2020.
