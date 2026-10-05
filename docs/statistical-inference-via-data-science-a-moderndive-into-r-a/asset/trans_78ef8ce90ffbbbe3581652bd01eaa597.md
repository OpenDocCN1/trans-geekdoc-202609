

## 224

## 7 采样

每次我们选择时，任何杏仁被选中的概率都是相同的。获取 25 颗杏仁的样本是进行 25 次试验以获得 25 个重量。然后，这 25 个数字的平均值就是 25 颗杏仁样本的平均重量或均值。这就是我们所说的样本均值。

使用随机变量，现在令 $X_1$ 为代表选取之前第一颗杏仁重量的随机变量，$X_2$ 为第二颗杏仁的重量。这些是随机变量，因为它们可以取碗中可能的杏仁重量值。第一次试验完成后，$X_1$ 的 $t$ 值被实现为所选的第一颗杏仁的重量（克）。我们表示这个值时可以写成 $X_1 = x_1$。第二次试验完成后，$X_2 = x_2$，其中 $x_2$ 是观测到的杏仁重量，依此类推。由于我们的实验是进行 25 次试验然后找到它们的平均值，那么在试验进行之前，这个平均值或均值也可以表示为一个随机变量：

```
$\overline{X} = \frac{X_1 + X_2 + \dots + X_{25}}{25}$
```

观察到 $\overline{X}$ 是这 25 次试验的平均值或均值。这就是为什么 $\overline{X}$ 被称为样本均值。回想在处理比例时，即伯努利试验仅用 0 或 1 表示。在这种背景下，样本比例是样本均值的特殊特例。我们现在使用的试验不再局限于 0 和 1，且样本均值不再是样本比例。例如，让我们关注之前使用的 25 颗杏仁重量样本以及它们的样本均值：almonds_sample

```# A tibble: 25 x 3
# Groups: [1]
  replicate ID weight
<int> <int> <dbl>
1       1 4645     3
2       1 3629     3.9
3       1 4796     4
4       1 2669     3.8
5       1 3488     4.3
6       1  105     4.1
7       1 1762     3.6
8       1 1035     4.2
9       1 4880     3.2
10      1  398      4
# 15 more rows
```

### 7.4 第二次活动：巧克力裹杏仁

通过查看 almonds_sample 帧中的重量，观察 $X_1 = 3.0$ 克，$X_2 = 3.9$ 克，$X_3 = 4.0$ 克，依此类推。如果你查看整个帧，例如在 R 中执行 `View(almonds_sample)`，你可以检查 $X_{23} = 3.3$，$X_{24} = 4.4$ 以及 $X_{25} = 3.6$，因此样本均值为：

$$\bar{X} = \frac{3.0 + 3.9 + 4.0 + \dots + 3.3 + 4.4 + 3.6}{25} = 3.67$$

在 R 中：

```
almonds_sample |
  summarize(sample_mean_weight = mean(weight))
```

```
# A tibble: 1 x 2
  replicate sample_mean_weight
<int> <dbl>
1         3.67
```

所以，一旦这个样本被观测到，随机变量 $\bar{X}$ 被实现为 $\bar{X} = 3.67$，**样本均值**为 3.67 克。注意，$\bar{X}$ 可能的所有值都是从碗中 25 颗杏仁样本中所有可能的样本均值。获得这些样本均值的概率取决于碗中杏仁重量的配置。

当 $\bar{X}$ 构建为给定样本的样本均值时，样本均值的抽样分布正是 $\bar{X}$ 的分布。在这种背景下，回想我们感兴趣确定的内容：

1. $\bar{X}$ *分布*的中心
2. $\bar{X}$ *分布*中*抽样变异*的影响以及样本量对*抽样变异*的影响
3. $\bar{X}$ *分布*的形状

正如我们处理样本比例时一样，我们再次使用模拟来产生 $\bar{X}$（杏仁样本均重量）分布的良好近似。我们还处理了大小为 25、50 和 100 的样本，以学习样本量变化时抽样变异的变化。

这是我们遵循的步骤：

- 我们生成 1000 个样本，
- 计算杏仁重量的样本均值，
- 使用它们绘制直方图。

## 226 7 采样

我们执行三次，并将 `size` 参数分别设置为 25、50 和 100。我们单独运行以下每个代码段，然后比较生成的直方图。

```
# 代码段 1: sample size = 25
# 1.a) 计算 1000 个样本均值，每个均来自大小为 25 的随机样本
virtual_mean_weight_25 <- almonds_bowl |>
  rep_slice_sample(n = 25, reps = 1000) |
  summarize(mean_weight = mean(weight), n = n())
```

