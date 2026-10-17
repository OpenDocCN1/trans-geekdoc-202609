

## 5.4 汇总与分组

`summarize()` 用于查找观测值的数量。在 `mean()` 和 `median()` 函数中，我们设置 `na.rm=TRUE` 以在计算这些值之前移除 NA（否则，输出可能会是 NA）。

```r
nhanes_df %>%
filter(RACE == "Non-Hispanic Black") %>%
summarize(TOT = n(), MEAN_SBP = mean(SBP1, na.rm=TRUE),
          MEAN_DBP = mean(DBP1, na.rm=TRUE))
#>
#>   TOT MEAN_SBP MEAN_DBP
#> 1 6041    129   72.6
```

如果我们想对其他种族群体重复此操作，则每次都需要更改 `filter()` 函数的参数。为了避免重复代码和/或多次执行此操作，我们可以使用 `group_by()` 函数，该函数接受一个数据框以及一个或多个用于分组的列。在以下代码中，我们使用 RACE 变量进行分组。查看打印输出时，它看起来与之前几乎相同，只是我们可以看到其类别现在是分组数据框（grouped data frame），该信息打印在顶部。实际上，分组数据框（或分组 tibble）的作用类似于一组数据框：每个组一个。如果我们使用索引为 1 的 `slice()` 函数，它将返回每个组的第一行。

```r
nhanes_df %>%
group_by(RACE) %>%
slice(1)
#> # A tibble: 5 x 20
#> # Groups:   RACE [5]
#>    AGE SEX   RACE  EDUCATION PIR SMOKE_STATUS YEAR LEAD
#>  <dbl> <fct> <fct> <fct>     <dbl> <chr>      <dbl> <dbl>
#> 1   70 Male  Mexican~ LessThan~ 1.07 Quit Smoking 1999 1.6
#> 2   61 Female Other H~ MoreThan~ 3.33 Current Smo~ 1999 2.2
#> 3   77 Male  Non-His~ MoreThan~ 5   Never Smoked 1999 5
#> 4   38 Female Non-His~ HS        0.92 Current Smo~ 1999 1.8
#> 5   63 Female Other R~ MoreThan~ 5   Never Smoked 1999 1.2
#> # i 11 more variables: HYP <dbl>, ALC <chr>, DBP1 <dbl>, DBP2 <dbl>,
#> #   DBP3 <dbl>, DBP4 <dbl>, SBP1 <dbl>, SBP2 <dbl>, SBP3 <dbl>,
#> #   SBP4 <dbl>, EVER_SMOKE <chr>
```

将数据分组与 `summarize()` 函数结合使用非常有用。与 `slice()` 函数类似，`summarize()` 会为每个组计算汇总值。我们现在可以找到每个种族群体的观测总数以及平均收缩压和舒张压值。请注意，返回的汇总数据是 tibble 格式。

```r
nhanes_df %>%
  group_by(RACE) %>%
  summarize(TOT = n(), MEAN_SBP = mean(SBP1, na.rm=TRUE),
            MEAN_DBP = mean(DBP1, na.rm=TRUE))
#> # A tibble: 5 x 4
#>   RACE                   TOT MEAN_SBP MEAN_DBP
#>   <fct>                <int>    <dbl>    <dbl>
#> 1 Mexican American      5277      124.     70.4
#> 2 Other Hispanic        2279      123.     70.1
#> 3 Non-Hispanic White   15473      125.     70.4
#> 4 Non-Hispanic Black    6041      129.     72.6
#> 5 Other Race            2195      122.     72.6
```

汇总后，数据不再按种族分组。如果我们想要从数据中移除分组结构，可以使用 `ungroup()` 函数，它会将数据恢复为单个数据框。按种族取消分组后，我们可以看到 `slice()` 函数返回单个观测值。

```r
nhanes_df %>%
  select(SEX, RACE, SBP1, DBP1) %>%
  group_by(RACE) %>%
  ungroup() %>%
  arrange(desc(SBP1)) %>%
  slice(1)
#> # A tibble: 1 x 4
#>   SEX    RACE                    SBP1  DBP1
#>   <fct>  <fct>                  <dbl> <dbl>
#> 1 Female Non-Hispanic White      270   124
```

### 5.4.1 练习题

创建一个数据框，按吸烟状况汇总高血压患者的百分比。结果应如图 5.2 所示。

| SMOKE_STATUS | PCT_HYP |
|---|---|
| <chr> | <dbl> |
| Current Smoker | 0.5096351 |
| Never Smoked | 0.5140850 |
| Quit Smoking | 0.6559079 |

