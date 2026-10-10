
### 19.7
我们使用`t`统计量（见表 19.1）测试斜率差异是否显著：$t = \frac{b_{11} - b_{12}}{SE(b_{11} - b_{12})}$，$s_e^2 = \frac{1}{\frac{1}{SS_{X1}} + \frac{1}{SS_{X2}}} = \frac{1}{\frac{1}{200} + \frac{1}{200}}$

$s_1^2 = 15.5$ 和 $s_2^2 = 12.2$ 的加权平均值为 194.545，所以 $s_e = 13.95$。代入 $t$ 方程，得到 $t(76) = 7.17$，我们可以拒绝斜率相等的假设。

### 19.9
R 为 .40 告诉我们，在样本中，实际 Y 分数关于回归线的变异仅占其总变异的 84%；回归所解释的变异比例为 $.40^2 = .16$。

## 第20章

### 20.1
(a)

| var | var2 | cor |
| :--- | :--- | :--- |
| Number | 0.76 | 1.91e-05 |
| Difficulty | 0.34 | 1.05e-01 |

| Number | Difficulty | sd |
| :--- | :--- | :--- |
| 1 | 493 | 10.5 |
| 2 | 532 | 35.7 |
| 3 | 546 | 63.0 |
| 4 | 583 | 40.5 |
| 5 | 584 | 30.4 |
| 6 | 647 | 44.7 |
| 7 | 626 | 70.5 |
| 8 | 670 | 40.0 |

(b) `Y = 402.375 + 22.825 Number + 4.575 Difficulty`。对于 `Number`, `t(21) = 6.192`, `p < .001`；对于 `Difficulty`, `t(21) = 2.775`, `p = .011`。在 ANOVA 中，`Number` 和 `Difficulty` 都显著，但它们的交互作用不显著。回归的结果并不同于 ANOVA。回归预测一个变量在保持另一个变量不变的情况下与总体是否为 0。在 ANOVA 中，`Number` 的检验了总体均值是否相同。

(c) 估计值 `β0`, `β1`, `β2` 分别为 402.375, 22.825 和 4.575，CI 所示。总体真实值都在 95% CI 内。

```
> confint(data=dat, Time ~Difficulty))
             2.5%     97.5%
(Intercept) 335.9871  468.7620
Number     15.1528  30.40972
Difficulty  1.14676   8.03214
```

### 20.3
对 `X1` 和 `X2` 回归 `Y` 得到方程 `Y = -16.294 + 9.916X1 + 9.941X2`，

(b) 在初始回归中，`X1` 和 `X2` 的系数不同于0，`t(14) = 2.420`, `p = .030` 和 `t(14) = 3.378`, `p = .005`。因此，两个变量都应包含。`X1` 和 `X2` 相关 `r=.39`，但相关性不显著 (`p=.125`)。

### 20.5
$R^2 = .25$ 因为有四个参数（截距 + 三斜率）和四个观测值，模型是饱和的。

```
> predict(lm(data=dat, Y-X1+X2+X3))
      1      2      3      4      5      6      7
0.150000 0.090000 -3.360000 -1.340000 -2.246814 3.856283 2.366806
      8      9     10     11     12     13     14
3.8305393 -4.877584 -5.412753 -5.067257 -5.781341 -0.317699 1.716259
```

前四个案例的预测值（精确到七位小数）与观测 Y 值相同。

(c) 如果将预测值存储在 `p` 中并将原始数据存储在 `dat` 中，`cor(p[1:4], dat[1:4])` 将前四个案例观测Y值和预测Y值的相关性为1.0，而 `cor(p[5:15], dat[5:15])` 将剩余11个案例的相关性。第二个相关性仅为 .244，因为 N/p 比例很小（示例中为4/1）。

### 20.7
使用名为 `datcv` 的 data frame 中的选定数据

```
> model.jack <- lm(tc ~, data = datcv)
> delpred <- datcv$tc - predict(model.jack, type="predictive")
> cor.test(delpred, datcv$tc)
```

Pearson's product-moment correlation

```
data: delpred and datcv$tc
t = 7.6727, df = 179, p-value = 1.045e-12
alternative hypothesis: true correlation is not equal to 0
95 percent confidence interval:
0.3791371 0.599817
sample estimates:
cor
```

