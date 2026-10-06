

## 7.3.2 理论证明

我们首先从给定的图像 $x_q$ 开始，在概念 $\phi^*$ 和提示 $S_n$ 的条件下，$y_q$ 最具有概率的文本输出与提示分布 $p_{prompt}$ 中概率最大的类别相同。然后，我们证明在我们的去噪上下文学习中，当获得 MLLM 预测器输出的最可能的预测 $z$ 时，预训练分布 $p$ 中的类别文本 $y_q$ 与提示分布 $p_{prompt}$ 中的类别相同，这与给定的图像 $X_q$ 完全匹配。

在开始分析二分类预测 $z$ 之前，我们首先研究由提示和查询 $\max_y p(y|S_n, x_q)$ 给出的最可能的类别 $y$。

定理 22。假设上述假设成立，如果对于所有 $\phi \in \Phi, \phi \neq \phi^*$，概念 $\phi^*$ 满足可区分条件：$\sum_{j=1}^k \mathcal{L}_j(\phi^*) > \epsilon_{start}^* + \epsilon_{delim}$，那么当 $n \to \infty$ 时，根据预训练分布的预测 $y$ 为：

$$\max_y p(y|S_n, \phi^*) \to \max_y p_{prompt}(y|X_q). \quad (7.54)$$

因此，上下文预测器 $f_n$ 实现了最优 $0-1$ 风险：$\lim_{n\to\infty} \mathcal{L}_{0-1}(f_n) = \inf_f \mathcal{L}_{0-1}(f)$。

该定理的详细证明类似于 Xie 等人 [297]，请参考原论文的 D 节。

在此假设下，上下文预测器具有最高的概率生成与查询图像 $x_q$ 完全匹配的类别描述 $y$。另一种说法，当 $x_q$ 不属于 $y$ 时，概率 $p(y|S_n, x_q)$ 小于最优值。

引理 6。在定理 22 的相同条件下，根据预训练分布的预测 $z$ 为：

$$\max_z p(z|S_n, x_q, y_q, \phi^*) \to \max_z p_{prompt}(z|X_q, y_q). \quad (7.55)$$

## 7.3 MVT 的证明

通过将 $y$ 视为固定提示，可以基于定理 22 轻松推导出引理 6。

定理 23。假设上述假设成立，当 $n \to \infty$ 时，在概念 $\phi^*$ 下给定提示获得 $z$ 最大预测概率时，对应的类别描述 $y$ 遵循从提示分布中获得的相同 $y$：

$$\arg_y p(z|S_n, x_q, y, \phi^*) \rightarrow \arg_y p_{prompt}(z|x_q, y) \quad (7.56)$$

证明。由于我们已经有了定理 22，如果我们可以证明：

$$\arg_y p(y|S_n, x_q, \phi^*) = \arg_y p(z|S_n, x_q, y, \phi^*) \quad (7.57)$$

$$\arg_y p_{prompt}(y|x_q) = \arg_y p_{prompt}(z|x_q, y) \quad (7.58)$$

那么我们就可以完成证明。

$$p(z|S_n, x_q, \phi^*) = \sum_{h^{start} \in \mathcal{H}} p(z|h_q^{start})p(h^{start}|S_n, x_q, y, \phi^*) \quad (7.59)$$

通过展开最后一项，我们得到：其中 ($h^{start}$) 被视为常数。此外，根据假设 21，联合分布 $p(x_q, y)$ 由预训练分布定义，它不影响 $z$ 的边缘分布，因此我们可以得到：

$$p(x_q, y|h_q^{start}, S_n, \phi^*) = \frac{p(y|S_n, x_q, h_q^{start}, \phi^*)p(x_q|h_q^{start})}{p(x_q, y)} \quad (7.62)$$

由于 $y$ 的变化不影响 $p(z|h_q^{start})$ 的量，因此在等式两边应用 argmax 以寻找最优的 $y$：

$$\arg max_y p(z|S_n, x_q, y, \phi^*) = \arg max_y \sum_{h_q^{start}\in H} p(z|h_q^{start}) p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.64)$$

$$= \arg max_y p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.65)$$

相似地，我们有：

$$p_{prompt}(z|x_q, y) = \sum_{h_q^{start}\in H} p(z|h_q^{start}, \phi^*) p_{prompt}(h_q^{start}|x_q, y), \quad (7.66)$$

$$p_{prompt}(h_q^{start}|x_q, y) = \frac{p_{prompt}(x_q, y) p_{prompt}(h_q^{start})}{p_{prompt}(x_q, y)} \quad (7.67)$$

$$\propto p_{prompt}(x_q|h_q^{start}) \quad (7.68)$$

$$\propto p(y|h_q^{start}) p_{prompt}(x_q|h_q^{start}) \quad (7.69)$$

$$\arg max_y p_{prompt}(z|x_q, y) = \arg max_y \sum_{h_q^{start}\in H} p_{prompt}(z|h_q^{start}, \phi^*) p_{prompt}(y|x_q, h_q^{start}) \quad (7.70)$$

