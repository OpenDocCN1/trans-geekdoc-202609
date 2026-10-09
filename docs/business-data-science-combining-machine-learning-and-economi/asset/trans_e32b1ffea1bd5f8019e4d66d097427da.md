
...场景）。然而，在高维问题中，极大似然估计（MLE）可能是一个糟糕的模型估计（或者在参数数量多于观测数量的情况下，它甚至可能不存在）。在实践中，我建议从一个比全样本 Lasso 偏差更小、但实际上不是零偏差估计的模型中进行模拟。关于如何做到这一点没有硬性规则，但在我实践中行之有效的一个指导原则是：取全样本 AICc 或交叉验证最小值（CV-min）选定的惩罚项——设为 $\hat{\lambda}$——然后在用于生成数据的模型拟合中，使用大小约为其 25% 的惩罚项，即 $\overline{\lambda} \approx \hat{\lambda}/4$。然而，在实际应用中，你应该考虑对此选择的敏感性，并将其与稍后讨论的替代子抽样程序进行比较。

再次强调，由于 Lasso 是有偏估计量，你应该直接针对置信区间，而不是通过标准误差估计来针对置信区间。这与算法 2 中关于置信区间自举的讨论平行：你需要量化自举估计与原估计量之间的差异，以及它们是否存在高估或低估的偏差。完整流程详见算法 9。

## 算法 9 用于 Lasso 置信区间的参数化自举

你拥有数据 $\{[\mathbf{x}_i, y_i]\}_{i=1}^{n}$，以及在惩罚项 $\hat{\lambda}$（例如通过 AICc 或 CV-min 规则选定）下的全样本 Lasso 系数估计 $\hat{\boldsymbol{\beta}}$。

通过似然最大化（适用于低维情况）或使用较小惩罚项 $\overline{\lambda} \approx \hat{\lambda}/4$ 的 Lasso，获得低/无惩罚项估计 $\overline{\boldsymbol{\beta}}$。然后，对于 $b=1\dots B$：

- 从由 $\overline{\boldsymbol{\beta}}$ 参数化的拟合回归模型中生成 $n$ 个响应观测值 $\{y_{i}^{b}\}_{i=1}^{n}$，并使用样本协变量 $\{\mathbf{x}_{i}\}_{i=1}^{n}$。例如，在线性回归中，生成

$$ y_{i}^{b} \sim \mathrm{N} \left(\mathbf{x}_{i}^{\prime} \overline{\boldsymbol{\beta}}, \overline{\sigma}^{2}\right), \tag{3.8} $$

其中 $\overline{\sigma}^{2}$ 是对应于 $\overline{\boldsymbol{\beta}}$ 拟合的残差方差。

- 使用与估计 $\hat{\boldsymbol{\beta}}$ 时相同的惩罚项选择算法，在数据 $\{[\mathbf{x}_{i}, y_{i}^{b}]\}_{i=1}^{n}$ 上获得你的自举系数估计 $\overline{\boldsymbol{\beta}}_{b}$。

要获得系数的某个函数——设为 $f(\beta)$——的 $\alpha\%$ 置信区间（CI），你随后计算误差 $\{f(\hat{\beta}_b)-f(\hat{\boldsymbol{\beta}})\}_{b=1}^{B}$ 的 $\alpha/2$ 和 $1-\alpha/2$ 百分位数——设为 $\alpha/2$ 和 $t_{1-\alpha/2}$——并按如下设置你的区间：

$$[f(\hat{\boldsymbol{\beta}})-t_{1-\alpha/2}, f(\hat{\boldsymbol{\beta}})-t_{\alpha/2}]. \qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad\qquad (3.9)$$

回想我们的曲棍球例子。从图 3.11 的右面板可以看出，AICc 选定的惩罚权重是 $\hat{\lambda} \approx \exp[-9]$。我们将对同一路径上较小惩罚项的模型拟合运行参数化自举，$\hat{\lambda} \approx \exp[-11.25]$。为了从这个拟合模型中生成数据，我们首先获得对应于此 $\hat{\boldsymbol{\beta}}$ 的二项分布概率。

```r
> log(nhlreg$lambda[61])
> Q1open <- drop(predict(nhlreg, x, select=61, type="response"))
```

然后，我们可以使用 `rbinom` 函数生成新的 0/1 响应值，以指示在自举样本中每个进球是由客队还是主队打进的。

由于运行每次 Lasso 拟合的时间成本，我们将运行相对较少次数的算法 9 迭代，$B = 100$。

```r
> Bhat <- coef(nhlreg)
> Bparboot <- sparseMatrix(dims=c(nrow(Bhat),0),i={},j={})
> B <- 100
> for(b in 1:B){
+   yb <- rbinom(nrow(x), Q1open, size=1)
+   fitb <- gamlr(x, yb,
+       free=1:(ncol(config)+ncol(team)),
+       family="binomial", standardize=FALSE)
+   Bparboot <- cbind(Bparboot, coef(fitb)) }
```