### 20.9
`TC = 161.9 + .010 age + 2.14 bmi`, $R^2 = .046$ 只有 `bmi` 是显著预测因子：`t(180) = 2.948`, `p = .004`。Adjusted R-squared: 0.03547。

## 第21章

### 21.1
(a) `> summary(aov(data = dat, performance ~ dosage))`

| Df Sum Mean Sq F value Pr(>F) |
| :--- | :--- | :--- | :--- | :--- |
| dosage 3 | 12.31 | 44.10 | 7.29 | 0.00305 ** |
| Residuals 15 | 90.74 | 6.05 | | |

(b) `> summary(lm(data = dat, performance ~ dosage))`

```
Call:
lm(formula = performance ~ dosage, data = dat)
```

```
Residuals:
Min Q1 Median 3Q Max
-4.4778 -2.1458 1.3250 5.6750 5.278
```

Coefficients:
Estimate Std. Error t Pr<|t| |

| :--- | :--- | :--- | :--- |
| (Intercept) 5.2666 1.7741 2.965 | 0.0068 ** |
| dosage 0.1652 0.0643 2.561 | 0.02023 |

```
Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * .1 ' 1
Residual standard error: 3.077 on 17 degrees of freedom
Multiple R-squared: 0.2785, Adjusted R-squared: 0.236
F-statistic: 6.561 on 1 and 17, p-value: 0.02023

> anova(data = dat, performance ~ dosage)
Analysis of Variance Table
```

Response: performance

Df Mean Sq F Pr(>F)

dosage   3 44.10 7.29 0.00305 **

Residuals 17 9.467

(c) 从 ANOVA 找到 $SS_{pure\_error}$ = 90.74.$SS_{nonlinearity} - SS_{pure\_error} = 160.94 - 90.74 = 70.2$。df_{nonlinearity} - df_{residual} = 17 - 15 = 2$。所以，$F(2,15) = \frac{MS_{nonlinearity}}{MS_{pure\_error}} = (70.2) / (90.74 / 15) = 5.8$. - pf(5.8, 2, 15) = p = .0136$。存在显著的线性效应。

(d) `dosage` 和 `doseq` 都有显著的部分斜率，因此存在显著的线性和二次（曲率最小）成分：-4.71 + 1.12 $dosage - .02doseq$。

**21.3** 在每情况下，计算 $f^2 = \frac{\Delta R^2}{1-R^2}$ 然后使用 `G*Power`。

(a) $f^2 = .37/.429$ 所以 $N = 39$。

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_798_0.png)

(b) $N = 62$。

(c) $N = 130$。

### 21.5
计算 $f^2 = \frac{\Delta R^2}{1-R^2} = .05/(1-.35) = 0.77$，然后使用 G*Power 找到 $N^* = 139$。如果预测变量是随机的，$N = N^* + p - 1 = 139 + 7 - 1 = 145$。

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_799_0.png)

### 21.7
如果将 $X_s$ 加入回归方程会导致 $R^2$ 从 .21 增加到 .27，则 $\Delta R^2 = .06$且 $f^2 = \frac{\Delta R^2}{1-R^2} = .06 / (1-.27) = .082$。为了测试引入 $X_s$ 带来的预测增量是否显著，使用部分 $F$ 比率：

# 780 选定练习题答案

$F = \frac{R_{Y_{1234}}^2 - R_{Y_{123}}^2}{(1-R_{Y_{1234}}^2) / (N-p-1)} = \frac{.06}{(1-.27)/35} = 2.877$。当 $\alpha = .05$ 时，$F(1,35)$ 的临界值为 4.121，因此 $X_i$ 的系数不显著。G*Power 我们需要 $N=98$ 来涵盖较低的教育水平以测试 $X_i$，因此 $N=98+4-1=101$。

### 21.9
老年人的受教育水平往往较低；年龄与受教育程度之间的相关性为 $p = .22$。这意味着通过受教育程度衡量的“教育”效应确实再次出现了。如果我们对受教育程度和年龄进行回归，发现 `tc = 146.06-2.33` 受教育程度 `+1.70`，且受教育程度的偏斜系数不显著。为了解决这个问题，我们希望确定在年龄相近的人群中是否存在教育效应。数据中的一个变量是 `agegrp`，它有四个水平：小于等于40岁、40–49岁、50–59岁、大于等于60岁。`tc` 对受教育程度的回归在任何组中均未达到显著水平（尽管注意样本量小得多）。从这些分析来看，所谓的效应很大可能是由于教育上的年龄差异。

