

## 11.1.1 示例：脑膜炎导致的死亡人数

数据来源于**健康衡量与评估研究所 (IHME)**，并包含了**脑膜炎导致的死亡人数**，以及 1990 年至 2021 年撒哈拉以南非洲（中非共和国、赞比亚比亚、埃斯瓦尼、莱索托和马拉维）地区风险因素——特定颗粒物（PM2.5）和吸烟的两种暴露水平。数据包含在 `{gmsidwR}` 包中。

```r
install.packages("gmsidwR")
# 或
# 安装 book 包的开发版本
devtools::install_github("Fgazzelloni/gmsidwR")
```

让我们来看数据的前几行：

```r
# 加载库和数据
library(tidyverse)
library(gmsidwR)
meningitis %>% head()
# # 一个表格: 6 x 6
# year location
# dbl <chr>
# 1 1990 Eswatini 12.6 669.5 5.91 55.0
# 2 1990 Malawi 52.7 3160. 7.57 78.7
# 3 1990 Zambia 54.9 3101. 6.71 66.9
# 4 1990 Lesotho 10.1 541. 10.6 61.2
# 5 1990 Central African Republic 33.7 2142. 6.61 80.0
# 6 1991 Zambia 55.4 3101. 6.71 66.6
```

**脑膜炎**（Meningitis）是一种严重的全球健康问题，其特征是脑和脊髓周围包膜的炎症。它可以由感染性或非感染性原因引起，通常与高死亡率和长期并发症有关。

在这个示例中，我们探索了环境风险因素——**颗粒物（PM2.5）和吸烟**——如何影响脑膜炎死亡率。这些变量代表了可能减少脑膜炎相关死亡的**聚合暴露水平**。

脑膜炎死亡率在不同国家和随时间变化很大。首先，我们可视化这些比例在 1990 年至 2021 年间撒哈拉以南非洲国家的变化。散点图将显示各国的年度死亡率，而平滑线将揭示整体趋势，帮助在建模之前建立背景认知。

```r
meningitis %>%
  ggplot(aes(x = year, y = deaths)) + 
  geom_line(aes(group = location,
              linetype = location)) + 
  geom_smooth() + 
  labs(title = "脑膜炎导致的死亡人数",
      subtitle = "1990年至2021年的撒哈拉以南非洲",
      y = "死亡率", x = "时间（年份)") + 
  theme(legend.position = "bottom",
      legend.position = element_blank())
```

> 1-脑膜炎，n.d., https://www.who.int/news-room/fact-sheets/detail/meningitis.

# 脑膜炎导致的死亡人数
1990 年至 2021 年撒哈拉以南非洲

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_191_0.png)

- 中非共和国
- 埃斯瓦尼
- 莱索托
- 马拉维
- 赞比亚

**图 11.1** 1990 年至 2021 年撒哈拉以南非洲脑膜炎导致的死亡人数。实线代表揭示整体趋势的平滑线，而其他线代表每个国家的死亡率。

为了了解人口死亡率的估计平均值，可以使用 `lm()` 函数拟合一个简单的线性回归模型，公式为 `deaths - 1`，这意味着我们正在拟合一个仅包含截距的模型（即没有预测变量）。然后我们绘制一个 Q-Q 图²（通过绘制两组分数的对比生成的散点图）来检查残差的正态性。

```r
mod0 <- lm(deaths - 1, data = meningitis)
summary(mod0)
#
# 调用:
# lm(formula = 1, data = meningitis)
#
# 残差:
# Min 1Q Median 3Q Max
# -17.092 -11.372 -3.745 6.822 32.369
#
# 系数:
# Estimate Std. Error t value Pr>|t|
# (Intercept) 25.826 1.062 24.332 <2e-166 ***
#
# 显著性代码: 0 *** 0.001 ** 0.01 * 0.05 . .1 .
```

> ²-Q-Q 图，2025年3月20日，https://en.wikipedia.org/w/index.php?title=Q%E2%80%93_plot&cold=d=12831823.

## 174 通过可视化解释模型结果

```r
#>
> Residual standard error: 13.43 on 159 degrees of freedom
```

该模型的摘要显示截距值为死亡率的估计平均值。我们可以通过直方图查看死亡率的分布：

