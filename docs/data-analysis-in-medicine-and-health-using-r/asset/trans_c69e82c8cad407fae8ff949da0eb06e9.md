
本研究基于美国国家癌症研究所 SEER 数据库 2017 年版（1973 年至 2015 年数据）的最新发布数据。根据国际疾病分类标准第三版（ICD-O-3）组织学代码 9451，从 SEER 数据库中筛选出诊断为血管骨肉瘤（AO）的患者。该数据集中共有 1824 名诊断为 AO 的患者。

## 12.4 分析

数据集包含了我们感兴趣的所有变量。为了本次作业，我们希望探索年龄、手术状态和婚姻状况与 AO 患者生存率之间的预后因素关联。数据集中的变量如下：

- age：研究开始时的生物年龄。该数据为数值型。
- surgery：患者是否接受过手术。编码为“Yes”（是）和“No”（否）。
- marital：分配时的婚姻状况。编码为“single”（单身）、“married”（已婚）或“separated/divorced/widowed”（分离/离婚/寡偶）。
- survival：生存时间（以月为单位）。该数据为数值型。
- status：生存状态，编码为“1 = 死亡”和“0 = 删失”。

我们使用了以下包：

- here：用于指定工作目录的位置。
- tidyverse：用于探索性数据分析、数据清洗和绘图。
- gsummary：提供良好的统计表格。
- broom：为估计值提供整洁精美的表格。
- flexsurv：对时间事件数据执行灵活参数生存分析模型，包括广义 Gamma 分布、广义 F 分布和 Royston-Parmar 样条模型，并支持自定义分布。
- SurvRefCensCov：将基于输出的 Weibull分布转换为更自然的参数化方法。

```
library(here)

# here starts at C:/Users/drkim/Downloads/multivariate_data_analysis/multivariate_data_analysis

library(tidyverse)

# -- Attaching tidyverse ---------------------------------------------------------------- tidyverse 2.0.0 -

# v dplyr      1.1.1 v readr      2.1.4
# v forcats    1.0.0 v string    1.5.0
# v ggplot2    3.4.2 v tibble     3.2.1
# v lubridate  1.9.2 v tidyr      1.3.0
# v purrr       1.0.1

# -- Conflicts --
tidyverse_conflicts() --
# x dplyr::filter()  masks stats::filter()
# x dplyr::lag()      masks stats::lag()
```

## 使用 conflicted 包（<http://conflicted.r-lib.org/> 可强制将所有冲突变为错误）

```
library(gtsummary)
library(broom)
library(flexsurv)
```

## 加载所需的包: survival

```
library(SurvRegCensCov)
```

## Registered S3 方法被 'SurvRegCensCov' 覆盖
## 方法来自
## print.src

## 12.4.3 读取数据集

```
d1 <- read_csv('data','survivaloa.csv')
```

```
## Rows: 1824 Columns: 8
## 列规格
---
## 分隔符: ","
## chr (5): marital, sex, surgery, race, first
## dbl (3): age, status, survivaltime
##
## i 使用 `spec()` 来检索此数据的完整列规格。
## i 指定列类型或设置 `show_col_types = FALSE` 以静默此消息。
```

## 12.4.4 数据清洗

我们将只选择这些变量来简化模型构建过程：

- age
- surgery
- marital
- survivaltime
- status

## 12.4 分析

我们将所有字符变量转换为因子变量。

```
d1 <- d1 %>%
  dplyr::select(age, surgery, marital, survivaltime, status) %>%
  mutate_if(is.character, as.factor)
glimpse(d1)

# Rows: 1,824
# Columns: 5
# $ age           <dbl> 4, 4, 4, 5, 5, 5, 6, 6, 8, 9, 11, 11, 11
# $ surgery       <fct> Yes, Yes, Yes, No, Yes, Yes
# $ marital       <fct> Single, Single, Single, Single, Single
# $ survivaltime   <dbl> 9, 10, 141, 12, 54, 161, 60, 8, 15, 298, 83
# $ status          <dbl> 0, 1, 0, 1, 1, 0, 1, 0, 1
```

## 12.4.5 探索性数据分析 (EDA)

我们将进行一些简单的：

