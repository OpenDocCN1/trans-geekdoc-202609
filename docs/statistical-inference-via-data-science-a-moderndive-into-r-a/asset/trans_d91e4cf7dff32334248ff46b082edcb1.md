

## 8.2 使用自助法进行估计

注意，数据本身没有改变，但 `Response: weight (numeric)` 元数据改变了。这类似于 dplyr 中的 `group_by` 动词没有改变数据，只是添加了“分组”元数据，正如我们在第3.4节中所看到的那样。

我们还可以通过在 `specify()` 中引入公式 `formula = y ~ x` 来指定哪些变量是研究重点。这与你在第5和第6章回归模型中看到的公式表示相同：响应变量 `y` 被 `~`（波浪号）与解释变量 `x` 分隔。以下使用 `formula` 参数的 `specify()` 将产生与之前相同的结果：

```
almonds_sample_100 |>
specify(formula = weight ~ NULL)
```

在杏果案例中，我们只有一个响应变量，没有感兴趣的解释变量。因此，我们将 `~` 右侧的 `x` 设置为 `NULL`。

在推断聚焦于单个样本的情况下（如杏果重量示例），两种指定方式均有效。在我们在后续章节中提供的示例中，公式指定更加简单且灵活。特别是在即将到第8.4节比较两个比例以及第10.3节回归推断中会涉及到这一点。

## 2. 生成副本

![](img/445742518041017e8f01f11b0c3190d9_307_0.png)

图 8.16：`generate()` 生成副本的图。

## 8 估计、置信区间与自助法

在我们 `specify()` 了感兴趣的变量后，我们将结果放入 `generate()` 函数中以生成副本。该函数根据之前指定的变量，产生自助样本或执行多次自助重采样过程，如图8.16所示。回想我们此此操作了1000次。

`generate()` 函数的第一个参数是 `reps`，它设置了我们想要生成的副本数量。由于我们想对 `almonds_sample_100` 中的100颗杏仁进行1000次有放回重采样，因此我们设置 `reps = 1000`。

第二个参数决定了计算机模拟的类型。将 `type` 设置为 `"bootstrap"` 会使用有放回重采样产生自助样本。我们在第9章中会介绍 `type` 的不同选项。

```
almonds_sample_100 |>
specify(response = weight) |
generate(reps = 1000, type = "bootstrap")
```

```
Response: weight (numeric)
# A tibble: 100,000 x 2
# Groups: replicate [1,1000]
replicate weight
<int> <dbl>
1 1 3.6
2 1 3.4
3 1 4.2
4 1 3.4
5 1 3.5
6 1 3.4
7 1 3.8
8 1 3.7
9 1 4.1
10 1 3.4
```

观察发现，结果的数据有100,000行。这是因为我们找到了1000个自助样本，每个样本有100行。

变量 `replicate` 标识了下方每一行对应的自助样本，从1到1000，每个副本重复了100次。在这种情况下，`type` 参数的默认值为 `"bootstrap"`，因此包含它仅是为了完整性。最后一行可以简单地写为 `generate(reps = 1000)`，结果是相同的。

与原始工作流对比：注意，到目前为止 `infer` 工作流的步骤产生的结果与我们之前看到的使用 `rep_sample_n()` 函数的原始工作流相同。换句话说，以下两个代码块产生相似的结果：

```
# infer workflow:
almonds_sample_100 |>
specify(response = weight) |>
generate(reps = 1000)

# Original workflow:
almonds_sample_100 |>
rep_sample_n(size = 100,
replace = TRUE,
reps = 1000)
```

## 3. 计算汇总统计量

![](img/445742518041017e8f01f11b0c3190d9_309_0.png)

图 8.17：`calculate()` 汇总统计量的图。

在我们 `generate()` 了1000个自助样本后，我们对每个样本进行汇总，例如通过计算每个样本的样本平均值。如图所示，`calculate()` 函数正是此作用。

