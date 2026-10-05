
## 10.1 简单线性回归模型

响应变量 $Y$ 的观测值。由于样本有 $n$ 个观测值，我们令 $i = 1, ..., n$。

在我们的示例中，$n = 114$，$(x_2, y_2) = (259, 184)$。图 10.2 显示了整个样本的散点图，并设置了透明度以检查是否存在过度绘制（overplotting）：

![](img/445742518041017e8f01f11b0c3190d9_393_0.png)

**图 10.2：喷持续与等待时间关系的散点图。**

这种关系似乎是正相关的，并且在某种程度上是线性的。

### 10.1.4 最小二乘法

如果这些变量之间的关联是线性或近似线性的，我们可以将 10.1.2 节描述的线性模型应用于样本中的每个观测值：

```
$$y_1 = \beta_0 + \beta_1 \cdot x_1 + \epsilon_1$$
$$y_2 = \beta_0 + \beta_1 \cdot x_2 + \epsilon_2$$
$$\vdots$$
$$\vdots$$
$$y_n = \beta_0 + \beta_1 \cdot x_n + \epsilon_n$$
```

我们希望能够使用该模型来描述解释变量与响应之间的关系，但参数 $\beta_0$ 和 $\beta_1$ 对我们来说是未知的。我们通过第 5.1 节引入的*最小二乘*方法，利用随机样本来估计这些参数。我们计算截距 $(\beta_0)$ 和斜率 $(\beta_1)$ 的估计量，使得*残差平方和*最小化：

```
$$\sum_{i=1}^{n} [y_i - (\beta_0 + \beta_1 \cdot x_i)]^2$$
```

## 10 回归推理

这是一个优化问题，通过解析法求解它需要微积分，且该主题超出了本书的范围。对于熟悉该方法的人，我们在这里提供解决方案的简述：使用上述表达式找到对 $\beta_0$ 的偏导并使其等于零，找到对 $\beta_1$ 的偏导并使其等于零，然后利用这两个方程求解 $\hat{\beta}_0$ 和 $\hat{\beta}_1$。这些解是第 5.1 节引入的回归系数：$\hat{\beta}_0$ 是 $\beta_0$ 的估计量，$\hat{\beta}_1$ 是 $\beta_1$ 的估计量。它们被称为最小二乘估计量，其数学表达式为：

```
$b_1 = \frac{\sum_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})}{\sum_{i=1}^n (x_i - \bar{x})^2} \quad b_0 = \bar{y} - b_1 \cdot \bar{x}.$
```

此外，$\epsilon_i$ 标准差的*估计量*由给出

```
$s = \sqrt{\frac{\sum_{i=1}^n [y_i - (b_0 + b_1 \cdot x_i)]^2}{n-2}} = \sqrt{\frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{n-2}}$
```

这些等效计算在 R 中使用 `lm()` 函数时完成。对于 `old_faithful_2024` 我们得到：

```r
# 拟合回归模型：
model_1 <- lm(waiting ~ duration, data = old_faithful_2024)

# 获取模型的系数和标准差
coef(model_1)
sigma(model_1)
```

# 表 10.1：Old faithful 间隙回归系数

| 系数 | 数值 |
|---|---|
| (截距) b0 | 79.459 |
| duration b1 | 0.371 |
| s | 20.370 |

基于这些数据并假设线性模型是合适的，我们可以说持续时间每增加一秒，下次等待时间平均增加 0.37 分钟。任何喷发持续时间大于零，因此截距没有实际意义。最后，预计下次喷发的等待时间距离回归线平均 20.37 分钟。

## 10.1 简单线性回归模型

### 10.1.5 最小二乘估计量的性质

最小二乘法通过选择使残差和最小的最小二乘估计量 $b_0$ 和 $b_1$ 来产生最佳拟合直线。$b_0$ 和 $b_1$ 的选择取决于样本。对于每个随机样本，$b_0$ 和 $b_1$ 的值将不同。从这个意义上说，最小二乘估计量 $b_0$ 和 $b_1$ 是随机变量，并且具有非常有用的性质：

