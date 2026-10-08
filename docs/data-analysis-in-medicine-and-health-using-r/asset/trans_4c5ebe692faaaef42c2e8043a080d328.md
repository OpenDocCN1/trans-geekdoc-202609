

# 探索性数据分析

在本章节结束时，读者将能够：

- 使用图形化方法进行探索性数据分析 (EDA)
- 使用描述性统计进行 EDA
- 获得使用 `ggplot2` 和 `gtsummary` 包的基本技能

探索性数据分析或 EDA 是一个对数据进行初步调查的关键过程，通过汇总统计量和图形化表示来发现模式、识别异常、测试假设并检查假设条件。

在统计学中，探索性数据分析（EDA）是一种数据分析方法，用于总结数据的主要特征，通常采用视觉化方法。可以使用统计模型，也可以不使用，但其主要目的是在正式建模或假设检验任务之外，数据还能告诉我们什么。

探索性数据分析由约翰·特纳基（John Tukey）推广，旨在鼓励统计学家探索数据，并可能制定导致新数据收集的假设（来源¹）。

> https://en.wikipedia.org/wiki/Exploratory_data_analysis

## 6.3 使用 ggplot2 包进行 EDA

### 6.3.1 ggplot2 的用法

我们总是从 `ggplot()` 函数开始，指定特定的数据集。接下来，我们选择审美映射（使用 `aes()`）来表示要绘制图的变量，然后添加层。这些层可以转换为下面的 R 代码：

- `geom_X` : `geom_point()`, `geom_histogram()`
- 比例尺（如 `scale_colour_brewer()`）
- 规格（如 `facet_wrap()`）
- 坐标系（如 `coord_flip()`）。

## 6.4 准备工作

### 6.4.1 加载库

我们将使用这些包进行数据探索：

1. **tidyverse** 包用于绘图和数据清洗
2. **gtsummary** 包用于汇总统计
3. **patchwork** 用于组合图表
4. **here** 用于指定正确的工作目录
5. **readxl** 用于读取 MS Excel 文件

tidy 是一组为数据科学设计的 R 包集合，具有特定的设计理念。所有包共享一个底层设计哲学、语法和数据结构。我们可以在这里找到关于该包更多信息²。

```r
library(tidyverse)
# -- Attaching core tidyverse packages --------- tidyverse 2.0.0 -
# v dplyr 1.1.1 v readr 2.1.4
# v forcats 1.0.0 v stringr 1.5.0
# v ggplot2 3.4.2 v tibble 3.2.1
# v lubridate 1.9.2 v tidyr 1.3.0
# v purrr 1.0.1
```

> ²https://www.tidyverse.org/

## 6.4 准备工作

```r
## -- Conflicts -----------------------------
tidyverse_conflicts() --
# x dplyr::filter() masks stats::filter
# x dplyr::lag() masks stats::lag
# i Use the conflicted package (http://conflicted-lib.org/) to force all conflicts to become errors
```

```r
library(gtsummary)
library(patchwork)
library(here)
```

here 开始 C:/Users/drkim/Downloads/multivariate_data_analysis/multivariate_data_analysis

```r
library(readxl)
```

### 6.4.2 将数据集读入 R

让我们读取 MS Excel 格式的胃溃疡数据。为此，我们将：

- 加载 `readxl` 包
- 使用函数 `read_xlsx()` 将数据读入 R

```r
pe <- read_xlsx(here('data', 'peptic_ulcer.xlsx'))
```

通过观察观测数量、变量类型和变量名称来检查数据。

```r
glimpse(pep)
```

```
## Rows: 121
## Columns: 34
## $ age
## $ gender
## $ epigastric_pain
## $ vomiting
## $ nausea
## $ fever
## $ diarrhea
## $ melena
## $ onset_more_24_hrs
## $ NSAIDS
## $ septic_shock <dbl> 42, 66, 66, 19, 77, 39, 62, 71, 69, 97, 52, 21, 57-
<chr> "male","female","male","male","male","male",
<chr> "yes","yes","yes","yes","yes","yes",
<chr> "no","no","no","yes","no","no","no",
<chr> "no","no","no","no","yes","no","no",
<chr> "no","no","no","no","yes","yes","yes",
<chr> "no","no","yes","no","no","no","no",
<chr> "no","no","no","no","no","no","no",
<chr> "no","no","no","yes","yes","yes","yes",
<chr> "no","no","no","no","no","no","no",
<chr> "no","no","no","no","no","no","no",
```

## 6 探索性数据分析

```r
# $ ASA
<dbl> 1, 1, 1, 1, 2, 1, 2, 1, 1, 2, 1, 2, -
```

```r
# $ systolic
<dbl> 141, 197, 126, 90, 147, 115, 103, 159, 145, 185,
```

```r
# $ diastolic
<dbl> 98, 88, 73, 40, 82, 56, 58, 74, 50, 86,
```

