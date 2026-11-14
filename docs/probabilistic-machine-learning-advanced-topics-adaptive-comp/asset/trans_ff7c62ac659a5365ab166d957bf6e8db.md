

后验，其中 $Z_0$ 是先验的归一化常数。为了简化记法，我们令 $f_0(\boldsymbol{\theta}) = p_0(\boldsymbol{\theta})$ 为先验。
我们将近似后验如下：

```
\( q(\boldsymbol{\theta}) = \frac{1}{Z_q} \tilde{q}(\boldsymbol{\theta}), \quad \tilde{q}(\boldsymbol{\theta}) = p_0(\boldsymbol{\theta}) \prod_{k=1}^K \tilde{f}_k(\boldsymbol{\theta}) \)
```

其中 \(\tilde{f}_k \in \mathcal{Q}\) 是近似局部因子，而 \(\mathcal{Q}\) 是指数族中某个可处理的家族，通常是高斯分布 [Gel+14b]。

我们将逐一优化每个 \(\tilde{f}_i\)，保持其他因子固定。我们使用家族 \(\mathcal{Q}\) 中的非信息分布来初始化每个 \(\tilde{f}_i\)。因此 \(q(\boldsymbol{\theta}) = p_0(\boldsymbol{\theta})\)。为了计算新的局部因子 \(\tilde{f}_i^{\text{new}}\)，我们按以下步骤进行。首先，通过从近似后验中除去 \(\tilde{f}_i\) 来计算 **腔分布**：

```
\( q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) = \frac{q(\boldsymbol{\theta})}{\tilde{f}_i(\boldsymbol{\theta})} \propto \prod_{k \neq i} \tilde{f}_k(\boldsymbol{\theta}) \)
```

该除法操作可以通过减去自然参数来实现，如第 2.3.3.2 节所述。腔分布表示除了 \(f_i\) 之外所有因子的效果（\(f_i\) 由 \(\tilde{f}_i\) 近似）。

接下来，我们（概念上）通过将精确因子 \(f_i\) 乘到腔分布上来计算 **倾斜分布**：

```
\( q_i^{\text{tilted}}(\boldsymbol{\theta}) = \frac{1}{Z_i} f_i(\boldsymbol{\theta}) q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) \)
```

其中 \(Z_i = \int q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) f_i(\boldsymbol{\theta}) d\boldsymbol{\theta}\) 是倾斜分布的归一化常数。这是将当前近似（排除因子 \(i\)）与精确的 \(f_i\) 项相结合的结果。

不幸的是，得到的倾斜分布可能超出我们的模型家族（例如，如果我们将高斯先验与非高斯似然相结合）。因此，我们将按以下方式近似倾斜分布：

```
\( q_i^{\text{proj}}(\boldsymbol{\theta}) = \text{proj}(q_i^{\text{tilted}}) \triangleq \underset{\tilde{q} \in \mathcal{Q}}{\text{argmin}} D(q_i^{\text{tilted}} || \tilde{q}) \)
```

这可以看作是将倾斜分布投影到近似家族中。如果 \(D(q_i^{\text{tilted}} || q) = D_{\text{KL}}(q_i^{\text{tilted}} || q)\)，这可以通过矩匹配来完成，如第 5.1.4.2 节所示。例如，假设腔分布是高斯分布，\(q_{-i}^{\text{cavity}}(\boldsymbol{\theta}) = \mathcal{N}_c(\boldsymbol{\theta}|\mathbf{r}_{-i}, \mathbf{Q}_{-i})\)，使用规范参数化。那么倾斜分布的对数由以下给出：

```
\(\log q_i^{\text{tilted}}(\boldsymbol{\theta}) = \alpha \log f_i(\boldsymbol{\theta}) - \frac{1}{2} \boldsymbol{\theta}^\top \mathbf{Q}_{-i} \boldsymbol{\theta} + \mathbf{r}_{-i}^\top \boldsymbol{\theta} + \text{const}\)
```

让 \(\hat{\boldsymbol{\theta}}\) 成为该目标的局部最大值。如果 \(\mathcal{Q}\) 是高斯分布的集合，我们可以计算投影倾斜分布为具有以下参数的高斯分布：

```
\(\mathbf{Q}_{\backslash i} = -\nabla_{\boldsymbol{\theta}}^2 \log q_i^{\text{tilted}}(\boldsymbol{\theta})|_{\boldsymbol{\theta}=\hat{\boldsymbol{\theta}}}, \quad \mathbf{r}_{\backslash i} = \mathbf{Q}_{\backslash i} \hat{\boldsymbol{\theta}}\)
```

![](img/ca72c1626f4850f058a9edc138c1ac73_505_0.png)

图 10.15：将逻辑似然因子 \(f_i = p(y_i|\theta)\) 与腔先验 \(q_{-i}^{cavity} = g_{-i}(\theta)\) 相结合，以得到倾斜分布 \(q_i^{tilted} = p(y_i|\theta)g_{-i}(\theta)\)。改编自 [Gel+14b] 的图 2。

这被称为 **拉普拉斯传播** [SVE04]。对于更一般的分布，我们可以使用蒙特卡洛近似；这被称为 **黑盒 EP** [HL+16a; Li+18c]。最后，我们计算一个局部因子，如果与腔分布相结合，将产生与此投影分布相同的结果：

