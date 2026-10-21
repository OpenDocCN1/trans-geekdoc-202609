
流行的模型，将在44.4节中展示。最后在44.5节中得出结论，并提出未来研究的建议。

## 44.2 自适应 L_q SVM

### 44.2.1 支持向量机

支持向量机的一般形式用于解决二分类问题。给定一组信用数据点 G = {(\vec{x}_i, y_i)}^n_{i=1}，其中 \vec{x}_i \in R^m 是第 i 个输入记录，y_i \in {1,-1} 是相应的观测结果，SVM 的主要目标是找到一个最优分离超平面，该超平面可以表示为 \langle \vec{\omega}, \vec{x} \rangle + b = 0，并最大化分类间隔（即超平面与每个类别最近数据点之间的距离），同时最小化经验分类误差。因此，寻找最优分离超平面的问题可以转化为以下优化问题：

min ½||\vec{\omega}||² + C \sum_{i=1}^n \xi_i, s.t. y_i(\vec{\omega}^T \phi(x_i) + b) \ge 1 - \xi_i, \xi_i \ge 0, \; i = 1, ..., n (44.1)

其中变量 \xi_i 是非负松弛变量，表示分类误差；正则化参数 C 是一个常数，表示最大间隔和最小经验风险之间的权衡。

上述二次优化问题可以通过将其转化为拉格朗日函数来求解

L(\vec{\omega}, b, \xi, \alpha) = ½||\vec{\omega}||² + C \sum_{i=1}^n \xi_i - \sum_{i=1}^n \alpha_i (y_i(\vec{\omega}^T \phi(\vec{x}_i) + b) - 1 + \xi_i) - \sum_{i=1}^n \theta_i \xi_i (44.2)

其中 \alpha_i 和 \theta_i 表示拉格朗日乘子；\alpha_i \ge 0 且 \theta_i \ge 0。

在最优值点，我们有以下鞍点方程：\frac{\partial L}{\partial \vec{\omega}} = 0, \; \frac{\partial L}{\partial b} = 0 \; 和 \; \frac{\partial L}{\partial \xi_i} = 0,

即 \vec{\omega} = \sum_{i=1}^n \alpha_i y_i \phi(\vec{x}_i), \; \sum_{i=1}^n \alpha_i y_i = 0 \; 和 \; \alpha_i = C - \theta_i \; i = 1, ..., n. (44.3)

将 (44.3) 代入 (44.2)，并用核函数 $k(\vec{x}_i, \vec{x}_j)$ 替换 $(\phi(\vec{x}_i) \cdot \phi(\vec{x}_j))$，我们得到对偶优化问题

$$\max \sum_{i=1}^{n} \alpha_i - \frac{1}{2} \sum_{i=1}^{n} \sum_{j=1}^{n} \alpha_i \alpha_j y_i y_j k(\vec{x}_i, \vec{x}_j),$$
s.t. $\sum_{i=1}^{n} \alpha_i y_i = 0,$
$0 \le \alpha_i \le C, \quad i = 1, \dots, n.$
(44.4)

常用的核函数包括多项式核、径向基函数（RBF）核和 sigmoid 核，分别如 (44.5)、(44.6) 和 (44.7) 所示。

$k(\vec{x}, \vec{y}) = (\vec{x} \cdot \vec{y} + c)^d, \quad \text{for } d \in N, c \ge 0, \quad (44.5)$
$k(\vec{x}, \vec{y}) = \exp(-\gamma \|\vec{x} - \vec{y}\|^2), \quad \text{for } \gamma > 0, \quad (44.6)$
$k(\vec{x}, \vec{y}) = \tanh(\gamma (\vec{x} \cdot \vec{y}) + c), \quad \text{for } \gamma > 0, c \ge 0. \quad (44.7)$

在求解对偶优化问题时，解 $\alpha_i$ 决定了最优超平面的参数。由此得到决策函数，表示为

$$f(\vec{x}) = \operatorname{sgn}\left( \sum_{i=1}^{n} y_i \alpha_i k(\vec{x}_i, \vec{x}) + b \right), \quad (44.8)$$

其中 $b = y_j - \sum_{i=1}^{n} y_i \alpha_i k(x_i, x_j)$，对于某个 $j$，$\alpha_i \le C$。

通常，在分类问题中，只有一小部分拉格朗日乘子 $\alpha_i$ 大于零。具有非零 $\alpha_i^*$ 的训练向量称为支持向量；最优决策超平面仅依赖于这些支持向量：

$$f(\vec{x}) = \operatorname{sgn}\left( \sum_{i \in SV} y_i \alpha_i^* k(\vec{x}_i, \vec{x}) + b^* \right). \quad (44.9)$$

### 44.2.2 自适应 $L_q$ 惩罚 SVM

SVM 模型 (44.1) 或 (44.4) 以及许多其他改进的 SVM 都采用固定的惩罚形式，但不同的数据结构适用于不同类型的惩罚形式。因此，Liu 提出了一种自适应 $L_q$ 惩罚 SVM，以便针对不同的数据结构找到最佳的惩罚 q（例如，参见 Liu et al., 2007）。

在一般正则化框架下，用于二分类问题的标准 SVM 可以修改如下：

$$\min_{f} \frac{1}{n}\sum_{i=1}^{n} l(f(x_i),y_i)+\lambda\|f\|_{2}^{2}, \tag{44.10}$$

