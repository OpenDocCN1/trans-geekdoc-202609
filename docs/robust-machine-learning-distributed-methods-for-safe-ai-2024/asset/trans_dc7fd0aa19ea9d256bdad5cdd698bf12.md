
在本分析中，我们研究在迭代算法的轨迹上，候选（辅助）函数的增长情况，该函数被称为 Lyapunov 函数或势函数（在本例中为 Robust DMHB 算法）。候选 Lyapunov 函数是 \(\theta\) 的实值正函数，其值随着 \(\theta\) 接近期望状态而减小，例如平均损失函数 \(\mathcal{L}_H\) 的局部最小值。候选 Lyapunov 函数的一个例子是损失函数的优化误差，即 \(\mathcal{L}_H(\theta) - \mathcal{L}_H^*\)。请回顾我们曾研究过这个特定的 Lyapunov 函数，以便分别推导出第 3 章和第 4 章中 DMGD 和 Robust DMGD 的收敛结果。然而，为了分析 Robust DMHB 的收敛性，我们需要在 Lyapunov 函数中纳入动量偏差，如第 6.2.2 节中即将介绍的那样。通过对所选 Lyapunov 函数的分析，我们同时捕捉到了分布式动量对聚合误差和梯度估计偏差（即动量偏差）的相反影响。这使我们能够设计一个合适的常数动量系数 \(\beta\)，使得 Robust DMHB 算法能够收敛到具有最优渐近误差的近似平稳点，同时提供合理的梯度复杂度。与 Robust DMGD 的情况类似，我们从非凸情形开始。

### 6.2.2 非凸损失函数情形

在下面给出的定理 6.1 中，我们通过假设聚合规则 \(F\) 为 \((f, \kappa)\)-鲁棒平均，得到了 Robust DMHB，即算法 6，到（近似）平稳性的收敛。利用该收敛结果，我们随后推导出可通过 Robust DMHB 实现的 \((f, \varepsilon)\)-平稳鲁棒性，其中使用的聚合方案在第 4 章和第 5 章中已有描述。我们考虑常数学习率 \(\gamma\)，即对所有 \(t\) 都有 \(\gamma_t = \gamma\)，使得 \(\gamma \le 1/c\)，其中 \(c\) 为正常数。为了控制动量偏差的增长，同时减小噪声对聚合误差的影响，我们考虑常数动量系数 \(\beta\) 满足

\[
\beta := \sqrt{1 - c\gamma}. \tag{6.24}
\]

我们可以快速验证，使用上述动量系数 \(\beta\) 的值，动量偏差的主导增长因子，由引理 6.3 中的 \((1 + \gamma L)(1 + 4\gamma L)\beta^2\) 给出，可通过选择足够大的 \(c\)（例如 \(c > 5L\)）使其小于 1。这意味着我们可以控制动量向量与瞬时梯度之间的偏差。相反，通过选择随 Robust DMHB 算法总迭代次数 \(T\) 递减的学习率，上述动量系数也会减弱引理 6.2 中分析的局部梯度噪声对聚合误差的影响。这些观察结果表明，尽管 \(\beta\) 对聚合误差和动量向量与真实梯度之间的偏差具有相反的影响，但公式 (6.24) 中定义的动量系数或许能够使算法收敛。

为了得到收敛结果，我们分析 Lyapunov 函数 \(V_t : \boldsymbol{\theta}_t \mapsto \mathbb{R}_+\) 在执行 \(T\) 次 Robust DMHB 迭代后生成的参数向量序列 \(\boldsymbol{\theta}_t\) 上的增长情况，该函数定义如下。具体而言，

\[
V_t := 2\left(\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H^*\right) + \frac{1}{8L}\|\boldsymbol{\xi}_t\|^2. \tag{6.25}
\]