```
\(\tilde{f}_i^{new}(\theta) = \frac{q_i^{\text{proj}}(\theta)}{q_{-i}^{\text{cavity}}(\theta)}\) (10.198)
```

我们可以看到 \(q_{-i}^{\text{cavity}}(\theta)\tilde{f}_i^{new}(\theta) = q_i^{\text{proj}}(\theta)\)，因此将这个近似因子与腔分布相结合，得到的分布是使用精确因子的结果在 \(\mathcal{Q}\) 范围内的最佳可能近似。

## 10.7.2 示例

图 10.15 说明了将非常非高斯的似然 \(f_i\) 与高斯腔先验 \(q_{-i}^{\text{cavity}}\) 相结合，以产生近似高斯的倾斜分布 \(q_i^{tilted}\) 的过程，随后可以使用投影将其近似为高斯分布。

因此，我们不再试图孤立地对每个似然项 \(f_i\) 进行 "高斯化"（例如在 EKF 中所做的那样），而是试图找到最佳局部因子 \(\tilde{f}_i\)（在某个家族内），当它与所有其他项（由腔分布 \(q_{-i}\) 表示）相结合时，能产生与使用精确因子 \(f_i\) 大致相同的效果。也就是说，我们选择一个在所有其他因子的上下文中效果良好的局部因子。

## 10.7.3 EP 作为广义 ADF

我们可以将 EP 视为第 8.6 节讨论的 ADF 算法的推广。ADF 是一种序列贝叶斯推断形式。在每一步，它维护后验的可处理近似 \(q_t(\mathbf{z}) \in \mathcal{Q}\)，使用下一次观测的似然 \(\hat{p}_{t+1}(\mathbf{z}) \propto q_t(\mathbf{z})p(\mathbf{x}_t|\mathbf{z})\) 对其进行更新，然后使用 \(q_{t+1} = \text{argmin}_{q \in \mathcal{Q}} D_{\text{KL}}(\hat{p}_{t+1} || q)\) 将更新后的后验投影回可处理家族。ADF 在所需方向上最小化 KL。然而，它是一个为在线设置设计的序列算法。在批处理设置中，该方法可能会根据更新执行的顺序给出不同的结果。此外，如果对数据进行多次遍历，我们会多次包含相同的似然项，导致过度自信的后验。EP 解决了这个问题。

## 10.7.4 优化问题

在实践中，EP 可能在数值上不稳定。例如，如果我们将高斯分布用作局部因子，在减去自然参数时可能会得到负方差。为了降低这种可能性，通常使用阻尼，即以步长 \(\delta\) 对每个因子进行部分更新。更准确地说，我们将最后一步更改为以下内容：

```
\(\tilde{f}_i^{\text{new}}(\theta) = \left( \tilde{f}_i(\theta) \right)^{1-\delta} \left( \frac{q_i^{\text{proj}}(\theta)}{q_{-i}^{\text{cavity}}} \right)^\delta\) (10.199)
```

这可以通过将自然参数按 \(\delta\) 缩放来实现。[ML02] 建议将 \(\delta = 1/K\) 作为一种安全策略（其中 \(K\) 是因子的数量），但这会导致收敛非常缓慢。[Gel+14b] 建议从 \(\delta = 0.5\) 开始，然后在 \(K\) 次迭代中逐步减少到 \(\delta = 1/K\)。

除了数值稳定性之外，EP 在其原生形式下没有收敛保证，尽管经验上它可以很好地工作，特别是对于对数凹因子 \(f_i\)（例如在 GP 分类器中）。

## 10.7.5 幂 EP 和 \(\alpha\)-散度

在近似倾斜分布时，我们也可以选择使用什么差异度量 \(D(q_i^{\text{tilted}}\|q)\)。如果使用 \(D_{\text{KL}}(q_i^{\text{tilted}}\|q)\)，我们将恢复经典 EP，如上文所述。如果使用 \(D_{\text{KL}}(q\|q_i^{\text{tilted}})\)，我们将恢复标准变分推断中使用的反向 KL。我们可以通过使用 \(\alpha\)-散度（第 2.7.1.2 节）来推广上述结果，这使我们能够在模式搜索和模式覆盖行为之间进行插值，如图 2.20 所示。我们可以使用 [Min04] 的 **幂 EP** 方法来优化 \(\alpha\)-散度。

从算法上讲，这是对常规 EP 的一个相当小的修改。特别是，我们首先计算腔分布 \(q_{-i}^{\text{cavity}} \propto \frac{q}{f_i^\alpha}\)；然后近似倾斜分布 \(q_i^{\text{proj}} = \text{proj}(q_{-i}^{\text{cavity}} f_i^\alpha)\)；最后计算新的因子

```
\(\tilde{f}_i^{\text{new}} \propto \left( \frac{q_i^{\text{proj}}}{q_{-i}^{\text{cavity}}} \right)^{1/\alpha}\) .
```

## 10.7.6 随机 EP

EP 在大数据环境中的主要缺点是，我们需要存储每个数据点 \(n\) 的 \(\tilde{f}_n(\theta)\) 项，以便计算腔分布。如果 \(\theta\) 有 \(D\) 个维度，并且我们使用完整协方差高斯分布，这需要 \(O(ND^2)\) 的内存。

**随机 EP** [LHLT15] 的思想是使用一个共享因子来近似局部因子，该因子充当聚合似然，即：

```
\(\prod_{n=1}^N f_n(\theta) \approx \tilde{f}(\theta)^N\) (10.200)
```