## 第 22 章

### 22.1
(a) `> summary(aov(dat, performance ~ as.factor(dose)))`

| Df | Sum Sq | Mean Sq | F value | Pr>(F) |
| :--- | :--- | :--- | :--- | :--- |
| as.factor(dose) | 3 | 132.31 | 44.10 | 7.29 | 0.00305 ** |
| Residuals | 15 | 90.74 | 6.05 | |

+ (b) `> anova(lm(data = dat, performance ~ dose + dose + dosecb))`

方差分析表

响应变量: performance

| Df | Sum Sq | Mean Sq | F | Pr>(F) |
| :--- | :--- | :--- | :--- | :--- |
| dose | 1 | 62.110 | 62.110 | 10.267 | 0.05912 ** |
| doseq | 1 | 65.375 | 65.375 | 10.807 | 0.00496 ** |
| dosecb | 1 | 4.821 | 4.821 | 0.797 | 0.368685 |

Performance = 3.0-.105 dose +.037 dose -.001 dosecb。只有 dose 显著。在只有两个预测变量的情况下，performance = -4.71 +1.12 dose -.02 dosecb。

### 22.3
在这些数据中，老年人的受教育水平往往显著较低：受教育程度对年龄进行回归，我们看到 schooling = 6.37-.02 age (p = .001)。女性的受教育程度也显著低于男性——受教育程度对性别进行回归，其中 sex = 1 表示女性身份，我们看到 schooling = 5.69-.545，因此女性参与者的受教育水平较低（p < .001）。年龄与性别的交互作用作为回归预测并不显著（p = .20）。

### 22.5
(a) 对于男性，`tc = 16.19+.010 age + 2.14 bmi`，其中年龄的系数不显著 (p = .97)，`bmi` 的系数显著 (p = .004);$R^2 = .046$。对于女性，`tc = 92.24 +1.74 age + 1.47 bmi`，其中年龄 (p < .001) 和 `bmi` 的系数显著 (p = .007);$R^2 = .272$。

(B) 我们预计 `tc` 与 `bmiplusnorm05` 的相关性会比与 `bmi` 的相关性小，尽管考虑到值是从分布中随机选择的，这种情况并不一定发生。在一个随机样本中，女性与 `tc` 的相关性为：`bmi` 为 .23，`bmiplusnorm05` 为 .21；男性的相关性分别为 .21 和 .08。当然，不同的随机样本会导致不同的值。

额外的测量误差越大，变量作为预测变量的能力越弱，它们的回归系数就越小。同样，不同的随机样本会导致不同的值。

## 第23章

### 23.1
(a) r = .509, p = .044.

(b) $t' (13.9) = -2.21, p = .044.

(c) 我们需要一个虚拟变量，因为这些数据中性别（Gender）只有两个水平：(i) 男性 = 1，女性 = -1（或反之）；(ii) 男性 = 0，女性 = 1（或反之）。

(d) (i) 效应编码（Effect coding）：

```
> summary(lm(data = dat,Y ~ Gender))
```

```
Call:
lm(formula = Y ~ Gender, data = dat)
```

Residuals:

| Min 1Q Median 3Q Max |
|---|---|---|---|---|
| -10.375 | -3.875 | 1.312 | 3.969 | 7.000 |

Coefficients:

| Estimate Std. Error t value Pr(>|t|) |
|---|---|---|---|
| (Intercept) | 28.188 | 1.442 | 19.55 | 1.47e-11 *** |
| Gender | -3.188 | 1.442 | -2.21 | 0.0442 * |

Signif. codes: 0 **** .001 *** .01 ** .05 * .01 ' 1

Residual standard error: 5.769 on 14 degrees of freedom
Multiple R-squared: 0.2587, Adjusted R-squared: 0.2057
F-statistic: 4.885 on 1 and 14 DF, p-value: 0.04424

(ii) 虚拟编码（Dummy Coding）：

```
> summary(lm(data = dat,Y ~ Gender))
```

```
Call:
lm(formula = Y ~ Gender, data = dat)
```