```r
# $ introp
<chr> "no", "no", "no", "no", "no",
```

```r
# $ pulse
<dbl> 109, 126, 64, 112, 89, 96, 100, 57, 100, 109,
```

```r
# $ tenderness
<chr> "generalized", "generalized", "generalized",
```

```r
# $ guarding
<chr> "yes", "yes", "yes", "yes",
```

```r
# $ hemoglobin
<dbl> 18.0, 12.0, 12.0, 11.0, 8.1, 13.3,
```

```r
# $ twc
<dbl> 6.0, 6.3, 13.0, 21.0, 4.0, 5.0, 12.0, 6.0,
```

```r
# $ platelet
<dbl> 2, 3, 2, 7, 1, 2, 4, 3, 6, 1,
```

```r
# $ creatinine
<dbl> 135, 66, 84, 137, 102, 69, 92, 94, 104, 58,
```

```r
# $ albumin
<chr> "27", "32", "42", "38", "30", "41",
```

```r
# $ PULP
<dbl> 2, 3, 2, 7, 1, 2, 5, 4, 6, 1,
```

```r
# $ perforation
<dbl> 0.5, 1.0, 0.5, 1.0, 3.0, 0.5, 1.5,
```

有很多变量。为了简单起见，我们将使用 `select()` 选择几个。

```r
pe <- select(age, systolic, diastolic, hemoglobin, twc, ASA, perforation, epigastric_pain, tenderness)

## 表格中的 EDA

可以使用 `tbl_summary()` 获取胃溃疡数据的整体描述性统计量。

```r
pe <- pep %>% tbl_summary(
```

| Characteristic | N = 121 |
|---|---|
| age | 60.43 (18.05) |
| systolic | 128.56 (24.51) |
| diastolic | 72.07 (13.99) |
| hemoglobin | 12.32 (3.33) |
| twc | 13.03 (6.66) |
| ASA | |
| 1 | 63 / 121 (52%) |
| 2 | 50 / 121 (41%) |
| 3 | 8 / 121 (6.6%) |
| PULP | |
| perforation | 3.53 (2.28) |
| gender | 1.22 (0.91) |
| female | 25 / 121 (21%) |
| male | 96 / 121 (79%) |
| epigastric_pain | 116 / 121 (96%) |
| malena | 4 / 121 (3.3%) |
| tenderness | |
| generalized | 84 / 121 (69%) |
| localized | 37 / 121 (31%) |
| degree_perforation | |
| large | 26 / 121 (21%) |
| moderate | 20 / 121 (17%) |
| outcome | 75 / 121 (62%) |
| alive | 83 / 121 (69%) |
| dead | 38 / 121 (31%) |

> ¹Mean (SD); n / N (%)

要根据变量结果指定描述性统计量，我们使用参数 `by =`。

```r
tab_outcome <- pep %>%
tbl_summary(
  by = outcome,
  statistic = list(all_continuous()) ~ "{mean ({sd})",
  all_categorical() ~ "{n} / {N} ({p})",
  digits = all_continuous() ~ 2) %>%
  modify_caption("Patient Characteristics and Fatality (N = {N})")
```

```r
tab_outcome %>% as_gt()
```

| Characteristic | alive, N = 83 | dead, N = 38 |
|---|---|---|
| age | 58.20 (18.53) | 65.29 (16.14) |
| systolic | 130.95 (25.06) | 123.34 (22.71) |
| diastolic | 73.25 (14.02) | 69.50 (13.75) |
| hemoglobin | 12.74 (3.14) | 11.41 (3.57) |
| twc | 12.75 (6.00) | 13.64 (7.96) |
| ASA | |
| 1 | 49 / 83 (59%) | 14 / 38 (37%) |
| 2 | 28 / 83 (34%) | 22 / 38 (58%) |
| 3 | 6 / 83 (7%) | 2 / 38 (5%) |
| PULP | |
| perforation | 4.32 (1.86) | 3.32 (2.34) |
| gender | |
| female | 25 / 83 (30%) | 13 / 38 (34%) |
| male | 58 / 83 (70%) | 25 / 38 (66%) |
| epigastric_pain | 79 / 83 (95%) | 24 / 38 (63%) |
| malena | 3 / 83 (4%) | 1 / 38 (3%) |
| tenderness | |
| generalized | 67 / 83 (81%) | 27 / 38 (71%) |
| localized | 16 / 83 (19%) | 11 / 38 (29%) |
| degree_perforation | |
| large | 18 / 83 (22%) | 5 / 38 (13%) |
| moderate | 65 / 83 (78%) | 33 / 38 (87%) |
| outcome | |
| alive | 70 / 83 (84%) | 26 / 38 (68%) |
| dead | 13 / 83 (16%) | 12 / 38 (32%) |

