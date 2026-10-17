
```
Rows: 188
Columns: 4
$ country <chr> "Afghanistan", "Albania", "Algeria", "Andorra", "..."
$ life_exp <dbl> 53.6, 79.5, 78.0, 83.4, 62.1, 77.8, 78.3, 76.1, 83...
$ continent <fct> Asia, Europe, Africa, Europe, North America...
$ gdp_per_capita <dbl> 356, 6810, 4343, 41993, 3000, 19260, 13651, 7018...
```

注意观察 `Rows: 188` 表示 `gapminder2022` 中有 188 行/观测值，其中每行对应一个国家。换句话说，*观测单元*是一个独立的国家。此外，观察到变量 `continent` 的类型为 `<fct>`，代表 *factor*（因子），这是 R 编码分类变量的方式。

通过阅读相关的帮助文件，可以找到 `un_member_states_2024` 中所有变量的完整描述（在控制台中运行 `un_member_states_2024`）。然而，我们只完整描述了在 `gapminder2022` 中选出的 4 个变量：

- 1. `country`：一种字符型/文本类型的标识变量，用于区分数据集中的 142 个国家。
- 2. `life_exp`：该国出生时预期寿命的数值型变量。这是我们感兴趣的结果变量 `$y$`。
- 3. `continent`：一个具有五个层级的分类变量。“levels”对应于可能的类别：非洲、亚洲、美洲、欧洲和大洋洲。这是我们感兴趣的解释变量 `$x$`。
- 4. `gdp_per_capita`：该国按通货膨胀调整后的美元计算的人均 GDP 数值型变量，我们将在本节末尾的学习检查中将其作为另一个结果变量 `$y$`。

接下来，我们查看表 5.4 中从 188 个国家中随机抽取的三个国家样本。

```r
gapminder2022 |> sample_n(size = 3)
```

# 表 5.4：从 193 个国家中随机抽取的 5 个国家样本

| country | life_exp | continent | gdp_per_capita |
|---|---|---|---|
| Panama | 77.6 | North America | 17358 |
| Micronesia, Federated States of | 74.4 | Oceania | 3714 |
| Burundi | 67.4 | Africa | 259 |
| United Arab Emirates | 79.6 | Asia | 53708 |
| India | 67.2 | Asia | 241 |

随机抽样可能会产生不同的 3 行子集。现在我们已经查看了 `gapminder2022` 数据框中的原始值并对数据有了初步了解，现在计算统计量。我们再次应用 modernverse 包中的 `tidy_summary()`。回顾该函数接收一个数据框，进行汇总并返回常见的统计量。我们获取 `gapminder2022` 数据框，选择结果和大洲，并将它们传递给 `tidy_summary()`：

```r
gapminder2022 |> select(life_exp, continent) |> tidy_summary()
```

# 表 5.5：预期寿命摘要

| column | n | type | min | Q1 | median | Q3 | max | sd |
|---|---|---|---|---|---|---|---|
| life_exp | 188 | numeric | 53.6 | 69.4 | 75.2 | 78.4 | 89.6 | 11.9 |
| Africa | 44 | fct | | | | | | |
| Asia | 53 | fct | | | | | | |
| Americas | 39 | fct | | | | | | |
| Europe | 36 | fct | | | | | | |
| Oceania | 14 | fct | | | | | | |

我们看到数据是左偏的，也称为负偏：一些预期寿命较低国家拉了平均值。然而，中位数对异常值的影响不敏感；中位数大于平均值。

记住，我们想要在大洲之间和内部比较预期寿命。换句话说，我们的可视化需要某种大洲的概念。我们可以很容易地通过分面直方图来实现。回顾 2.6 节，分面（facets）允许根据另一个变量的不同值分割可视化图形。通过添加 `facet_wrap(~ continent, nrow = 2)`，我们在图 5.7 中展示了生成的可视化结果。

```r
ggplot(gapminder2022, aes(x = life_exp)) +
  geom_histogram(binwidth = 5, color = "white") +
  labs(x = "Number of countries",
       title = "Histogram of distribution of worldwide expectancies") +
  facet_wrap(~ continent, nrow = 2)
```

![](img/44572518041017e8f011b0c31d9169_0.png)

**图 5.6：**2022 年预期寿命分布直方图。

## 5.2 一个分类变量

回想一下通过分类变量可视化数值划分分布的另一种方法是使用并列箱线图（side-by-side boxplot）。在图 5.8 中，我们将分类变量 `continent`（大陆）映射到 x 轴，并将每个地区的预期寿命映射到 y 轴。

