

我们需要形式化玩家对损失函数的访问。我们将以下述随机方式制定此形式。

## 定义 A.1

算法 ORACLE 被称为 (\(\beta\), \(\delta\)) 弱梯度 if

\[
\langle \text{ORACLE}(f, p), \nabla_f F(f, p) \rangle \ge \beta
\]

(A.3)

以概率 \(1 - \delta\)。

此处 \(\nabla_f\) 表示 \(F\) 的函数梯度。这一概念与通常用于提升文献中的弱学习假设类似。给出这样的 oracle，可以寻找类似于凸优化一阶方法（例如梯度下降）的方法来求解 minimax 问题。这些算法会迭代维护两个玩家的候选解，并利用另一名玩家状态的反馈来更新各自的候选解。在我们的特定设置中，假设玩家使用公式 (2.3) 中的向量 \(h\) 进行更新。

## 激励示例

令 \(\mathcal{F}\) 为假设类，令 \(\mathcal{P}\) 为有限样本集 \(\{x_1, \dots, x_n\}\) 上所有分布的集合，并令 \(L\) 为 0-1 损失。请注意，在此设置中，定义 A.1 中的 oracle 类似于弱学习。在此设置中，根据 minimax 定理和弱学习者的存在，我们得到存在一组假设的单一混合 \(\sum_i \alpha_i f_i\)，使得在 \(\mathcal{P}\) 中每个分布下的损失都对应于零训练误差。因此，我们可以将提升算法视为在算法上逼近这个 minimax 平衡。同样，[118] 中的弱学习条件在精神上与上述条件相似。

有了定义 A.1 的条件，可以考虑许多求解 minimax 博弈的框架。一种通用技术是考虑两个用于在线凸优化的无悔算法相互对弈。让我们简要看一下在此设置中悔恨的定义。

## 定义 A.2（无悔）

令 \(K, A\) 为凸集。在每个时刻，一名玩家观察一个点 \(x_t \in K\) 并选择一个动作 \(a_t \in A\)。算法的悔恨定义为

\[
R_T = \max_{a \in A} \sum_{t=1}^T \langle a, x_t \rangle - \sum_{t=1}^T \langle a_t, x_t \rangle.
\]

(A.4)

在线学习是机器学习中一个研究深入的领域，与数学和计算机科学的多个领域有着丰富的联系。特别是，有用于构建算法的框架，例如跟随受干扰领导者（follow-the-perturbed leader）、跟随正则化领导者（follow-the-regularized leader）和镜下下降（mirror descent）。我们的算法可以被视为带有熵正则化项的镜下下降的一个版本，而 Theorem 2.1 则可视为该算法悔恨保证的一个版本。除了上述提到的框架外，还有几种其他用于求解 minimax 博弈的框架，例如变分不等式、额外梯度方法、乐观方法等。我们认为这个通用框架对于许多学习任务很有用，特别是在存在函数近似的设置中。

## A.2 主定理的证明

在此，我们提供 Theorem 2.1 的证明，该定理重述如下：

### 定理

假设类 \(\mathcal{F}\) 满足对于所有 \(f \in \mathcal{F}\)，\(\|f - g\|_\infty \le G_\infty\)。令 \(F = \{f_t\}\) 为算法 1 经过 \(T\) 轮后的集成，最终输出为 \(F_t = \frac{1}{T} \sum_{t=1}^T f_t\)。如果对于所有 \(t \le T\)，\(f_t\) 满足公式 (2.7)，那么对于 \(T \ge \ln 2N\) 以及

\[
\eta = \frac{1}{G_\infty} \sqrt{\frac{\ln 2N}{T}}
\]

我们有对于所有 j

\[
\|F_{t,j} - g_j\|_\infty \le G_\infty \sqrt{\frac{\ln 2N}{T}} - \frac{1}{T} \sum_{t=1}^T \gamma_t(j)
\]

其中 \(F_{t,j}\) 和 \(g_j\) 分别是函数 \(F_t\) 和 \(g\) 的第 \(j\) 个坐标。

### 证明

为简化起见，假设 \(f_t\) 和 \(g\) 是标量值函数，因为证明是逐坐标进行的。在每个时刻，定义弱学习算法的优势为

\[
\gamma_t = \sum_i K_t^+(i)(f_t(x_i) - g(x_i)) + \sum_i K_t^-(i)(g(x_i) - f_t(x_i))
\]

令 \(Z_t\) 表示时刻 \(t\) 的归一化常数，即，

\[
Z_t = \sum_i K_t^+(i) \exp \left( -\eta (f_t(x_i) - g(x_i)) \right) + K_t^-(i) \exp \left( \eta (f_t(x_i) - g(x_i)) \right)
\]

根据更新规则，

\[
\begin{aligned}
K_{T+1}^+(i) &= \frac{K_T^+(i)e^{\eta(f_T(x_i)-g(x_i))}}{Z_T} \\
&= \frac{K_1^+(i)\exp \left( -\eta \sum_{t=1}^T (f_t(x_i)-g(x_i)) \right)}{\prod_{t=1}^T Z_t} \\
&= \frac{K_1^+(i)\exp \left( -\eta T (F_T(x_i)-g(x_i)) \right)}{\prod_{t=1}^T Z_t}
\end{aligned}
\]

类似地，

\[
K_{T+1}^-(i) = \frac{K_1^-(i) \exp(\eta T (F_T(x_i) - g(x_i)))}{\prod_{t=1}^T Z_t}
\]

首先，对 \(\ln(Z_t)\) 进行界定：

