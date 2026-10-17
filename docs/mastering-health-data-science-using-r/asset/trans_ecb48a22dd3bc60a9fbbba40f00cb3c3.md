

```r
year %in% c(2020, 2021)) %>%
pivot_wider(names_from = year, values_from = total_rate) %>%
na.omit() %>%
rename("y2020" = "2020", "y2021" = "2021")
head(county_rates)
#> # A tibble: 6 x 3
#>   county y2020 y2021
#>   <chr> <dbl> <dbl>
#> 1 Anderson 6.84 5.07
#> 2 Andrews 1.85 0.792
#> 3 Angelina 5.81 6.00
#> 4 Aransas 3.44 7.18
#> 5 Archer 1.47 0.733
#> 6 Armstrong 0 0
```

```r
ggplot(county_rates) +
geom_point(aes(x = y2020, y = y2021)) +
labs(x = "2020 ITOP Rates", y = "2021 ITOP Rates")
```

![](img/58a554e865d49ca347d9a3f76f8f0812_190_0.png)

我们之前已经了解如何使用 `cor()` 函数计算两列之间的相关性。我们也可以使用 `cov()` 函数计算协方差。如所预料的那样，存在正相关。估计的协方差约为 5.2。

```r
cor(county_rates$y2020, county_rates$y2021)
#> [1] 0.5
cov(county_rates$y2020, county_rates$y2021)
#> [1] 5.2
```

除了计算相关性的值之外，我们还可以检验该相关性是否显著不为零。`cor.test()` 函数使用皮尔逊积矩相关系数、肯德尔 τ 或斯皮尔曼 ρ 来检验配对样本之间的关联。与 `t.test()` 和 `wilcox.test()` 函数类似，我们也可以指定 `alternative` 和 `conf.level` 参数。在下面的代码中，我们使用皮尔逊积矩相关来检验 2020 年和 2021 年县级比率之间是否存在非零相关性。从得到的 p 值可以看出，我们可以拒绝相关性为零的原假设，并得出结论：该相关性与零存在显著差异。这次我们还输出了估计值的计算置信区间。

```r
cor_test_res <- cor.test(county_rates$y2020,
                         county_rates$y2021,
                         method = "pearson")
cor_test_res
#>
#>  Pearson's product-moment correlation
#>
#> data:  county_rates$y2020 and county_rates$y2021
#> t = 9, df = 250, p-value <2e-16
#> alternative hypothesis: true correlation is not equal to 0
#> 95 percent confidence interval:
#>  0.401 0.587
#> sample estimates:
#> cor
#> 0.5
```

```r
cor_test_res$conf.int
#> [1] 0.401 0.587
#> attr(,"conf.level")
#> [1] 0.95
```

## 11.3 连续变量的双样本检验

如果我们想直接比较 2020 年和 2021 年比率之间的差异，可以使用双样本检验。在这种情况下，由于样本按县配对，我们可以使用双样本配对 t 检验。具体来说，我们通过指定两个不同的向量 x 和 y，使用双侧检验来检验比率相等的原假设。请注意，我们使用了默认值 mu = 0 和 alternative = "two.sided"。此外，我们使用了默认值 var.equal = FALSE，这意味着样本可能具有不同的方差。从结果来看，我们在 0.05 显著性水平下拒绝了这两个县级比率相等的原假设。我们还输出均值差的 95% 置信区间。

```r
t_test_two_res <- t.test(x = county_rates$y2020,
                         y = county_rates$y2021)

t_test_two_res
#>
#> Welch Two Sample t-test
#>
#> data:  county_rates$y2020 and county_rates$y2021
#> t = 2, df = 497, p-value = 0.01
#> alternative hypothesis: true difference in means is not equal to 0
#> 95 percent confidence interval:
#>  0.145 1.278
#> sample estimates:
#> mean of x mean of y
#>   5.28    4.57
t_test_two_res$conf.int
#> [1] 0.145 1.278
#> attr(,"conf.level")
#> [1] 0.95
```

在 tex_itop 数据集中，每个县还根据其是城市还是农村进行了分类。假设我们想比较农村县和城市县在 2020 年到 2021 年间堕胎率的变化。首先，我们使用下面的代码创建一个描述这些年之间比率变化的变量。我们选择使用比率的变化而不是百分比变化，以避免无穷大或未定义的值。

```r
county_rates_type <- tex_itop %>%
  dplyr::select(c(county, urban, county_type, total_rate, year)) %>%
filter(total_rate < 15, year %in% c(2020, 2021)) %>%
pivot_wider(names_from = year, values_from = total_rate) %>%
na.omit() %>%
rename("y2020" = "2020", "y2021" = "2021") %>%
mutate(rate_change = (y2021 - y2020))
```