```r
ggplot(gapminder2022, aes(x = continent, y = life_exp)) +
geom_boxplot(x) + 
labs(x = "Continent",
  y = "Life expectancy",
  title = "Life expectancy by continent")
```

### 各地区的预期寿命

![](img/445742518041017e8f01f11b0c3190d9_171_0.png)

**图 5.8：**2022年各地区的预期寿命（箱线图）。

有些人倾向于使用箱线图比较分类变量不同水平之间数值变量的分布，而不是使用分面直方图。这是因为我们可以通过想象的水平线对分类变量的不同水平进行快速比较。例如，观察图 5.8，我们可以通过在 y = 81 附近画一条想象的线，快速地确信欧洲的中位数预期寿命最高。此外，正如我们在分面直方图图 5.7 中观察到的，非洲和亚洲的预期寿命变化最大，这从它们的高四分位距（箱体的大小）中得到了证明。

重要的是，箱体中间的实线对应于中位数（中间值），而不是平均值（平均数）。例如，如果你观察亚洲，实线表示约 75 年的中位数预期寿命。这告诉我们，亚洲有一半的国家预期寿命低于 75 年，而另一半则高于 75 年。我们通过少量的数据处理计算了每个地区的中位数平均预期寿命，并将结果显示在表 5.6 中。

简单线性回归

```r
life_exp_by_continent <- gapminder2022 |> 
group_by(continent) |>
summarize(median = median(life_exp), mean = mean(life_exp))
life_exp_by_continent
```

### 表 5.6：各地区的预期寿命

| continent | median | mean |
|---|---|---|
| Africa | 66.1 | 66.3 |
| Asia | 75.4 | 75.0 |
| Europe | 81.5 | 79.9 |
| North America | 76.1 | 76.3 |
| Oceania | 74.6 | 74.4 |
| South America | 75.4 | 75.2 |

观察第二列中位数预期寿命的顺序：非洲最低，欧洲最高，其他地区的中位数介于非洲和欧洲之间。这种排序与我们并列图图 5.8 中箱体内部黑色实线的顺序对应。

现在我们将注意力转到第三列的平均值上。以非洲 66.31 年的平均预期寿命作为比较基准，我们开始与其他四个地区的平均预期寿命进行比较，并将这些值放入表 5.7 中，我们将在本节稍后重新回顾该表。

- 对于亚洲，高出 74.95 - 66.31 = 8.64 年。
- 对于欧洲，高出 79.91 - 66.31 = 13.6 年。
- 对于北美，高出 76.29 - 66.31 = 9.98 年。
- 对于大洋洲，高出 74.42 - 66.31 = 8.11 年。
- 对于南美，高出 75.23 - 66.31 = 8.92 年。

### 表 5.7：各地区的平均预期寿命以及相对于非洲的差异

| continent | mean | Difference versus Africa |
|---|---|---|
| Africa | 66.3 | 0.00 |
| Asia | 75.0 | 8.64 |
| Europe | 79.9 | 13.60 |
| North America | 76.3 | 9.99 |
| Oceania | 74.4 | 8.11 |
| South America | 75.2 | 8.92 |

## 5.2 一个分类解释变量

### 学习检查

(LC5.11) 进行一次新的探索性数据分析，使用相同的解释变量 `x`（`continent`），但将 `gdp_per_capita` 作为结果变量 `y`。根据这一探索，你可以看到不同大陆之间人均 GDP 的什么差异？

(LC5.12) 在回归中使用分类解释变量时，基准组（baseline group）代表什么？

- A. 平均值最高的组
- B. 选择与其他所有组进行比较的组
- C. 数据点最多的组
- D. 标准差最低的组

### 5.2.2 线性回归

在 5.1.2 节中，我们介绍了简单线性回归，它涉及对数值结果变量 `y` 与数值解释变量 `x` 之间关系的建模。在预期寿命示例中，我们拥有的是分类解释变量。我们的模型不会产生像图 5.3 那样的“最佳拟合”回归线，而是产生相对于基准的偏移量。

正如我们在 5.1.2 节中研究生育率与预期寿命的关系时的那样，我们输出该模型的回归系数。这通过两个步骤完成：

1. 首先使用 `lm(y ~ x, data)` “拟合”线性回归模型并保存到 `life_exp_model` 中。
2. 通过对 `life_exp_model` 应用 `coef()` 函数获取回归系数。

```r
life_exp_model <- lm(life_exp ~ continent, data = gapminder2022)
coef(life_exp_model)
```

| (Intercept) | continentAsia | continentEurope |
|---|---|---|
| 66.31 | 8.64 | 13.60 |
| continentNorth America | continentOceania | continentSouthAmerica |
| 9.99 | 8.11 | 8.92 |

