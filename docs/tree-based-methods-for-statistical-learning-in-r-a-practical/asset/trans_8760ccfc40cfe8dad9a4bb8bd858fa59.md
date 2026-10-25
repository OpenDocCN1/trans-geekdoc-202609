

![](img/2c227bfb3620dc3d159fa5e6598afa30_157_0.png)

图 3.9：酒质评分对酒精体积含量（左）、挥发性酸度（中）和硫酸钾水平（右）的部分依赖。

```r
library(survival)

# Prep the data a bit
pbc2 <- pbc[!is.na(pbc$trt), ] # use randomized subjects
pbc2$id <- NULL # remove ID column
# Consider transplant patients to be censored at day of transplant
pbc2$status <- ifelse(pbc2$status == 2, 1, 0)
facs <- c("sex", "spiders", "hepato", "ascites", "trt", "edema")
for (fac in facs) { # coerce to factor
  pbc2[[fac]] <- as.factor(pbc2[[fac]])
}
```

如第 1.4.9 节简要讨论的那样，生存（或可靠性）分析关注寿命的分布，通常是指人类、动物或机器部件的寿命。生存分析中的响应变量是时间至事件，例如，时间至死亡或再入院（例如，用于比较两种药物的随机临床试验受试者）或机器中某个部件失效的时间（例如，运行中的电机）。

图 1.11 给出了对照组和治疗组（即药物组）生存函数的 Kaplan-Meier 估计。与所有生存曲线一样，生存概率随时间降低。通常我们不太关注总体生存曲线，而是关注其在组间的差异。在本示例中，我们的目标是查看额外协变量是否可用于有效区分具有不同生存分布的组。

Loh [2014] 提供了树结构生存模型的概述。CTree 采用的方法相当直接。随访时间（time）和事件指示器（status）被合并为单个数值响应，并视为单变量连续；因此，前面讨论的技术直接适用。在 CTree 中，右删失数据使用 coin 包中的 logrank_trafo() 函数转换为秩和检验得分；也就是说，影响函数 h() 将右删失生存时间转换为秩和检验得分。

为说明这一点，让我们检验预测因子 bili（血清胆红素（mg/dl））与响应的秩和检验得分之间总体独立性的原假设：

```r
library(coin)
```

```r
independence_test(Surv(time, status) ~ bili, data = pbc2,
  teststat = "quadratic")
```

```
#>
#> Asymptotic General Independence Test
#>
#> data: Surv(time, status) by bili
#> chi-squared = 77, df = 1, p-value < 2e-16
```

```
# Our 'gi.test()' function from earlier should also work
```

```r
lr.scores <- coin::logrank_trafo(Surv(pbc2$time, pbc2$status))
```

```r
gi.test(pbc2$bili, y = lr.scores)
```

```
#>
#> chisq pval
#> 77.5 0.0
```

使用 alpha = 0.05，我们将拒绝原假设（p < 0.001）并得出结论：血清胆红素水平与生存率相关。但这除此之外没能告诉我们太多。血清胆红素水平较高的受试者是否倾向于生存更长时间？要回答此类问题，我们可以使用 CTree，通过每个特征与秩和检验得分之间的基于条件推断的独立性检验，递归地划分数据：

```r
(pbc2.ct <- partykit::ctree(Surv(time, status) ~ ., data = pbc2))
```

```
#>
#> Model formula:
#> Surv(time, status) ~ trt + age + sex + ascites + hepato + spiders +
#> edema + bili + chol + albumin + copper + alk.phos + ast +
#> trig + platelet + protime + stage
#>
#> Fitted party:
#> [1] root
#> |   [2] bili <= 1.9
#> |   |   [3] edema in 0
#> |   |   |   [4] stage <= 2: Inf (n = 61)
#> |   |   |   [5] stage > 2: 4191 (n = 104)
#> |   |   [6] edema in 0.5, 1: Inf (n = 16)
#> |   |   [7] bili > 1.9
#> |   |   [8] protime <= 11.2
#> |   |   |   [9] age <= 44.5
#> |   |   |   |   [10] bili <= 5.6: 3839 (n = 29)
#> |   |   |   |   [11] bili > 5.6: 1080 (n = 7)
#> |   |   |   [12] age > 44.5: 1487 (n = 45)
#> |   |   |   [13] protime > 11.2
#> |   |   |   |   [14] albumin <= 3.6: 597 (n = 43)
#> |   |   |   |   [15] albumin > 3.6: 2540 (n = 7)
#>
#> Number of inner nodes:  7
#> Number of terminal nodes: 8
```