生成的矩阵 $B_{\text{parboot}}$ 是 $\hat{\boldsymbol{\beta}}_{b}$ 系数估计（在 AICc 惩罚项选择下获得）的 $p \times B$ 样本。你可以应用公式 3.9 来针对任何特定系数获得 90% 区间。例如，你可能想知道由于 Sidney Crosby 带来的进球几率倍增器的 90% 置信区间。由于这是逻辑回归，球员 $i$ 的几率倍增器为 $f(\boldsymbol{\beta})=e^{\beta i}$。

```r
> # try other players too
> WHO <- "SIDNEY_CROSBY"
> fB <- exp(Bhat[WHO,])
> tval <- quantile(exp(Bparboot[WHO,]), c(.95,.05))
> 2*fB - tval
      95%     5%
1.383667 1.786985
```

我们发现，Crosby 在场时，企鹅队（Penguins）进球的几率增加了 $38\%$ 到 $79\%$ 之间。我们还可以为上一小节末尾计算的主场优势提供不确定性界限。

```r
> fB <- exp(coef(nhlreg)[1,])
> tval <- quantile (exp(Bparboot[1,]), c(.95,.05))
> 2*fB - tval
      95%     5%
1.068819 1.096128
```

在其他条件相同的情况下，主队进球的概率比客队进球的概率高出 $6\%$ 到 $10\%$。

参数化自举的缺点在于它严重依赖于你所假设的数据生成过程的正确性。例如，如果你在处理线性 Lasso，你需要从高斯分布中生成新误差，通常具有恒定的方差，因此假设算法 9 中的方程 3.8 模型*完全*成立。在实践中，即使你不相信该模型真实成立，你也经常使用线性 Lasso 进行回归估计。与最小二乘法（OLS）的情况一样，即使例如误差是异方差且每个观测值都有自身的方差 $\sigma_i$，线性建模也可以给出 $\boldsymbol{\beta}$ 的良好估计。然而，如果你在这种错误设定的情况下应用参数化自举，它可能会给出严重不准确的估计不确定性（通常是低估）。

### 子抽样提供了一种自举的替代方案

非参数自举不适用于模型选择，因为无放回抽样中的重复观测使得预测看起来人为容易。在子抽样（subsampling）中$^{12}$，你改为使用 $B$ 个大小为 $m$ 的*无放回*子样本重新估计你的目标，其中 $m$ 小于全样本大小 $n$。理想情况下，这些子样本没有重叠。例如，你会将数据分成大约 $B = n/m$ 折，并在每个独立折上获得参数。然而，你需要同时使 $B$ 足够大以获得抽样分布的良好视图，并使 $m$ 足够大以获得类似于全样本结果的估计量行为。例如，在 Lasso 问题中，$m$ 不能小得使子样本估计中的所有系数都被设为零。但也许只有当 $m \geq n/5$ 时才会发生这种情况，并且你需要超过 $B = 5$ 个子样本估计才能获得合理的置信区间。

在实践中，你应该选择尽可能大的 $B$，受限于你的计算时间$^{13}$，并选择尽可能小的 $m$，使得你的估计例程仍然给出看起来合理的点估计。后一项建议是主观的；我使用 $m \approx n/4$ 作为经验法则，但你需要调整这个数字，以确保你的区间不会对其取值过于敏感。

与自举算法类似，你的估计在不同子集之间的变异性可用于建模全样本估计量的抽样变异性。但与无参数自举不同的是，每个子样本估计是基于大致独立的数据。因此，子抽样在自举失败的环境中有效（例如 Lasso 估计和模型选择之后）。

子抽样的问题在于，你的每个估计基于的样本比你实际拥有的样本更小。因此，子抽样算法要求你假设一个*学习率*，允许你将大小-$m$ 样本的不确定性调整为你的大小-$n$ 样本估计。学习率定义了你的标准误差随样本大小减小的速度。例如，在常见的均值估计设定中，你使用样本均值 $\bar{x}_n = (1/n) \sum_i x_i$ 作为真实均值 $\mathbb{E}[x]$ 的估计量（其中 $n$ 下标表示依赖于样本大小），并且这个估计量具有标准误差

$$\text{se}(\bar{x}_n) = \sqrt{\frac{\text{var}(\bar{x})}{n}}. \qquad\qquad (3.10)$$

在这里，我们会说学习率是 $\sqrt{n}$：因为 var(x) 是一个常量，标准误差随样本大小的平方根减小。例如，假设你有 $\bar{x}_m$，即较小大小-$m$ 的均值
