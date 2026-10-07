
```
$\mathbb{E} [m Z^e_{var}] = 2\mathbb{P} \left[ \frac{1}{M_{var}} m_{i\in[M_{inv},M]} Z_{var}^e > 0 \mid Y^e = 1 \right]$$
$$= p^{\frac{Q^e_{inv}}{M_{var}}} - 1,$ (7.46),
```

```
$Err^e \le \mathbb{P} [|m Z^e_{var}| - \mathbb{E} [|m Z^e_{var}|] \ge 1 \mid Y^e = 1]$$
$$\le 2e^{-2(\frac{Q^e_{inv}}{M_{var}}-1)M_{var}} = \mathcal{O}(e^{-(p^e)^2})$ (7.47)
```

# 7.3 MVT 的证明

本节提供了定理 5 的证明。

**预训练分布公式化。** 我们基于 Xie 等人 [297] 提出的上下文学习框架。在该框架中，来自概念空间 `$\Phi$` 的隐变量概念 `$\phi$` 定义了从词汇表 `O` 观察到的 prompt 标记 `o` 的预训练分布 `p`。为了生成所需的内容，我们首先从先验 `p(\phi)` 中采样一个概念，然后根据该概念采样标记。我们将预训练示例的总长度标记为 `T`：

```
$p(o_1, \dots, o_T) = \int_{\phi \in \mathcal{O}} p(o_1, \dots, o_T|\phi)p(\phi)d\phi.$
```

条件概率 `p(o_1, \dots, o_T)` 由隐马马尔可夫模型 `HMM` 定义。根据概念 `$\phi$`，可以找到来自隐状态空间 `$\mathcal{H}$` 的 HMM 隐状态 `h_1,\dots,h_T` 的转移矩阵。

**Prompt 分布公式化。** 在上下文学习过程中，我们从新分布 `p_{prompt}` 中采样 prompt；该分布包含 `n` 个独立示例和 1 个查询示例，它们都条件于共享的 prompt 概念 `$\phi^*$`。目标是基于标记的图像特征 `x_i = O_i[1:k_i]`、描述图像断言的文本 `y_i = O_i[k_x : k_x + k_y]` 以及判断图像断言是“真”还是“假”的二分类预测（在每个示例的末尾标记为 `z_i = O_i[k_x + k_y : k_x + k_y + 1]`）。该示例示例的生成过程如下：

- (1) 从 prompt 分布 `p_{prompt}` 生成起始隐状态 `h^{start}`

- (2) 给定 `h^{start}`，从 `p(O_i|h^{start}, \phi^*)` 生成示例序列 `O_i = [x_i, y_i, z_i]`，示例条件于给定的 prompt 概念 `$\phi^*$`。

查询示例 `Q` 同样采样，但不包含二分类预测 `z_q`，即 `Q = [x_q, y_q]`。在每个示例和查询示例之间，有一个特殊的分隔符 `o^{delim}` 表示每个示例的结束。prompt 可以公式化为：

```
$[S_n, Q] = [x_1, y_1, z_1, o^{delim}, x_2, y_2, z_2, \dots, x_n, y_n, z_n, o^{delim}, x_q, y_q] \sim p_{prompt},$
```

其中 `S_n` 表示上下文示例。

**去噪上下文学习。** 在我们的上下文学习中，每个图像和文本对 `[x, y]` 的输出预测 `z` 是基于 prompt `P_{prompt}(z|x, y)` 采样的：

```
$z_q \sim p_{prompt}(z|x, y) = \mathbb{E}_{h_{start}^Q}p[z|Q, h_q^{start}, \phi^*], (7.50)$
```

`h_q^{start}` 表示对应于 `Q` 的标记的隐状态。我们的目标是分析上下文预测器 `f_n(x_q, y_q) = \arg max_z p(z|S_n, x_q, y_q)`，它在从 prompt 分布 `p_{prompt}` 采样的示例 `S_n` 上输出预训练分布 `p` 中概率最大的预测。我们假设预测器通过 `n` 个示例的 `0-1` 误差进行训练：