$$= \arg max_y p(y|x_q, h_q^{start}), \quad (7.71)$$

其中 $y$ 的变化不影响 $p_{prompt}(z|h_q^{start})$ 的量。由于：

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.72)$$

$$p_{prompt}(y|x_q) = \sum_{h_q^{start}\in H} p_{prompt}(y|h_q^{start}, x_q) p_{prompt}(h_q^{start}|x_q), \quad (7.73)$$

很容易发现：

$$\arg max_y p_{prompt}(y|x_q) = \arg max_y p(y|x_q, h_q^{start}) \quad (7.74)$$

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.75)$$

因此，当 $n \to \infty$ 时：

$$p(z|S_n, x_q, \phi^*) = \arg max_y p_{prompt}(z|x_q, y) \quad (7.76)$$

引理 6 和定理 23 表明，给定 $x_q$，如果 $p_{prompt}(y|x_q)$ 为真实标签，则上下文预测器可以识别该类别。

## 7.4 V 的下界

回想：

$$p(x_q, y|h_q^{start}, S_n, \phi^*) = \frac{p(y|S_n, x_q, h_q^{start}, \phi^*)p(x_q|h_q^{start})}{p(x_q, y)} \quad (7.77)$$

由于 $y$ 的变化不影响 $p(z|h_q^{start})$，因此在等式两边应用 argmax 以寻找最优的 $y$：

$$\arg max_y p(z|S_n, x_q, y, \phi^*) = \arg max_y \sum_{h_q^{start}\in H} p(z|h_q^{start}) p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.78)$$

$$= \arg max_y p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.79)$$

相似地，我们有：

$$p_{prompt}(z|x_q, y) = \sum_{h_q^{start}\in H} p(z|h_q^{start}, \phi^*) p_{prompt}(h_q^{start}|x_q, y), \quad (7.80)$$

$$p_{prompt}(h_q^{start}|x_q, y) = \frac{p_{prompt}(x_q, y) p_{prompt}(h_q^{start})}{p_{prompt}(x_q, y)} \quad (7.81)$$

$$\propto p_{prompt}(x_q|h_q^{start}) \quad (7.82)$$

$$\propto p(y|h_q^{start}) p_{prompt}(x_q|h_q^{start}) \quad (7.83)$$

$$\arg max_y p_{prompt}(z|x_q, y) = \arg max_y \sum_{h_q^{start}\in H} p_{prompt}(z|h_q^{start}, \phi^*) p_{prompt}(y|x_q, h_q^{start}) \quad (7.84)$$

$$= \arg max_y p(y|x_q, h_q^{start}), \quad (7.85)$$

其中 $y$ 的变化不影响 $p_{prompt}(z|h_q^{start}, \phi^*)$。由于：

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.86)$$

$$p_{prompt}(y|x_q) = \sum_{h_q^{start}\in H} p_{prompt}(y|h_q^{start}, x_q) p_{prompt}(h_q^{start}|x_q), \quad (7.87)$$

很容易发现：

$$\arg max_y p_{prompt}(y|x_q) = \arg max_y p(y|x_q, h_q^{start}) \quad (7.88)$$

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.89)$$

因此，当 $n \to \infty$ 时：

$$p(z|S_n, x_q, \phi^*) = \arg max_y p_{prompt}(z|x_q, y) \quad (7.90)$$

## 7.4.2 定理的证明

现在我们开始定理 7 的证明。

假设 24（松弛三角不等式）。对于距离函数 $d : \mathcal{Y} \times \mathcal{Y} \rightarrow \mathbb{R}^+$，存在 $c_d \geq 1$ 使得 $\hat{y}_1, \hat{y}_2, \hat{y}_3 \in \mathcal{Y}, d(\hat{y}_1, \hat{y}_2) \leq c_d(d(\hat{y}_1, \hat{y}_3) + d(\hat{y}_2, \hat{y}_3))$。

假设 25（逆 Lipschitz 茨条件）。对于函数 $d$，对于所有 $\forall$：

$$\mathbb{E}[d(h(x_1, x_2))] \leq |\mathcal{L}(h) - \mathcal{L}(h^*)| \quad (7.91)$$

其中 $h^*$ 是 $x_1$ 和 $x_2$ 上的贝叶斯最优分类器，且：

$$\mathbb{E}[d(h(x), h^*(x))] \leq |\mathcal{L}(h) - \mathcal{L}(h^*)| \quad (7.92)$$

假设 26（分类器最优性）。与贝叶斯最优分类器 $h^*$ 相比，任何分类器 $h$，都存在常数 $\epsilon > 0 使得 $|\mathcal{L}(h) - \mathcal{L}(h^*)|^2 \leq \epsilon$。

> $^1$我们关注 $p(Y^O|X^O)$ 的优化，且 $p(Y|X^1)$ 是给定的且固定的。