\[
\begin{aligned}
\ln(Z_t) &= \ln \left( \sum_i K_t^+(i) \exp(-\eta(f_t(x_i) - g(x_i))) + \sum_i K_t^-(i) \exp(\eta(f_t(x_i) - g(x_i))) \right) \\
&\le \ln \Bigg( \sum_i K_t^+(i) \Big( 1 - \eta(f_t(x_i) - g(x_i)) + \eta^2(f_t(x_i) - g(x_i))^2 \Big) \\
&\quad + \sum_i K_t^-(i) \Big( 1 + \eta(f_t(x_i) - g(x_i)) + \eta^2(f_t(x_i) - g(x_i))^2 \Big) \Bigg) \\
&\le \ln \Bigg( 1 - \eta \sum_i K_t^+(i)(f_t(x_i) - g(x_i)) + \eta \sum_i K_t^-(i)(f_t(x_i) - g(x_i)) + \eta^2 G_\infty^2 \Bigg) \\
&\le -\eta \gamma_t + \eta^2 G_\infty^2
\end{aligned}
\]

其中第二步利用恒等式 \(\exp(x) \le 1 + x + x^2\)（适用于 \(x \le 1\)），前提是 \(\eta \le \frac{1}{G_\infty}\)。这给出了 \(T\) 轮后回归误差的界：

\[
\begin{aligned}
-\eta T (F_T(x_i) - g(x_i)) &= \ln(K_{T+1}^+(i)) - \ln(K_1^+(i)) + \sum_{t=1}^T \ln(Z_t) \\
&\le \ln \left( \frac{K_{T+1}^+(i)}{K_1^+(i)} \right) + \sum_{t=1}^T -\eta \gamma_t + \eta^2 G_\infty^2 \\
&= \ln \left( \frac{K_{T+1}^+(i)}{K_1^+(i)} \right) + \eta^2 T G_\infty^2 - \eta \sum_{t=1}^T \gamma_t \\
&\le \ln 2N + \eta^2 T G_\infty^2 - \eta \sum_{t=1}^T \gamma_t ,
\end{aligned}
\]

其中最后的界是由于 \(K_1^+ = \frac{1}{2N}\) 且 \(K_{T+1}^+ \le 1\)。类似地，注意界

\[
\eta T (F_T(x_i) - g(x_i)) \le \ln 2N + \eta^2 T G_\infty^2 - \eta \sum_{t=1}^T \gamma_t
\]

结合两个方程，

\[
\sup_i |F_T(x_i) - g(x_i)| = \|F_T - g\|_\infty \le \frac{\ln 2N}{\eta T} + \eta G_\infty^2 - \frac{1}{T} \sum_{t=1}^T \gamma_t .
\]

让我们选择 \(\eta = \frac{1}{G_\infty}\sqrt{\frac{\ln 2N}{T}}\) 以最小化该表达式，并得到回归误差的以下界：

\[
\|F_t - g\|_\infty \le -\frac{1}{T} \sum_{t=1}^T \gamma_t + G_\infty\sqrt{\frac{\ln 2N}{T}}.
\]

这正是公式 (2.8)。请注意，\(\eta\) 的值仅在 \(T \ge \ln 2N\) 时满足条件 \(\eta \le \frac{1}{G_\infty}\)，即界成立的时间范围。\(\square\)

现在，我们提供 Theorem 2.2 的证明，它源自 VC 维界和 Theorem 2.1。在开始之前，我们设置一些记号。给定一个函数 \(f\)、空间 \(\mathcal{X} \times \mathcal{Y}\) 上的分布 \(\mathcal{D}\)（其中 \(\mathcal{X}\) 是输入空间，\(\mathcal{Y}\) 是标签空间）以及由 \(N\) 个 iid 样本 \((x, y) \sim \mathcal{D}\) 组成的数据 \(D\)，我们定义

\[
\widehat{\text{err}}(f) = \Pr_{(x,y)\sim D} [\text{sign}(F_T(x) \neq y)] \quad \text{err}(f) = \Pr_{(x,y)\sim \mathcal{D}} [\text{sign}(F_T(x) \neq y)]
\]

### 定理（过剩风险）

假设数据 \(D\) 包含来自分布 \(\mathcal{D}\) 的 \(N\) 个 iid 样本。假设函数 \(g\) 在数据 \(D\) 上具有大边距，即

\[
\Pr_{x\sim D} [|g(x)| < \epsilon] < \mu
\]

进一步假设类 \(\mathcal{C}_T\) 具有 VC 维 \(d\)，那么对于

\[
T \ge \frac{4G_\infty^2 \ln 2N}{\epsilon^2},
\]

在数据 \(D\) 的抽取中以概率 \(1 - \delta\)，经过算法 1 \(T\) 轮后得到的集成 \(F_T\) 的泛化误差由以下界定：

\[
\text{err}(F_T) \le \widehat{\text{err}}(g) + O \left( \sqrt{\frac{d \ln(N/d) + \ln(1/\delta)}{N}} \right) + \mu
\]

证明。回顾 Schapire 和 Freund [36, theorem 2.5] 的以下概率界（它源自 Sauer 引理）：

\[
\text{Pr} [\exists f \in \mathcal{C}_T : \text{err}(f) \ge \widehat{\text{err}}(f) + \epsilon] \le 8 \left( \frac{Ne}{d} \right)^d e^{-N\epsilon^2/32}
\]

该界在 \(|D| = N \ge d\) 时成立。因此，在样本中以概率 \(1 - \delta\)，对于所有 \(f \in \mathcal{C}_T\) 都有

\[
\text{err}(f) \le \widehat{\text{err}}(f) + O \left( \sqrt{\frac{d \ln(N/d) + \ln(1/\delta)}{N}} \right)
\]

(A.5)

