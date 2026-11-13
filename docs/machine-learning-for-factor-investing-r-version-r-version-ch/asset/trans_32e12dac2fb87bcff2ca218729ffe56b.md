

在线学习的基本方法实际上与神经网络的批量训练非常相似。参数的更新基于

```
\mathbf{z}_{t+1} = \boldsymbol{\theta}_t - \eta_t \nabla L_t(\boldsymbol{\theta}_t), \quad (14.4)
```

其中 $\nabla L_t(\boldsymbol{\theta}_t)$ 表示当前损失 $L_t$ 的梯度。可能出现的一个问题是 $\mathbf{z}_{t+1}$ 超出了为 $\boldsymbol{\theta}_t$ 规定的边界。因此，新参数的候选向量 $\mathbf{z}_{t+1}$ 将被投影到我们在此称为 $S$ 的可行域中：

```
\boldsymbol{\theta}_{t+1} = \Pi_S(\mathbf{z}_{t+1}), \quad \text{with } \Pi_S(\mathbf{u}) = \underset{\boldsymbol{\theta} \in S}{\arg\min} \|\boldsymbol{\theta} - \mathbf{u}\|_2. \quad (14.5)
```

因此，$\boldsymbol{\theta}_{t+1}$ 尽可能接近中间选择 $\mathbf{z}_{t+1}$。Hazan et al. (2007) 表明，在适当假设下（例如，$L_t$ 严格凸且梯度有界 $\sup_{\boldsymbol{\theta}} \nabla L_t(\boldsymbol{\theta}) \le G$），遗憾 $R_T$ 满足

```
R_T \le \frac{G^2}{2H}(1 + \log(T)),
```

其中 $H$ 是学习率（也称为步长）的缩放因子：$\eta_t = (Ht)^{-1}$。

更复杂的在线算法通过整合黑塞矩阵 $\nabla^2 L_t(\boldsymbol{\theta}) := [\nabla^2 L_t]_{i,j} = \frac{\partial}{\partial \theta_i \partial \theta_j} L_t(\boldsymbol{\theta})$ 和/或通过引入惩罚项来减少 $\boldsymbol{\theta}_t$ 中的不稳定性，从而推广了 (14.4) 和 (14.5)。关于这些扩展的更多细节，请参阅 Hoi et al. (2018) 的第 2 节。

参数更新的一个有趣流派是 Crammer et al. (2006) 正式化的被动-攻击算法（PAAs）。基本情况涉及分类任务，但下面我们坚持回归设置（Crammer et al. (2006) 的第 5 节）。PAAs 的一个强局限性是它们依赖于损失为零或可忽略的参数集：$\Theta^* = \{ \boldsymbol{\theta}, L_t(\boldsymbol{\theta}) < \epsilon \}$。对于一般损失函数和学习器 $f$，该集在很大程度上不可访问。因此，Crammer et al. (2006) 中的算法被限制在特定情况，即线性 $f$ 和 $\epsilon$-不敏感铰链损失：

```
L(\boldsymbol{\theta}) = \begin{cases} 0 & \text{if } |\boldsymbol{\theta}^\top \mathbf{x} - y| \le \epsilon \quad (\text{close enough prediction}) \\ |\boldsymbol{\theta}^\top \mathbf{x} - y| - \epsilon & \text{if } |\boldsymbol{\theta}^\top \mathbf{x} - y| > \epsilon \quad (\text{prediction too far}) \end{cases}
```

对于某个参数 $\epsilon > 0$。如果权重 $\boldsymbol{\theta}$ 使得模型足够接近真实值，则损失为零；否则，它等于误差的绝对值减去 $\epsilon$。在 PAA 中，参数的更新由以下公式给出：

```
\boldsymbol{\theta}_{t+1} = \underset{\boldsymbol{\theta}}{\arg\min} \|\boldsymbol{\theta} - \boldsymbol{\theta}_t\|_2^2, \quad \text{subject to } L(\boldsymbol{\theta}) = 0,
```

