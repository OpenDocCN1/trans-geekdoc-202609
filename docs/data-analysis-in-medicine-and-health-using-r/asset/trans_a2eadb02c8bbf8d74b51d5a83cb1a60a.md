

## 10.5.5 多变量分析

对于多变量分析，我们将 `cigar_day` 和 `smoke_yrs` 作为病例的预测因子。

```r
pois_case = glm(case - cigar_day + smoke_yrs, data = smoke,
    family = "poisson", offset = log(person_yrs))

summary(pois_case)
```

## Call:
## glm(formula = case - cigar_day + smoke_yrs, family = "poisson",
    data = smoke, offset = log(person_yrs))

## 离离度 (Deviances):
## Min 1Q Median 3Q Max
## -2.1066 -0.9440 -0.3337 0.4366 1.7439

## 系数 (Coefficients):
## Estimate Std. Error z value Pr>|z|)
## (Intercept) -11.31762 1.007492 -11.233 < 2e-16 ***
##   cigar_day 0.064631 0.008601 10.054 < 2e-16 ***
##   smoke_yrs20-24 0.962417 1.015469 0.833 0.40457
##   smoke_yrs25-29 1.718894 1.028420 3.144 0.00167 **
##   smoke_yrs30-34 3.207676 1.020378 3.144 0.0017 **
##   smoke_yrs35-39 3.242776 1.024187 3.166 0.00154 *
##   smoke_yrs40-44 4.208631 1.013726 4.151 3.30e-05 ***
##   smoke_yrs45-49 4.448972 1.017054 4.374 1.22e-05 ***
##   smoke_yrs50-54 4.893674 1.019945 4.798 1.60e-06 ***
##   smoke_yrs55-59 5.372600 1.023404 5.250 1.52e-07 ***

## 显著性代码: 0 '***' 0.001 '** 0.01 * 0.05 . 0.1 1

## (泊松族的离散参数取值为 1)

## 空离度: 445.089，自由度为 62
## 差离离度: 68.015，自由度为 53
## AIC: 207.86
```

从输出来看，两个变量都是肺癌病例发生率的显著预测因子，尽管我们注意到在主要模型中，`smoke_yrs20-24` 和 `smoke_yrs25-29` 哑变量的 p 值显著显著。

## 10.5.6 交互作用

现在，加入 `cigar_day` 和 `smoke_yrs` 之间的二项交互项。从输出中，我们注意到交互项并不显著，`cigar_day` 和交互项的标准误非常大。这可能表明模型存在数值问题（Hosmer et al., 2013）。因此，我们可能会从我们的[模型]中删除交互项：

```r
pois_casex = glm(case - cigar_day * smoke_yrs, data = smoke,
family = "poisson", offset = log(person_yrs))
```

```r
# Warning: glm.fit: fitted rates numerically @ occurred
```

```r
summary(pois_casex)
```

## Call:
## glm(formula = case - cigar_day * smoke_yrs, family = "poisson",
## data = smoke, offset = log(person_yrs))

## 离离度残差 (Deviance Residuals):
## Min 1Q Median Max
## -2.3232 -0.8816 -0.1886 0.4965 1.6851

## 系数 (Coefficients):
## Estimate Std. Error z value Pr(|z|)
## (Intercept) -9.2463 1.0000 -9.246 < 2e-16 ***
## cigar_day -2.8137 319.6350 -0.009 0.992974
## smoke_yrs20-24 -0.7514 1.5114 -0.497 0.619084
## smoke_yrs25-29 -0.2539 1.3518 -0.188 0.851032
## smoke_yrs30-34 1.2493 1.1032 1.132 0.257489
## smoke_yrs35-39 0.5856 1.1660 0.502 0.615438
## smoke_yrs40-44 1.9076 1.0790 1.768 0.036708
## smoke_yrs45-49 2.1070 1.0982 1.919 0.055044
## smoke_yrs50-54 3.0710 1.0761 2.854 0.004318
## smoke_yrs55-59 3.5704 1.0706 3.335 0.000853 ***
## cigar_day:smoke_yrs20-24 2.8609 319.6351 0.009 0.992859
## cigar_day:smoke_yrs25-29 2.8736 319.6350 0.009 0.992827
## cigar_day:smoke_yrs30-34 2.8736 319.6350 0.009 0.992827
## cigar_day:smoke_yrs35-39 2.8997 319.6350 0.009 0.992762
## cigar_day:smoke_yrs40-44 2.8845 319.6350 0.009 0.992980
## cigar_day:smoke_yrs45-49 2.8886 319.6350 0.009 0.992790
## cigar_day:smoke_yrs50-54 2.8869 319.6350 0.009 0.992844
## cigar_day:smoke_yrs55-59 2.8641 319.6350 0.009 0.992851

## 显著性代码: 0 '***' 0.001 '** 0.01 * 0.05 . 0.1 1

## (泊松族的离散参数取值为 1)

## 空离度: 445.089，自由度为 62
## 差离离度: 68.015，自由度为 53
## AIC: 207.86
## 迭代次数: 18

再次，我们通过卡方拟合优检验来评估模型、模型间的 比较、卡方统计量以及标准化残差。

```r
dispersion(pois_case)
```

## 泊松假设拟合优检验 (Goodness-of-fit test for Poisson)
## $chisq 68.0151
## $df 53
## $p.value 0.080266

卡方拟合优的 p 值大于 0.05，表明模型拟合良好。

```r
AIC(pois_case1, pois_case2, pois_case)
```

## df 2 448.5549
## pois_case2 9 308.0129
## pois_case 10 207.8574

AIC 比较明显显示多变量模型 `pois_case` 是最好的，因为它的 AIC 最小。

## 泊松回归发生率

```r
pois_case = glm(case - cigar_day + smoke_yrs, data = smoke,
            family = "poisson",
            offset = log(person_yrs))
