

11. 请注意，此处的 $X$ 包含截距项。
12. Halbert White. 异方差一致性协方差矩阵估计量以及异方差的直接检验方法。*Econometrica: Journal of the Econometric Society*, 页码 817–838, 1980.
13. Dale J Poirier. 基于知情贝叶斯自助法的异方差一致性协方差估计量的贝叶斯解释。*Econometric Reviews*, 30(4): 457–468, 2011.

![](img/315929ad4bddd26368466d02e06e2385_108_0.png)

## 正则化

在高维场景中，即模型中包含许多可能的信号时，你需要谨慎地选择最适合预测*未来*数据的最佳模型，以避免过拟合。为此，你首先使用能产生一系列候选模型的方法。然后，你在这些候选模型中进行选择，以最小化预测新数据时的误差率估计。本章介绍了此类高维建模的关键工具。

### 样本外表现

在前一章中，我们引入了*偏差*（deviance）作为衡量模型拟合训练数据紧密程度的指标。当你将模型应用于预测和决策时，你实际上并不关心*样本内*偏差。真正重要的是*样本外*（OOS）偏差；换言之，你的模型拟合*新*数据的难度如何？

你真正关心的唯一 $R^2$ 是样本外 $R^2$。*样本内*与*样本外* $R^2$ 之间的区别在于用于拟合 $\hat{\beta}$ 的数据以及计算偏差所用的数据不同。假设你拥有数据 $[x_1, y_1] \ldots [x_n, y_n]$，并使用这些数据在线性回归中拟合 $\hat{\beta}$。那么样本内偏差为：

$$
\text{dev}_{IS}(\hat{\beta}) = \sum_{i=1}^{n}(y_i - x_i^t \hat{\beta})^2 \tag{3.1}
$$

对于样本外 $R^2$，$\hat{\beta}$ 是相同的（仍然使用观测值 $1 \ldots n$ 拟合），但偏差现在是在新的观测值上计算的；例如：

$$
\text{dev}_{OOS}(\hat{\beta}) = \sum_{i=n+1}^{n+m}(y_i - x_i^t \hat{\beta})^2 \tag{3.2}
$$

这一区别至关重要。当拥有大数据和大量输入时，很容易对训练数据过拟合，导致模型受到噪声的驱动，而这些噪声在未来观测中不会重现。这会给你的预测增加误差，并且过拟合模型可能比完全没有模型还要差。

举个例子，让我们考虑半导体制造过程中的质量控制数据。这种工业环境涉及许多复杂的操作，容错率极低。生产线沿线有数百个诊断传感器，测量过程中的各种输入和输出。我们的目标是建立一个模型，将传感器数据映射到芯片故障的预测。然后，可以将面临故障风险的芯片标记出来，以便进行进一步的（昂贵的人工）检查。

对于训练数据，我们有 1500 个观测值，每个观测值是一个长度为 200 的诊断信号向量 $x$，以及关于芯片是否故障的二进制数据。¹ 逻辑回归模型则为：

$$
p_i = \text{P}(\text{fail}_i | x_i) = \frac{e^{\alpha + x_i \beta}}{(1+e^{\alpha + x_i \beta})} \tag{3.3}
$$

我们可以使用 R 进行拟合，并利用 glm 计算样本内偏差。²

```r
> full <- glm(FAIL ~ ., data=SC, family=binomial)
Warning message:
glm.fit: fitted probabilities numerically 0 or 1 occurred
> 1 - full$deviance/full$null.deviance
[1] 0.5621432
```

我们可以看到，该回归的 $R^2$ 为 56%——200 个诊断信号解释了故障与成功之间变异的超过一半。注意，由于这是逻辑回归，此 $R^2$ 使用公式 2.24 中的二项分布偏差。

**图 3.1** 展示了我们在半导体回归中对原假设 $\hat{\beta}_k = 0$ 进行检验的 200 个 *p* 值的分布。回顾我们在**第 1 章**中关于错误发现率（FDR）的讨论，来自原假设的 *p* 值服从均匀分布；相比之下，这里我们可以看到零附近有一个峰值（表示有用的诊断信号），而其余部分则分散趋向于 1（很可能是对故障预测无用的信号）。你可以使用 Benjamini – Hochberg 算法来获得一个具有受控错误发现率（FDR；参见**第 1 章**）的更小模型。**图 3.2** 展示了 FDR 为 10% 时的程序。这得出了一个 $\alpha = 0.0122$ 的 *p* 值拒绝阈值，意味着有 25 个显著的回归系数（其中预计有 22 到 23 个是真实信号）。