请回顾 \(\mathcal{L}_H^* := \min_{\boldsymbol{\theta}\in\mathbb{R}^d}\mathcal{L}_H(\boldsymbol{\theta})\)，\(L\) 表示假设 3.1 中定义的逐点损失函数 \(\ell(\cdot,\boldsymbol{\theta})\) 的 Lipschitz 平滑系数（关于 \(\boldsymbol{\theta}\)），而 \(\boldsymbol{\xi}_t := \mathbf{m}_t^H - \nabla\mathcal{L}_H(\boldsymbol{\theta}_t)\) 为动量偏差。我们在引理 6.5 中看到，与损失函数 \(\mathcal{L}_H(\boldsymbol{\theta}_t)\) 不同，此特定 Lyapunov 函数的增长可以被一致地从上方界定。当动量系数 \(\beta\) 由 (6.24) 定义时，该界可以通过调整学习率 \(\gamma\) 来控制。

**Lemma 6.5.** 假设 3.1、3.2 和 4.1 成立。考虑使用 \((f,\kappa)\)-鲁棒平均规则 \(F\) 的算法 6，批大小 \(b \in [1,m)\)，每个迭代 \(t\) 的 \(\gamma_t = \gamma \le \frac{1}{24L}\)，以及由 (6.24) 定义的常数动量系数 \(\hat\beta\)，其中 \(c = 24L\)。那么，对于 (6.25) 中定义的 \(V_t\)，我们得到对每个迭代 \(t > 1\)，

\[
\mathbb{E}[V_t - V_{t-1}] \le -\frac{\gamma}{4}\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2\right] + 3\gamma\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right] + \frac{(1-\beta)^2\sigma^2}{8Lb(n-f)}.
\]

**Proof.** 考虑任意迭代 \(t > 1\)。记 \(z := \frac{1}{8L}\)，我们可以写出

\[
V_t = 2\left(\mathcal{L}_H(\boldsymbol{\theta}_t) - \mathcal{L}_H^*\right) + z\|\boldsymbol{\xi}_t\|^2. \tag{6.26}
\]

根据引理 6.3，代入 \(\gamma_{t-1}=\gamma\)、\(\beta_t=\beta\)，并在不等式两边应用全期望 \(\mathbb{E}[\cdot]\)，我们得到

\[
\mathbb{E}\left[\|\boldsymbol{\xi}_t\|^2\right] \le (1+\gamma L)(1+4\gamma L)\beta^2\mathbb{E}\left[\|\boldsymbol{\xi}_{t-1}\|^2\right] + 2L\gamma(1+\gamma L)\beta^2\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right] + 4L\gamma(1+\gamma L)\beta^2\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2\right] + \frac{(1-\beta)^2\sigma^2}{b(n-f)}. \tag{6.27}
\]

接下来，根据引理 6.4，我们得到

\[
\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_t)-\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\right] \le -\gamma\left(\frac{1}{2}-2\gamma L\right)\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2\right] + \gamma(1+2\gamma L)\mathbb{E}\left[\|\boldsymbol{\xi}_{t-1}\|^2\right] + \gamma(1+\gamma L)\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right]. \tag{6.28}
\]

因此，将 (6.28) 和 (6.27) 代入 (6.26)，我们得到

\[
\begin{aligned}
\mathbb{E}[V_t - V_{t-1}] &= 2\mathbb{E}\left[\mathcal{L}_H(\boldsymbol{\theta}_t)-\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\right] + z\mathbb{E}\left[\|\boldsymbol{\xi}_t\|^2 - \|\boldsymbol{\xi}_{t-1}\|^2\right] \\
&\le \left(-2\gamma\left(\frac{1}{2}-2\gamma L\right)+4zL\gamma(1+\gamma L)\beta^2\right)\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2\right] \\
&\quad + \left(2\gamma(1+2\gamma L)+z(1+\gamma L)(1+4\gamma L)\beta^2 - z\right)\mathbb{E}\left[\|\boldsymbol{\xi}_{t-1}\|^2\right] \\
&\quad + \left(2\gamma(1+\gamma L)+z2L\gamma(1+\gamma L)\beta^2\right)\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right] + z\frac{(1-\beta)^2\sigma^2}{b(n-f)}.
\end{aligned}
\]

