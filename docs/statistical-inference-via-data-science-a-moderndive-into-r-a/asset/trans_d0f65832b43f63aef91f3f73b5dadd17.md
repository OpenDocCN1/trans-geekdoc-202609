

## 9.6 案例研究：动作片还是浪漫片的评分更高？

# A tibble: 58,788 x 24 列
| title | year budget rating votes | r1 | r2 | r3 | r4 | r5 |
| <chr> | <int> | <int> | <dbl> | <int> | <dbl> | <dbl> | <dbl> | <dbl> |
| 1 | 1971 | 121 | NA | 6.4 | 4.5 | 4.5 | 4.5 | 14.5 |
| 2 | $1000 ~ | 1939 | 71 | NA | 6 | 20 | 14.5 | 4.5 | 24.5 | 14.5 |
| 3 | $21 a ~ | 1941 | 70 | NA | 8.2 | 5 | 0 | 0 | 0 |
| 4 | $40,000 | 1996 | 70 | NA | 8.2 | 6 | 14.5 | 0 | 0 |
| 5 | $55,000 ~ | 1975 | 71 | NA | 3 | 17 | 24 | 4.5 | 0 | 14.5 | 14.5 |
| 6 | Spent | 2000 | 91 | NA | 4.3 | 45 | 4.5 | 4.5 | 4.5 | 24.5 |
| 7 | Swindle | 2002 | 93 | NA | 5.3 | 200 | 45 | 4.5 | 4.5 | 24.5 |
| 8 | '15' | 2002 | 25 | NA | 6.7 | 24 | 4.5 | 4.5 | 4.5 | 4.5 |
| 9 | '38 | 1987 | 97 | NA | 6.6 | 18 | 4.5 | 4.5 | 4.5 | 0 |
| 10 | '49'-57,888 | 1917 | 61 | NA | 6 | 51 | 4.5 | 4.5 | 4.5 |

# i 13 个变量: r6 <dbl>, r8 <dbl>, r9 <dbl>, r10 <dbl>
# mpaaa <chr>, Action, Animation <int>, Comedy <int>, Drama <int>
# Documentary <int>, Romance <int>, Short <int>

我们关注的是 68 部被归类为“动作”或“浪漫”但不同兼得的随机样本。我们忽略了同时被归类为这两者的电影，这样我们可以将这 68 部全部分配到其中一类别。此外，由于原始数据集有点混乱，我们在 `moderndive` 包包含的 `movies_sample` 数据框中提供了一个预处理版本。如果你感兴趣，可以在 GitHub 上查看执行此操作所需的数据清洗代码。

movies_sample

# A tibble: 68 x 4 列
| title | year rating genre |
| <chr> | <int> | <dbl> | <chr> |
| 1 Underworld | 1985 | 3.1 Action |
| 2 Love Affair | 1932 | 6.3 Romance |
| 3 Junglee | 1961 | 6.8 Romance |
| 4 Eversville, New Jersey | 1989 | 5 Romance |
| 5 Search and Destroy | 1979 | 4 Action |
| 6 Secreto de Romelia, El | 1988 | 4.9 Romance |
| 7 Amants Du-Neuf, Les | 1991 | 7.4 Romance |
| 8 Illicit Dreams | 1995 | 3.5 Action |

> https://github.com/moderndive/moderndive/blob/master/data-raw/process_data_sets.R

# 9 Kabhie Kabhie

## 9 假设检验

| 9 Kabhie Kabhie | 1976 | 7.7 Romance |
| 10 Electric Horseman, The | 1979 | 5.8 Romance |

# i 58 更多行

变量包含了电影标题和拍摄年份。此外，我们有一个数值型变量 `rating`，它是 IMDb 的 10 星制评分，以及一个二分类变量 `genre`，指示该电影是否为动作片或浪漫片。我们感兴趣的是动作片或浪漫片的平均评分更高。

让我们对这些数据进行探索性数据分析。回想第 2.7.1 节，箱线图是一种我们可以展示数值变量与分类变量之间关系的可视化工具。你在第 2.6 节中看到的另一种选择是使用分面直方图。然而，为了起见，我们只在图 9.14 中展示箱线图。

```r
ggplot(data = movies_sample, aes(x = genre, y = rating)) +
geom_boxplot() +
labs(y = "IMDB rating")
```

![](img/445742518041017e8f01f11b0c3190d9_370_0.png)

图 9.14：IMDb评分与类型的箱线图。

肉眼观察图 9.14，浪漫片的中位数评分更高。然而，我们是否有理由相信，动作片的平均评分与浪漫片的平均评分之间存在显著差异？仅凭此图很难判断。

## 9.6 案例研究：动作片还是浪漫片的评分更高？

这张箱线图显示浪漫片的样本中位数评分更高。

然而，箱体之间存在大量的重叠。请记住，中位数并不等同于平均值，这取决于分布是否偏斜。

让我们按二分类分类变量 `genre` 分组计算一些汇总统计量：电影数量、平均评分以及按类型划分的标准差。我们将使用 `dplyr` 的清洗操作符来实现此。请特别注意我们如何使用 `n()` 统计函数计算每种类型电影的数量。

```r
movies_sample |>
  group_by(genre) |>
  summarize(n = n(), mean_rating = mean(rating), std_dev = sd(rating))
```

```r
# A tibble: 2 x 4
  genre    n mean_rating std_dev
  <chr> <int> <dbl> <dbl>
1 Action  32       5.275     1.361
2 Romance 36       6.322     1.609
```

观察结果，动作片的平均评分为 5.275，浪漫片的平均评分为 6.322。因此，浪漫片的评分高出 1.047。这种差异是由于随机抽样导致的吗？还是浪漫片确实评分更高？

## 9.6.2 抽样场景

让我们从术语的角度重新审视这个问题。我们建立原假设（$H_0$）和备择假设（$H_A$）。

> 在这种情况下，原假设 $H_0$ 认为动作片和浪漫片的平均评分没有差异，即我们假设的宇宙是成立的。另一方面，备择假设 $H_A$ 认为动作片和浪漫片的平均评分存在差异。

## 9.6.3 进行假设检验

我们将预设一个低显著性水平 $\alpha = 0.001$。通过设置这个低值，在其他相同的情况下，$p$ 值小于 $\alpha$ 的概率较低。因此，只有较小的概率拒绝原假设 $H_0$ 而接受备择假设 $H_A$。换句话说，只有当我们有足够的证据时我们才会这样做。

### 1. 指定变量

现在让我们执行 `infer` 工作流的所有步骤。我们首先使用公式 `rating ~ genre` 在 `movies_sample` 数据框中指定感兴趣的变量。这告诉 `infer` 数值变量 `rating` 是结果变量，而二分类变量 `genre` 是解释变量。注意，与之前关注比例不同，由于我们现在感兴趣的是数值变量的平均值，因此不需要设置 `success` 参数。

```r
movies_sample |>
  specify(formula = rating ~ genre)
```

```r
Response: rating (numeric)
Explanatory: genre (factor)
# A tibble: 68 x 2
  rating genre
<dbl> <fct>
1  3.1 Action
2  6.3 Romance
3  6.8 Romance
4  5 Romance
5  4 Action
6  4.9 Romance
7  7.4 Romance
8  3.5 Action
9  7.7 Romance
10 5.8 Romance
# i 58 more rows
```

此时观察到，`movies_sample` 中的数据没有变化。目前为止的变化只是新定义的 Response: rating (numeric) 和 Explanatory: genre (factor) 元数据。