在我们的示例中，我们通过在 `calculate()` 函数内部将 `stat` 参数设置为 `"mean"` 来计算每个自助样本的平均重量。`stat` 参数可以用于其他常见的统计量，如"median"(中位数）、"sum"(总和）、"sd"(标准差）和"prop"(比例）。要查看其他可能的汇总统计量列表，请输入 `?calculate` 并阅读帮助文件。

让我们将结果存在名为 `bootstrap_means` 的数据框中并探索其内容：

```
bootstrap_means <- almonds_sample_100 |>
specify(response = weight) |>
generate(reps = 1000) |>
calculate(stat = "mean")
bootstrap_means
```

## 8 估计、置信区间与自助法

Response: weight (numeric)
# A tibble: 1000 x 2
replicate stat
<int> <dbl>
1 3.68
2 3.688
3 3.632
4 3.68
5 3.679
6 3.675
7 3.678
8 3.706
9 3.643
10 3.68

观察发现结果的数据框有1000行和2列，分别对应1000个 `replicate` 值。它同样在变量 `stat` 中保存了每个自助样本的平均重量。

与原始工作流对比：你可能已经意识到，`infer` 工作流中的 `calculate()` 步骤产生的输出与原始工作流中 `summarize()` 步骤产生的输出相同。

```
# infer workflow:
almonds_sample_100 |>
specify(response = weight) |>
generate(reps = 1000) |>
calculate(stat = "mean")

# Original workflow:
almonds_sample_100 |>
rep_sample_n(size = 100,
replace = TRUE,
reps = 1000) |>
summarize(stat = mean(weight))
```

## 4. 可视化结果

![](img/445742518041017e8f01f11b0c3190d9_310_0.png)

图 8.18：`visualize()` 结果的图。

## 8.2 使用自助法进行估计

`visualize()` 动词提供了一种快速方法，以数值 `stat` 值的直方图形式可视化自助分布。用于探索自助结果的主要 `infer` 动词的流水线如图8.18所示。

```
visualize(bootstrap_means)
```

## 基于模拟的自助分布

![](img/445742518041017e8f01f11b0c3190d9_311_0.png)

图 8.19：自助分布。

与原始工作流对比：事实上，`visualize()` 是 `ggplot()` 函数的包装函数，使用了 `geom_histogram()` 层。回想我们在图5.5和第5.2节中说明了包装函数的概念。

```
# infer workflow:
visualize(bootstrap_means)

# Original workflow:
gg(bootstrap_means, aes(x = stat)) +
geom_histogram()
```

`visualize()` 函数可以接受许多其他参数来进一步自定义。在未来的章节中，我们将利用这种灵活性。此外，它通过辅助函数在直方图中添加对应置信区间值的阴影。我们已经介绍了构建自助分布并对其可视化的 `infer` 工作流的不同元素。这些步骤的总结见图8.20。

## infer 中的置信区间

![](img/445742518041017e8f01f11b0c3190d9_311_1.png)

图 8.20：置信间的 infer 包工作流。

## 8.2.4 使用自助 使用置信区间

我们准备好通过自助引入置信区间。我们介绍了两种构建95%置信区间的方法作为未知参数的区间估计：百分位数法和标准误差法。让我们看看显式构建这些内容的 `infer` 包代码。`infer` 也内置了一些用于可视化结果置信间的简洁函数。

## 百分位数法

回想在第8.2.3节中，我们生成了1000个自助样本并存储在数据框 `bootstrap_means` 中：

```
bootstrap_means
Response: weight (numeric)
# A tibble: 1000 x 2
replicate stat
<int> <dbl>
1         1.368
2         2.688
3         3.632
4         3.688
5         3.679
6         3.675
7         3.768
8         3.706
9         3.643
10        3.688
# 990 rows
```

`bootstrap_means` 中存储的平均值是对所有可能的自助样本自助分布的良好近似。构建95%置信区间的百分位数法将置信间的下端设置为 `bootstrap_means` 的第2.5百分位数，同样地将上端设置为第97.5百分位数。所得区间捕捉了 `bootstrap_means` 中杏仁样本平均值的中间95%。这是对整个碗中杏仁总体平均重量的区间估计。

我们可以通过将 `bootstrap_means` 传递给 `infer` 包中的 `get_confidence_interval()` 函数来计算95%置信区间，并将 `confidence_level` 设置为0.95，`confidence_interval` 类型设置为 `"percentile"`。我们将结果存在 `percentile_ci` 中。