```
$\mathcal{L}_{0-1}(f_n) = \mathbb{E}_{x_q,y_q} \sim p_{prompt}[1[f_n(x_q) \neq y_q]], (7.51)$
```

对于预测 `$\hat{z}_q$` 也是：

```
$\mathcal{L}_{0-1}(f_n) = \mathbb{E}_{x_q,z_q} \sim p_{prompt}[1[f_n(x_q) \neq z_q]]. (7.52)$
```

我们去噪策略的一个主要区别在于，我们不仅使用显示精确图像文本匹配的正样本（即 `(x, y)`），还使用了图像和文本不对应的负样本。为了构建这样的 prompt，我们必须首先选择理想的 `y`，根据 `x` 和 `y` 的匹配结果，我们可以获得预测 `z`。因此，在随后的理论证明中，我们分别对 `y` 和 `z` 进行两步分析。

### 7.3.1 假设

我们的理论框架基于 Xie 等人 [297]，其假设适用于我们的分析。

**假设 16（分隔状态）。** 令分隔状态 `$\mathcal{D}$` 为 `$\mathcal{H}$` 的子集。对于任何 `h^{delim} \in \mathcal{D}` 和 `$\phi$`，`p(o^{delim}|h, \phi) = 1`，且对于任何 `h \notin \mathcal{D}`，`p(o^{delim}|h, \phi) = 0`。

**假设 17（分隔转移边界）。** 对于任何分隔状态 `h^{delim} \in \mathcal{D}` 和任何 `h \in \mathcal{H}`，在 `$\phi$` 下转移到分隔状态的概率上限为 `p(h^{delim}|\phi) < c_2`，而对于 `$\phi^*$`，`p(h^{delim}|\phi^*) > c_1`。

**假设 18（来自 prompt 起点的分布偏移）。** 我们假设 prompt 起点分布 `p_{prompt}` 与所有转移分布（在 `$\phi^*$` 下）的 TV 距离接近：

```
$$\max_{h \in \mathcal{D}} TV(p_{prompt}(h)|p(h^{delim}, \phi^*)) < \tau/4.$$
```

在这里，`$\Delta = p_{max}(y_{max}|Q) - \max_{y} p_{prompt}(y|Q)$` 是最大概率标签 `y_{max}` 与第二概率标签之间的间隔。

**假设 19（良好规范）。** prompt 概念 `$\phi^*$` 属于 `$\Phi$`。

**假设 20（正则性）。** 预训练分布 `p` 满足：(1) 概念 `$\phi^*$` 的转移概率下界：对于任意隐状态对 `h, h' \in \mathcal{H}`，`p(h|h', \phi^*) > c_2 > 0`。(2) 起始状态下界有界：对于任何 `h \in \mathcal{H}`，`p(h|\phi^*) > c_8 > 0`。(3) 所有标记均可发射：对于每个符号 `o`，存在某些隐状态 `h \in \mathcal{H}` 使得 `p(o|h, \phi^*) > c_6`，(4) 先验 `p(\phi)` 在整个概念族 `$\Phi$` 上有支撑且处处有上界。

**假设 21（分布一致性）。** 预训练分布 `p` 和 prompt 分布 `p_{prompt}` 满足 `$\sqrt{(x_q, y_q)} \sim p_{prompt}, p(x_q, y_q) = p_{prompt}(x_q, y_q)$`。

## 7.3.2 理论证明

我们首先从给定的图像 `x_q` 开始，在概念 `$\phi^*$` 和提示 `S_n` 的条件下，`y_q` 最具有概率的文本输出与提示分布 `p_{prompt}` 中概率最大的类别相同。然后，我们证明在我们的去噪上下文学习中，当获得 MLLM 预测器输出的最可能的预测 `z` 时，预训练分布 `p` 中的类别文本 `y_q` 与提示分布 `p_{prompt}` 中的类别相同，这与给定的图像 `X_q` 完全匹配。

