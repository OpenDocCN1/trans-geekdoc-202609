
利用亚高斯范数的定义（回顾命题 2.6.6(i) 和注记 2.6.3），不等式 (9.5) 变为

$$
p(s) := P\left\{ \frac{\left| \|Ax\|_2 - \|Ay\|_2 \right|}{\|x-y\|_2} \ge s \right\} \le 4 \exp\left(-\frac{c s^2}{K^4}\right) \quad \forall s > 0. \tag{9.9}
$$

（这里用常数 4 而不是 2，会给我们留出更多的回旋余地。）

### 情形 1：\(s \le 2\sqrt{m}\)

让我们使用步骤 2 的结果。为了应用它，将定义 \(p(s)\) 的不等式两边同时乘以 \(\|Ax\|_2 + \|Ay\|_2\)，并回顾 \(\Delta\) 的定义 (9.7)，可得

$$
p(s) = P\left\{ |\Delta| \ge s (\|Ax\|_2 + \|Ay\|_2) \right\} \le P\left\{ |\Delta| \ge s \|Ax\|_2 \right\}.
$$

由 (9.4) 我们知道 \(\|Ax\|_2 \approx \sqrt{m}\) 以高概率成立。因此，自然地考虑两种情形：一种是可能的情形，即 \(\|Ax\|_2 \ge \sqrt{m}/2\)，从而 \(|\Delta| \ge s\sqrt{m}/2\)；另一种是不太可能出现的情形，即 \(\|Ax\|_2 < \sqrt{m}/2\)（在这种情况下我们舍弃有关 \(\Delta\) 的条件，只会使概率增大）。于是得到

$$
p(s) \le P\left\{ |\Delta| \ge s\sqrt{m}/2 \right\} + P\left\{ \|Ax\|_2 < \sqrt{m}/2 \right\} := p_1(s) + p_2(s).
$$

步骤 2 的结果处理可能的情形：

$$
p_1(s) \le 2 \exp\left(-\frac{c s^2}{K^4}\right),
$$

而步骤 1 的结果 (9.4) 结合三角不等式处理不太可能出现的情形：

$$
p_2(s) \le P\left\{ \left| \|Ax\|_2 - \sqrt{m} \right| > \sqrt{m}/2 \right\} \le 2 \exp\left(-\frac{c m}{K^4}\right).
$$

将两者相加，我们得到所需的界

$$
p(s) \le 4 \exp\left(-\frac{c s^2}{K^4}\right).
$$

### 情形 2：\(s > 2\sqrt{m}\)

根据三角不等式，\(\left| \|Ax\|_2 - \|Ay\|_2 \right| \le \|A(x-y)\|_2\)，所以

$$
p(s) \le P\{ \|Au\|_2 \ge s \}
\le P\{ \|Au\|_2 - \sqrt{m} \ge s/2 \}
\le 2 \exp\left(-\frac{c s^2}{K^4}\right),
$$

其中 \(u = (x-y)/\|x-y\|_2\) 如前所述，第二个不等式利用了 \(s > 2\sqrt{m}\)，最后一个不等式则由步骤 1 的结果 (9.4) 对 \(u\)（而非 \(x\)）应用得到。

因此，无论哪种情形，我们都得到所需的界 (9.9)。

### 步骤 4：完全一般性

最后，我们来证明 (9.3) 对任意 \(x, y \in \mathbb{R}^n\) 成立。通过伸缩变换，我们可以不失一般性地假设

$$
\|x\|_2 = 1 \quad \text{且} \quad \|y\|_2 \ge 1.
$$

一个尾界。对任意 \(u \ge 0\)，事件

$$
\sup_{x\in T}\left\| \|Ax\|_2 - \sqrt{m}\|x\|_2 \right\| \le CK^2\left[w(T)+u\cdot\operatorname{rad}(T)\right] \tag{9.11}
$$

以至少 \(1-2\exp(-u^2)\) 的概率成立。这里 \(\operatorname{rad}(T)=\sup_{x\in T}\|x\|_2\) 是 \(T\) 的半径。你能看出为什么 (9.11) 蕴含期望界吗？

**注记 9.1.5**（平方的矩阵偏差）。如果你对二次型过程 \(\|Ax\|_2^2\) 的偏差感兴趣，可以很容易地从**定理 9.1.1** 推出这一点：

