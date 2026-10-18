

特征创建是将现有变量组合起来生成新变量。例如，合并 `SibSp` 和 `Parch` 变量来创建 `FamSize` 就是特征创建的一个例子。利用特征提取和特征创建，我们可以提取数据集中存在的预测信息，但这些信息目前的形式还无法发挥最大效用。

最后，我们的数据中常常会包含一些没有预测价值的变量。例如，知道乘客的姓名或船舱编号是否有助于我们预测是否生还？可能没有帮助，那就把它们删除吧。将预测价值很小甚至没有预测价值的变量纳入数据，会给数据增加噪声，并对模型的表现产生负面影响，因此最好将它们删除。

这是另一个极其重要的机器学习任务，称为*特征选择*，从名称上就能大致理解其含义：保留能增加预测价值的变量，删除没有预测价值的变量。有时候，哪些变量是有效的预测因子，对我们人类来说是一目了然的。例如，乘客姓名就没有用，因为每位乘客的姓名都不相同！在这种情况下，删除这些变量是常识。然而，很多时候并没有那么明显，我们可以用更复杂的方法将特征选择过程自动化。我们将在后面的章节中探讨这一点。

这三项任务（转换为因子、特征工程和特征选择）都在代码清单 4.2 中完成。为了让操作更简便，我先定义了一个包含我们想要转换为因子的变量的向量，然后用 `mutate_at()` 函数将它们全部转换为因子。`mutate_at()` 函数与 `mutate()` 函数类似，但它允许我们一次修改多个列。我们将现有变量以字符向量的形式提供给 `.vars` 参数，并通过 `.funs` 参数告诉它我们要对这些变量做什么。在这个例子中，我们提供了所定义的变量向量，并提供了“factor”函数将它们转换为因子。

我们将结果通过管道传递给一个 `mutate()` 函数调用，该调用定义了一个新变量 `FamSize`，它是 `SibSp` 与 `Parch` 之和。

最后，我们将结果通过管道传递给 `select()` 函数调用，只选择我们认为可能对模型有一定预测价值的变量。当我们打印新的 tibble 时，可以看到 `Survived`、`Pclass` 和 `Sex` 现在都是因子（在上面的输出中，这些列的上方显示了 `<fct>`），我们有了新变量 `FamSize`，并且删除了不相关的变量。

## 代码清单 4.2 清理泰坦尼克号数据，为建模做好准备

```
fctrs <- c("Survived", "Sex", "Pclass")

titanicClean <- titanicTib %>%
  mutate_at(.vars = fctrs, .funs = factor) %>%
  mutate(FamSize = SibSp + Parch) %>%
  select(Survived, Pclass, Sex, Age, Fare, FamSize)

titanicClean
# A tibble: 891x6
  Survived Pclass Sex      Age  Fare FamSize
  <fct>    <fct>  <fct>   <dbl> <dbl>  <int>
1 0        3      male      22  7.25      1
2 1        1      female    38 71.3       1
3 1        3      female    26  7.92      0
4 1        1      female    35 53.1       1
5 0        3      male      35  8.05      0
6 0        3      male      NA  8.46      0
7 0        1      male      54 51.9       0
8 0        3      male       2 21.1       4
9 1        3      female    27 11.1       2
10 1       2      female    14 30.1       1
# ... with 881 more rows
```

注意，value 列是一个字符向量（<chr>）。这是因为其中包含了 Sex 变量中的“male”和“female”。由于一个列只能保存单一类型的数据，所有数值数据也被转换成了字符型。

### 4.2.3 绘制数据

既然我们已经对数据做了一些清理，现在就来绘制图形，以便更深入地了解数据中的关系。这里有一个小技巧，可以简化使用 `ggplot2` 同时绘制多个变量的过程。我们使用 `gather()` 函数将数据转换为非整洁格式，使每个预测变量的名称都保存在一列中，而它们的值保存在另一列中（如果不记得了，可以翻到第 2 章末尾复习一下）。

> **注意** `gather()` 函数会警告“测量变量之间的属性不一致；它们将被丢弃。”这只是在提醒你，将要合并到一起的变量没有相同的因子水平。通常情况下，这可能意味着你合并了一些本不想合并的变量，但在这种情况下，我们可以放心地忽略这个警告。

```
titanicUntidy <- gather(titanicClean, key = "Variable", value = "Value",
- Survived)
titanicUntidy
# A tibble: 4,455x3
Survived Variable Value
<fct> <chr> <chr>
1 0 Pclass 3
2 1 Pclass 1
3 1 Pclass 3
4 1 Pclass 1
5 0 Pclass 3
6 0 Pclass 3
7 0 Pclass 1
8 0 Pclass 3
9 1 Pclass 3
10 1 Pclass 2
# ... with 4,445 more rows
```

你可能想知道我们为什么要这样做。原因在于，它让我们能够使用 ggplot2 的分面系统将不同的变量一起绘制出来。在代码清单 4.4 中，我以 titanicUntidy 这个 tibble 为对象，筛选出 Variable 不等于 Pclass 或 Sex 的行（因为这些是因子，我们会单独绘制它们），然后将这些数据通过管道传递给 ggplot() 调用。

```
titanicUntidy %>%
filter(Variable != "Pclass" & Variable != "Sex") %>%
ggplot(aes(Survived, as.numeric(Value))) +
facet_wrap(~ Variable, scales = "free_y") +
geom_violin(draw_quantiles = c(0.25, 0.5, 0.75)) +
theme_bw()
```

你能看出分面是如何起作用的吗？数据中 Variable 取值不同的行被绘制在不同的子图中！这就是我们需要将数据转换为非整洁格式的原因：这样我们就可以提供一个单独的变量供 ggplot2 进行分面。

### 练习 4.1 重新绘制图 4.10 中的图形，但添加一个 geom_point() 图层，将 alpha 参数设为 0.05，并将 size 参数设为 3。这样做是否让小提琴图更有意义？

现在，我们对数据集中的因子变量做同样的操作：筛选出只包含 Pclass 和 Sex 变量的行。这一次，我们希望了解每个因子水平中幸存乘客所占的比例。因此，我们将 Value 作为 x 轴美学映射来绘制因子水平，并希望使用不同颜色来表示幸存与未幸存，所以将 Survived 作为填充美学映射。和之前一样，我们按 Variable 进行分面，并添加一个条形几何对象，参数为 position = "fill"，它会将幸存者和未幸存者的数据堆叠起来，使总和为 1，从而显示各自的比例。得到的图如图 4.11 所示。

```
titanicUntidy %>% 
  filter(Variable == "Pclass" | Variable == "Sex") %>% 
  ggplot(aes(Value, fill = Survived)) + 
  facet_wrap(~ Variable, scales = "free_x") + 
  geom_bar(position = "fill") + 
  theme_bw()
```

