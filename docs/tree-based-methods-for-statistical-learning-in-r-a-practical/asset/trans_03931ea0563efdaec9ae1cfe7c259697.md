

```r
pred[highest]
#> 433
#> 503
```

```r
# fastshap needs to know how to compute predictions from your model
pfun <- function(object, newdata) predict(object, newdata = newdata)
```

```r
# Need to supply feature columns only in fastshap::explain()
X <- subset(ames.trn, select = -Sale_Price) # feature columns only
newx <- ames.tst[highest, names(X)]
```

```r
# Compute feature contributions for observation with highest prediction
set.seed(1434) # for reproducibility
ex <- explain(ames.bag, X = X, nsim = 100, newdata = newx,
pred_wrapper = pfun, adjust = TRUE)
ex[1, 1:5] # peek at a few
```

```
#> # A tibble: 1 x 5
#>   MS_SubClass MS_Zoning Lot_Frontage Lot_Area Street
#>   <dbl> <dbl> <dbl> <dbl> <dbl>
#> 1 0.930 0.0275 0.472 3.80 0
```

```r
autoplot(ex, type = "contribution", num_features = 10,
feature_values = newx)
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_240_0.png)

图 6.6：来自艾姆斯房价袋装树集成的最高训练预测的前十个（基于 Shapley 的）特征贡献。

接下来，我将使用 fastshap 和 R = 50 次蒙特卡洛重复为 Gr_Liv_Area 构建一个 Shapley 依赖图。结果显示在图 6.2 中。与图 6.2 和 6.4 一样，预测售价倾向于随地上方形面积的增加而增加。与图 6.4 中的 c-ICE 曲线一样，图中日益增加的离散程度表明与至少一个其他特征存在潜在交互作用。如果你知道要找什么，按另一个特征的值对 Shapley 依赖图进行着色可以帮助可视化这种交互作用。

```r
ex <- explain(ames.bag, feature_names = "Gr_Liv_Area", X = X,
nsim = 50, pred_wrapper = pfun)
```

```r
# Shapley dependence plot
autoplot(ex, type = "dependence", X = X, alpha = 0.3)
```

![](img/2c227bfb3620dc3d159fa5e6598afa30_241_0.png)

图 6.7：预测售价对地上方形面积的 Shapley 依赖。

### 6.4 现有方法的缺点

如 Hooker 等人 [2019] 所讨论，置换-预测方法——如部分依赖图（PD 图）、ICE 图和置换重要性——可能会产生高度误导的结果。例如，计算基于置换的 VI 分数的标准方法涉及独立地置换单个特征。这隐含地假设观察到的特征在统计上是独立的。然而，在实践中，特征通常并不独立，这可能导致荒谬的 VI 分数。缓解此问题的一种方法是使用 Strobl 等人 [2008b] 中描述的条件方法；Hooker 等人 [2019] 提供了其他替代方案，例如置换-重学习重要性。不幸的是，据我所知，此方法尚未用于通用目的。类似的修改可以应用于部分依赖图 [Parr and Wilson, 2019]。

我已经提到，在存在强交互作用效应时，部分依赖图可能会产生误导。如前所述，可以通过改用 ICE 图来缓解这一问题。另一种替代方案是使用累积局部效应（ALE）图 [Apley and Zhu, 2020]。与部分依赖图相比，ALE 图的优势在于计算更快，且较少受特征间强依赖的影响。然而，缺点是 ALE 图的实现更复杂。ALE 图可在 R 的 ALEPlot [Apley, 2018] 和 iml 包中使用。

Hooker [2007] 还认为，特征重要性（仅涉及主效应）在高维环境中可能会产生误导，尤其是当特征之间存在强依赖和交互作用效应时，并建议采用基于广义功能 ANOVA 分解的方法——然而，据我所知，此方法在开源软件中尚未广泛实现。

### 6.5 最后的想法

可解释机器学习（IML）正在兴起，与 IML 相关的开源软件也是如此。一个章节中要讨论的方法和有用的包实在太多，因此我只涉及了其中一小部分。如果您想了解更多，我建议从 Patrick Hall 托管的 IML awesome 列表开始：

https://github.com/jphall663/awesome-machine-learning-interpretability.

R 用户的一个好资源是 Maksymiuk 等人 [2021]。当然，Molnar [2019] 是一个免费可用的资源，包含直观的解释以及 R 和 Python 中相关软件的链接。Molnar 等人 [2021] 也值得一读，因为他们讨论了在使用模型无关的解释方法时需要注意的一些陷阱。

## 泰勒与弗朗西斯
泰勒与弗朗西斯集团
http://taylorandfrancis.com

## 随机森林

> 在一棵有十万棵树的森林里，没有两片叶子是相同的。
> 没有两段沿同一路径的旅程是相同的。
>
> Paulo Coelho

### 7.1 简介

随机森林（RF）本质上是带有额外变化的袋装树集成，在表格数据上，它们往往能提供与许多最先进的监督学习算法相似的准确性，同时相对较不难调参。换句话说，RF 开箱即用往往具有竞争力。但请注意，RF——像任何统计和机器学习算法一样——有其自身的缺点。正如我们在本章中将看到的，RF 还包含许多花哨的功能，数据科学家可以利用这些功能进行非预测任务，例如检测异常/离群值、填补缺失值等等。

### 7.2 随机森林算法

请回顾，袋装树集成（第 5.1 节）由数百（有时数千）棵独立生长的决策树组成，每棵树都在原始训练数据的不同自助样本上进行训练。每棵树都被有意地生长得很深（低偏差），并通过对集成中所有树的预测进行平均来减少方差。对于分类，使用单个树之间的相对多数投票。

不幸的是，相关性限制了平均值的方差降低效果。请参考以下示例进行说明。假设 $\{X_i\}_{i=1}^N \stackrel{iid}{\sim} (\mu, \sigma^2)$ 是来自某个分布的随机样本，均值为 $\mu$，方差为 $\sigma^2$。令 $\bar{X} = \sum_{i=1}^N X_i / N$ 为样本均值。如果观测值是独立的（如随机样本的通常标注），则 $\text{E}(\bar{X}) = \mu$ 且 $\text{V}(\bar{X}) = \sigma^2 / N$。换句话说，平均值的方差小于样本元素的方差。这当然假设 $X_i$ 之间不相关。如果任意两个观测值之间的成对相关性为 $\rho = \rho(X_i, X_j) (i \neq j)$，则

$$ \text{V}(\bar{X}) = \rho \sigma^2 + \frac{1-\rho}{N} \sigma^2, $$

当 $N \to \infty$ 时，这将收敛于 $\rho \sigma^2$。换句话说，无论样本量如何，相关性都限制了平均值的方差降低效果。图 7.1 对此进行了说明，其中每个箱线图均由 30,000 个样本均值构成，每个样本均值均基于大小为 $N = 30$ 的来自指定中心高斯分布且具有指定成对相关性（x 轴）的样本；请注意，当我们从 $\rho = 0$ 到 $\rho = 1$（从左到右）时，样本均值的变异性会增加。

![](img/2c227bfb3620dc3d159fa5e6598afa30_246_0.png)

图 7.1：来自大小为 $N = 30$ 的样本的 100 个模拟平均值，成对相关性从零增加到一。

同样，对一组相关预测器（即产生相似预测的模型）进行袋装只能将方差降低到一定程度。由于每棵树都是使用原始训练数据的独立自助样本构建的，袋装集成中的树之间会存在一定的相关性。如果我们能降低树之间的相关性，树将更加多样化，平均值可以进一步提高集成的预测和泛化性能。

图 7.2 显示了应用于电子邮件垃圾邮件训练数据的六棵袋装决策树；每棵树的最大深度均限制为三，以帮助可视化。由于每棵树都是从同一训练集的独立自助样本中诱导出来的，树之间自然非常相似。例如，请注意，终端节点 15（以绿色突出显示）的路径在六棵树中有四棵是相同的，尽管分割点略有不同。如果我们能使树更加多样化，组合集成的性能可能会得到改善。

![](img/2c227bfb3620dc3d159fa5e6598afa30_247_0.png)

图 7.2：应用于电子邮件垃圾邮件训练数据的六棵袋装决策树。每棵树中都突出显示了通往终端节点 15 的路径。

幸运的是，Leo Breiman 和 Adele Cutler 想出了一种在袋装树集成中降低相关性的巧妙方法；也就是说，使树更加多样化。其思路是将树中每个节点的潜在分割变量限制为可用预测器的一个随机子集，这通常会产生一个更加多样化的树集成。本质上，袋装通过有放回抽样在行中引入随机性来构建多样化的树集成，而随机森林还通过对特征进行子采样在列中引入随机性，从而进一步提高树的多样性。

