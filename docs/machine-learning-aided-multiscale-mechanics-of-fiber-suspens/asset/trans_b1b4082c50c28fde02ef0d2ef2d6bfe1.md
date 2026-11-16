

状态 \(\underline{\lambda}\)，我们希望识别模型参数 \(\underline{a}\)，以最小化所研究载荷情况集 \(\tilde{\boldsymbol{D}}_\gamma\) 的最坏情况损失 \(\mathcal{L}\)，使得

\(\underline{a}(\lambda) = \underset{\underline{a} \in \mathbb{R}^m}{\text{argmin}} \max_{\underline{D} \in \tilde{\mathcal{D}}_\gamma} \mathcal{L}(\tilde{\underline{D}}, \underline{\lambda}, \underline{a}).\quad (4.41)\)

这里，所研究载荷情况集 \(\tilde{\boldsymbol{D}}_\gamma\) 通过方程 (3.44) 和 (3.35) 定义。然而，由于前一节描述的模型关于模型参数 \(\underline{a}\) 不是凸的，并且具有多个局部极小值，因此精确极小值 \(\underline{a}\) 难以确定。在开始我们的研究之前，我们首先提出一个警告：基于计算多尺度模拟识别模型参数并不能被视为一个数学意义上良设问题（Kabanikhin, 2008），原因有多种。首先，可能不存在唯一解，而且学习过程的结果，即模型参数，可能会对数据的微小变化产生剧烈变化。此外，学习到的模型参数还可能因优化算法和优化超参数的不同而有所变化。因此，本章所介绍的监督学习程序得到的模型参数可能并非优化问题 (4.41) 的全局极小值点。

然而，正如我们在下一节 4.4.6 中所示，所介绍的监督学习程序可以用于成功识别模型参数，这些参数能使模型预测达到工程精度。为了利用非凸优化和机器学习领域的最新进展，我们使用 Python 编程语言和机器学习框架 PyTorch (Paszke et al., 2019) 的 1.12 版本来识别模型参数 \(\underline{a}\)。撰写本章时，已有更新的 PyTorch 版本可用，它们具有即时（JIT）编译功能，可能提升自定义代码模块的性能。然而，为了与现有代码兼容，我们使用 1.12 版本。对于每个模型和纤维取向状态 \(\underline{\lambda}\)，我们随机初始化了 5000 个参数向量 \(\underline{a}\) 的实现，然后使用经检验的 ADAM (Kingma and Ba, 2014) 算法改进初始猜测，从而生成极小化参数向量集 \(S_{\min}\)。

我们从 PyTorch 框架中可用的优化算法中选择了 ADAM 算法，因为 ADAM 算法将自适应学习率与基于经典动量 (Polyak, 1964) 的方法相结合。这相比于标准梯度下降法 (Kabel et al., 2014; Ruder, 2016) 以及仅依赖自适应学习率的算法（如 AdaGrad (Duchi et al., 2011)、AdaDelta (Zeiler, 2012) 和 RMSprop (Tieleman et al., 2012)）具有优势。关于 ADAM 算法及其变体的收敛特性的详细讨论，我们请读者参考 Chen et al. (2018) 的文章。此外，关于机器学习中各种其他优化算法的概述，我们请读者参考 Sun et al. (2019) 的综述。

方便的是，ADAM 算法的学习率超参数是优化步长的近似边界。利用这一特性，我们使用 PyTorch 的选项来定义参数组，为不同数量级的参数设置单独变化的学习选项，以便标称大参数的步长不受标称小参数步长的限制。作为一阶优化技术的可行替代方案，PyTorch 还提供了强大的二阶优化算法 L-BFGS (Liu and Nocedal, 1989)。然而，撰写本章时，PyTorch 的 L-BFGS 算法不支持多个学习率和参数组，而我们发现这些对于加速收敛很有价值。因此，我们决定使用一阶优化算法 ADAM。

总体而言，我们使用四个参数组，分别对应函数 \(\bar{\mathbb{V}}_0\) 和 \(\bar{\mathbb{V}}_\infty\) 的参数各一组，以及与各向异性和张量函数 \(\mathbb{T}_8\) 中编码的非线性过渡速率相关的参数各一组，参见方程 (4.31)、(4.32) 和 (4.36)。我们使用符号 \(G_8^{\text{aniso}}\) 区分与张量函数 \(\mathbb{T}_8\) 相关的两个参数组，该组在函数 \(\mathbb{T}_8^{(1)}\) 的情况下包含六个参数，在函数 \(\mathbb{T}_8^{(2)}\) 的情况下包含 36 个参数；以及组 $G_8^{\text{expo}}$，分别为函数 \(\mathbb{T}_8^{(1)}\) 和 \(\mathbb{T}_8^{(2)}\) 包含一个和六个参数。除了 Model 1 以外，各参数组的学习率选择如表 4.4 所示。特别是对于 Model 1，与函数 \(\bar{\mathbb{V}}_0\) 相关的参数的学习率选为 0.5，因为 Model 1 不使用标量关系 (4.37)。我们通过试错法确定了每个参数组的学习率数值。

