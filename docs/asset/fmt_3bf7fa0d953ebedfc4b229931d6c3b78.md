
Residuals:

| Min 1Q Median 3Q Max |
|---|---|---|---|---|
| -10.375 | -3.875 | 1.312 | 3.969 | 7.000 |

Coefficients:

| Estimate Std. Error t value Pr(>|t|) |
|---|---|---|---|
| (Intercept) | 31.375 | 2.040 | 15.38 | 3.64e-10 *** |
| Gender | -6.675 | 2.884 | -2.21 | 0.0442 * |

Signif. codes: 0 **** .001 *** .01 ** .05 * .01 ' 1

Residual standard error: 5.769 on 14 degrees of freedom
Multiple R-squared: 0.2587, Adjusted R-squared: 0.2057
F-statistic: 4.885 on 1 and 14 DF, p-value: 0.04424

784 选定练习答案

注意，两种分析的方差分析（ANOVA）表是相同的；在两种情况下，性别变量都解释了均值所有的变异。然而，斜率系数是不相同的。在第一次分析中的效应（EFFECT）系数为 -3.188，表示男性的均值比男女平均均值低 3.188 个单位；而第二次分析中的虚拟（DUMMY）系数为 -6.375，表示男性的得分均值比女性的得分均值低 6.375 个单位。

23.3 (a) 为了对一个变量三个水平进行编码，我们需要两个虚拟变量。在 R 中不需要手动生成这些变量，考虑它们的作用是有帮助的：

| | 效应编码 (Effect Coding) | 虚拟编码 (Dummy Coding) | |
|---|---|---|---|
| 17 | 1 | 0 | 0 |
| 33 | 1 | 0 | 0 |
| 26 | 1 | 0 | 0 |
| 27 | 1 | 0 | 0 |
| 21 | 1 | 0 | 0 |
| 11 | 0 | 1 | 0 |
| 18 | 0 | 1 | 0 |
| 14 | 0 | 1 | 1 |
| 18 | 0 | 1 | 1 |
| 9 | -1 | 1 | 0 |
| 12 | -1 | 1 | 0 |
| 10 | -1 | 1 | 0 |
| 8 | -1 | 1 | 0 |
| 14 | -1 | 1 | 0 | - c > `summary(lm(data = dat, Y ~ C, contrasts = list(C = contr.sum)))`

```
Call:

lm(formula = Y ~ C, data = dat, contrasts = list(C = contr.sum))
```

Residuals:
| Min Std. Median 3Q Max |
|---|---|---|---|---|
| -7.800 | -2.350 | 0.300 | 2.612 | 8.200 |

Coefficients:
| Estimate Std. Error t value Pr(|t|) |
|---|---|---|---|
| (Intercept) | 16.883 | 1.165 | 14.491 | 1.64e-08 |
| C1 | 7.917 | 1.616 | 4.900 | 0.00472 *** |
| C2 | -1.633 | 1.710 | -0.955 | 0.35985

Signif. codes: 0 **** .001 *** .01 (*) .05 (.) 1Residual standard error: 4.335 on 11 degrees of freedom
Multiple R-squared: 0.716, Adjusted R-squared: 0.664
F-statistic: 13.87 on 2 and 11, p-value: 0.00984

785 选定练习答案

> `dat$C <- relevel(dat$C,ref = 3)`
> `summary(lm(data = dat, Y ~ C))`

Call:
`lm(formula = Y ~ C, data = dat)`

Residuals:

| Min 1Q Median 3Q Max |
|---|---|---|---|---|
| -7.800 | -2.350 | 0.300 | 2.612 | 8.200 |

Coefficients:

| Estimate Std. Error t value Pr(>|t|) |
|---|---|---|---|
| (Intercept) | 10.600 | 1.939 | 5.467 | 0.00196 *** |
| C1 | 14.200 | 2.742 | 5.179 | 0.00304 |
| C2 | 4.650 | 2.908 | 1.599 | 0.13814 |

Signif. codes: 0 **** .001 *** .01 ** .05 (.) 1Residual standard error: 4.350 on 11 degrees of freedom
Multiple R-squared: 0.716, Adjusted R-squared: 0.664
F-statistic: 13.87 on 2 and 11, p-value: 0.00984

两种分析的方差分析表是相同的。(d) 系数的解释取决于编码方案。对于效应编码，$b_0$ = $Y_i$ 组的均值；$b_1$ = 组 1 的均值 - $b_0$；$b_2$ = 组 2 的均值 - $b_0$。对于虚拟编码，参考组设置为 $Y_3，$b_0$ = 组 3 的均值；$b_1$ = 组 1 的均值 - $b_0$；$b_2$ = 组 2 的均值 - $b_0$。

- 集合 1 是合适的——效应编码。
- 集合 2 是合适的——虚拟编码。
- 集合 3 使用建议的虚拟变量是合适的，会产生 $SS_{between}$，尽管系数是可以解释的。
- 集合 4 是不合适的，因为 $X_i$ 的值只是常数 3。$X_1$ 和 $X_2$ 完全相关，所以我们实际上只有一个虚拟变量。
- 集合 5 是不合适的。只有一个虚拟变量，只有当条件均值与 $X_1$ 的值相关时，$SS_{between}$ 才会等于 $SS_{within}$。
- 集合 6 是不合适的，因为有三个虚拟变量，但条件效应有两个自由度。将 $Y$ 回对 $X_1$ 和 $X_2$ 的任意两个将产生 $SS_{between}=SS_{between}$。

