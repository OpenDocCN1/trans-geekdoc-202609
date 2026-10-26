
为简单起见，我们考虑 $h\circ\mathcal{F}^{(1)}$ 有界且 $h$ 单调且 Lipschitz 的情形。以下结果首次由 Koltchinskii 和 Panchenko (2002) 提出，是定理 10.8 的直接推论。

### 定理 11.26
考虑由 (11.15) 定义的 $K$ 层神经网络。假设对所有 $\theta \in \Theta$ 和 $x \in \mathcal{X}$ 都有 $h(\theta^T x) \in [-M, M]$。同时假设 $h$ 是 1-Lipschitz 且单调。那么存在常数 $C$，使得对 $\mathcal{X}$ 上的所有分布 $D$，都有

$R(\mathcal{F}^{(k)},\mathcal{S}_n) \le A M \frac{32\sqrt{d+1}}{\sqrt{n}}$,

其中 $A = 2^{k-2} \prod_{\ell=2}^{k} A_{\ell}$。

证明 我们通过归纳法证明该命题。情形 $k = 2$ 由推论 11.10 可得。假设该命题在第 $k-1$ 层成立，则在第 $k$ 层有

$R(\mathcal{F}^{(k)},\mathcal{S}_n) \le A_k[R(h \circ \mathcal{F}^{(k-1)},\mathcal{S}_n) + R(-h \circ \mathcal{F}^{(k-1)},\mathcal{S}_n)] \le 2A_k R(\mathcal{F}^{(k-1)},\mathcal{S}_n)$。

第一个不等式使用了定理 10.8。第二个不等式使用了 $\gamma_i = 1$ 且 $h = 0$ 时的定理 6.28。现在利用归纳法，我们得到期望的上界。

该结果表明，如果对深度神经网络的每一层使用 $L_1$ 正则化，则 Rademacher 复杂度可以利用逐层 $L_1$ 正则化参数的乘积轻松得到上界。对于 ReLU 函数，$L_1$ 正则化可以移到最后一层。还值得注意的是，若用 $L_1$ 正则化来度量，定理 11.4 中考虑的函数复合示例的学习复杂度仍然很高。这并不令人惊讶，因为具有指数级交叉数的函数很复杂，而 $L_1$ 正则化允许存在具有大量神经元的大型神经网络。

定理 11.26 中泛化界的一个好处是泛化性能不依赖于神经元的数量。因此使用的神经元越多越好。这与经验观察一致，即宽神经网络更容易优化。如果允许神经元数量趋于无穷，则可在相同的 Rademacher 复杂度学习界下得到深度神经网络的连续形式。

## 11.7 双下降与良性过拟合

现代神经网络通常是过参数化的，即模型参数的数量显著大于训练数据量。这与 NTK 观点和平均场观点都一致，两者都考虑 $m \to \infty$ 的极限。在没有适当正则化的情况下，根据经典统计学，这样的系统会导致过拟合。然而，通过适当的正则化，例如 NTK 观点中的 RKHS 正则化，以及平均场观点中的 $L_1$ 正则化，这类系统在用以下量度量的情况下具有有界复杂度

![](img/49407831b69246276f2b471882509fb2_252_0.png)

### 图 11.4 双下降曲线

如 Rademacher 复杂度。一般而言，这种复杂度度量意味着有效模型维度较小，如第 9.5 节所述。在经典设定中，有效维度应小于训练数据量，随着模型复杂度增加，通常会观察到 U 形的测试损失。这在图 1.1 中显示。然而，一些现代过参数化模型超出了这一范式，其中观察到这些模型（包括神经网络）在模型规模增大时会表现出所谓的双下降现象（见 Belkin 等，2019）。

双下降现象如图 11.4 所示。可以看出，当有效维度小于训练数据量时，我们处于经典范式，测试损失呈 U 形。在过参数化范式中，当有效模型维度与训练数据量大致相同时，测试损失很大，但当有效维度超过训练数据量时，测试损失会进一步下降。在此范式中，过拟合发生，模型通常开始插值观测到的函数值，而该函数值可能包含噪声。这种过拟合被称为良性过拟合，因为尽管学习到的函数对噪声过拟合，测试损失仍会下降，并且可以达到的最小测试损失小于经典范式中可以达到的最小测试损失。