$$
\mathbb{E}\sup_{x\in T}\left| \|Ax\|_2^2 - m\|x\|_2^2 \right| \le CK^4\gamma(T)^2+CK^2\sqrt{m}\,\operatorname{rad}(T)\gamma(T).
$$

请在**习题 9.3** 中验证这一点。

作为练习，将矩阵偏差不等式推广到经验过程（**习题 9.5**），并证明随机投影的一个版本（**习题 9.6**——这道题很有挑战性！）。

## 9.2 随机矩阵、协方差估计与 Johnson–Lindenstrauss

矩阵偏差不等式有许多有用的推论。在本章余下部分，我们将讨论其中几个。

### 9.2.1 随机矩阵的奇异值

对单位欧几里得球面 \(T=S^{n-1}\) 应用矩阵偏差不等式，可以得到**第 4.6 节**中的奇异值界。

快速验证如下：因为对球面有

$$
\operatorname{rad}(T)=1 \quad \text{且} \quad w(T)\le\sqrt{n},
$$

矩阵偏差不等式 (9.11) 表明，事件

$$
\sqrt{m}-CK^2(\sqrt{n}+u)\le\|Ax\|_2\le\sqrt{m}+CK^2(\sqrt{n}+u)\quad\forall x\in S^{n-1}
$$

以至少 \(1-2\exp(-u^2)\) 的概率成立。利用 (4.14)，这转化为

$$
\sqrt{m}-CK^2(\sqrt{n}+u)\le s_n(A)\le s_1(A)\le\sqrt{m}+CK^2(\sqrt{n}+u),
$$

从而以不同的方式重新得到了我们之前证明过的**定理 4.6.1**。

### 9.2.2 集合的随机投影

矩阵偏差不等式的另一个直接应用，是**第 7.6 节**中随机投影界的一个（更精细的！）版本：

**命题 9.2.1**（集合随机投影的大小）。设 \(T \subset \mathbb{R}^n\) 是有界集，\(A\) 是行为独立、各向同性且亚高斯的 \(m \times n\) 矩阵 \(A_i\)。则缩放后的矩阵 \(P = \frac{1}{\sqrt{n}}A\)（一个“亚高斯投影”）满足

$$
\mathbb{E}\,\mathrm{diam}(PT) \le \sqrt{\frac{m}{n}}\,\mathrm{diam}(T) + C K^2 w_s(T).
$$

这里 \(K = \max_i \|A_i\|_{\psi_2}\)，\(w_s(T)\) 是 \(T\) 的球宽度（回顾第 7.5.1 节）。

这比我们之前的界（定理 7.6.1 和习题 7.25）稍微精细一些——在 \(\sqrt{m/n}\) 前面没有常数因子。

**证明。** 定理 9.1.1 通过三角不等式蕴含：

$$
\mathbb{E}\sup_{x\in T}\|Ax\|_2 \le \sqrt{m}\sup_{x\in T}\|x\|_2 + C K^2 \gamma(T),
$$

我们可以用 \(AT\) 和 \(T\) 的半径将其重写为：

$$
\mathbb{E}\,\mathrm{rad}(AT) \le \sqrt{m}\,\mathrm{rad}(T) + C K^2 \gamma(T).
$$

将这个界应用于差集 \(T - T\)（而不是 \(T\)），得到

$$
\mathbb{E}\,\mathrm{diam}(AT) \le \sqrt{m}\,\mathrm{diam}(T) + 2 C K^2 w(T),
$$

其中我们使用引理 7.5.11(a) 从高斯复杂度过渡到高斯宽度。两边同时除以 \(\sqrt{n}\)，即可完成证明。

现在试试这个：将命题 9.2.1 中的期望界提升为高概率界（习题 9.7），并在习题 9.8 中分析实际的随机投影（而不是“高斯”投影）。

### 9.2.3 低维分布的协方差估计

让我们重新审视第 4.7 节中的协方差估计问题。我们希望利用样本协方差矩阵 \(\Sigma_m = \frac{1}{m}\sum_{i=1}^m X_i X_i^{\mathsf T}\)，从 \(m\) 个独立同分布样本中估计一个 \(n\) 维分布的协方差矩阵 \(\Sigma = \mathbb{E} X X^{\mathsf T}\)。

一般来说，\(m = O(n \log n)\) 个样本就足够了（第 5.6 节），但对于亚高斯分布，\(m = O(n)\) 就足够了（第 4.7 节）。

