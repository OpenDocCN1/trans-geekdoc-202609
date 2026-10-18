

注意，当 $\alpha \to 0$ 时，$\mathcal{E} \to \frac{\lambda}{2}\sum_{i=1}^{n}(g(x_i)-y_i)^2$，因此 MAP 估计收敛于最小二乘估计。此外，当 $\alpha > 0$ 时，([12.12](#c12.xhtml#c12-disp-0021)) 中 $\mathcal{E}$ 的第二项随 $\boldsymbol{\beta}$ 的范数增加而增大，因此可以将其视为正则化项，这意味着 MAP 估计可以被视为对最小二乘估计的一种正则化。当 $\alpha$ 较大时，得到的 $\boldsymbol{\beta}$ 趋向于 $\mathbf{0}$；而随着 $\alpha$ 减小，先验分布趋近于均匀分布，这呼应了 $\mathcal{E}$ 中较弱的正则化。作为补充说明，参数 $\alpha$ 的选择可能会根据数据结构而有所不同。例如，当所有 $x_i$ 均介于 0 和 1 之间，而响应 $y$ 的幅度较大时，$\boldsymbol{\beta}$ 的估计值可能不可避免地较大。为此，我们可以选择较小的 $\alpha$ 以取得平衡。

除了正则化之外，([12.12](#c12.xhtml#c12-disp-0021)) 中 $\mathcal{E}$ 表达式中的惩罚项也有助于防止过拟合，因为我们寻求的是更简单的模型。具有较大次数 $M$ 的模型通常会受到较大的惩罚，通过比较不同 $M$ 值模型的 $\mathcal{E}$ 值，我们可以选择估计多项式的适当次数 $M$，以避免过拟合并提升样本外预测效果。这可以被视为著名的 *贝叶斯信息准则* (BIC) 的一种替代方法，BIC 定义为 $\text{BIC} := -2 \ln \hat{L} + k \ln n$，其中 $\hat{L}$ 是最大化似然，$k$ 是待估计参数的数量，$n$ 是样本量；另请参见 [附录 12.A.212.6.2](#c12.xhtml#c12-sec-0018)，了解通过拉普拉斯近似对 BIC 的动机。

对 ([12.11](#c12.xhtml#c12-disp-0020)) 进行直接计算表明，后验分布确实是另一个多元正态分布：

$$
\boldsymbol{\beta} \mid \boldsymbol{y} = \tilde{y} \sim \mathcal{N}_{M+1}\left(\lambda \boldsymbol{S} \sum_{i=1}^{n} y_i \boldsymbol{\phi}(x_i), \boldsymbol{S}\right)
$$

