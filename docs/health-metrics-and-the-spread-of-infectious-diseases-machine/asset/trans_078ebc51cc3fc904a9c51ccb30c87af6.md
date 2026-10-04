
# 按位置和年份划分结核病 YLDs

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_172_0.png)

**图 9.11** 按位置和年份划分结核病 YLDs

2019年全球地区结核病的残疾权重设定为 0.333。持续时间源自 GBD 2021 并基于系统评价，针对已治疗和未治疗的病例进行了调整：估计未治疗病例的持续时间为3 年，已治疗病例为 6 个月。

公式 *YLDs ~ Prevalence + year + (1|location)* 规定了一个线性混合效应模型，用于预测结核病导致的残疾生存年限（YLDs）。该模型包含了流行率（prevalence）和年份的固定效应，以及位置的随机截距 ((1|location))。这允许在考虑位置变异性的同时估计 YLDs。

```r
# 定义公式
formula <- YLDs ~ Prevalence + year + (1 | location)

# 拟合混合效应模型
model <- lmer(formula, data = tuberculosis)
model
# REML 拟合线性混合模型 ['lmerMod']
# 公式: YLDs ~ Prevalence + year + (1 | location)
# 数据: tuberculosis
# 收敛时的 REML 准则: 34.6921
# 随机效应:
# Groups Name Std.Dev.
# location (Intercept) 0.6202
# Residual 0.1773
# 观测值: 12, groups: 6
# 固定效应:
```

> ⁴Edine W. Tiersma et al., “Natural History of Tuberculosis: Duration and Fatality of Untreated Pulmonary Tuberculosis in HIV Negative Patients: A Systematic Review,” PLOS ONE 6, no. 4 (April, 2011): e17601, doi:10.1371/journal.pone.017601.

# 示例：结核病导致的 YLDs - 混合效应模型

```r
# (Intercept) Prevalence year
# 67.7989019 0.0001619 -0.0336388
# 拟合警告:
# 某些预测变量的尺度差异巨大：考虑重新缩放

# 提取固定效应
fixed_effects <- fixef(model)

fixed_effects
# (Intercept) Prevalence year
# 67.798018583 0.001619458 -0.0336387726
```

仅考虑固定效应，模型函数变为：

```r
$YLDs = 67.79889 + 0.00016 * Prevalence - 0.03364 * year  (9.12)
```

特别是在流行率方面，系数 0.00016 意味着流行率每增加一个单位，YLDs 增加 0.00016；而年份系数 -0.03364 意味着每年增加一个单位，YLDs 减少 0.03364。

查看随机效应，我们可以看到模型如何解释不同位置之间的变异。

```r
# 提取随机效应
random_effects <- ranef(model)

random_effects
$location
# (Intercept)
# Canada -0.40736806
# Germany 0.44667833
# Italy -0.09317570
# Japan -0.06401586
# UK 0.87190488
# US -0.75023060
```

```r
# 带有 "location" 的条件方差
```

带有每个位置随机效应的模型函数变为：

```r
$YLDs = 67.79889
+ 0.00016 * Prevalence
- 0.03365 * year  (9.13)
```

然后，使用混合效应模型对观测数据和新数据对结核病导致的 YLDs 进行预测。将预测值与实际 YLDs 进行比较，以评估模型的性能。

```r
# 预测观测数据的 YLDs
predictions <- predict(model,
  tuberculosis,
  allow.new.levels = TRUE)
```

156

预测建模及其他

tuberculosis$predicted_YLD <- predictions

结核病导致的预测 YLDs 与估计 YLDs 如下图所示：

```r
ggplot(tuberculosis) %>%
  filter(!location=="Global") %>%
  aes(x = YLDs, y = predicted_YLD,
      group = location) +
  geom_point(aes(shape = factor(location))) +
  geom_abline() +
  facet_wrap(~ year) +
  labs(title = "结核病导致的 YLDs",
      subtitle = "预测 vs 估计",
      x = "YLDs",
      y = "预测 YLDs",
      shape = "位置")
```

# 结核病导致的 YLDs

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_174_0.png)

图 9.12 结核病预测与估计的 YLDs

该图显示了预测值与估计 YLDs 之间拟合得良好，表明模型能够捕捉数据中的潜在趋势。误差计算为预测值与估计 YLDs 之间的绝对差，除以估计 YLDs，并乘以 100 以百分比形式表示。

```r
tuberculosis %>%
  mutate(ape = abs(predicted_YLD - YLDs) / YLDs * 100) %>%
  summarise(mape = mean(ape, na.rm = TRUE))
#> A tibble: 1 x 1
#>
#> mape
#> <dbl>
#> 1 6.21
```

# 示例：结核病导致的 YLDs - 混合效应模型 157

平均绝对百分比误差 (MAPE) 为 6.2%，表明模型能够以合理的准确水平预测 YLDs。

残差平方和 (RSE) 的计算方法为残差平方和的根除以观测值数量减去模型中的参数数量。RSE 是衡量模型与数据拟合程度的指标，值越低表示拟合越良好。

```r
tuberculosis %>%
  mutate(residuals) = predicted_YLD - YLDs) %>%
  summarise(
  rse = sqrt(sum(residuals^2) / (nrow(tuberculosis) - length(fixef(model))))
# # A tibble: 1 x 1
#> rse
#> # 1 0.126
```

2021 年的 RSE 为 0.126147，表明模型能够以合理的准确水平预测 YLDs。

让我们使用留出的 2021 年数据来拟合模型。

```r
tuberculosis_2021 <- tidyr::g7_hmetrics %>%
  filter(measure %in% c("Prevalence",
  "YLDs"),
  str_detect(cause, "Tuberculosis"),
  year == 2021,
  !location == "Global",
  metric == "Rate") %>%
  pivot_wider(names_from = measure, values_from = val)
# A tibble: 6 x 4
#   year location Prevalence YLDs
# # Rows: 6 x 4
#  $ year location   dbl     dbl
#  1 2021 Canada     0.0002 67.798
#  2 2021 Germany   0.0002 67.798
#  3 2021 Italy     0.0002 67.798
#  4 2021 Japan     0.0002 67.764
#  5 2021 UK        0.0002 67.871
#  6 2021 US        0.0002 67.750
```