![](img/315929ad4bddd26368466d02e06e2385_110_0.png)

**图 3.1：** 半导体回归系数 *p* 值的直方图。

![](img/315929ad4bddd26368466d02e06e2385_110_1.png)

**图 3.2：** 半导体 *p* 值的 FDR。位于直线下方的点是在 FDR 为 10% 条件下显著的 25 个 $\hat{\beta}_k$。

我们可以识别出这 25 个显著信号，并仅针对这些变量重新运行 glm，从而得到一个更简约的模型。

```r
> signif <- which (pvals <= 0.0122)
> head (signif) # first 5 of 25
   SIG2 SIG17 SIG19 SIG20 SIG22 SIG24 
    2    17    19    20    22    24
> cutvar <- c("FAIL", names (signif)) # the keepers
> cut <- glm(FAIL ~ ., data=SC[,cutvar], family="binomial")
> 1 - cut$deviance/cut$null.deviance # new in-sample R2
[1] 0.1811822
```

注意，仅使用 25 个信号的 *cut* 模型，其 $R^2_{cut}=0.18$。这远小于 *full* 模型的 $R^2_{full}=0.56$。通常，*样本内* $R^2$ *随着协变量数量的增加而总是增加*。样本内 $R^2$ 正是极大似然估计 $\hat{\beta}$ 被拟合以最大化的目标，因此如果你给 glm 更多的旋钮可以调节（更多的 $\hat{\beta}_k$），它就能为你提供更紧密的拟合。这正是我们为什么不关心样本内 $R^2$ 的原因——仅通过在设计中加入无用变量，就可以让它看起来任意好。真正的问题是，每个模型预测*新*数据的性能如何？

当然，由于你拥有未见过的数据，因此你无法知晓其在未见数据上的表现。然而，你可以通过在训练样本中留出部分数据来评估模型，以此模拟在未预见数据上进行预测的体验。算法 4 详细说明了该实验。

### 算法 4 K 折样本外（OOS）验证

- 给定一个包含 $n$ 个观测值的数据集，$\{[\mathbf{x}_i, y_i]\}_{i=1}^n$：
  - 将数据分割为 $K$ 个大小相等的随机子集（*折*）。
  - 对于 $k = 1 \dots K$：
    - 使用除第 $k$ 折以外的所有数据拟合系数 $\hat{\beta}$。
    - 记录在留出的第 $k$ 折上的 $R^2$。

这将产生 $K$ 个样本外 $R^2$ 值的样本。该样本是你模型在新数据上预测性能分布的一个*估计*。

对于半导体数据，我们可以对 *full* 和 *cut* 回归模型都进行样本外验证。为此，我们首先需要定义一些函数来计算偏差和 *R*²。

```r
> ## pred must be probabilities (0<pred<1) for binomial
> deviance <- function(y, pred, family=c("gaussian", "binomial")){
+         family <- match.arg(family)
+         if(family=="gaussian"){
+               return( sum( (y-pred) ^2 ))
+         }else{
+               if (is.factor(y)){ y <- as.numeric (y)>1 }
+               return( -2*sum( y*log(pred) + (1-y)*log(1-pred)) )
+         }
+ }
>
> ## get null deviance too, and return R2
> R2 <- function(y, pred, family=c("gaussian", "binomial")){
+         fam <- match.arg(family)
+         if (fam=="binomial"){
+               if (is.factor(y)){ y <- as.numeric(y)>1 }
+         }
+         dev <- deviance(y, pred, family=fam)
+         dev0 <- deviance(y, mean(y), family=fam)
+         return (1-dev/dev0)
+ }
```

这些函数可用于线性回归或逻辑回归。在后续章节中，你将使用 R 包函数，这些函数内置了这些偏差计算，但自己编写一次也是很好的练习。接下来，我们将数据划分为折。