我们再次关注这些系数值。为什么有 6 个项目？我们将它们拆解为：

- 1. `intercept` 对应非洲国家 66.31 年的平均预期寿命。
- 2. `continentAsia` 对应亚洲，值 +8.64 是相对于非洲的预期寿命差异。换句话说，亚洲的平均预期寿命为 66.31 + 8.64 = 74.95。
- 3. `continentEurope` 对应欧洲，值 +13.6 是相对于非洲的预期寿命差异。换句话说，欧洲的平均预期寿命为 66.31 + 13.6 = 79.91。
- 4. `continentNorth America` 对应北美，值 +9.98 是相对于非洲的预期寿命差异。换句话说，北美的平均预期寿命为 66.31 + 9.98 = 76.29。
- 5. `continentOceania` 对应大洋洲，值 +8.11 是相对于非洲的预期寿命差异。换句话说，大洋洲的平均预期寿命为 66.31 + 8.11 = 74.42。
- 6. `continentSouthAmerica` 对应南美，值 +8.92 是相对于非洲的预期寿命差异。换句话说，南美的平均预期寿命为 66.31 + 8.92 = 75.23。

总结来说，6 个回归系数值对应于“比较基准”非洲（截距），以及来自亚洲、北美、大洋洲和南美的五个“偏移量”。你可能会问为什么选择非洲作为“比较基准”组，原因在于按字母顺序靠前；如果你操作 `continent` 因子的“水平”，可以更改此基准。请参见《R for Data Science》（Grolem and Wickham, 2017）。我们现在为拟合值 $\hat{y}$ = `life_exp` 写方程：

$$\hat{y} = b_0 + b_{Asia} \cdot \mathbb{1}_{Asia}(x) + b_{Europe} \cdot \mathbb{1}_{Europe}(x) + b_{NorthAmerica} \cdot \mathbb{1}_{NorthAmerica}(x) + b_{Oceania} \cdot \mathbb{1}_{Oceania}(x) + b_{SouthAmerica} \cdot \mathbb{1}_{SouthAmerica}(x)$$

哇！这看起来很令畏！但是，当你理解了所有元素是如何大大简化时，不要担心。首先，$\mathbb{1}_{A}(x)$ 是数学上所谓的“指示函数”。它返回两个值 0 和 1 之一：

$$\mathbb{1}_{A}(x) = \begin{cases} 1 & \text{if } x \text{ is in } A \\ 0 & \text{otherwise}\end{cases}$$

在统计建模范围内，这也是虚拟变量（dummy variable）。在我们的情况下，我们考虑第一个这样的指示变量 $\mathbb{1}_{Amer}(x)$。如果国家位于亚洲，该指示返回 1，否则返回 0：

$$\mathbb{1}_{Amer}(x) = \begin{cases} 1 & \text{if } x \text{ is in Asia} \\ 0 & \text{otherwise}\end{cases}$$

其次，$b_0$ 之前一样对应截距；在这种情况下，它是非洲所有国家的平均预期寿命。第三，$b_{Asia}, b_{Europe}, b_{NorthAmerica}, b_{Oceania}$ 和 $b_{SouthAmerica}$ 代表回归系数中五个“相对于比较基准的偏移”。

我们将这一切整合在一起，计算非洲国家拟合值 $\hat{y}$ = `life_exp`。由于该国家位于非洲，所有五个指示函数 $\mathbb{1}_{Asia}(x), \mathbb{1}_{Europe}(x), \mathbb{1}_{NorthAmerica}(x), \mathbb{1}_{Oceania}(x)$ 和 $\mathbb{1}_{SouthAmerica}(x)$ 都将等于 0，因此：

$$\hat{y} = b_0 + b_{Asia} \cdot \mathbb{1}_{Asia}(x) + b_{Europe} \cdot \mathbb{1}_{Europe}(x) + b_{NorthAmerica} \cdot \mathbb{1}_{NorthAmerica}(x) + b_{Oceania} \cdot \mathbb{1}_{Oceania}(x) + b_{SouthAmerica} \cdot \mathbb{1}_{SouthAmerica}(x)$$
$$= 66.31 + 8.64 \cdot 0 + 13.6 \cdot 0 + 9.98 \cdot 0 + 8.11 \cdot 0 + 8.92 \cdot 0$$
$$= 66.31$$

换句话说，剩下的只有截距 $b_0$，对应非洲国家 66.31 年的预期寿命。接下来，假设我们考虑一个亚洲的国家。在这种情况下，只有亚洲的指示函数 $\mathbb{1}_{Asia}(x)$ 等于 1，而其他所有函数都等于 0，因此：

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