一些论文试图解释双下降现象，即使对于过参数化线性回归模型也会出现，特别是在最小 L2 范数估计量中，我们尝试用最小 L2 范数拟合线性模型。这等价于正则化参数趋近于零的岭回归。尽管双下降看起来很神秘，但它并不违背经典学习理论。在经典学习理论中，模型类越复杂，获得最优训练损失所需的训练损失越低，观察到的过拟合越多。在模型类极其复杂的最极端情况下，最优权衡可能需要对训练数据进行过拟合。

为了解释导致双下降现象的原因，我们考虑贝叶斯设定下 $(X, Y) \in \mathbb{R}^d \times \mathbb{R}$ 的以下简单问题：

$$\begin{cases}
Y = w_*^\top X + \epsilon \\
X \sim N(0, I_{d\times d}) \\
\epsilon \sim N(0, \sigma^2) \\
w_* \sim N\left(0, \frac{\tau^2}{d} I_{d\times d}\right).
\end{cases}\tag{11.16}$$

我们在过参数化设定下考虑最小二乘回归，其中观测到 $n \ll d$ 个训练数据 $\{(X_i, Y_i) : i = 1, \dots, n\}$。在这种情况下，模型属于一个非常复杂的函数类，因为目标是一个稠密的过参数化族，数据由稠密的目标向量 $w_* \in \Omega$ 生成。不可能准确学习 $w_*$，但我们仍将尝试从训练数据中找到 $\hat w$ 以实现最小的测试损失：

$$\mathbb{E}_{(X,Y)\sim \mathcal{D}}(\hat w^\top X - Y)^2 = \|\hat w - w_*\|_2^2 + \sigma^2.$$

请注意，我们假设 $w_*$ 的生成过程，使得最优贝叶斯估计量，即所有可能学习算法中最好的估计量，可以显式计算。然后我们可以将其他方法的结果与该估计量进行比较。简单的计算表明，最小化该量的最优贝叶斯估计量由岭回归给出：

$$\hat w = \arg\min_w \left[ \sum_{i=1}^n (w^\top X_i - Y_i)^2 + \lambda d \|w\|_2^2 \right], \tag{11.17}$$

其中 $\lambda = \sigma^2 / \tau^2$。以下结果比较了岭回归的训练损失和测试损失。

### 定理 11.27

考虑固定 $\tau, \sigma, n$ 时的 (11.16)。设 $X = [X_1, \dots, X_n]$ 为 $d \times n$ 数据矩阵，响应 $Y = [Y_1, \dots, Y_n]^\top$。给定任意 $\delta \in (0,1)$，令

$$c = \sqrt{\frac{\min(n,d)}{\max(n,d)}} + \sqrt{\frac{2\ln(2/\delta)}{\max(n,d)}}.$$

那么以概率 $1-\delta$ 关于 $X$ 的随机选择，岭回归估计量 (11.17) 满足以下陈述。存在 $c', c'' \in [-\min(1,c), c]$ 使得期望训练损失和期望测试损失满足以下方程。当 $d \le n$ 时，

$$\mathbb{E}\left[\frac{1}{n}\|X^\top \hat w - Y\|_2^2 \mid X\right] = \left(1 - \frac{d}{n}\right)\sigma^2 + \frac{d^2}{n^2} \cdot \frac{\lambda^2(\tau^2(1 + c')^2 + (d/n)\sigma^2)}{((1 + c')^2 + \lambda d/n)^2},$$

$$\mathbb{E}\left[\|\hat w - w_*\|_2^2 + \sigma^2 \mid X\right] = \sigma^2 + \frac{d}{n} \cdot \frac{(\lambda^2 \tau^2 (d/n) + (1 + c'')^2 \sigma^2)}{((1 + c'')^2 + \lambda d/n)^2},$$