```r
hist1 <- meningitis %>%
  ggplot(aes(x = deaths)) +
  geom_histogram(bins = 10,
                 fill = "grey70", color = "grey40") +
  geom_vline(aes(intercept = mean(deaths)),
             color = "black",
             size = 2,
             linetype = "dashed") +
  labs(title = "脑膜炎导致死亡率直方图",
       x = "死亡率", y = "计数") +
  theme(legend.position = "bottom",
        legend.title = element_blank())
```

```r
# 为 x 轴添加对数尺度
hist2 <- hist1 +
  scale_x_log10()
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_192_0.png)

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_192_1.png)

(a) 脑膜炎导致死亡率直方图

(b) 脑膜炎导致死亡率直方图（对数尺度）

图 11.2 脑膜炎导致死亡率直方图清楚地显示了数据的右偏。虚线代表死亡率的平均值。

为了研究死亡人数与两个风险因素之间的非线性关系，我们可以使用 {mgcv} 中的 `s()` 函数使用广义相加模型 (GAM)。`s()` 函数用于向模型拟合平滑曲线，这允许我们捕捉预测变量与响应变量之间的非线性关系。

```r
library(mgcv)
mod1 <- gam(deaths ~ s(smoking), data = meningitis)
mod2 <- gam(deaths ~ s(smoking) + s(pm25),
            data = meningitis)
```

总结，模型结果以表格形式呈现，包含每个模型的估计系数，我们可以看到截距以及吸烟和

PM

PM2.5 的系数均为正值且在统计学上显著（p < 0.05），表明这些风险因素的较高水平与较高的脑膜炎死亡率相关。

**表 11.1** 模型的估计系数

| 模型 | Beta0 | Beta1 | Beta2 |
| --- | --- | --- | --- |
| mod0 - 线性模型 | 25.83 | NA | NA |
| mod1 - gam 1个预测变量 | 25.83 | 25.99 | NA |
| mod2 - gam 2个预测变量 | 25.83 | 14.68 | 1.18 |

```r
plot(mod1)
plot(mod2)
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_193_0.png)

(a) **吸烟** - mod1

(b) **吸烟** - mod2

(c) **PM2.5** - mod2

**图 11.3** 平滑值：吸烟和 PM2.5

进一步的比较通过 AIC 函数进行：

```r
AIC(mod1, mod2)
> df AIC
> mod1 1102.339 10.6
> mod2 1060.531 16.1
```

第二个模型 (mod2) 明显优于第一个 (mod1)：AIC 下降了约 42 点，这是一个强有证据（>10）。

现在我们在模型中引入年份变量，以解释数据中的时间趋势。我们还可以引入年份和国家之间的交互项。`s(year, by = location)` 项允许为每个国家的水平均拟合平滑项。

我们将 location 设置为因子：

```r
meningitis$location <- as.factor(meningitis$location)
```

然后我们可以拟合第三个模型：

```r
par(mfrow = c(2, 3))
for (i in 1:5) {
  plot(mod3, select = i + 2, shade = TRUE,
       main = levels(meningitis$location)[i])
}
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_194_0.png)

图 11.4 各国家的脑膜炎死亡率。实线代表揭示整体趋势的平滑线，而其他线代表每个国家的死亡率。

# 表 11.2 模型指标

| 模型 | R2 | DevExp |
| --- | --- | --- |
| mod0 - 线性模型 | 0.7030403 | 0.7190617 |
| mod1 - gam 1个预测变量 | 0.7784592 | 0.7981222 |
| mod2 - gam 2个预测变量 | 0.9957811 | 0.9968419 |

结论，我们从仅包含吸烟作为影响因素的广义相加模型开始，然后拟合了一个将吸烟和 PM2.5 都建模为平滑函数的第二个模型。第二个模型解释了近 80% 的死亡率变化。然而，通过纳入国家特定的非线性时间趋势，我们极大地提高了拟合效果，解释率超过了 99%。这强调了在健康数据中考虑时间性和空间结构的重要性，特别是在对跨国长期趋势建模时。

关于吸烟和 PM2.5 对脑膜炎死亡的暴露效应仍需考虑。