在开始分析二分类预测 `z` 之前，我们首先研究由提示和查询 `$\max_y p(y|S_n, x_q)$` 给出的最可能的类别 `y`。

定理 22。假设上述假设成立，如果对于所有 `$\phi \in \Phi, \phi \neq \phi^*$`，概念 `$\phi^*$` 满足可区分条件：`$\sum_{j=1}^k \mathcal{L}_j(\phi^*) > \epsilon_{start}^* + \epsilon_{delim}$`，那么当 `n \to \infty` 时，根据预训练分布的预测 `y` 为：

$$\max_y p(y|S_n, \phi^*) \to \max_y p_{prompt}(y|X_q). \quad (7.54)$$

因此，上下文预测器 `f_n` 实现了最优 `0-1` 风险：`$\lim_{n\to\infty} \mathcal{L}_{0-1}(f_n) = \inf_f \mathcal{L}_{0-1}(f)$`。

该定理的详细证明类似于 Xie 等人 [297]，请参考原论文的 D 节。

在此假设下，上下文预测器具有最高的概率生成与查询图像 `x_q` 完全匹配的类别描述 `y`。另一种说法，当 `x_q` 不属于 `y` 时，概率 `p(y|S_n, x_q)` 小于最优值。

引理 6。在定理 22 的相同条件下，根据预训练分布的预测 `z` 为：

$$\max_z p(z|S_n, x_q, y_q, \phi^*) \to \max_z p_{prompt}(z|X_q, y_q). \quad (7.55)$$

## 7.3 MVT 的证明

通过将 `y` 视为固定提示，可以基于定理 22 轻松推导出引理 6。

定理 23。假设上述假设成立，当 `n \to \infty` 时，在概念 `$\phi^*$` 下给定提示获得 `z` 最大预测概率时，对应的类别描述 `y` 遵循从提示分布中获得的相同 `y`：

$$\arg_y p(z|S_n, x_q, y, \phi^*) \rightarrow \arg_y p_{prompt}(z|x_q, y) \quad (7.56)$$

证明。由于我们已经有了定理 22，如果我们可以证明：

$$\arg_y p(y|S_n, x_q, \phi^*) = \arg_y p(z|S_n, x_q, y, \phi^*) \quad (7.57)$$

$$\arg_y p_{prompt}(y|x_q) = \arg_y p_{prompt}(z|x_q, y) \quad (7.58)$$

那么我们就可以完成证明。

$$p(z|S_n, x_q, \phi^*) = \sum_{h^{start} \in \mathcal{H}} p(z|h_q^{start})p(h^{start}|S_n, x_q, y, \phi^*) \quad (7.59)$$

通过展开最后一项，我们得到：其中 (`h^{start}`) 被视为常数。此外，根据假设 21，联合分布 `p(x_q, y)` 由预训练分布定义，它不影响 `z` 的边缘分布，因此我们可以得到：

$$p(x_q, y|h_q^{start}, S_n, \phi^*) = \frac{p(y|S_n, x_q, h_q^{start}, \phi^*)p(x_q|h_q^{start})}{p(x_q, y)} \quad (7.62)$$

由于 `y` 的变化不影响 `p(z|h_q^{start})` 的量，因此在等式两边应用 argmax 以寻找最优的 `y`：

$$\arg max_y p(z|S_n, x_q, y, \phi^*) = \arg max_y \sum_{h_q^{start}\in H} p(z|h_q^{start}) p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.64)$$

$$= \arg max_y p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.65)$$

相似地，我们有：

$$p_{prompt}(z|x_q, y) = \sum_{h_q^{start}\in H} p(z|h_q^{start}, \phi^*) p_{prompt}(h_q^{start}|x_q, y), \quad (7.66)$$

