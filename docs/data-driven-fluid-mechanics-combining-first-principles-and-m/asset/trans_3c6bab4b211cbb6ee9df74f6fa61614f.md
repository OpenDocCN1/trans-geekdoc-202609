
控制向量不一定必须重合；因此，我们在各自的范数中选择两个不同的权重矩阵。此外，我们在时间范围的末端 t = τ 处评估增益，这与更传统的（不）稳定概念相吻合。这种评估方式导致 (13.6) 中 w = δ(τ − t)。我们有

j(q,f) = ||q||_Q^2 / ||f||_R^2 = q^H Q q / f^H R f . (13.14)

其中 R 表示控制变量的权重矩阵，在我们的情形中取为初始条件，即 f = q(t = 0)。因此，演化算子形式为 N(q,f) = L q + f δ(t)。

在此设定下，我们可以重新考虑一般的迭代优化框架，并利用控制方程的线性性来简化。直接-伴随循环中的第一步是在时间区间 [0, τ] 上求解控制方程 (13.11a)。该问题的解可形式地写为

q(τ) = exp(L τ) f . (13.15)

这里引入了将初始条件 f 变换为输出扰动 q(τ) 的矩阵指数。第二步基于方程 (13.11b)，对我们的 LTI 情形¹ 进行简化

− d/dt q† = L^H q† + 2Q / ||f||_R^2 w q . (13.16)

其可再次形式地求解为 q†(0) = exp(L^H τ) 2Q / ||f||_R^2 q(τ) . (13.17) 第三步也是最后一步使用代价泛函梯度 (∂j/∂f)^H w = −δ(t) q† . (13.18)，其中右端项 δ(t) 等价于我们特殊情形下的梯度 ∂N/∂f。

在此阶段，我们将使用上述梯度在用户指定的优化程序（如共轭梯度，例如）中以得到改进的初始条件 f。然而在此特殊情形中，我们通过选择最速下降法作为基于梯度的优化程序，进一步简化直接-伴随循环（图 13.5）。这导致了新初始条件的显式表达式。我们有 (∂j/∂f)^H w = − ||q||_Q^2 / ||f||_R^4 2 R f w . (13.19) 结合 (13.15)、(13.17)、(13.18) 和 (13.19)，我们得到 R^{−1} exp(L^H τ) Q exp(L τ) f = ||q(τ)||_Q^2 / ||f||_R^2^2 f . (13.20) ¹ 回忆二次型 x^H A x 对 x 的导数为 2 A x，其中 A 为对称矩阵。

该最后一个公式可进一步化为 **f** 的表达式

$$[\exp(\bar{L}\tau)]^H \exp(\bar{L}\tau) \bar{\mathbf{f}} = \sigma^2 \bar{\mathbf{f}},\tag{13.21}$$

描述了直接-伴随循环的一次完整迭代。我们引入了能量增益 $\sigma^2 = \|\mathbf{q}(\tau)\|_Q^2 / \|\mathbf{f}\|_R^2$，以及变换后的矩阵 $\bar{L} = FLG^{-1}$ 和变换后的初始条件 $\bar{\mathbf{f}} = G\mathbf{f}$。矩阵 $R = G^H G$ 已被分解为其 Cholesky 因子 $G$。

方程 (13.21) 是能量增益 $\sigma^2$ 的特征值问题。由此可知，最大特征值产生最优能量增长，而相关特征向量 $\bar{\mathbf{f}}$ 给出最优初始条件 $\mathbf{f}$。(13.21) 中的两个矩阵指数互为共轭转置；其乘积产生实增益 $\sigma^2$。这种配置还表明特征值问题可以转化为 $\exp(\bar{L}\tau)$ 的奇异值问题：最大奇异值（即矩阵指数的 $L_2$-范数）产生 $\sigma$，主左奇异向量对应于 $\mathbf{f}$，而主右奇异向量给出相应的最优输出 $\mathbf{q}(\tau)$。后者关系是非模态稳定性理论的核心：矩阵指数的范数度量最大瞬态能量放大。以上表明其现在可被视为 LTI 系统直接-伴随循环程序的特殊情形。迭代优化程序等价于对 (13.21) 中复合矩阵应用的幂迭代，且优化问题可通过直接的线性代数运算求解。

## 线性时不变系统的感受性

第 13.3 节通过计算指定时间范围内的扰动最大增益来讨论平衡态的稳定性。另选地，扰动的放大也可以通过恒定激励实现。这种替代设定解决了感受性问题，即流动对其扰动环境（如自由来流湍流或壁面粗糙度）的易感性。由于底层方程的线性性，我们可以将一般的受迫问题重构为对谐波激励的频率响应分析，并利用叠加原理捕捉更一般的扰动环境。这类分析被称为线性感受性分析。

与之前一样，我们考虑一个 LTI 系统并将 (13.11) 中的右端简化为 $N(\mathbf{q},\mathbf{f}) = L\mathbf{q} + \mathbf{f}\exp(i\omega t)$，其中 $\omega$ 表示激励频率，$\mathbf{f}$ 为其空间形状。我们将频率响应增益定义为响应的能量（范数）除以激励的能量（范数）。由于线性性，响应将采用激励的频率；因此，仅激励和响应的空间形状与分析相关。我们选择