图 5.2：分组与汇总数据。

```r
# Insert your solution here:
```

## 5.5 练习

以下练习使用 HDSinRdata 包中的 covidcases 数据集。在完成练习之前，请务必阅读该数据的文档（?covidcases）。

```r
data(covidcases)
```

- 1. 假设我们对各州每周病例的分布感兴趣。首先，在 covidcases 中创建一个名为 region 的新列，指定每个州属于东北部、中西部、南部还是西部（你可以手动使用此列表¹来划分各州所属地区，也可以使用 R 中 datasets 包中的 state.region）。然后，创建一个数据框，汇总东北部每周病例的平均值和标准差。

- 2. 现在，创建一个数据框，按每个地区汇总平均值和标准差，而不是像问题 1 那样只针对一个选定地区。将此数据框按平均每周病例数从高到低排序。为了更准确地比较这些地区的平均病例数，你还需要哪些其他信息？

¹https://en.wikipedia.org/wiki/List_of_regions_of_the_United_States

- 3. 在此数据第 15 周中，找出中西部地区每周死亡人数最少的十个县（忽略并列情况，使用 `slice_min()` 查找所需的参数）。你注意到这些最小值有什么特点？请参阅数据文档了解我们观察到这些值的原因。

- 4. 筛选数据以包含第 9 周和第 20 周（大约在疫情开始时），获取该时间段内每个县的病例总数，然后找出每个州中总病例数最多的县。

## 案例研究：清理肺结核筛查数据

在本章中，我们通过一个案例研究来综合运用一些 R 技能。该案例研究侧重于数据清理和预处理。我们使用 HDSinRdata 包中的 tb_diagnosis_raw 数据。此数据包含南非农村地区 1,634 名患者的信息，这些患者因出现结核病相关症状而到卫生诊所就诊，并接受了 Xpert MTB/RIF 结核病（TB）检测。我们的目标是清理这些数据，以反映 Baik 等人（2020）所述的预处理过程。该论文使用这些数据推导出一个简单的风险评分模型，用于在等待 Xpert 结果期间对患者进行筛查以决定是否治疗。我们使用 tidyverse 包以及 gtsummary 中的汇总表。

```r
library(HDSinRdata)
library(tidyverse)
library(gt)
library(gtsummary)
```

首先，读入数据并查看原始列的描述。数据文档中需要注意的一些事项包括未知、缺失或拒绝回答的值的编码方式，以及某些列之间的关联方式。

```r
# Read in data
data("tb_diagnosis_raw")

# Inspect variable descriptions
# ?tb_diagnosis_raw
```

首先，我们选择分析所需的变量。具体来说，我们删除与参与调查和寻求护理相关的列。由于其中一些变量包含冗长或模糊的名称，我们还重命名了大部分变量。

```r
# Select variables and rename
tb_df <- tb_diagnosis_raw %>%
  select(c(xpert_status_fac, age_group, sex, hiv_status_fac,
           other_conditions_fac___1, other_conditions_fac___3,
           other_conditions_fac___88, other_conditions_fac___99,
           symp_fac___1, symp_fac___2, symp_fac___3, symp_fac___4,
           symp_fac___99, length_symp_unit_fac, length_symp_days_fac,
           length_symp_wk_fac, length_symp_mnt_fac, length_symp_yr_fac,
           smk_fac, dx_tb_past_fac, educ_fac)) %>%
  rename(tb = xpert_status_fac, hiv_pos = hiv_status_fac,
         cough = symp_fac___1, fever = symp_fac___2,
         weight_loss = symp_fac___3, night_sweats = symp_fac___4,
         symptoms_missing = symp_fac___99,
         ever_smoke = smk_fac,
         past_tb = dx_tb_past_fac, education = educ_fac)
```

然后，我们使用汇总表来了解所观察变量的初始分布。这也有助于突出显示缺失或未知数据的位置。

```r
tbl_summary(tb_df) %>%
as_gt()
```

| 特征 | N = 1,634 |
|---|---|
| tb | |
| 1 | 765 (47%) |
| 2 | 869 (53%) |
| age_group | |
| [15,25) | 240 (15%) |
| [25,35) | 333 (20%) |
| [35,45) | 385 (24%) |
| [45,55) | 343 (21%) |
| [55,99) | 333 (20%) |
| sex | |
| 1 | 830 (51%) |
| 2 | 804 (49%) |
| hiv_pos | |
| 1 | 632 (39%) |
| 2 | 815 (50%) |
| 77 | 139 (8.5%) |
| 88 | 48 (2.9%) |
| other_conditions_fac___1 | 895 (55%) |