令

\[
A := 2\left(\frac{1}{2}-2\gamma L\right) - 4zL(1+\gamma L)\beta^2, \tag{6.29}
\]

\[
B := 2\gamma(1+2\gamma L) + z(1+\gamma L)(1+4\gamma L)\beta^2 - z, \tag{6.30}
\]

\[
C := 2\gamma(1+\gamma L) + z2L\gamma(1+\gamma L)\beta^2. \tag{6.31}
\]

因此，我们可以将上述不等式重写为

\[
\mathbb{E}[V_t - V_{t-1}] \le -\gamma A\,\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2\right] + B\,\mathbb{E}\left[\|\boldsymbol{\xi}_{t-1}\|^2\right] + C\,\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right] + z(1-\beta)^2\frac{\sigma^2}{b(n-f)}. \tag{6.32}
\]

接下来，我们分别分析 \(A\)、\(B\) 和 \(C\)。

**Term A.** 将 \(z = \frac{1}{8L}\) 代入 (6.29)，并回顾 \(\gamma \le \frac{1}{24L}\) 且 \(\beta^2 < 1\)，我们得到

\[
A \ge 1 - 4\gamma L - \frac{4L}{8L}(1+\gamma L) \ge \frac{1}{2} - \frac{9\gamma L}{2} \ge \frac{1}{2} - \frac{3}{16} \ge \frac{1}{4}. \tag{6.33}
\]

**Term B.** 由 (6.30) 可得

\[
B = 2\gamma(1+2\gamma L) + z\beta^2(1 + 5\gamma L + 4\gamma^2 L^2) - z = -(1 - \beta^2)z + \gamma\left(2 + 4\gamma L + 5z\beta^2 L + 4z\beta^2\gamma L^2\right).
\]

代入 \(z = \frac{1}{8L}\)，并回顾 \(\beta^2 \le 1\) 且 \(\gamma \le \frac{1}{24L}\)，我们得到

\[
B \le -(1 - \beta^2)\frac{1}{8L} + \gamma\left(2 + \frac{4}{24} + \frac{5}{8} + \frac{4}{24 \times 8}\right) \le -(1 - \beta^2)\frac{1}{8L} + 3\gamma.
\]

将 (6.24) 中 \(c = 24L\) 的情况代入上式，其中 \(1 - \beta^2 = 24\gamma L\)，我们得到

\[
B \le -24\gamma L \cdot \frac{1}{8L} + 3\gamma = 0. \tag{6.34}
\]

**Term C.** 将 \(z = \frac{1}{8L}\) 代入 (6.31)，并回顾 \(\beta^2 < 1\) 且 \(\gamma \le \frac{1}{24L}\)，我们得到

\[
C \le 2\gamma(1+\gamma L) + \frac{\gamma}{4}(1+\gamma L) = \frac{9\gamma}{4}(1+\gamma L) \le \frac{9\gamma}{4}\left(1+\frac{1}{24}\right) \le 3\gamma. \tag{6.35}
\]

将 (6.33)、(6.34) 和 (6.35) 代入 (6.32)，我们得到

\[
\mathbb{E}[V_t - V_{t-1}] \le -\frac{\gamma}{4}\mathbb{E}\left[\|\nabla\mathcal{L}_H(\boldsymbol{\theta}_{t-1})\|^2\right] + 3\gamma\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right] + z\frac{(1 - \beta)^2\sigma^2}{b(n - f)}.
\]

请回顾上式中 \(z = \frac{1}{8L}\)。证明完毕。

在上述分析中，我们得到了所考虑 Lyapunov 函数 \(V_t\) 增长的上界。注意该上界与动量偏差无关。因此，由于在常数动量下，聚合误差 \(\mathbb{E}\left[\|\boldsymbol{\delta}_{t-1}\|^2\right]\) 的依赖性可借助引理 6.2 被一致界定，我们现在可以得到 Robust DMHB（即算法 6）轨迹上损失函数平方梯度范数平均值的上界。具体而言，我们有以下收敛结果。