```

离散值（即缩放卡方统计量）接近 1。这表明模型拟合良好。

```r
std_res = residuals(pois_case)
abs(std_res) > 1.96
```

最后，我们注意到观测值与预测病例之间只有少数观测值（6, 8 和 18）存在差异：
-1.99530, -2.0255, -2.25382。这显示了拟合回归对数据的解释程度。

## 展示与解释

现在，我们决定最终模型：

```r
pois_case_final = pois_case
```

并使用 `tbl_regression()` 得到结果表格。再次，对系数进行指数化以获得发生率比 IRR。

```r
tbl_regression(pois_case_final, exponentiate = TRUE)
```

| 特征 | IRR | 95% CI | p值 |
|---|---|---|---|
| cigar_day smoke_yrs 15-19 | 1.07 | 1.05, 1.08 | < 0.001 |
| 20-24 | 2.62 | 0.34, 5.9 | 0.4 |
| 25-29 | 5.53 | 0.94, 1.05 | 0.11 |
| 30-34 | 24.7 | 5.23, 442 | 0.002 |
| 35-39 | 25.6 | 5.35, 459 | 0.002 |
| 40-44 | 67.2 | 14.6, 1195 | < 0.001 |
| 45-49 | 85.5 | 18.3, 1525 | < 0.001 |
| 50-54 | 133 | 28.3, 2385 | < 0.001 |
| 55-59 | 215 | 45.1, 3862 | < 0.001 |

> † 发生率比 (Incidence Rate Ratio), CI = 置信区间 (Confidence Interval)

从表中，我们对 IRR 值解释如下：
- 在控制其他变量的情况下，每天多抽一根烟会导致肺癌风险增加 1.07 (95% CI: 1.05, 1.08)。
- 吸烟时长在 30 到 34 年的人患肺癌风险更高，IRR 为 24.7 (95% CI: 5.2)，在控制其他变量的情况下。

我们现在呈现最终结果：

```r
write.csv(pois_case_final, "pois_case.csv")
```

将其导出到：

```r
round(summary(pois_case)$coefficients, 2)
```

## Estimate Std. Error z value Pr(|z|)
## (Intercept) -11.32 1.01 -11.23 < 2e-16 ***
## cigar_day 0.06 0.01 10.05 < 2e-16 ***
## smoke_yrs20-24 0.96 1.02 0.83 0.40457
## smoke_yrs25-29 1.72 1.03 3.144 0.00167 **
## smoke_yrs30-34 3.21 1.02 3.144 0.0017 **
## smoke_yrs35-39 3.24 1.02 3.166 0.00154 *
## smoke_yrs40-44 4.21 1.01 4.151 3.30e-05 ***
## smoke_yrs45-49 4.45 1.02 4.374 1.22e-05 ***
## smoke_yrs50-54 4.89 1.02 4.798 1.60e-06 ***
## smoke_yrs55-59 5.37 1.02 5.250 1.52e-07 ***

并将值代入方程。记住在方程中包含 offset。

```
ln(case) = ln(person_yrs) - 11.32 + 0.06 * cigar_day
+ 0.96 * smoke_yrs(20 - 24) + 1.71 * smoke_yrs(25 - 29)
+ 3.21 * smoke_yrs(30 - 34) + 3.24 * smoke_yrs(35 - 39)
+ 4.21 * smoke_yrs(40 - 44) + 4.45 * smoke_yrs(45 - 49)
+ 4.89 * smoke_yrs(50 - 54) + 5.37 * smoke_yrs(55 - 59)
```

