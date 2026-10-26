
**证明**  LSI 对于强凹密度函数成立，这是 Bakry–Emery 判据（Bakry and Emery, 1985）的直接推论。众所周知，LSI 在有界扰动下是稳定的（参见 Holley and Stroock, 1987），由此可得该结果。

**例 11.22**  引理 11.21 蕴含以下结果。假设 $g_0(w,q)$ 关于 $w$ 光滑：对所有 $w$ 和 $q$，有 $\|\nabla_w^2 g_0(w,q)\|_2 \le L$。若取 $r(w)=\lambda'\|w\|^\alpha$，则对任意 $\lambda'>0$ 和 $\alpha>2$，(11.11) 对某个 $\mu>0$ 成立（见练习 11.7）。这意味着定理 11.20 中的收敛结果成立。

### 泛化分析

由于平均场模型的参数 $q$ 是一个分布，这种连续形式下的两层神经网络可以被视为各个模型 $u h(\theta^\mathsf{T}x)$ 的凸包。因此我们可以应用第 10 章的 $L_1$ 正则化结果和熵正则化结果来计算相应的 Rademacher 复杂度。下面的结果与命题 11.9 相同，只是我们允许 $q$ 同时对参数 $[u,\theta]$ 进行学习。

**命题 11.23**  *设*

$$\mathcal{F}^{\mathrm{mf}}_A=\left\{\mathbb{E}_{[u,\theta]\sim q}u h(\theta^\mathsf{T}x):\mathbb{E}_{u\sim q}|u|\le A\right\},$$

则

$$R(\mathcal{F}^{\mathrm{mf}}_A,\mathcal{S}_n)\le AM\frac{32\sqrt{d+1}}{\sqrt{n}}.$$

此外，定理 11.20 表明，平均场公式的带噪梯度下降会导致熵正则化。我们可以利用定理 10.17 中的 Rademacher 复杂度分析来分析其泛化性能，或者使用定理 10.18 而不假设 $uh(\cdot)$ 的有界性。

除定理 11.20 外，在适当条件下也可以在不进行熵正则化的情况下证明收敛性（见 Chizat and Bach, 2018）。我们可以将 (11.8) 的全局解作为两层神经网络 ERM 方法的极限解来研究其性质。对于不带熵正则化的平均场公式 (11.8)，一个有趣的观察是：对 $u$ 的任何凸正则化都会导致 $L_1$ 正则化，这意味着命题 11.23 可以直接应用于平均场公式的解。

**命题 11.24**  *考虑* $\mathcal{X}\times\mathcal{Y}$ *上的任意分布* $\widehat{D}$。*假设* $\sup\{|h(\theta^\mathsf{T}x)|:\theta\in\Omega\}$ *有界。设* $\Delta(\mathbb{R}\times\Omega)$ *为* $(u,\theta)\in\mathbb{R}\times\Omega$ *上概率测度的集合。考虑如下优化问题：*

$$\min_{q\in\Delta(\mathbb{R}\times\Omega)}\ \mathbb{E}_{(X,Y)\sim\widehat{D}}\left[L\left(\mathbb{E}_{[u,\theta]\sim q}u h(\theta^\mathsf{T}X),Y\right)+\mathbb{E}_{u\sim q}r(|u|)\right].$$

*其中 $r(\cdot)$ 是 $\mathbb{R}_+$ 上的递增严格凸函数。设 $\hat{q}$ 是一个最优解。则存在 $A > 0$，使得 $|u| = A$ 对 $u \sim \hat{q}(\cdot)$ 几乎处处成立，且 $\hat{q}$ 是下述问题的解：*

$$\min_{q\in\Delta(\mathbb{R}\times\Omega)} \mathbb{E}_{(X,Y)\sim\widehat{D}} L\left( \mathbb{E}_{[u,\theta]\sim q} u h(\theta^\top X), Y\right) \quad \text{subject to} \quad \mathbb{E}_{u\sim q}|u| \le A.$$

**证明**  为记号简洁，我们考虑离散的 $\hat{q}$（连续情形类似，只是记号更复杂）。考虑离散值 $[u_1,\theta_1]$ 具有概率 $\hat{q}_1 > 0$，$[u_2,\theta_2]$ 具有概率 $\hat{q}_2 > 0$。不失一般性，我们可假设 $|u_1| \ge |u_2| \ge 0$。

我们用反证法证明第一个结论。若 $|u_1| > |u_2|$，则可找到 $\delta > 0$，并令 $\hat{q}_1' = \hat{q}_1 + \delta$，$\hat{q}_2' = \hat{q}_2 - \delta$，使得 $|u_1'| = |u_2'|$，其中 $u_1' = u_1 \hat{q}_1/\hat{q}_1'$，$u_2' = u_2 \hat{q}_2/\hat{q}_2'$。令 $\hat{q}'$ 为 $[u,\theta]$ 上的分布，它在所有其他点上与 $\hat{q}$ 相同，只是将 $[u_j,\theta_j]$ 上的概率质量 $\hat{q}_j$ 变为 $[u_j',\theta_j]$ 上的概率质量 $\hat{q}_j'$（$j = 1,2$）。该构造意味着 $\mathbb{E}_{[u',\theta]\sim\hat{q}'} u' h(\theta^\top x) = \mathbb{E}_{[u,\theta]\sim\hat{q}} u h(\theta^\top x)$，且