```
# 1.b) 通过直方图绘制分布
ggplot(virtual_mean_weight_25, aes(x = mean_weight)) +
  geom_histogram(binwidth = 0.02, boundary = 3.6, color = "white") +
  labs(x = "25 颗杏仁随机样本的样本均值",
  title = "25")
```

```
# 代码段 2: sample size = 50
# 2.a) 计算 1000 个样本均值，每个均来自大小为 50 的随机样本
virtual_mean_weight_50 <- almonds_bowl |>
  rep_slice_sample(n = 50, reps = 1000) |
  summarize(mean_weight = mean(weight), n = n())
```

```
# 2.b) 通过直方图绘制分布
ggplot(virtual_mean_weight_50, aes(x = mean_weight)) +
  geom_histogram(binwidth = 0.02, boundary = 3.6, color = "white") +
  labs(x = "50 颗杏仁随机样本的样本均值",
  title = "50")
```

```
# 代码段 3: sample size = 100
# 3.a) 计算 1000 个样本均值，每个均来自大小为 100 的随机样本
virtual_mean_weight_100 <- almonds_bowl |>
  rep_slice_sample(n = 100, reps = 1000) |
  summarize(mean_weight = mean(weight), n = n())
```

```
# 3.b) 通过直方图绘制分布
ggplot(virtual_mean_weight_100, aes(x = mean_weight)) +
  geom_histogram(binwidth = 0.02, boundary = 3.6, color = "white") +
  labs(x = "100 颗杏仁随机样本的样本均值",
  title = "100")
```

## 259 7.4 第二次活动：巧克力裹杏仁

通过查看 almonds_sample 帧中的重量，观察 $X_1 = 3.0$ 克，$X_2 = 3.9$ 克，$X_3 = 4.0$ 克，依此类推。如果你查看整个帧，例如在 R 中执行 `View(almonds_sample)`，你可以检查 $X_{23} = 3.3$，$X_{24} = 4.4$ 以及 $X_{25} = 3.6$，因此样本均值为：

$$\bar{X} = \frac{3.0 + 3.9 + 4.0 + \dots + 3.3 + 4.4 + 3.6}{25} = 3.67$$

在 R 中：

```
almonds_sample |
  summarize(sample_mean_weight = mean(weight))
```

```
# A tibble: 1 x 2
  replicate sample_mean_weight
<int> <dbl>
1         3.67
```

所以，一旦这个样本被观测到，随机变量 $\bar{X}$ 被实现为 $\bar{X} = 3.67$，**样本均值**为 3.67 克。注意，$\bar{X}$ 可能的所有值都是从碗中 25 颗杏仁样本中所有可能的样本均值。获得这些样本均值的概率取决于碗中杏仁重量的配置。

当 $\bar{X}$ 构建为给定样本的样本均值时，样本均值的抽样分布正是 $\bar{X}$ 的分布。在这种背景下，回想我们感兴趣确定的内容：

1. $\bar{X}$ *分布*的中心
2. $\bar{X}$ *分布*中*抽样变异*的影响以及样本量对*抽样变异*的影响
3. $\bar{X}$ *分布*的形状

正如我们处理样本比例时一样，我们再次使用模拟来产生 $\bar{X}$（杏仁样本均重量）分布的良好近似。我们还处理大小为 25、50 和 100 的样本，以学习样本量变化时抽样变异的变化。

这是我们遵循的步骤：

- 我们生成 1000 个样本，
- 计算杏仁重量的样本均值，
- 使用它们绘制直方图。

## 260 7 采样

我们执行三次，并将 `size` 参数分别设置为 25、50 和 100。我们单独运行以下每个代码段，然后比较生成的直方图。

```
# 代码段 1: sample size = 25
# 1.a) 计算 1000 个样本均值，每个均来自大小为 25 的随机样本
virtual_mean_weight_25 <- almonds_bowl |>
  rep_slice_sample(n = 25, reps = 1000) |
  summarize(mean_weight = mean(weight), n = n())
```

```
# 1.b) 通过直方图绘制分布
ggplot(virtual_mean_weight_25, aes(x = mean_weight)) +
  geom_histogram(binwidth = 0.02, boundary = 3.6, color = "white") +
  labs(x = "25 颗杏仁随机样本的样本均值",
  title = "25")
```