$$j(\mathbf{q},\mathbf{f}) = \frac{\|\mathbf{q}_w\|_Q^2}{\|\mathbf{f}\|_R^2},\tag{13.22}$$

其中 $\mathbf{q}_w$ 表示受迫响应 $\mathbf{q} = \mathbf{q}_w \exp(i\omega t)$ 的空间形状。我们注意到 $j(\mathbf{q},\mathbf{f})$ 与时间无关，因此我们无需指定 $w$，但仍

将其假设为常数。上述分析与传递函数相关，读者应与第 4 章和第 9 章的相关内容进行比较。

直接问题 (13.11a) 化简为

$$\mathbf{q}(t) = \int_{0}^{t} \exp(\mathrm{L}(t-t')) \mathbf{f} \exp(i\omega t') dt', \qquad (13.23a)$$ $$= (i\omega - \mathrm{L})^{-1} [\exp(i\omega t) - \exp(\mathrm{L}t)] \mathbf{f}. \qquad (13.23b)$$

我们看到方程 (13.23a) 表示谐波激励与线性系统输入响应的卷积（参见第 5 章以获取更多材料）。在继续之前，我们强调上述解假设系统是渐近稳定的，L 的所有特征值均位于稳定半平面内。本质上，我们只考虑系统的长期响应，而忽略建立该长期响应的瞬态过程。因此，(13.23b) 中包含矩阵指数的项可以忽略。我们有

$$\mathbf{q} = (i\omega - \mathrm{L})^{-1} \mathbf{f} \exp(i\omega t) = \mathbf{q}_{w} \exp(i\omega t). \qquad (13.24)$$

重新表述我们特殊情形下 (13.11b) 中的伴随方程，我们得到

$$- \frac{d}{dt} \mathbf{q}^{\dagger} = \mathrm{L}^{H} \mathbf{q}^{\dagger} + \frac{2\mathrm{Q}}{\|\mathbf{f}\|_{\mathrm{R}}^{2}} \mathbf{q}_{w} \exp(i\omega t) w, \qquad (13.25)$$

其形式解为

$$\mathbf{q}^{\dagger} = (-i\omega - \mathrm{L}^{H})^{-1} \frac{2\mathrm{Q}}{\|\mathbf{f}\|_{\mathrm{R}}^{2}} \mathbf{q}_{w} \exp(i\omega t) w. \qquad (13.26)$$

由最优性条件 (13.19) 和 $\mathbf{q}^{\dagger}$ 的表达式可得

$$- \frac{\|\mathbf{q}_{w}\|_{\mathrm{Q}}^{2}}{\|\mathbf{f}\|_{\mathrm{R}}^{4}} 2\mathrm{R} \mathbf{f} w = \left(\frac{\partial \mathrm{N}}{\partial \mathbf{f}}\right)^{H} \mathbf{q}^{\dagger} = \exp(-i\omega t) \mathbf{q}^{\dagger}. \qquad (13.27)$$

结合 (13.24) 和 (13.26) 得到

$$\mathrm{R}^{-1} (-i\omega - \mathrm{L}^{H})^{-1} \mathrm{Q} (i\omega - \mathrm{L})^{-1} \mathbf{f} = \sigma^{2} \mathbf{f}, \qquad (13.28)$$

其中 $\sigma^{2}$ 为所求的响应增益，定义为 $\|\mathbf{q}_{w}\|_{\mathrm{Q}}^{2}/\|\mathbf{f}\|_{\mathrm{R}}^{2}$。利用权重 Q 和 R 的 Cholesky 分解（见上文），我们可以将上述表达式更紧凑地写为 $$\big[(i\omega - \bar{\mathrm{L}})^{-1}\big]^{H} (i\omega - \bar{\mathrm{L}})^{-1} \bar{\mathbf{f}} = \sigma^{2} \bar{\mathbf{f}}, \qquad (13.29)$$ 其中 $\bar{\mathrm{L}} = \mathrm{F}\mathrm{L}\mathrm{G}^{-1}$ 且 $\bar{\mathbf{f}} = \mathrm{G}\mathbf{f}$。与之前一样，我们得到增益 $\sigma^{2}$ 的特征值问题：给定频率 $\omega$ 的最优频率响应增益是 $\big[(i\omega - \bar{\mathrm{L}})^{-1}\big]^{H} (i\omega - \bar{\mathrm{L}})^{-1}$ 的最大特征值，或等价地是 $(i\omega - \bar{\mathrm{L}})^{-1}$ 的第一个奇异值。后者算子被称为 resolvent。最优激励和输出分别由主右奇异向量和左奇异向量给出（Schmid & Henningson 2001, Schmid 2007）。Resolvent 在流体行为研究中得到了广泛应用（参见例如 McKeon & Sharma 2010, Moarref et al. 2014, Yeh & Taira 2019）。