且当 $d \ge n$ 时，

$$\mathbb{E}\left[\frac{1}{n}\|X^{\top} \hat{w} - Y\|_2^2 \mid X\right] = \frac{\lambda^2(\tau^2(1 + c')^2 + \sigma^2)}{((1 + c')^2 + \lambda)^2},$$
$$\mathbb{E}\left[\|\hat{w} - w_*\|_2^2 + \sigma^2 \mid X\right] = \sigma^2 + \left(1 - \frac{n}{d}\right)\tau^2 + \frac{n}{d} \cdot \frac{(\lambda^2\tau^2 + (1 + c'')^2\sigma^2)}{((1 + c'')^2 + \lambda)^2}.$$

*条件期望关于 $w_*$ 和 $\{Y_i\}$ 均成立。*

证明 设 $Y = [Y_1,\dots,Y_n]^\top$ 且 $\epsilon = Y - X^\top w_*$ 为噪声向量。我们可以表示

$$\hat{w} = X (X^\top X + \lambda d I_{n\times n})^{-1} X^\top w_* + X (X^\top X + \lambda d I_{n\times n})^{-1} \epsilon.$$

设 $K = \frac{1}{d}X^\top X$ 为 $n \times n$ 矩阵。易于验证

$$\mathbb{E}\left[\frac{1}{n}\|X^\top \hat{w} - Y\|_2^2 \mid X\right] = \frac{\lambda^2}{n}\operatorname{trace}((\tau^2 K + \sigma^2 I)(K + \lambda I)^{-2}), \quad (11.18)$$

$$\mathbb{E}\left[\|\hat{w} - w_*\|_2^2 \mid X\right] = \left(1 - \frac{n}{d}\right)\tau^2 + \frac{1}{d}\operatorname{trace}\big((\lambda^2\tau^2 I + \sigma^2 K)(K + \lambda I)^{-2}\big). \quad (11.19)$$

由于 $X$ 是具有 iid 标准高斯项的 $d \times n$ 矩阵，众所周知（例如见 Rudelson 和 Vershynin, 2010），以至少 $1 - \delta$ 的概率，$X$ 的任意奇异值都属于区间

$$\left[\sqrt{\max(n,d)}(1 - c),\sqrt{\max(n,d)}(1 + c)\right].$$

若 $d \le n$，则 $K$ 的 $d$ 个特征值属于 $[(n/d)(1 - \min(1,c))^2, (n/d)(1 + c)^2]$，而 $K$ 的 $n - d$ 个特征值为零。我们现在可以通过将该估计代入 (11.18) 和 (11.19) 得到期望的结果。

若 $d \ge n$，则 $K$ 的全部 $n$ 个特征值都属于 $[(1 - \min(1,c))^2, (1 + c)^2]$。我们现在可以通过将该估计代入 (11.18) 和 (11.19) 得到期望的结果。

定理 11.27 的结果关注 $\min(n,d) \ll \max(n,d)$ 的情形，这意味着 $c',c'' \to 0$。当 $\sqrt{n/d} \to c \in (0,\infty)$ 且 $d,n \to \infty$ 时，也有可能推导出比定理 11.27 更精确的渐近结果。在这种情况下，利用随机矩阵理论中的 Marchenko–Pastur 定律（见 Bai 和 Silverstein, 2010, 定理 3.7 和引理 3.11），我们可以得到定理 11.27 证明中 $K$ 的极限特征值分布，并用它来计算训练损失和测试损失的渐近精确刻画。我们将详细计算留给练习 11.10。具体而言，当 $\lambda = 0$ 时，以下渐近表达式在 $n \to \infty$ 且 $\sqrt{n/d} \to c < 1$ 时成立：

$$\mathbb{E}\left[\frac{1}{n}\|X^\top \hat{w} - Y\|_2^2 \mid X\right] = \sigma^2 + \frac{n}{d - n}\sigma^2 + \left(1 - \frac{n}{d}\right)\tau^2 + o_p(1). \quad (11.20)$$
