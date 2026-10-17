
# 寿命损失年 (YLLs) 计算

基于这些思想，Mary Demsey 在1947年将该概念正式化，以评估结核病的负担，并创造了“寿命损失年”（YLLs）这一术语。该指标专门用于识别需要改进的领域，以减少损失并防止过早死亡。她的工作使 YLLs 成为理解和解决早死对人口健康产生的不比例影响的关键工具。

过早丧失对社会的影响不仅限于失去亲人的悲痛苦；它还包括失去生产性劳动力成员的经济和社会成本。而过早死亡会给社区带来沉重负担，影响整体经济稳定和社会福祉。

## 标准公式

```
YLL = N * le (3.1)
```

在公式 3.1 中，`N` 是早死人数，`le` 是死亡年龄时的标准预期寿命。该计算考虑了每个年龄段的死亡人数，并将其乘以该年龄段剩余的标准预期寿命，使用全球生命寿命表来确定预期寿命。关于 YLLs 概念的更多细节请见下一章（第 4 章），在附录 A 中可以找到带有预期寿命相对估计的生命表构建示例。

通常情况下，全球疾病负担（GBD）研究使用标准生命表来一致地衡量各种疾病的影响。这种方法允许在不同状况和人群之间进行可靠的比较，提供全球范围内疾病负担的全面评估。此外，特定国家的预期寿命对于研究由健康原因（如致命疾病）导致的早死非常有价值。例如，经常推荐某些类型的国家预期寿命提供对长寿特征的洞察，这可以为决策者提供参考并协助预防工作，日本预期寿命就是一个例子。一项 G7 跨国研究表明，日本寿命最长，这主要归于缺血性疾病和癌症的低死亡率，根据 GBD 研究，这些是大多数国家的首要死亡原因。

### 3.1.1 示例：中风导致的 YLLs

中风可能是几种感染性的结果，例如 COVID-19、结核病（TB）和疟疾。这些疾病对心血管系统的影响会导致中风，因为感染会导致炎症、血栓形成或对脑血管的直接损伤。

下文中，我们计算 2019 年全球地区中风导致的 YLLs。我们使用了全球疾病负担（GBD）研究，该研究

> 2Mary Demsey, "Decline in Tuberculosis," American Review of Tuberculosis, April 23, 2019, https://www.ajjournals.org/epdf/10.1164/art.1947.56.2.1576=tab.

> 3 Robert C Simon and Israel Lu, "The Overlapping Burden of the Leading Causes of Disease in Adults and Children," Nature Communications 13, no. 1 (December 6, 2022): 7457; doi:10.1038/s41467-022-3424-6

> 4brecht Devchsler et al., "Valuing the Years of Life Lost Due to COVID-19: The Differences and Pitfalls," International Journal of Public Health 65, no. 6 (2020): 719-20, doi:10.1007/s00038-020-01430-2.

> 5Shoichiro Tsugane, "Why Japan is the World's Long-Lived Country: Insights from a Food and Nutrition Perspective," European Journal of Clinical Nutrition 75, no. 6 (2021): 921-28, doi:10.1038/s41537-020-0877-5.

## 方法与计算

不同地区中风导致的死亡人数估算值可以从 `hmsidWR` 包下载，该包包含了此计算所需的数据集。`deaths2019` 数据集包含 2754 个观测值和 9 个变量，涵盖全球、法国、意大利、德国、英国和美国等地区。我们使用全球健康观察生命表来估计不同年龄的预期寿命，用于计算 YLLs。

```
install.packages("hmsidWR")
# install.packages("devtools")
```

```
library(tidyverse)
library(hmsidWR)
```

```
install_github("Fgazzoni/hmsidWR")
```

```
unique(hmsidWR::deaths2019$cause)
# [1] "Lower respiratory infections"
# [2] "Stroke"
# [3] "Chronic obstructive pulmonary disease"
# [4] "Road injuries"
# [5] "Diabetes and kidney diseases"
# [6] "Colon and rectum cancer"
# [7] "Tracheal, bronchus, and lung cancer"
# [8] "Breast cancer"
# [9] "Alzheimer's disease and other dementias"
```

特定任务是计算 2019 年全球地区中风导致的寿命损失年（YLLs）。我们将 `location` 过滤为 "Global"，`cause` 过滤为 "Stroke"。使用 `str_detect()` 来匹配死亡原因在死亡原因不是完全匹配时非常有用。

```
deaths_stroke <- hmsidWR::deaths2019 %>%
arrange(age) %>%
filter(location == "Global",
       str_detect(cause, "Stroke")) %>%
select(-location, -cause, -upper, -lower)
```

```
deaths_stroke %>% head()
# A tibble: 6 x 3
# sex age dx
#  <chr> <ord> <dbl>
# 1 male <1
# 2 female <1
# 3 both <1
# 4 male 01-04
# 5 female 01-04
# 6 both 01-04
```