```
# 代码段 2: sample size = 50
# 2.a) 计算 1000 个样本均值，每个均来自大小为 50 的随机样本
virtual_mean_weight_50 <- almonds_bowl |>
  rep_slice_sample(n = 50, reps = 1000) |
  summarize(mean_weight = mean(weight), n = n())
```

```
# 2.b) 通过直方图绘制分布
ggplot(virtual_mean_weight_50, aes(x = mean_weight)) +
  geom_histogram(binwidth = 0.02, boundary = 3.6, color = "white") +
  labs(x = "50 颗杏仁随机样本的样本均值",
  title = "50")
```

```
# 代码段 3: sample size = 100
# 3.a) 计算 1000 个样本均值，每个均来自大小为 100 的随机样本
virtual_mean_weight_100 <- almonds_bowl |>
  rep_slice_sample(n = 100, reps = 1000) |
  summarize(mean_weight = mean(weight), n = n())
```

```
# 3.b) 通过直方图绘制分布
ggplot(virtual_mean_weight_100, aes(x = mean_weight)) +
  geom_histogram(binwidth = 0.02, boundary = 3.6, color = "white") +
  labs(x = "100 颗杏仁随机样本的样本均值",
  title = "100")
```

## 259 7.4 第二次活动：巧克力裹杏仁

通过查看 almonds_sample 帧中的重量，观察 $X_1 = 3.0$ 克，$X_2 = 3.9$ 克，$X_3 = 4.0$ 克，依此类推。如果你查看整个帧，例如在 R 中执行 `View(almonds_sample)`，你可以检查 $X_{23} = 3.3$，$X_{24} = 4.4$ 以及 $X_{25} = 3.6$，因此样本均值为：

$$\bar{X} = \frac{3.0 + 3.9 + 4.0 + \dots + 3.3 + 4.4 + 3.6}{25} = 3.67$$

在 R 中：

```
almonds_sample |
  summarize(sample_mean_weight = mean(weight))
```

```
# A tibble: 1 x 2
  replicate sample_mean_weight
<int> <dbl>
1         3.67
```

所以，一旦这个样本被观测到，随机变量 $\bar{X}$ 被实现为 $\bar{X} = 3.67$，**样本均值**为 3.67 克。注意，$\bar{X}$ 可能的所有值都是从碗中 25 颗杏仁样本中所有可能的样本均值。获得这些样本均值的概率取决于碗中杏仁重量的配置。

当 $\bar{X}$ 构建为给定样本的样本均值时，样本均值的抽样分布正是 $\bar{X}$ 的分布。在这种背景下，回想我们感兴趣确定的内容：

1. $\bar{X}$ *分布*的中心
2. $\bar{X}$ *分布*中*抽样变异*的影响以及样本量对*抽样变异*的影响
3. $\bar{X}$ *分布*的形状

正如我们处理样本比例时一样，我们再次使用模拟来产生 $\bar{X}$（杏仁样本均重量）分布的良好近似。我们还处理大小为 25、50 和 100 的样本，以学习样本量变化时抽样变异的变化。

这是我们遵循的步骤：

- 我们生成 1000 个样本，
- 计算杏仁重量的样本均值，
- 使用它们绘制直方图。

## 261

## n = 25

```
virtual_mean_weight_25 |>
  summarize(E_X_25 = mean(weight), sd = sd(weight))
```

## n = 50

```
virtual_mean_weight_50 |>
  summarize(E_X_50 = mean(weight), sd = sd(weight))
```

## n = 100

```
virtual_mean_weight_100 |>
  summarize(E_X_100 = mean(weight), sd = sd(weight))
```

TABLE 7.1: 比较三个样本量的期望值和标准误差

| 样本量 | 期望值 | 标准误差 |
|---|---|---|
| 25 | 3.65 | 0.077 |
| 50 | 3.65 | 0.053 |
| 100 | 3.65 | 0.038 |

总结：

- 1. 估计期望值是 3.65 或 3.64。这接近或等于 $\mu = 3.64$，整个碗中杏仁的平均重量。
- 2. 标准误差随着样本量的增加而减小。如果我们关注 $n = 100$ 的结果，标准误差为 0.038。与总体标准差 $\sigma = 0.392$ 相比，该标准误差约为 $\sigma$ 的十分之一。同样，当 $n = 25$ 时，标准误差 0.077 约为 $\sigma$ 的五分之一，这种模式在 $n = 50$ 时也成立。

这也是一个理论结果，可以表示为：

> $SE_{\bar{X}} = \frac{\sigma}{\sqrt{n}}$

# 学习检查

(LC7.15) 增加样本量如何影响样本均值的标准误差？