$$\mathbb{E}_{u'\sim\hat{q}'} r(|u'|) - \mathbb{E}_{u\sim\hat{q}} r(|u|) = (\hat{q}_1 + \hat{q}_2) r\left( \frac{\hat{q}_1|u_1| + \hat{q}_2|u_2|}{\hat{q}_1 + \hat{q}_2} \right) - \sum_{j=1}^2 \hat{q}_j r(|u_j|) < 0,$$

其中我们使用了 $|u_1'| = |u_2'| = (\hat{q}_1|u_1| + \hat{q}_2|u_2|)/(\hat{q}_1 + \hat{q}_2)$。这与 $\hat{q}$ 的最优性矛盾。因此必有 $|u_1| = |u_2|$。这意味着当 $u \sim \hat{q}(\cdot)$ 时 $|u| = \mathrm{const}$。

我们用反证法证明第二个结论。若 $\hat{q}$ 不是 $L_1$ 正则化公式的解，则我们可以找到具有更小目标值的 $\hat{q}'$，使得 $\mathbb{E}_{u'\sim\hat{q}'} |u'| \le A$。根据前述分析，我们还可以找到一个解 $\hat{q}'$，使得对于某个 $A' \le A$，有 $|u'| = A'$ 且目标值更小。然而，这是不可能的，因为 $\hat{q}'$ 会导致相对于 $r(\cdot)$ 正则化公式的正则化损失比 $\hat{q}$ 更小。

命题 11.24 可以解释如下。即使我们在两层神经网络中对 $u$ 使用 $L_2$ 正则化（这看似与核方法相关），当我们允许 $u$ 和 $\theta$ 同时优化时，它实际上求解的是平均场公式的 $L_1$ 正则化问题。$\theta$ 的优化将 $u$ 上的 $L_2$ 正则化转化为关于函数类 $\{h(\theta^\top x)\}$ 的 $L_1$ 正则化。这意味着命题 11.23 可用于刻画平均场公式的复杂度。

在离散平均场公式 (11.7) 中，$\{[u_j,\theta_j]\}$ 可视为来自 $q$ 的 $m$ 个独立样本。在这样的公式中，$[u_j,\theta_j]$ 被同时训练。以下结果表明，在 $L_1$ 正则化下，Rademacher 复杂度对 $m$ 不敏感。

**推论 11.25**  设

$$\mathcal{F}_{A,m}^{\mathrm{mf}} = \left\{ \frac{1}{m} \sum_{j=1}^m u_j h(\theta_j^\top x) : \|u\|_1 \le mA \right\}.$$

假设 $h(\cdot) \in [-M, M]$ 且 $h(\cdot)$ 是单调的。则

$$R(\mathcal{F}_{A,m}^{\mathrm{mf}}, \mathcal{S}_n) \le A M \frac{32\sqrt{d+1}}{\sqrt{n}}.$$

注意，与推论 11.10（其中 $\{\theta_j\}$ 是随机的）不同，推论 11.25 允许 $\{\theta_j\}$ 与 $\{u_j\}$ 一起训练。这意味着使用较小的 $m$ 学习正确的特征表示更为有效。

## 11.6 深度神经网络的分析

将 NTK 分析扩展到深度神经网络是可能的，只需对两层神经网络的线性近似 (11.6) 进行扩展，难度不大。为简单起见，我们在此不予考虑。它与随机特征和两层神经网络的核方法有类似的缺陷，即线性化要求模型参数被限制在初始化附近的一个小区域内。

NTK 近似的一个额外缺点是，它可以被视为使用线性模型对深度网络进行的浅层网络近似。根据定理 11.4，具有大穿越数的高度振荡函数无法用 NTK 高效逼近，尽管它们可以用深度神经网络很好地逼近。这与 NTK 无法高效学习特征有关。然而，特征表示的高效学习正是深度神经网络的关键优势。因此，在本节中，我们将直接研究深度神经网络方法，而不考虑 NTK 近似。

这里我们考虑一种深度神经网络的公式，它可以被视为两层神经网络平均场公式的扩展，然后研究其泛化性能。深度函数类递归定义如下：

$\mathcal{F}^{(1)} = \{\theta^\top x : \theta \in \Theta\}$,

对于 $k = 2, \dots, K$，使用第 10.2 节的记号，我们定义

$$\mathcal{F}^{(k)} = \mathcal{F}_{A_k, L_1} \big(h \circ \mathcal{F}^{(k-1)}\big) \tag{11.15}$$

$$= \left\{ \sum_{j=1}^m w_j h\big(f_j(x)\big) : \|w\|_1 \le A_k,\ f_j \in \mathcal{F}^{(k-1)},\ m > 0 \right\}.$$

当 $A_1, \dots, A_k$ 足够大时，显然任何可由深度 $K$ 层神经网络表示的函数 $f(x)$ 都属于 $\mathcal{F}^{(K)}$。该表示允许 $m$ 任意大，因此可以处理连续深度神经网络。这意味着它可以被视为两层平均场公式的扩展，而正如我们已经展示的，它也隐式地使用了 $L_1$ 正则化。

