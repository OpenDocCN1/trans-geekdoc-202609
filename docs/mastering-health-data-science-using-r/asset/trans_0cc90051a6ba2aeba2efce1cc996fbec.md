
数值向量，以及 g，一个指定组别的向量。此检验来自 **car** 包，其输出与其他检验略有不同。特别是，要访问 p 值，我们需要访问名为 'Pr(>F)' 的值。在此情况下，我们确实在 0.05 水平上拒绝了原假设。

```
levene_test <- leveneTest(y2021 ~ as.factor(county_type),
                              county_rates_type)
print(levene_test)
#> Levene's Test for Homogeneity of Variance (center = median)
#>       Df F value   Pr(>F)  
#> group  2  3.41 0.034 *
#>       245
#> ---
#> Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
levene_test[['Pr(>F)']]
#> [1] 0.0345   NA
```

## 11.4 类别变量的两样本检验

在之前的两样本检验中，我们比较的是连续变量的分布。现在我们来看比较类别变量分布的方法。我们首先根据 2020 年各县的堕胎率是高于还是低于 11.2（即当年的全国平均水平）对各县进行分类。我们使用下面的列联表按城乡分组显示该变量的分布。

```
county_rates_type$below_nat_avg <-
  ifelse(county_rates_type$y2020 > 11.2, "Above Nat Avg",
         "Below Nat Avg")
table(county_rates_type$below_nat_avg, county_rates_type$urban)
#>
#>           Rural Urban
#> Above Nat Avg   3     4
#> Below Nat Avg 185    56
```

我们可以使用 Fisher 精确检验来检验高于和低于全国平均水平的分类与农村和城市分类之间是否存在关联。在此情况下，原假设是农村县和城市县低于全国平均水平的几率相等。fisher.test() 函数可以接受矩阵形式的列联表，也可以由两个因子向量 x 和 y 指定，这正是我们在以下代码中实现的方式。此外，还可以指定 alternative 和 conf.level 参数。我们在 0.05 水平上未观察到城市和农村县之间存在统计学显著差异，估计的比值比约为 0.23。

```
fisher_test <- fisher.test(county_rates_type$urban,
                           county_rates_type$below_nat_avg)
fisher_test
#>
#>  Fisher's Exact Test for Count Data
#>
#> data:  county_rates_type$urban and county_rates_type$below_nat_avg
#> p-value = 0.06
#> alternative hypothesis: true odds ratio is not equal to 1
#> 95 percent confidence interval:
#>  0.0325 1.3955
#> sample estimates:
#> odds ratio
#>   0.229
fisher_test$estimate
#> odds ratio
#>   0.229
```

另一种检验是 Pearson 卡方检验，适用于大样本量。在‘高于全国平均水平’类别中，农村和城市县的计数非常小，因此我们将结果重新分类为等于或高于得克萨斯州平均水平，以避免此问题。chisq.test() 函数也可以接受矩阵形式的列联表，或由两个因子向量 x 和 y 指定。另一个有用的参数是 correct（默认值为 TRUE），用于指示是否应用连续性校正。对于此检验，我们观察到农村和城市县之间高于全国平均水平的县比例存在统计学显著差异，并在 0.05 水平上拒绝原假设。

```
tex_mean <- mean(county_rates_type$y2020)
county_rates_type$below_tex_avg <-
  ifelse(county_rates_type$y2020 > tex_mean, "Above Texas Ave",
         "Below Texas Ave")
table(county_rates_type$below_tex_avg, county_rates_type$urban)
#>
#>  Rural Urban
#>  Above Texas Ave   84   39
#>  Below Texas Ave  104   21
```

```
chi_sq <- chisq.test(county_rates_type$below_tex_avg,
                       county_rates_type$urban)
chi_sq
#>
#>  Pearson's Chi-squared test with Yates' continuity correction
#>
#>  data:  county_rates_type$below_tex_avg and county_rates_type$urban
#>  X-squared = 7, df = 1, p-value = 0.01
chi_sq$p.value
#> [1] 0.00953
```

### 11.4.1 练习题

重复卡方检验，但这次使用 RUCC 代码代替 urban 列。你应该得到一个 p 值为 0.2799。思考一下可能解释这些结果差异的原因。

```
# Insert your solution here:
```

## 11.5 将假设检验添加到汇总表中

在第 4 章中，我们使用 gt 和 gtsummary 包创建变量的汇总表。在创建分层表（通过添加 by 参数实现）时，我们可以使用 add_p() 函数自动添加跨人群比较的假设检验 p 值。默认情况下，add_p() 函数对连续变量使用 Kruskal-Wallis 秩和检验（当 by 变量有两个水平时则使用 Wilcoxon 秩和检验），对类别变量使用卡方列联表检验（当任何预期单元格计数小于五时则使用 Fisher 精确检验）。所选检验显示为脚注。