其中 $l(f(x_i),y_i)=[1-y_i f(x_i)]_{+}$ 是凸合页损失；$\|f\|_{2}^{2}$ 是 f 的 $L_{2}$ 惩罚，作为 f 的粗糙度惩罚的正则化项；$\lambda>0$ 是调优参数，控制由 l 度量的数据拟合度与 f 在 $\|f\|_{2}^{2}$ 方面的复杂度之间的权衡。

基于扩展的 SVM 模型 (44.10)，自适应 $L_{q}$ 惩罚 SVM 可以简要描述为：

$$\min \frac{1}{n}\sum_{i=1}^{n}c(-y_i)[1-y_i f(x_i)]_{+}+\lambda\|f\|_{q}^{q}, \tag{44.11}$$

其中 $f(x)=\sum_{d=1}^{m}\varpi_{d}B_{d}(x)$ 是决策函数，$c(+1)$ 和 $c(-1)$ 分别是假正例和假负例的代价。与标准二分类 SVM 不同，这里有两个需要调优的参数 $\lambda$ 和 $q$。参数 $\lambda$ 与非自适应 SVM 中的作用相同，控制最小化合页损失与对 $f$ 的惩罚之间的权衡。参数 $q$ 决定对 $f$ 的惩罚函数。这里，$q\in(0,2]$ 被视为调优参数，它可以与 $\lambda$ 一起由数据自适应选择。最佳的 $q$ 取决于数据结构的特点。如果输入中存在许多噪声属性，则选择 $q\le1$ 的 $L_{q}$ 惩罚，因为它会自动选择重要属性并去除噪声属性。否则，如果所有属性都重要，则使用 $q>1$ 以避免删除任何属性。

与标准 SVM 一样，$f(x)$ 是线性决策函数。对于二分类，决策函数表示为 $f_{k}(x)=\vec{\omega}_{k}^{T}x+b_{k}$，其中 $\vec{\omega}_{k}=(\varpi_{k1},\dots,\varpi_{km})^{T}$，且 $k=1,2$。为了获得唯一解，系数需满足 $b_{1}+b_{2}=0$ 和 $\vec{\omega}_{1}+\vec{\omega}_{2}=0$。于是优化问题变为

$$\min_{\{(\varpi_{k},b_{k})_{k=1,2}\}}\frac{1}{n}\sum_{i=1}^{n}\sum_{k=1}^{2}[\vec{\varpi}_{k}^{T}x+b_{k}+1]_{+}c(k\ne y_{i})+\lambda\sum_{k=1}^{2}\sum_{d=1}^{m}|\varpi_{kd}|^{q}\tag{44.12}$$ s.t. $b_{1}+b_{2}=0,\quad\varpi_{1d}+\varpi_{2d}=0\quad d=1,2,\dots,m.$

对 $x$ 进行分类的最终决策规则是 $\operatorname{argmax}[f_{1}(x),f_{2}(x)]$。

## 44.3 基于 ES 的 ALqG-SVM

### 44.3.1 带高斯核的自适应 Lq SVM

当 q = 2 时，优化问题 (44.12) 可以通过二次规划（QP）求解。当 q = 1 时，(44.12) 可以简化为线性规划（LP）。许多标准软件包都可以求解这些问题。除了这两种特殊情况外，问题 (44.12) 本质上是一个非线性规划（NLP）问题，难以求解。另一个问题是，当 q < 1 时，函数 ||f||_q^q 在 \vec{w} 上不是凸的。因此，标准优化例程可能无法求解该问题。为此，提出了 LQA 算法，通过迭代二次优化来求解该问题并最小化 (44.12)（例如，参见 Liu et al., 2007）。对于固定参数 (λ, q)，求解 (44.12) 的 LQA 算法可以概括为以下三个步骤：

- **步骤 1:** 设 l = 1 并给定初始值 η^(l)；
- **步骤 2:** 令 η^0 = η^(l)。最小化 F(η) = η^T Q η + η^T L 以获得 η^(l+1)；
- **步骤 3:** 设 l = l+1 并返回步骤 2，直至收敛。

其中 η 表示参数向量；F(η) 是模型 (44.12) 目标函数的泰勒一阶近似，其中 Q = Q_A1 + Q_B1 + Q_C1 + Q_C2，L = L_A1 + L_A2 + L_B1 + L_B2。LQA 算法的更多细节见 Liu et al. (2007)。

通常，训练向量 x_i 通过函数 Φ(−) 映射到更高（可能是无限）维的空间。然后，SVM 在该高维空间中找到一个具有最大间隔的线性分离超平面。研究人员提出了几种核函数，其中高斯核如 (44.13) 所示，在一般情况下使用更频繁，且性能优于其他核函数（例如，参见 Burges, 1998）。因此，将高斯核引入自适应 L_q 惩罚 SVM 模型以提高分类性能（例如，参见 Sun et al., 2008）。

$$k(\vec{x}, \vec{y}) = \exp(-||\vec{x} - \vec{y}||^2 / \sigma^2). \tag{44.13}$$

在 LQA 算法中，高斯核被引入步骤 2 中的 Q_A1 和 Q_B1，其定义如下：

$$Q_{A1} = \frac{1}{4n} \sum_{i=1}^{n} \frac{c_{i1}}{|\eta^{0T} \tilde{x}_i + 1|} \tilde{x}_i \tilde{x}_i^T = \frac{1}{4n} \sum_{i=1}^{n} \hat{x}_i \hat{x}_i^T = Ker_{Q_{A1}}^{m \times m}, \tag{44.14}$$