因此，新的参数值被选择以满足两个条件：- 损失为零（根据损失的定义，这意味着模型足够接近真实值）；- 并且，参数尽可能接近先前的参数值。

从构造上讲，如果模型足够好，模型就不移动（被动阶段）；但如果不够好，它会迅速移向产生满意结果的值（主动阶段）。

我们以一段历史说明结束本节。在线学习的一些想法源于金融文献，以及由 Cover (1991) 特别提出的 **通用投资组合** 概念。设置如下。假设函数 $f$ 为线性 $f(\mathbf{x}_t) = \theta'\mathbf{x}_t$，数据 $\mathbf{x}_t$ 由资产收益率组成，因此，只要 $\theta'\mathbf{1}_N = 1$（预算约束），这些值就是投资组合收益率。损失函数 $L_t$ 对应于凹效用函数（例如，对数函数），而遗憾被反转：

```
$$R_T = \sup_{\theta^* \in \Theta} \sum_{t=1}^T L_t(\mathbf{r}'_t \theta^*) - \sum_{t=1}^T L_t(\mathbf{r}'_t \theta_t),$$
```

其中 $\mathbf{r}'_t$ 为收益率。因此，该程序被转换为最大化一个凹函数。多篇文章（通常来自计算机科学或机器学习社区）对此类问题提出了解决方案：Blum and Kalai (1999)、Agarwal et al. (2006) 和 Hazan et al. (2007)。大多数贡献仅使用价格数据，值得注意的例外是 Cover and Ordentlich (1996)，该文提到了外部数据（“_侧信息_”）。在后一篇文章中，证明了根据两个随机分布进行持续再平衡的投资组合实现的增长率接近无法达到的最优增长率。这两个分布是均匀分布（再次等权重）和参数恒定为 1/2 的狄里克莱分布。在这个通用分布下，Cover and Ordentlich (1996) 表明获得的财富有如下下界：

```
$\text{wealth universal} \ge \frac{\text{wealth from optimal strategy}}{2(n+1)^{(m-1)/2}},$
```

其中 \(m\) 是资产数量，\(n\) 是周期数量。

关于在线投资组合配置的文献在 Li and Hoi (2014) 中进行了综述，并在 Li and Hoi (2018) 中进行了更详细的阐述。在线学习与神经网络的早期停止相结合，在 Wong et al. (2020) 中应用于因子投资。最后，在线学习与 Khedmati and Azin (2020) 中的聚类方法相关联，用于投资组合选择。

## 14.2.3 齐次迁移学习

本小节主要是概念性的，不会通过代码应用进行说明。迁移学习背后的思想具有价值，因为它们可以激发新的想法，因此我们下面简要介绍它们。

迁移学习已被多次综述。一个经典参考文献是 Pan and Yang (2009)，但 Weiss et al. (2016) 更新且更全面。假设我们有两个数据集 \(D_S\)（源域）和 \(D_T\)（目标域）。每个数据集都有自己的特征 \(\mathbf{X}^S\) 和 \(\mathbf{X}^T\) 以及标签 \(\mathbf{y}^S\) 和 \(\mathbf{y}^T\)。在经典监督学习中，目标集的模式仅通过 \(\mathbf{X}^T\) 和 \(\mathbf{y}^T\) 学习。迁移学习提出通过源域数据上的函数 \(f^S\)（由 \(y_i^S = f^S(\mathbf{x}_i^S) + \epsilon_i^S\) 得到）来改进目标域数据上的函数 \(f^T\)（通过最小化拟合 \(y_i^T = f^T(\mathbf{x}_i^T) + \epsilon_i^T\) 得到）。当特征空间不变时，称为齐次迁移学习，这正是我们所处的情况。在资产管理中，如果例如加入新预测变量（例如，基于替代数据，如情绪、卫星图像、信用卡日志等），则情况可能并非总是如此。

