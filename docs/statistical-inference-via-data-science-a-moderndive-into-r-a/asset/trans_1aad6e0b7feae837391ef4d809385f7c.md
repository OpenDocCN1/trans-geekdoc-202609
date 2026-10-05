

# 142
## 5 简单线性回归

```
$life \exp = b_0 + b_{Asia} \cdot \mathbb{1}_{Asia}(x) + b_{Europe} \cdot \mathbb{1}_{Europe}(x)
+ b_{North America} \cdot \mathbb{1}_{North America}(x) + b_{Oceania} \cdot \mathbb{1}_{Oceania}(x)
+ b_{South America} \cdot \mathbb{1}_{South America}(x)
= 66.31 + 8.64 \cdot \mathbb{1}_{Asia}(x) + 13.6 \cdot \mathbb{1}_{Europe}(x)
+ 9.98 \cdot \mathbb{1}_{North America}(x) + 8.11 \cdot \mathbb{1}_{Oceania}(x)
+ 8.92 \cdot \mathbb{1}_{South America}(x)
= 66.31 + 8.64 \cdot 13.6 + 9.98 \cdot 0.81 \cdot 0.81 \cdot 8.92
= 66.31 + 8.64
= 74.95$
```

这正是表 5.7 中亚洲国家的平均预期寿命为 74.9 年。注意“相对于比较基准的偏移量”为 +8.6 年。

再来一个。我们考虑南美洲的一个国家。在这种情况下，南美洲的唯一指标 $\mathbb{1}_{South America}(x)$ 将为 1，而其他指标均为 0，因此：

```
$life \exp = b_0 + b_{Asia} \cdot \mathbb{1}_{Asia}(x) + b_{Europe} \cdot \mathbb{1}_{Europe}(x)
+ b_{North America} \cdot \mathbb{1}_{North America}(x) + b_{Oceania} \cdot \mathbb{1}_{Oceania}(x)
+ b_{South America} \cdot \mathbb{1}_{South America}(x)
= 66.31 + 8.64 \cdot \mathbb{1}_{Asia}(x) + 13.6 \cdot \mathbb{1}_{Europe}(x)
+ 9.98 \cdot \mathbb{1}_{North America}(x) + 8.11 \cdot \mathbb{1}_{Oceania}(x) + 8.92 \cdot \mathbb{1}_{South America}(x)
= 66.31 + 8.64 \cdot 0 + 13.6 \cdot 0 + 9.98 \cdot 0 + 8.92 \cdot 1
= 66.31 + 8.92
= 75.23$
```

这正是表 5.7 中南美洲国家的平均预期寿命为 75.23 年。“相对于比较基准的偏移量”为 +8.9 年。

我们推广了这一思想。如果我们使用具有 $k$ 个可能国家的分类解释变量 $x$ 来拟合回归模型，回归将返回一个截距和 $k-1$ 个“偏移量”。在我们的案例中，由于有 $k=6$ 个大洲，回归模型返回一个对应非洲基准组的截距，以及 $k-1=5$ 个对应亚洲、欧洲、北美、大洋洲和南美洲的偏移量。

在使用分类解释变量时，理解回归表格的输出对于许多经常感到困扰的人来说是一个新课题。解决这些困扰的真正办法是练习、练习、再练习。然而，一旦你熟悉了如何使用分类解释变量建立回归模型，你就可以将许多新变量纳入模型中，因为世界上大量的数据都是分类数据。

## 5.2 单分类解释变量

### 学习检查

(LC5.13) 使用 `lm(gdp_per_capita ~ continent, data = gapminder(2022))` 拟合线性回归，其中 `gdp_per_capita` 是新的结果变量 $y$。从回归系数中获取关于“最佳拟合”线的信息。回归结果与你之前的探索性数据分析结果如何匹配？

(LC5.14) 对于一个具有 4 个层级的分类变量，回归模型将输出多少个“偏移量”或与基准的差异？

- A. 1
- B. 2
- C. 3
- D. 4

### 5.2.3 观测值/拟合值与残差

回第 5.1.3 节，我们定义了以下三个概念：

1. 观测值 $y$，或结果变量的观测值
2. 拟合值 $\hat{y}$，或给定 $x$ 值在回归线上的值
3. 残差 $y - \hat{y}$，或观测值与拟合值之间的误差

我们使用 `modndrive` 包中的 `get_regression_points()` 函数获取了这些值和其他值。但这一次，我们添加了一个参数 `ID = "country"`：这告诉函数使用 `gapminder(2022)` 中的 `country` 变量作为输出中的`标识变量`。这将有助于我们的分析语境化，将值与国家匹配。

```r
regression_points <- get_regression_points(life_exp_model, ID = "country")
regression_points
```

### 表 5.8: 观测值/拟合值（前 10 个）

| country | life_exp | continent | life_exp_hat | residual |
| :--- | :--- | :--- | :--- | :--- |
| Afghanistan | 53.6 | Asia | 74.9 | -21.3 |
| Albania | 79.5 | Europe | 79.9 | -0.4 |
| Algeria | 78.0 | Africa | 66.3 | 11.7 |
| Andorra | 83.4 | Europe | 79.9 | 3.5 |
| Angola | 62.1 | Africa | 66.3 | -4.2 |
| Antigua and Barbuda | 77.8 | North America | 76.3 | 1.5 |
| Argentina | 78.3 | South America | 75.2 | 3.1 |
| Armenia | 76.1 | Asia | 74.9 | 1.2 |
| Australia | 83.1 | Africa | 66.3 | 16.8 |
| Austria | 82.3 | Europe | 79.9 | 2.4 |

观察表 5.8 中的 $y - \hat{y}$ = life\_exp - life\_exp\_hat。这是观测值与预测值的偏差。例如，阿富汗的残差为 $53.6 - 74.9 = -21.3$。

### 学习检查

(LC5.15) 回归中正系数的哪种解释是正确的？

- A. 指基准组。
- B. 它代表基准组。
- C. 对应的组平均值较高。
- D. 对应的组平均值较低。

(LC5.16) 关于残差的哪个陈述是正确的？

- A. 残差是拟合值与观测值之间的差异。
- B. 残差总是正。
- C. 残差对模型评估很重要。
- D. 残差是预测值。

## 5.3 专题

### 5.3.1 相关性不等于因果关系

在本章中，我们在解释回归系数时非常谨慎。我们总是讨论解释变量对结果变量 $y$ 的关联影响。例如，5.1.2 节中的陈述：“life_exp 每增加 1 个单位，fert_rate 就会关联减少 0.137 个单位。”我们包含“关联”一词是为了格外小心，不要暗示我们正在做出因果陈述。虽然 life_exp 与 fert_rate 负相关，但在没有更多信息的情况下，我们无法得出任何因果结论。

这里有另一个例子：一位不太好的医生查阅了病历，发现穿鞋睡觉的患者往往更容易头痛。于是这位医生宣布：“穿鞋睡觉会导致头痛！”

![](img/44574251804101e8f01f11b0c3190d9_179_0.png)

图 5.9：穿鞋睡觉会导致头痛吗？

然而，很有可能如果有人穿鞋睡觉，可能是因为他们醉酒了。此外，较高水平的酒精摄入会导致更多的宿醉和头痛。这里的酒精摄入量被称为混杂变量。它在背后“潜伏”，干扰了“穿鞋睡觉”与“醒来头痛”之间的因果关系（如果有的话）。我们可以通过图 5.10 中的因果图来总结这一点，其中：

