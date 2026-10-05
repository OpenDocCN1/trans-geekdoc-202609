

## 11.2 案例研究：西雅图房价

| | | | | | | | | |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 221900 | 5.3461 | 1180 | 3.0718 |
| 2 | 538000 | 5.7307 | 2570 | 3.4093 |
| 3 | 180000 | 5.2557 | 770 | 2.8869 |
| 4 | 604000 | 5.7814 | 1960 | 3.2926 |
| 5 | 510000 | 5.7075 | 1680 | 3.2251 |
| 6 | 1225000 | 6.0881 | 5420 | 3.7340 |
| 7 | 277500 | 5.4107 | 1715 | 3.2346 |
| 8 | 291850 | 5.4616 | 1060 | 3.0251 |
| 9 | 229500 | 5.3607 | 1780 | 3.2542 |
| 10 | 323000 | 5.5892 | 1890 | 3.2764 |

特别注意第六行和第三行的房屋。第六行房屋的价格为 $1,225,000，略高于一百万。由于 $10^6$ 等于一百万，其 $log_{10}$ 价格约为 6.9。与其他所有 $log_{10}$ 价格小于六的房屋进行对比，因为它们的价格都低于 $1,000,000。第三行的房屋是唯一一个 `sqft_living`（居住面积）小于 1000 的房屋。由于 $1000 = 10^3$，它是唯一的 $log_{10}$ 尺寸小于 3 的房屋。现在让我们在图 11.4 中可视化价格在进行此变换前后的效果。

```r
# Before log10 transformation
ggplot(house_prices, aes(x = price)) +
  geom_histogram(color = "white") +
  labs(x = "price (USD)", title = "House price: Before")
```

```r
# After log10 transformation
ggplot(house_prices, aes(x = log10_price)) +
  geom_histogram(color = "white") +
  labs(x = "log10 price (USD)", title = "House price: After")
```

![](img/445742518041017e8f0f11b0c3190d9_467_0.png)

**图 11.4：** log10 变换前后的房价。

观察发现，变换后分布的偏斜程度较小，并且在这种情况下，更加对称且呈钟形。现在你可以轻松地识别出低价房屋。让我们也对房屋尺寸进行相同的操作，其中变量 `sqft_living` 被 log10 变换为 `log10_size`。

```r
# Before log10 transformation
ggplot(house_prices, aes(x = sqft_living)) +
  geom_histogram(color = "white") +
  labs(x = "living space (square feet)", title = "House size: Before")
```

```r
# After log10 transformation
ggplot(house_prices, aes(x = log10_size)) +
  geom_histogram(color = "white") +
  labs(x = "log10 living space (square feet)", title = "House size: After")
```

![](img/445742518041017e8f0f11b0c3190d9_468_0.png)

图 11.5：log10 变换前后的房屋尺寸。

观察图 11.5 发现，log10 变换对消除偏斜有类似的效果。强调的是，在这两种情况下结果分布更加对称且呈钟形，这并非总是如此。考虑到 `log10_price` 和 `log10_size` 现在的对称性，我们将修改回归模型以使用以下变量：

1. 结果变量 $y$ 是房屋的 `log10_price`。
2. 两个解释变量：
   - 数值解释变量 $x_1$：以10为底测量的房屋尺寸 `log10_size`。
   - 分类解释变量 $x_2$：房屋状况，具有五个等级，1 表示“差”，5 表示“优”。

## 11.2 案例研究：西雅图房价

### 11.2.2 探索性数据分析：部分 II

让我们通过创建多元可视化继续我们的 EDA。与图 11.3、11.4 和 11.5 中的单变量直方图和条形图不同，多元可视化展示了多个变量之间的关系。这是 EDA 的重要步骤，因为建模的目标是探索变量之间的关系。由于我们的模型涉及一个结果变量和一个分类变量，我们处于与第 6.1 节研究数据集类似的回归建模情中。在那种情况下，结果变量是生育率，数值解释变量是预期寿命，分类解释变量是收入。

我们有两个模型可以拟合：(1) 交互作用模型，每个状况的回归线具有不同的斜率和截距；(2) 平行斜率模型，每个状况的回归线具有斜率但不同的截距。回顾第 6.1 节，`geom_parallel_slopes()` 函数是 Jenny Chvasnov 创建并包含在 `modderive` 包中的特殊函数，因为 `ggplot2` 包中的 `geom_smooth()` 方法没有方便的方法绘制平行斜率。我们在图 11.6 中绘制了结果模型，左侧是交互作用模型。

```r
# Plot interaction model
ggplot(house_prices, aes(x = log10_size, y = log10_price, col = condition)) +
  geom_point(alpha = 0.05) +
  geom_smooth(method = "lm", se = FALSE) +
  labs(y = "log10 price", x = "log10 size", title = "House prices in Seattle")

# Plot parallel slopes model
ggplot(house_prices, aes(x = log10_size, y = log10_price, col = condition)) +
  geom_point(alpha = 0.05) +
  geom_parallel_slopes(se = FALSE) +
  labs(y = "log10 price", x = "log10 size", title = "House prices in Seattle")
```

在两种情况下，我们都看到房价和尺寸之间存在正相关，这意味着房屋尺寸越大，往往越贵。此外，在 ![](img/445742518041017e8f0f11b0c3190d9_470_0.png) **图 11.6：** 交互作用模型和平行斜率模型。两幅图似乎显示状况 5 的房屋在各种尺寸下都最贵，这一点由状况 5 的线条最高、其次是状况 4 和 3 证明。对于状况 1 和 2，这种模式并不清晰。回顾图 11.3 中的单变量条形图，只有少数状况 1 或 2 的房屋。让我们在图 11.7 中也显示交互模型的分面版本。状况 1 或 2 的房屋是多么少要明显得多。

```r
ggplot(house_prices, aes(x = log10_size, y = log10_price, col = condition)) +
  geom_point(alpha = 0.4) +
  geom_smooth(method = "lm", se = FALSE) +
  labs(y = "log10 price", x = "log10 size", title = "House prices in Seattle") +
  facet_wrap(~ condition)
```

可以使用 `dplyr` 和 `count()` 函数进一步检查：

```r
house_prices %>% count(condition)
```

| condition | n |
| :--- | :--- |
| 1 | 30 |
| 2 | 172 |
| 3 | 440 |
| 4 | 569 |
| 5 | 701 |

![](img/445742518041017e8f0f11b0c3190d9_471_0.png)

图 11.7：交互模型的分面图。

哪种交互作用模型的探索性可视化更好？是图 11.6 的左侧图还是图 11.7 的分面版本？图 11.7 明显地看出状况 1 或 2 的房屋是多么少。在这两种情况下结果分布更加对称且呈钟形，这并非总是如此。这种对称性对于 `log10_price` 和 `log10_size` 并不是唯一的答案，取决于你想传达什么信息。在图 11.6 的左侧图中，这种方法是主观的。我们可以从回归表格中获得这些值：

```r
price_interaction <- lm(log10_price ~ log10_size * condition, data = house_prices)
get_regression_table(price_interaction)
```