为了在学习过程中提高向极小值收敛的速度 (Darken and Moody, 1990; Darken et al., 1992)，我们使用了 PyTorch 的 ReduceLROnPlateau 学习率调度器，如果损失 $\mathcal{L}$ 在 200 个 epoch 内未改善，则将学习率减半。该规则的冷却期为 400 个 epoch，其他所有选项均保持默认。对于 ADAM 算法，除学习率外，使用了标准超参数，使得两个动量系数 $\beta_1$ 和 $\beta_2$ 分别设置为 $\beta_1 = 0.9$ 和 $\beta_2 = 0.999$，稳定常数 $\varepsilon$ 设置为 $\varepsilon = 10^{-8}$。最后，当损失 $\mathcal{L}$ 在 2000 个 epoch 内未改善时，我们认为学习过程结束。

| | $\bar{\mathbb{V}}_0$ | $\bar{\mathbb{V}}_\infty$ | $G_8^{\text{aniso}}$ | $G_8^{\text{expo}}$ |
|---|---|---|---|---|
| 学习率 | $5 \cdot 10^{-3}$ | $5 \cdot 10^{-1}$ | $5 \cdot 10^{-7}$ | $5 \cdot 10^{-2}$ |

**表 4.4：** 用于 ADAM 算法的各参数组学习率超参数。表改编自 Serr et al. (2024b, Table 4)。

## 4.4.6 模型精度

为了比较所介绍模型的精度，我们在以下部分定义误差度量并描述验证程序。由于为问题 (4.41) 寻找全局最小值很困难，我们将范围限制在极小化参数集 $S_{\min}$，并识别参数 \(\underline{a}^{\min} \in S_{\min}\)，使其最小化所研究载荷情况集 \(\bar{D}_{\dot{\gamma}}\) 上的最坏情况损失 \(\mathcal{L}\)，使得

\(\underline{a}^{\text{min}}(\underline{\lambda}) = \underset{\underline{a} \in S_{\text{min}}}{\text{argmin}} \underset{\bar{\mathbf{D}} \in \bar{\mathcal{D}}_{\dot{\gamma}}}{\text{max}} \mathcal{L}(\bar{\mathbf{D}}, \underline{\lambda}, \underline{a}).\) (4.42)

极小化参数 \(\underline{a}^{\text{min}}\) 仅在具有同质化数据的给定离散点 \(\underline{\lambda}\) 上可用。然而，按照要求 (IV)，我们有兴趣将给定模型推广到没有可用极小化参数 \(\underline{a}^{\text{min}}\) 的纤维取向状态 \(\underline{\lambda}\)。为此，我们遵循 Köbler et al. (2018) 并使用凸线性组合来插值应力，如下所示。假设节点 \(\underline{\lambda}_1, \underline{\lambda}_2,\) 和 \(\underline{\lambda}_3\) 构成一个三角形，并且在该等节点中已知极小化参数 \(\underline{a}^{\text{min}}\)。然后我们在某一点 \(\underline{\lambda}\) 处计算有效应力 \(\bar{\tau}^{\text{C}}\)：

\(\bar{\tau}^{\text{C}}(\bar{\mathbf{D}}, \underline{\lambda}) = \sum_{i=1}^{3} s_i \bar{\tau}^{\text{model}}(\bar{\mathbf{D}}, \underline{\lambda}_i, \underline{a}^{\text{min}}(\underline{\lambda}_i)),\) (4.43)

\(\underline{\lambda} = s_1 \underline{\lambda}_1 + s_2 \underline{\lambda}_2 + s_3 \underline{\lambda}_3, \quad s_i \ge 0, i \in 1, 2, 3, \sum_{i=1}^{3} s_i = 1,\) (4.44)

通过对点 \(\underline{\lambda}_1, \underline{\lambda}_2,\) 和 \(\underline{\lambda}_3\) 处的模型应力 \(\bar{\tau}^{\text{model}}\) 进行插值得到。

除了在整个纤维取向三角形 \(S_{\text{T}}\) 上推广模型外，我们还使用方程 (4.43) 来验证基于 FFT 的计算同质化所得数据中的模型。为此，我们以类似于损失 \(\mathcal{L}\) 的方式定义验证误差 \(e_{\text{V}}\)，即定义

\(e_{\text{V}}(\bar{\mathbf{D}}, \underline{\lambda}) = \frac{\| \bar{\tau}^{\text{FFT}}(\bar{\mathbf{D}}, \underline{\lambda}) - \bar{\tau}^{\text{C}}(\bar{\mathbf{D}}, \underline{\lambda}) \|_2}{\| \bar{\tau}^{\text{FFT}}(\bar{\mathbf{D}}, \underline{\lambda}) \|_2},\) (4.45)

对每个考虑的模型。在集合 \(S_{\text{T}}^{109}\) 包含的 109 个三角剖分点 \(\underline{\lambda}\) 中，我们指定 45 个点作为拟合点 \(\underline{\lambda}^{\text{F}}\) 的集合 \(S_{\text{T}}^{\text{F}} \subset S_{\text{T}}^{109}\)，见图 4.5。为验证目的，我们指定