请注意，治疗组（药物）在任何节点均未被选为分割变量。这并不奇怪，因为 Fleming 和 Harrington [1991, p. 2] 得出结论：服用安慰剂者与服用药物者的生存时间之间没有实际显著差异。

我们还可以使用 `plot()` 方法显示树图；结果显示在图 3.10 中。对于删失结果，每个节点中显示生存曲线的 Kaplan-Meier 估计。图 3.10 中的树图清楚地表明，血清胆红素水平较高的受试者往往生存时间较短。你还能从树图中得出哪些其他结论？

```r
plot(pbc2.cit) # Figure 3.10
```

## 3.6 最后的想法

CTree 是过去二十年递归划分中更重要的发展之一；其他重要发展在第 4 章以及本书的在线补充中讨论。总结一下，与 CART 相比，CTree：

- 使用调整后的统计检验分别确定每个节点的分割变量和分割点（CART 只是使用穷举搜索）；
- 提供无偏的分割变量选择；
- 不需要剪枝（或大量调参）；
- 可以自然地考虑数据的性质——例如，当变量为任意类型时（例如，多变量、有序、右删失等）。

如果 CTree 在准确性方面与 CART 相当，不需要后剪枝，并提供无偏的分割变量选择，那么 CART 为何仍然如此流行？如 Loh [2014] 的答复中所指出的，“这似乎与第三种不良影响相关：许多提出或应用树算法的作者要么不了解，要么选择忽略该领域的类似工作。即使是近期的论文也不引用 2000 年以后的工作，因此忽略了十多年来可能高度相关的积极发展。” 另一个重要因素是软件可用性。许多树算法没有易于使用的开源实现。例如，在 Rusch 和 Zeileis 考虑的 99 种树算法中（参见 Loh [2014] 末尾的讨论），大约三分之一有免费开源实现可用（包括 CART 和 CTree）。类 CART 的决策树也在各种开源平台上广泛实现（参见第 2.9 节）。另一方面，据我所知，CTree 仅在 R 中可用。

使用类 CART 的决策树时，你应该担心变量选择偏差吗？当然应该。然而，如 Loh [2014] 的答复中所指出的，“……在某些情况下，如果树模型用于预测而非解释，选择偏差可能不会造成严重危害。” 虽然有偏的变量选择可能导致在无关特征上出现更多虚假分割，但如果样本量较大且此类变量不太多，使用交叉验证进行剪枝通常能有效移除它们。

![](img/2c227bfb3620dc3d159fa5e6598afa30_161_0.png)

图 3.10：应用于 Mayo Clinic PBC 数据子集的条件推断树。终端节点使用生存函数的 Kaplan-Meier 估计进行总结。树图突出了与不同生存分布相关的潜在风险因素。

Taylor & Francis
Taylor & Francis Group
http://taylorandfrancis.com

## 现代决策树的携带者指南 GUIDE

> 在我们可能撞到的所有树中，偏偏撞到了一棵会还击的树。
>
> J.K. Rowling
> 《哈利·波特与密室》

本章介绍了一种强大但似乎鲜为人知的决策树算法，用于 _广义、无偏、交互检测与估计_（GUIDE），该算法由 Loh [2002, 2009] 提出。不幸的是，与具有易于使用的开源实现的其他算法（如 CART（例如 **rpart**）和 CTree（例如 **partykit**））相比，GUIDE 在从业者和研究人员中似乎采用率要低得多。

与 CTree 类似，GUIDE 基于统计假设检验，力求实现无偏的分割变量选择。特别是，GUIDE 专门设计用于解决三个可能对决策树可解释性产生不利影响的问题：

- 1) 分割变量选择偏差；
- 2) 对局部交互不敏感；
- 3) 树结构过于复杂（例如，第 97 页图 2.23 中的 Ames 房价回归树）。