迁移学习有许多子类别，取决于源域 \(S\) 和目标域 \(T\) 之间发生了什么变化：是特征空间、标签分布，还是两者之间的关系？这些与第 14.2 节中的问题相同。后一种情况在金融中引人关注，因为与非平稳性的联系显而易见：即模型 \(f\) 在 \(\mathbf{y} = f(\mathbf{X})\) 中随时间变化。在迁移学习术语中，它写作 \(P[\mathbf{y}^S|\mathbf{X}^S] = P[\mathbf{y}^T|\mathbf{X}^T]\)：在从源域切换到目标域时，给定特征的标签的条件定律不相同。通常，术语“域自适应”被用作迁移学习的同义词。由于数据偏移，我们必须调整模型以提高其准确性。这些主题在 Quionero-Candela et al. (2009) 编选的系列章节中进行了综述。

理论中一个重要而优雅的结果由 Ben-David et al. (2010) 在二元分类情况下证明。我们如下陈述。我们考虑两个取值为 $\{0, 1\}$ 的分类器 $f$ 和 $h$。两者在域 $S$ 上的平均误差定义为

$$
\epsilon_S(f, h) = \mathbb{E}_S[|f(\mathbf{x}) - h(\mathbf{x})|].
$$

那么，

$$
\epsilon_T(f_T, h) \le \epsilon_S(f_S, h) + \underbrace{2 \sup_B |P_S(B) - P_T(B)|}_{\text{difference between domains}} + \underbrace{\min(\mathbb{E}_S[|f_S(\mathbf{x}) - f_T(\mathbf{x})|], \mathbb{E}_T[|f_S(\mathbf{x}) - f_T(\mathbf{x})|])}_{\text{difference between the two learning tasks}}
$$

其中 $P_S$ 和 $P_T$ 分别表示两个域的分布。上述不等式对 $h$ 的泛化性能给出了一个界限。如果取 $f_S$ 为 $S$ 的最佳可能分类器，$f_T$ 为 $T$ 的最佳分类器，那么 $h$ 在 $T$ 中产生的误差小于三个分量之和：

- $S$ 空间中的误差；
- 两个域之间的距离（数据空间偏移的程度）；
- 两个最佳模型（生成器）之间的距离。

迁移学习中经常提到的一种解决方案是实例加权。我们在此以一般环境下介绍它。在机器学习中，我们寻求最小化

$$
\epsilon_T(f) = \mathbb{E}_T [L(y, f(\mathbf{X}))]
$$

其中 $L$ 是取决于任务（回归与分类）的某个损失函数。这可以重写为

$$
\begin{aligned}
\epsilon_T(f) &= \mathbb{E}_T \frac{P_S(\mathbf{y}, \mathbf{X})}{P_S(\mathbf{y}, \mathbf{X})} L(y, f(\mathbf{X})) \\
&= \sum_{\mathbf{y}, \mathbf{X}} P_T(\mathbf{y}, \mathbf{X}) \frac{P_S(\mathbf{y}, \mathbf{X})}{P_S(\mathbf{y}, \mathbf{X})} L(y, f(\mathbf{X})) \\
&= \mathbb{E}_S \frac{P_T(\mathbf{y}, \mathbf{X})}{P_S(\mathbf{y}, \mathbf{X})} L(y, f(\mathbf{X}))
\end{aligned}
$$

因此，关键量是过渡比率 $\frac{P_T(\mathbf{y}, \mathbf{X})}{P_S(\mathbf{y}, \mathbf{X})}$（在某些假设下的 Radon–Nikodym 导数）。当然，该比率在实践中在很大程度上不可访问，但可以找到一种加权方案（针对实例），从而改善目标空间中的误差。该加权方案，如同 Coqueret and Guida (2020) 中所述，可以是二进制的，从而简单地在误差计算中排除某些观测值。仅仅从训练样本中移除观测值可以产生有益效果。

更一般地，上述表达式可以被视为用户指定实例加权的理论邀请（如第 6.4.7 节所述）。在资产配置术语中，这可以被视为引入关于哪些观测最有趣的观点，例如，如果用户认为价值股票携带更相关的信息，可以允许它们在损失计算中具有更大的权重。当然，随后仍然需要最小化此损失。