然后，我们使用 `geom_boxplot()` 按年龄组可视化中风导致的死亡人数。箱线图显示了不同年龄组死亡人数的分布，包括中、分位数和离群值。图表按年龄组划分并显示

```
deaths_stroke %%
filter(!sex == "both") %%
ggplot(aes(x = age, y = dx)) +
geom_boxplot() +
labs(title = "Male and Female Deaths to Stroke",
  subtitle = "Year 2019",
  caption = "IHME GBD 2019 Data",
  x = "Age Group", y = "Deaths") +
theme(axis.text.x = element_text(angle = 45, hjust = 1))
```

### 男性和女性的中风死亡

2019 年

![](img/6b1f0d3dcab44c0cdfe4e88d54c9_37_0.png)

图 3.1 显示按年龄组划分的男女中风死亡变化的箱线图（2019）。

在 `hmsidvr::ghtables` 数据集中提供的指标中，我们特别关注标记为 `ex` 的指标。年龄 x 的预期寿命 (`ex`) 指在已经达到 x 岁的情况下预期额外生活的平均年数。这一衡量通常被称为年龄 x 的预期寿命。该数据集是世界卫生组织（WHO）维护的全球健康观察（GHO）数据库的一部分。该数据集还包含生命表指标，例如年龄 x 以上的生存年（`lx`）、年龄 x 到 x+n 之间的生存年（`nLx`）、年龄 x 到 x+n 之间的年龄特异死亡率（`n_x`）、年龄 x 到 x+n 之间的死亡人数（`ndx`）以及年龄 x 到 x+n 之间的死亡概率（`nq`）。

#### 表 3.1 生命表指标

| 指标 | 描述 |
|---|---|
| `Tx` | 年龄 x 的生存年 |
| `ex` | 年龄 x 的预期寿命 |
| `lx` | 年龄 x 的生存人数 |
| `NLx` | 年龄 x 到 x+n 之间的生存年 |
| `nmx` | 年龄 x 到 x+n 之间的年龄特异死亡率 |
| `ndx` | 年龄 x 到 x+n 之间的死亡人数 |
| `nqx` | 年龄 x 到 x+n 之间的死亡概率 |

我们估计了男女 5 岁年龄组（如 `<1`, ..., `05-09`, `10-14` 等）的预期寿命值。

另一方面，标准预期寿命代表从出生起预期生活的最大年数。例如，根据联合国人口司在 2021 年发布的估计，日本的出生预期寿命约为 84.6 岁。这一数字远高于全球平均寿命 72.6 岁。

为了计算中风导致的 YLLs，我们需要使用不同年龄的预期寿命。我们将 `gh__tables` 数据集过滤为 2019 年（预期寿命数据的最新年份），并选择指标 `ex` 以获取不同年龄的预期寿命，将其重命名为 `le`。

```
ex2019 <- hmsidvr::gh_datatables %>%
filter(year == 2019, indicator == "ex") %>%
select(-indicator, -year) %>%
rename(le = value) %>%
head()
# A tibble: 6 x 3
# age sex le
#  <chr> <ord> <dbl>
# 1 male <1 70.8
# 2 female <1 75.9
# 3 both <1 73.3
# 4 male 01-04 72.0
# 5 female 01-04 76.9
# 6 both 01-04 74.4
```

然后我们使用 `full_join()` 函数将 `deaths_stroke` 与 `ex2019` 数据合并，以计算全球地区中风导致的 YLLs，并按年龄和性别创建一个向量 `YLL`，它是死亡人数与该年龄预期寿命的积。这些 YLLs 以百万为单位，并非真实值，而是估计值。它们的数值很大取决于预期寿命和中风导致的死亡人数，也可以对预期寿命值进行其他调整以获得更准确的结果。过去，YLL 的计算包含了折现率，但在最新的计算中已不再使用。

### YLL 计算

#### 表 3.2 全球地区各 5 年龄组因中风导致的 YLL

```r
YLL_global_stroke %>% 
# # head()
# # A tibble: 6 x 5
# # sex age dx le YLL
# # <chr> <ord> dbl dbl dbl
# # 1 male <1 3640. 70.8 125916.
# # 2 female <1 2404. 75.9 182396.
# # 3 both <1 6044. 73.3 443136.
# # 4 male 01-04 2049. 72.0 147563.
# # 5 female 01-04 1505. 76.9 115680.
# # 6 both 01-04 3553. 74.4 264248.
```

```r
YLL_global_stroke <- deaths_stroke %>% 
full_join(ex2019) %>% 
group_by(age, sex) %>% 
mutate(YLL = dx * le) %>% 
ungroup()
```

### 全球地区：因中风导致的寿命损失年 (YLLs)

2019 年 - 百万

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_39_0.png)

#### 图 3.2 全球地区因中风导致的 YLL

根据这些结果，我们可以得出结论：中风导致的 YLL 情况是衡量该疾病对全球地区个人生活质量影响的重要指标。中风导致的 YLL 在老年组中特别为高，这些组的死亡人数更多，预期寿命较低。这表明中风对全球地区的整体疾病负担有显著影响，特别是在老年人群中。