```
tbl_summary(tex_itop,
            by = "year",
            include = c(total_rate, white_rate, asian_rate,
                        hispanic_rate, black_rate,
                        native_american_rate),
            label = list(
              total_rate = "Overall",
              white_rate = "White",
              asian_rate = "Asian",
              hispanic_rate = "Hispanic",
              black_rate = "Black",
              native_american_rate = "Native American"),
            statistic = list(all_continuous() ~ "{mean} ({sd})")) %>%
add_p() %>%
modify_header(label = "**Variable**") %>%
as_gt() %>%
cols_width(label ~ "50pt",
everything() ~ "30pt")
```

| 变量 | 2016, N = 254¹ | 2017, N = 254¹ | 2018, N = 254¹ | 2019, N = 254¹ | 2020, N = 254¹ | 2021, N = 254¹ | p 值² |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 总体 | 4.8 (3.0) | 4.9 (4.9) | 5.3 (4.2) | 4.9 (3.3) | 6.2 (14.1) | 5.2 (7.9) | 0.2 |
| 白人 | 4.7 (3.8) | 5.1 (5.8) | 5.4 (6.0) | 5.1 (5.1) | 6.8 (21.3) | 5.5 (8.0) | 0.3 |
| 亚裔 | 7 (32) (46) | 12 | 8 (21) | 7 (20) | 14 (55) | 7 (37) | 0.066 |
| 西班牙裔 | 3.9 (3.7) | 4.7 (6.3) | 4.6 (4.6) | 4.6 (5.0) | 4.6 (5.8) | 4.4 (4.8) | 0.7 |
| 黑人 | 9 (21) (65) | 13 (153) | 26 (153) | 20 (80) | 25 (111) | 26 (121) | 0.13 |
| 美洲原住民 | 5.0 (24.0) | 9.3 (65.0) | 4.9 (17.8) | 2.3 (12.4) | 4.1 (21.1) | 2.5 (10.1) | 0.13 |

¹均值 (标准差)
²Kruskal-Wallis 秩和检验

我们观察到，Kruskal-Wallis 秩和检验被用于比较各年各种族群体的堕胎率。所有报告的 p 值均高于 0.05，因此总体上表明各年堕胎率没有统计学显著变化。

## 11.6 练习

对于以下练习，我们使用 **HDSinRdata** 包中的 `pain` 数据。

```
```r
data(pain)
```
```

- 1. 确定随访信息的存在或缺失是否与初始平均疼痛强度显著相关。结果提示什么？
- 2. 首先，按种族绘制 `PROMIS_PAIN_BEHAVIOR` 图（你可以使用第 8 章中定义的 `PAT_RACE_CAT` 变量）。你观察到了什么？接下来，选择一个适当的检验来确定该变量是否因种族而有显著差异。
- 3. 考察 `CCI_BIN` 和 `MEDICAID_BIN` 之间的关联。这些变量之间是否有显著关系？你会如何描述它们的关系？
- 4. 重新创建图 11.1 中的汇总表。然后，使用适当的检验重新创建 `PROMIS_DEPRESSION`、`PROMIS_ANXIETY` 和 `MEDICAID_BIN` 的 p 值。

| 特征 | 黑人, N = 1,379¹ | 其他, N = 145¹ | 白人, N = 7,271¹ | p 值² |
|---|---:|---:|---:|---:|
| PAIN_INTENSITY_AVERAGE | 8.00 (7.00, 9.00) | 7.00 (6.00, 8.00) | 6.00 (5.00, 8.00) | <0.001 |
| PROMIS_PHYSICAL_FUNCTION | 35 (30, 38) | 35 (31, 41) | 35 (30, 39) | <0.001 |
| PROMIS_PAIN_BEHAVIOR | 62.6 (60.9, 64.3) | 62.3 (59.8, 63.4) | 61.6 (59.0, 63.4) | <0.001 |
| PROMIS_DEPRESSION | 57 (50, 64) | 55 (48, 64) | 55 (48, 62) | 0.004 |
| PROMIS_ANXIETY | 60 (51, 65) | 58 (51, 65) | 56 (50, 63) | <0.001 |
| PROMIS_SLEEP_DISTURB_V1_0 | 63 (56, 68) | 61 (54, 68) | 60 (54, 65) | <0.001 |
| PROMIS_PAIN_INTERFERENCE | 68 (64, 72) | 68 (64, 72) | 67 (63, 72) | <0.001 |
| GH_MENTAL_SCORE | 41 (36, 48) | 44 (34, 51) | 44 (36, 51) | <0.001 |
| GH_PHYSICAL_SCORE | 32 (30, 37) | 35 (30, 40) | 35 (30, 40) | <0.001 |
| AGE_AT_CONTACT | 53 (43, 61) | 48 (37, 58) | 57 (46, 67) | <0.001 |
| BMI | 32 (27, 37) | 27 (23, 33) | 29 (25, 34) | <0.001 |
| PAT_SEX |  |  |  | <0.001 |
| &nbsp;&nbsp;female | 930 (67%) | 92 (63%) | 4,220 (58%) |  |
| &nbsp;&nbsp;male | 449 (33%) | 53 (37%) | 3,051 (42%) |  |
| MEDICAID_BIN | 573 (42%) | 52 (36%) | 1,536 (21%) | <0.001 |

¹中位数 (四分位距); n (%)
²Kruskal-Wallis 秩和检验; Pearson 卡方检验

图 11.1: 分层汇总表。