- 27.7 (a) `ANOVA(data = dat, Y ~ AX, contrasts = list(A = contr.sum)), type=3`

Response:

| Sum Sq DF F value Pr(>F) |
|---|---|---|---|
| (Intercept) | 0.00079 | 1 | 0.0382 | 0.8459 |
| A | 0.04765 | 2 | 1.1463 | 0.3275 |
| X | 0.48042 | 23 | 21.136 | 1.983e-05 *** |
| A:X | 0.01416 | 2 | 0.3407 | 0.7133 |
| Residuals | 0.8729 | 42 |

(b) 对四个虚拟变量和 X 回归，$R^2 = .4406$:

> `summary(lm(data = dat, Y ~ X+X1+X2+X3+X4), type=3)`

Call:
`lm(formula = Y ~ X + X1 + X2 + X3 + X4, data = dat)`

Residuals:

| Min 1Q Median 3Q Max |
|---|---|---|---|---|
| -0.30663 | -0.087095 | 0.000237 | 0.07195 | 0.304853 |

Coefficients:

| Estimate Std. Error t value Pr(|t|) |
|---|---|---|---|
| (Intercept) | 0.171282 | 0.153311 | 1.117 | 0.2703 |
| X | 0.005881 | 0.002406 | 2.415 | 0.0202 * |
| X1 | -0.240689 | 0.240925 | -0.999 | 0.3235 |
| X2 | -0.330506 | 0.226688 | -1.457 | 0.1526 |
| X3 | 0.002048 | 0.003990 | 0.524 | 0.6030 |
| X4 | 0.002765 | 0.003453 | 0.801 | 0.4277 |

--
Signif. codes: 0 **** .001 *** .01 ** .05 (.) 1

Residual standard error: 0.142 on 44 degrees of freedom
Multiple R-squared: 0.4315, Adjusted R-squared: 0.3927
F-statistic: 6.615 on 3 and 44, p-value: 0.00126

788 道选练习题解答

## 24.5 将 Y 回归对 X

```
> anova(lm(data=dat,Y~X))
```

方差分析表

响应：Y

| Df | Sq Mean Sq F value | Pr(>F) |
|---|---|---|---|---|---|
| X | 1 | 610.23 | 610.23 | 42.689 | 6.887e-06 *** |
| Residuals | 16 | 228.71 | 14.29 | | |

将 Y 回归对 X，以及 A 的虚拟变量，

```
> anova(lm(data = dat, Y~ X+X1+X2))
```

方差分析表

响应：Y

| Df | Sq Mean Sq F value | Pr(>F) |
|---|---|---|---|---|---|
| X | 1 | 610.23 | 610.23 | 186.159 | 1.771e-09 *** |
| X1 | 1 | 140.77 | 140.77 | 42.945 | 1.284e-05 *** |
| X2 | 1 | 42.05 | 42.05 | 12.828 | 0.003007 ** |
| Residuals | 14 | 45.89 | 3.28 | | |

从第一次分析中，我们得到 $R_{Y,X}^{SS} = 610.23$。从第二次分析中，我们得到 $R_{Y,X,A}^{SS} = 610.23+140.77+42.05 = 793.05$，因此：

> `$SS_{A(adj)} = (1 - R_{Y,X,A}^2)SS_{YY} = 793.05 - 610.23 = 182.82$`

以及

> `$SS_{S/A(adj)} = (1 - R_{Y,X}^2)SS_{SY} = 45.89$`

ANCOVA 统计量为 $F(2,14) = \frac{MS_{A(adj)}}{MS_{S/A(adj)}} {(a-1)/(N-a-1)} = 27.886$。

这是我们在 24.2 中计算的 F。

# 第 25 章

25.3 $f^2 = \frac{\Delta R^2}{1-R^2} = .021$，这是因为抑郁症（sqrtBdiplus）对女性职业和家庭体力活动的回归得出的 $R^2 = .024$。加入空闲时间体力活动使 $R^2$ 增加到 .044。Cohen 的指南对于小、中、大效应量分别为 .02、.15 和 .35，因此该效应属于中等到中等偏大水平。

25.5 看起来全职员工（status = 1）中男性的比例更高，而兼职员工中女性较多。

### A tibble: 4 x 3

### Groups: sex [Z]

| sex | employed | n(O) |
|---|---|---|
| 1 | 1 | 252 |
| 2 | 2 | 33 |
| 1 | 1 | 184 |
| 1 | 2 | 59 |

我们可以使用独立性卡方检验，发现受佣状态和性别不是独立的：

```
> chisq_test(dat$employed,dat$sex)

# A tibble: 1 x 6

n statistic p df method p.signif

* <int> <dbl <int> <chr>

1 528 13.8 0.000199 1 Chi-square test ***
```

或者，我们可以使用相关性。测试相关性通常不测试独立性，但当两个变量都是二分类变量时，它可以测试：

```
> cor.test(dat$employed,dat$sex)

Pearson 乘积矩相关
```

data: `dat$employed` and `dat$sex`
t = 3.8819, df = 526, p-value = 0.000168
备假设：真实相关性不等于 0
95% 置信区间: 0.0827337 0.248677
样本估计:
```
cor.166887
```