#### 表 3.3 2019 年全球地区中风全年龄段 IHME 指标

```r
stroke_ihme %>% 
mutate(across(where(is.numeric), ~round(., 2))) %>% 
filter(year == 2019,
  age == "All ages") %>% 
select(metric, DALYS, YLDs, YLLS)
# # A tibble: 3 x 4
# metric            DALYS      YLDs      YLLS
# <chr>             <dbl>        <dbl>        <dbl>
# # 1 Number       15262190   14426724   14179914
# # 2 Percent       0.06       0.02      0.08
# # 3 Rate           2018.     187.       1831.
```

#### 3.1.2 练习：全年龄段 YLL 估算

计算全球地区全年龄段中风导致的 YLL，并将结果与 2019 年的 IHME 数据进行比较。

2019 年全球地区因中风导致的 YLL-IHME 数据可以从 healthdata.org 下载，2019 年数据更新反映了 2021 年 GBD 结果。

`stroke_ihme` 数据集包含 2019 年和 2021 年全球地区全年龄段及年龄标准化的中风死亡人数、DALYs、YLDs、YLLs 指标的百分比和率的估计值。

通过过滤 2019 年全年龄段的数据，我们可以预见到全球地区因中风的所有指标值，如下所示。

在全球地区，所有年龄组因中风导致的 YLLs（寿命损失年）总计为 1.41799 亿，占总负担的 8%。平均而言，人口中每 10 万人中因中风过早损失了 1.830 年寿命。

使用表 3.2 数据集计算全球地区全年龄段中风导致的 YLL，并将结果与 2019 年的 IHME 数据进行比较。正如 IHME 所估计的，该计算基于中风导致的死亡人数和相应的预期寿命，后者决定了归因于中风的 YLL。注意，这些值并不一定是真实值，而是估算值。它们的数值很大程度上取决于预期寿命和死亡人数。在过去，YLL 的计算包含了折现率，而在最新的统计中已不再使用。为了可复现性，`stroke_ihme` 数据存储在 GitHub 仓库 (`https://github.com/gbd`) 中。> Ferrari et al., “1990–2019 Global Burden of Disease, Injury, and Risk Study: a systematic analysis for 204 countries and 205 territories,” The Lancet 399(10336): 2044–2060 (2021), doi:10.1016/S0140-6736(21)02757-X.

## YLDs 计算

```r
dwsev2019 %>% head()
# # A tibble: 6 x 4
# cause1 severity dw severity_n
# <chr> <chr> <dbl> <dbl>
# 1 Infectious disease mild 0.006 0.503
# 2 Infectious disease moderate 0.051 0.253
# 3 Infectious disease mild 0.006 0.503
# 4 Infectious disease mild 0.006 0.503
# 5 Infectious disease mild 0.006 0.503
# 6 Infectious disease mild 0.006 0.503
```

残疾权重和严重程度的值考虑了所有年龄；通常情况下，它们随年龄而异，并根据不同中风类型而异。

```r
dw_stroke <- dwsev2019 %>%
  filter(cause1 == "Stroke") %>%
  group_by(severity, severity_n) %>%
  reframe(avg_dw = mean(dw))
```

```r
dw_stroke
# # A tibble: 3 x 3
# severity severity_n avg_dw
# <chr> <dbl> <dbl>
# 1 mild 0.503 0.206
# 2 moderate 0.253 0.293
# 3 severe 0.244 0.632
```

然后，考虑到患病率（和/或发病率）乘以严重程度，计算受特定严重程度影响的人口比例。

例如，我们使用 `inprev_stroke` 和 `dw_stroke` 数据集计算中风导致的 YLDs，并观察发病率和患病率之间的差异。

> 健康指标值可以用数字、百分比或比率的形式表示：
- 如果 34-39 岁男性的患病率为 1,541,506.96，且以平均值表示，这意味着 35-39 岁年龄组大约有 1,541,507 人患有中风。
- 如果 34-39 岁男性的患病率为 0.58，且以百分比（%）表示，这意味着该年龄范围内人口的 0.58% 患有中风。
- 如果患病率以比率表示，则是人口中每 100,000 人中的中风病例数。

百分比和数字与该年龄组的人口数量有关。要在这些形式之间转换，你需要知道该年龄组的总人口数。

让我们考虑发病人数和患病人数，并将它们作为单独的向量分配到名为 `inc_prev_stroke_5y` 的新集中。我们使用 `pivot_wider()` 函数将数据扩展为宽格式，其中 `measure` 列作为键列，`val` 列作为值列。

### 26 方法与计算

```r
inc_prev_stroke_5y <- hmsidR::incprev_stroke %>%
  filter(year == 2019) %>%
  select(measure, sex, age, val) %>%
  pivot_wider(names_from = "measure", values_from = "val")
```

让我们检查 35-39 岁年龄组的值。