我们再次使用双样本双侧 t 检验，但这次数据不是配对的。在下面的代码中，我们展示了使用公式 lhs ~ rhs 指定 t 检验的另一种方法，其中 lhs 是数值列，rhs 是包含两个水平的因子列。在这种情况下，我们还必须指定数据。从此例的 R 输出中，我们无法在 0.05 显著性水平下拒绝原假设，并得出结论：城市县和农村县的比率变化没有显著差异。我们还使用 estimate 输出 t 检验中使用的估计值，该估计值显示两组的估计均值。

```r
t_test_unpaired <- t.test(rate_change ~ urban,
                           data = county_rates_type)
t_test_unpaired
#>
#>  Welch Two Sample t-test
#>
#> data:  rate_change by urban
#> t = 0.1, df = 205, p-value = 0.9
#> alternative hypothesis: true difference in means between group
#>   Rural and group Urban is not equal to 0
#> 95 percent confidence interval:
#>  -0.495  0.563
#> sample estimates:
#> mean in group Rural mean in group Urban
#>             -0.469             -0.503
t_test_unpaired$estimate
#> mean in group Rural mean in group Urban
#>             -0.469             -0.503
```

请注意，这与使用两个向量 x 和 y 指定数据得到的结果相同。

```r
x <- county_rates_type$rate_change[county_rates_type$urban == 'Urban']
y <- county_rates_type$rate_change[county_rates_type$urban == 'Rural']
t.test(x = x, y = y, paired = FALSE)
#>
#>  Welch Two Sample t-test
#>
#> data: x and y
#> t = -0.1, df = 205, p-value = 0.9
#> alternative hypothesis: true difference in means is not equal to 0
#> 95 percent confidence interval:
#> -0.563 0.495
#> sample estimates:
#> mean of x mean of y
#> -0.503 -0.469
```

除了 t 检验之外，我们还可以使用 wilcox.test() 函数进行双样本 Wilcoxon 非参数检验，该函数具有与 t.test() 函数相同的参数。t.test() 和 wilcox.test() 都只能比较两组。当我们要比较两个或更多独立样本时，可以使用 kruskal.test() 函数进行 Kruskal-Wallis 秩和检验，或使用 aov() 函数进行单因素方差分析（ANOVA）。

这次我们使用 county_type 列，该列根据美国农业部的 RUCC（农村-城市连续代码）指示该县是城市、郊区还是农村。对于 kruskal.test() 函数，我们可以指定公式（rate_change ~ county_type）和数据（county_rates_type）这两个参数，也可以指定两个向量：x（数值向量）和 g（表示组的因子）。对于 aov() 函数，我们使用公式和数据指定检验。要查看 p 值，我们必须使用 summary() 函数输出结果。同样，这两项检验都表明我们无法在 0.05 显著性水平下拒绝原假设。

```r
kruskal.test(county_rates_type$rate_change,
                     county_rates_type$county_type)
#>
#> Kruskal-Wallis rank sum test
#>
#> data: county_rates_type$rate_change and
#> county_rates_type$county_type
#> Kruskal-Wallis chi-squared = 2, df = 2, p-value = 0.3
```

```r
aov_res <- aov(rate_change ~ county_type,
                     data = county_rates_type)
summary(aov_res)
#>
#> Df Sum Sq Mean Sq F value Pr(>F)
#> county_type 2 7 3.36 0.53 0.59
#> Residuals 245 1547 6.31
```

### 11.3.1 练习题

使用适当的检验来确定 2016 年不同种族的 ITOP 率是否存在显著差异。检验统计量应为 263.53，相应的 p 值应小于 2.2e-16。

```
# Insert your solution here:
```

### 11.3.2 双样本方差检验

我们还可以检验连续变量的方差在组间是否相等。首先，我们使用 F 检验比较 2021 年城市县和农村县堕胎率的方差。该检验的原假设是两组的方差相等。var.test() 函数实现了 F 检验，其主参数与 t.test() 函数相同：向量 x 和 y，或公式和数据，备择假设 alternative，以及 conf.level。此外，我们可以通过参数 ratio（默认值为 1）指定方差的假设比值。请注意，该函数假设两个样本来自正态分布的总体。我们无法在 0.05 显著性水平下拒绝比率方差相等的原假设，并输出方差比的估计值，约为 1.11。

```r
f_test <- var.test(y2021 ~ urban, county_rates_type)
f_test
#>
#> F test to compare two variances
#>
#> data:  y2021 by urban
#> F = 1, num df = 187, denom df = 59, p-value = 0.6
#> alternative hypothesis: true ratio of variances is not equal to 1
#> 95 percent confidence interval:
#>  0.719 1.657
#> sample estimates:
#> ratio of variances
#>         1.12
f_test$estimate
#> ratio of variances
#>        1.12
#>
```

最后，我们实现 Levene 检验，以检验当组数多于两组时组间方差是否相等。该检验可以通过公式和数据集来指定，如演示所示，也可以通过提供两个向量 y, a 来指定。