```
d1 %>%
  mutate(status = recode(status, "0" = "Censored", "1" = "Death")) %>%
  tbl_summary(by = status,
              statistic = list(all_continuous() ~ "{mean} ({sd})",
                              all_categorical() ~ "{n} ({p})"),
              type = list(where.logical ~ "categorical"),
              label = list(age ~ "年龄（岁）",
                          surgery ~ "手术状态",
                          marital ~ "婚姻状况",
                          survivaltime ~ "时间（月）"),
              missing_text = "**缺失**") %>%
  modify_header(label = "**患者特征**") %>%
  modify_spanning_header(c("stat_1", "stat_2") ~ "**生存状态**") %>%
  modify_footnote(all_cols ~ "均值 (标准差) 或 百比 (%)") %>%
  bold_labels(everything()) %>%
  as_gt()
```

 生存状态

| 变量 | 删失, N = 835 | 死亡, N = 989 |
| :--- | :--- | :--- |
| 年龄（岁） | 45 (13%) | 52 (16%) |
| 手术状态 | 774 (93%) | 835 (84%) |
| 婚姻状况 | 531 (64%) | 606 (61%) |
| 分离/离婚/寡偶 | 96 (11%) | 174 (18%) |
| 单身 | 208 (25%) | 209 (21%) |
| 时间（月） | 83 (65%) | 38 (42%) |

*可以使用来自 **survival** 包的 `survreg()`。然而 `survreg()` 只执行 AFT 估计。

```
exp.mod.aft <- survreg(survivaltime, status) ~ age + marital + surgery,
              data = d1, dist = 'exponential')
```

```
## Call:
## survreg(formula = Surv(survivaltime, status) ~ age + marital +
##   surgery, data = d1, dist = "exponential"
##
## (Intercept)
##                 Value Std. Error Z
##                 -0.0487 0.1601 -41.45
## age               0.0609 0.0025 19.50 < 2e-16
## marital/divorced/widowed -0.0681 0.0871 -0.70 0.4848
## maritalSingle     -0.3068 0.0823 -3.70 0.0019
## surgeryYes        0.5250 0.0879 5.97 2.4e-09
##
## Scale fixed at 1
##
## Exponential distribution
## Loglik(model)=-5401.2 Loglik(intercept)=-5614.4
## Chisq=426.47 on 4 degrees of freedom, p=5.3e-9
## Number of Newton-Raphson Iterations: 5
## n=1824
```

## 12.4 分析

## 12.4.7 Weibull (加速失效)

我们首先估计 Weibull 参数生存模型，它将返回加速失效时间：

为此，我们将使用 `survreg()` 函数。

```
wei.mod.aft <- survreg(Surv(survivaltime, status) ~ age + surgery + marital,
               data = d1, dist = 'weibull')
summary(wei.mod.aft)
```

```
## Call:
## survreg(formula = Surv(survivaltime, status) ~ age + surgery +
##             marital, data = d1, dist = "weibull"
##             Value Std. Error z p
## (Intercept) 0.19724 34.58 2e-16
## age
## surgeryYes
## maritalSeparated/divorced/widowed
## maritalSingle
## Log(scale)
## Scale= 1.23
```

```
## Weibull distribution
## Loglik(model)= -5365.4 Loglik(intercept only)= -5533.6
## Chisq=336.9 on 4 degrees of freedom, p=1.2e-7
## Number of Newton-Raphson Iterations: 5
## n=1824
```

然而，从 `survreg()` 估计的参数并不合理。为此，我们将使用 `Weibull()` 转换为风险、AFT 模型。

```
Convertibull(wei.mod.aft, conf.level = 0.95)
```

## 12.4 参数生存

或者我们可以直接使用 `flexsurv()` 获取对数时间并

```
wei.mod.aft <- flexsurv(Surv(survivaltime, status) ~ age + surgery + marital,
              data = d1, dist = 'weibull')
```

```
## Call:
## flexsurv(formula = Surv(survivaltime, status) ~ age + surgery +
##             marital, data = d1, dist = "weibull")
```

```
## Estimates:

data mean           est      L95     U95
## shape             NA       8.13e-01 7.73e-01 8.55e-01
## scale              NA       -5.27e-02 -5.87e-02 -4.67e-02
## age                4.89e-01 -5.87e-02 -4.67e-01
## surgeryYes         8.82e-01 6.25e-01 4.12e-01 8.39e-01
## maritalSeparated/divorced/widowed 1.48e-01 -1.00e-01 -3.10e-01 1.10e-01
## maritalSingle      2.29e-01 -3.54e-01 -5.54e-01 -1.55e-01
```