$$p_{prompt}(h_q^{start}|x_q, y) = \frac{p_{prompt}(x_q, y) p_{prompt}(h_q^{start})}{p_{prompt}(x_q, y)} \quad (7.67)$$

$$\propto p_{prompt}(x_q|h_q^{start}) \quad (7.68)$$

$$\propto p(y|h_q^{start}) p_{prompt}(x_q|h_q^{start}) \quad (7.69)$$

$$\arg max_y p_{prompt}(z|x_q, y) = \arg max_y \sum_{h_q^{start}\in H} p_{prompt}(z|h_q^{start}, \phi^*) p_{prompt}(y|x_q, h_q^{start}) \quad (7.70)$$

$$= \arg max_y p(y|x_q, h_q^{start}), \quad (7.71)$$

其中 `y` 的变化不影响 `p_{prompt}(z|h_q^{start})` 的量。由于：

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.72)$$

$$p_{prompt}(y|x_q) = \sum_{h_q^{start}\in H} p_{prompt}(y|h_q^{start}, x_q) p_{prompt}(h_q^{start}|x_q), \quad (7.73)$$

很容易发现：

$$\arg max_y p_{prompt}(y|x_q) = \arg max_y p(y|x_q, h_q^{start}) \quad (7.74)$$

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.75)$$

因此，当 `n \to \infty` 时：

$$p(z|S_n, x_q, \phi^*) = \arg max_y p_{prompt}(z|x_q, y) \quad (7.76)$$

引理 6 和定理 23 表明，给定 `x_q`，如果 `p_{prompt}(y|x_q)` 为真实标签，则上下文预测器可以识别该类别。

## 7.4 V 的下界

回想：

$$p(x_q, y|h_q^{start}, S_n, \phi^*) = \frac{p(y|S_n, x_q, h_q^{start}, \phi^*)p(x_q|h_q^{start})}{p(x_q, y)} \quad (7.77)$$

由于 `y` 的变化不影响 `p(z|h_q^{start})`，因此在等式两边应用 argmax 以寻找最优的 `y`：

$$\arg max_y p(z|S_n, x_q, y, \phi^*) = \arg max_y \sum_{h_q^{start}\in H} p(z|h_q^{start}) p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.78)$$

$$= \arg max_y p(y|S_n, x_q, h_q^{start}, \phi^*) \quad (7.79)$$

相似地，我们有：

$$p_{prompt}(z|x_q, y) = \sum_{h_q^{start}\in H} p(z|h_q^{start}, \phi^*) p_{prompt}(h_q^{start}|x_q, y), \quad (7.80)$$

$$p_{prompt}(h_q^{start}|x_q, y) = \frac{p_{prompt}(x_q, y) p_{prompt}(h_q^{start})}{p_{prompt}(x_q, y)} \quad (7.81)$$

$$\propto p_{prompt}(x_q|h_q^{start}) \quad (7.82)$$

$$\propto p(y|h_q^{start}) p_{prompt}(x_q|h_q^{start}) \quad (7.83)$$

$$\arg max_y p_{prompt}(z|x_q, y) = \arg max_y \sum_{h_q^{start}\in H} p_{prompt}(z|h_q^{start}, \phi^*) p_{prompt}(y|x_q, h_q^{start}) \quad (7.84)$$

$$= \arg max_y p(y|x_q, h_q^{start}), \quad (7.85)$$

其中 `y` 的变化不影响 `p_{prompt}(z|h_q^{start}, \phi^*)`。由于：

$$p(y|S_n, x_q, \phi^*) = \sum_{h_q^{start}\in H} p(y|h_q^{start}, S_n, x_q, \phi^*) p(h_q^{start}|S_n, x_q) \quad (7.86)$$

$$p_{prompt}(y|x_q) = \sum_{h_q^{start}\in H} p_{prompt}(y|h_q^{start}, x_q) p_{prompt}(h_q^{start}|x_q), \quad (7.87)$$

很容易发现：
