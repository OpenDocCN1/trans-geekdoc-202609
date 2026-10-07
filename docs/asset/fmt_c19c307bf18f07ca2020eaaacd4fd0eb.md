
- 3. 获取样本均值、标准差、p 值。
- 4. 确定检验结果是否具有显著性（如果拒绝原假设）或不显著（如果未拒绝）。

## 9.1 将置信区间联系假设检验

在使用模拟法时，我们重复基于理论的方法的前两个步骤：

- 1. 用 `$\mu$` 表述原假设和备择假设。
- 2. 根据对第一类错误的容忍度设定显著性水平 `$\alpha$`。

模拟法考虑了这一点，但初次引入学生时，额外的平移操作往往会对该方法的产生产生困惑。为了完整性，我们在这里展示单样本检验的代码和结果。

```
null_dist <- almonds_sample_100 |
specify(response = weight) |
hypothesize(null = "point", mu = 3.6) |
generate(reps = 1000, type = "bootstrap") |
calculate(stat = "mean")
```

```
x_bar_almonds <- almonds_sample_100 |
summarize(sample_mean = mean(weight)) |
select(sample_mean)
null_dist |
get_p_value(obs_stat = x_bar_almonds, direction = "two-sided")
```

```
# A tibble: 1 x 1
p_value
<dbl>
1 0.032
```

p 值为 0.032。这与基于理论的方法得到的 p 值相当相当。使用相同的显著性水平 `$\alpha = 0.04$`，我们再次拒绝了原假设。

注意，在线附录中提供了更多关于模拟法的示例，包括一个使用置换法的单样本假设检验。

## 9.1.2 假设检验与置信区间

即使假设检验和置信区间是两个目标不同的方法，它们也是互补的。例如，在 8.1.4 节中，我们使用样本 `almonds_sample_100` 计算了杏仁均值 `$\mu$` 的 95% 置信区间。基于理论的方法公式如下：

> $$\bar{x} - 1.98\frac{s}{\sqrt{n}}, \bar{x} + 1.98\frac{s}{\sqrt{n}}$$

且 95% 置信区间为：

## 9.1 将置信区间与假设检验相结合

```r
almonds_sample_100 |>
summarize(lower_bound = mean(weight) - 1.98*sd(weight)/sqrt(length(weight)),
upper_bound = mean(weight) + 1.98*sd(weight)/sqrt(length(weight)))
```

```
# A tibble: 1 2
lower_bound upper_bound
<dbl> <dbl>
1 3.61028 3.75372
```

使用基于自助百分法（bootstrap percentile method）的模拟方法，95% 置信区间为

```r
bootstrap_means <- almonds_sample_100 |>
specify(response = weight) |>
ggenerate(reps = 1000, type = "bootstrap") |>
calculate(stat = "mean")
```

```r
bootstrap_means |>
get_confidence_interval(level = 0.95, type = "percentile")
```

```
# A tibble: 1 2
lower_ci upper_ci
<dbl> <dbl>
1 3.61198 3.756
```

95% 置信区间非常相似，更重要的是，这两个区间都不包含 `$\mu = 3.6$` 克。回想一下，当我们进行假设检验时，会拒绝原假设 `H_0 : \mu = 3.6`。使用置信区间得到的结论与假设检验的结论一致。

通常情况下，如果原假设下 `$\mu$` 的值不在置信区间内，则拒绝原假设。请注意，在构建区间时（在我们的示例中为 95%），需要与用于假设检验的显著性水平 `$\alpha$` 保持一致。特别是，当假设检验是双侧的且使用了显著性水平 `$\alpha$` 时，我们计算的置信区间对应等于 `(1-\alpha) \times 100\%` 的置信水平。例如，如果 `$\alpha = 0.05$`，则对应的置信水平为 `(1-0.05)=0.95` 或 `95\%`。这种对应关系是直接的，因为我们计算的置信区间总是双侧的。另一方面，如果使用的假设检验是单侧的（左侧或右侧），则计算置信水平等于 `(1-2\alpha) \times 100\%` 的置信区间。例如，如果 `$\alpha = 0.05$`

本节结束了对单样本假设检验的讨论。请，正如我们在置信区间中所做的那样，我们也可以对比例构建假设检验，并且当使用自助百分法时，我们也可以对其他量进行操作，例如总体中位数、四分位数等。

我们现在关注于为双样本问题构建假设检验。

## 9.2 音乐流行度活动

让我们从研究音乐流派对 Spotify 歌曲流行度的影响开始。

### 9.2.1 金属摇滚比深浩室音乐更流行吗？

想象你是 Spotify 的音乐分析师，你很好奇金属摇滚或深浩室粉丝是否对他们喜爱的流派更有热情。你想确定这两种流派的流行度是否存在显著差异。在这种情况下，流行度由 Spotify 衡量，例如，通过每个流派分类曲目的平均播放次数和最近的用户交互来衡量。（注意，Spotify 实际上并未披露此指标是如何计算的，因此我们必须做出最好的猜测。）这个问题为我们探索假设检验奠定了基础。

金属摇滚以其侵略性的声音、有力的歌声和复杂的乐器为特征，培养了一群忠实的粉丝，他们通常为对该流派的强度和技术水平的深度赞赏感到自豪。另一方面，深浩室音乐以其流畅、灵魂的旋律和稳定的节拍吸引了喜欢该流派宁静和沉浸式氛围的听众，这通常与深夜俱乐部和放松活动有关。

通过比较这两个流派之间的流行度指标，我们可以确定它们是否真的引起了 Spotify 听者的共鸣。这种探索不仅加深了我们对音乐偏好的理解，还作为假设检验原理的实战介绍。

开始分析

`modernrive` 包包含了 `spotify_by_genre` 数据框中按流派分类的歌曲数据。该数据中选择了六种流派（乡村、深浩室、调式、嘻哈、金属摇滚和滚）。你将在学习检查中有机会探索与其他流派以及流行度之间的关系。让我们通过仅关注金属摇滚和深浩室，查看 12 行随机选择的行以及我们感兴趣的列来探索这些数据。注意，我们还进行了分组选择，以便从 `track_genre` 和 `popular_or_not` 的四种可能组合中选择三首歌曲。

```r
spotify_metal_deephouse <- spotify_by_genre |>
filter(track_genre%in%c("metal", "deep-house")) |>
select(track_genre, artists, track_name, popularity, popular_or_not)
spotify_metal_deephouse |>
group_by(track_genre, popular_or_not) |>
sample_n(size = 3)
```

| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track-genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
| deep-house | Sunnovember | Just the Two of Us | 52 | popular |
| deep-house | Tensnake:Nazzereene | Latching Out You | 51 | popular |
| track_genre | artists | track_name | popularity | popular_or_not |
|---|---|---|---|---|
| deep-house | LYOD:Tom Auton | On May | 51 | popular |