对于近似低维分布，情况甚至更好。如果某个分布集中在某个 \(r\) 维子空间附近，那么 \(m = O(r \log n)\) 个样本就足够了（注记 5.6.3）。现在我们证明，对于亚高斯分布，\(m = O(r)\) 个样本就足够了：

**定理 9.2.2**（低维分布的协方差估计）。设 \(X\) 是 \(\mathbb{R}^n\) 中的亚高斯随机向量。更具体地说，假设存在 \(K \ge 1\)，使得

$$
\big\|\langle X, x\rangle\big\|_{\psi_2} \le K \big\|\langle X, x\rangle\big\|_{L^2} \quad \text{对任意 } x \in \mathbb{R}^n.
$$

那么，对每个正整数 \(m\)，有

$$
\mathbb{E}\|\Sigma_m - \Sigma\| \le C K^4\left(\sqrt{\frac{r}{m}}+\frac{r}{m}\right)\|\Sigma\|,
$$

其中 \(r = \operatorname{tr}(\Sigma)/\|\Sigma\|\) 是 \(\Sigma\) 的有效秩——衡量数据有效维度的量（参见注记 5.6.3）。

**证明。** 我们像定理 4.7.1 那样，先把分布化为各向同性位置：\(X = \Sigma^{1/2} Z\)，\(X_i = \Sigma^{1/2} Z_i\)，其中 \(Z\) 和 \(Z_i\) 是各向同性的，并且

$$
\begin{aligned}
\|\Sigma_m - \Sigma\| &= \|\Sigma^{1/2} R_m \Sigma^{1/2}\| \quad (\text{其中 } R_m = \frac{1}{m}\sum_{i=1}^m Z_i Z_i^{\mathsf T} - I_n)\\
&= \max_{x\in S^{n-1}} |x^{\mathsf T} \Sigma^{1/2} R_m \Sigma^{1/2} x| \quad (\text{参见注记 4.1.12})\\
&= \max_{x\in T} |x^{\mathsf T} R_m x| \quad (\text{若定义椭球 } T := \Sigma^{1/2} S^{n-1})\\
&= \max_{x\in T} \left|\frac{1}{m}\sum_{i=1}^m \langle Z_i, x\rangle^2 - \|x\|_2^2\right| \quad (\text{根据 } R_m \text{ 的定义})\\
&= \frac{1}{m} \max_{x\in T} \left| \|Ax\|_2^2 - m\|x\|_2^2 \right|,
\end{aligned}
$$

其中 \(A\) 是以 \(Z_i\) 为行的 \(m \times n\) 矩阵。与定理 4.7.1 的证明一样，\(Z_i\) 是各向同性的，并且满足 \(\|Z_i\|_{\psi_2} \lesssim 1\)。（为简单起见，我们在这个论证中隐藏对 \(K\) 的依赖。）这样我们就可以对 \(A\) 应用矩阵偏差不等式（采用习题 9.3 中给出的形式），得到

$$
\mathbb{E}\|\Sigma_m - \Sigma\| \lesssim \frac{1}{m}\big(\gamma(T)^2 + \sqrt{m}\,\operatorname{rad}(T)\gamma(T)\big).
$$

椭球 \(T = \Sigma^{1/2} S^{n-1}\) 的半径和高斯复杂度满足

$$
\operatorname{rad}(T) = \|\Sigma\|^{1/2} \quad \text{且} \quad \gamma(T) \le (\operatorname{tr}\Sigma)^{1/2}
$$

（请验证！）。因此，

$$
\mathbb{E}\|\Sigma_m - \Sigma\| \lesssim \frac{1}{m}\Big(\operatorname{tr}\Sigma + \sqrt{m\|\Sigma\|\operatorname{tr}\Sigma}\Big).
$$

代入 \(\operatorname{tr}(\Sigma) = r\|\Sigma\|\) 并简化界，即可完成证明。\(\square\)

**注记 9.2.3**（协方差估计：高概率保证）。与之前一样（参见注记 4.7.3 和 5.6.5），我们可以将定理 9.2.2 中的期望界提升为高概率界。对任意 \(u \ge 0\)，有

$$
\|\Sigma_m - \Sigma\| \le C K^4\left(\sqrt{\frac{r+u}{m}}+\frac{r+u}{m}\right)\|\Sigma\|
$$

以至少 \(1 - 2e^{-u}\) 的概率成立。请尝试在习题 9.9 中证明这一点！