- $b_0$ 和 $b_1$ 是 $\beta_0$ 和 $\beta_1$ 的无偏估计量，使用数学符号：$E(b_0) = \beta_0$ 且 $E(b_1) = \beta_1$。这意味着对于随机样本，$b_1$ 将大于 $\beta_1$，对于其他则小于 $\beta_1$。平均而言，$b_1$ 将等于 $\beta_1$。
- $b_0$ 和 $b_1$ 是观测响应 $y_1, y_2, ..., y_n$ 的线性组合。这意味着，对于 $b_1$，存在已知常量 $c_1, c_2, ..., c_n$ 使得 $b_1 = \sum_{i=1}^n c_i y_i$。
- $s^2$ 是方差 $\sigma^2$ 的无偏估计量。

这些性质在下一节执行基于理论的回归推理将是有用的。

### 10.1.6 回归与其他方法

为了结束本节，我们将研究回归与两种不同统计技术的关系。其中一种已经在书中介绍过了，即均值差异，另一个是本文新内容但相关的方差分析（ANOVA）。我们将看到两者如何在回归框架中表示。

### 双样本均值差异

双样本均值差异是一种常用的统计技术，用于比较两个组的均值，如 9.6 节所示。它通常用于确定两组（如治疗组和控制组）之间的平均响应是否存在显著差异。双样本均值差异可以使用表示两组的虚拟变量在回归框架中表示。

让我们再次考虑 `modernverse` 包中的 `movies_sample` 数据框。我们将再次比较“Action”与“Romance”流的平均评分。我们可以使用 `lm()` 拟合带有类型虚拟变量线性模型，然后使用 `get_regression_table()`：

```r
mod_diff_means <- lm(rating ~ genre, data = movies_sample)
get_regression_table(mod_diff_means)
```

## 10.2：双样本均值差异示例的回归表

| 项 | 估计值 | 标准误 | 统计量 | p 值 | 下限 CI | 上限 CI |
|---|---|---|---|---|---|---|
| intercept | 5.28 | 0.265 | 19.92 | 0.000 | 4.746 | 5.80 |
| genre: Romance | 1.05 | 0.364 | 2.88 | 0.005 | 0.321 | 1.77 |

注意 genre: Romance 的 p 值是以下假设检验的 p 值：

> $H_0$: action 和 romance 具有相同的均值
> $H_A$: action 和 romance 具有不同的均值

此 p 值结果与 9.6 节发现的结果高度吻合，但这里我们使用的是基于线性模型的理论方法。genre: Romance 的估计值是“Action”和“Romance”流派之间的观测均值差异，我们在 9.6 中也见过，只是在“Action”类型作为参考水平时符号反转了。

### 方差分析 (ANOVA)

ANOVA 是一种通过查看多个组别之间是否存在统计学显著差异来比较三个或多个组均值的统计技术。ANOVA 可以通过表示类型的虚拟变量在回归框架中表示。假设我们想比较 `spotify_by_genre` 数据框中“country”、“hip-hop”和“rock”流派的流行度（数值）值。在缩小所选集合和感兴趣的行之后，我们使用 `slice_sample()` 函数查看这些数据的几行情况。

```r
spotify_for_anova <- spotify_by_genre |>
select(artists, track_name, popularity, track_genre) |>
filter(track_genre %in%c("country", "hip-hop", "rock"))
```

```r
spotify_for_anova |>
slice_sample(n = 5)
```

# 表 10.3：从 spotify_for_anova 中随机取的五行

| artists | track_name | popularity | track_genre |
|---|---|---|---|
| Counting Crows | Mr. Jones | 0 | rock |
| Luke Bryan | Country Girl (Shake It For Me) | 2 | country |
| Salebarbes | Marcher l'plancher - Live | 42 | country |
| Darius Rucker | Wagon Wheel | 1 | country |
| Billy Joel | Vienna | 78 | rock |
