
```
## # A tibble:  6 x 22
##   area_code area_name       all_persons
##   <chr>     <chr>                 <dbl>
## 1 K04000001 England and Wales    59597300
## 2 E92000001 England              56489800
## 3 E12000001 North East           2647100
```

```text
## 4 E06000047 County Durham              522100
## 5 E06000005 Darlington                  107800
## 6 E06000001 Hartlepool                   92300
## # i 19 more variables: aged_4_years_and_under <dbl>,
## #   aged_5_to_9_years <dbl>,
## #   aged_10_to_14_years <dbl>,
## #   aged_15_to_19_years <dbl>,
## #   aged_20_to_24_years <dbl>,
## #   aged_25_to_29_years <dbl>,
## #   aged_30_to_34_years <dbl>, ...
```

下面的 `filter()` 步骤执行以下操作：

- 选择感兴趣的区域代码和人口类别。
- 加入详细的地理描述。
- 过滤等级 3 的值，但这会留下进一步细分为城市类别的 UA 地区。

```r
uk_census_pop_90 <- uk_census_pop_90 |>
  select(area_code, all_persons, aged_90_years_and_over) |>
  full_join(uk_census_geo_code, by = "area_code") |>
  # filter so that only UAs remain
  filter(geo_level == 3)
```

使用此表，可以计算出 90 岁及以上人员的比例，并按降序对表进行排序：

```r
uk_census_pop_90 |>
  mutate(
    pct_90_plus =
      round((aged_90_years_and_over / all_persons * 100), 1)
  ) |>
  arrange(desc(pct_90_plus)) |>
  select(area_name, aged_90_years_and_over, pct_90_plus) |>
  slice_head(n = 10)
```

\# 一个 tibble：10 × 3

列类型：`area_name` `<chr>`, `aged_90_years_and_over` `<dbl>`, `pct_90_plus` `<dbl>`

| # | `area_name` | `aged_90_years_and_over` | `pct_90_plus` |
|---|-----------|------------------------|------------|
| 1 | Dorset [note 10] | 6300 | 1.7 |
| 2 | East Sussex | 8100 | 1.5 |
| 3 | Conwy | 1700 | 1.5 |
| 4 | Isle of Wight | 2000 | 1.4 |
| 5 | Torbay | 2000 | 1.4 |
| 6 | Devon | 11200 | 1.4 |
| 7 | Herefordshire, C~ | 2400 | 1.3 |
| 8 | West Sussex | 11900 | 1.3 |
| 9 | Bournemouth, Chr~ | 5400 | 1.3 |
| 10 | North Somerset | 2800 | 1.3 |

# 7 导入数据：统计软件

本章中：

- 从包含标记数据格式的统计软件包导入调查数据，重点关注 SPSS。
- 从 Excel 文件导入调查数据，包括由调查软件创建的数据字典，并根据数据字典创建标签。
- 导入纯文本数据并应用统计软件包的语法来应用标签并以统计软件数据格式输出，重点关注 SPSS。

## 7.1 统计软件

如果你是统计学家、经济学家、社会学家、调查从业者以及许多其他人中的一员，或者与他们合作，你会发现自己会遇到使用软件包 SAS、SPSS 和 Stata 创建的数据文件。这些工具已经存在很长时间了（SAS 和 SPSS 的历史可以追溯到 20 世纪 60 年代末，而 Stata 是在 1985 年创建的），多年来它们不断发展，证明了其稳健性，并在许多学术、企业和政府环境中变得常见。

这些程序的一个特点是变量及其相关值可以被标记。如果你熟悉 R，值标记在概念上类似于因子标签的使用。这些标签可以携带大量细节，而你可能 otherwise 难以轻松获取。

R 包 `{haven}`（Wickham and Miller, 2021）提供了读取这三种类型文件¹ 的功能。我们还将使用与 `{haven}` 相关的其他包。

¹ `{haven}` 的参考页面在这里：https://haven.tidyverse.org/index.html

```r
library(haven)
```

在下面的示例中，我们将使用 `{palmer-penguins}` 数据（Horst et al., 2022; Horst, 2020）中的数据版本。我们将使用 SPSS 格式的文件；对于 SAS 和 Stata 格式的方法类似，只是细节有所不同。例如，`haven::read_()` 函数仅随扩展名而变化；Stata 数据文件扩展名为 “`.dta`”，因此读取函数为 `read_dta()`：

```r
haven::read_dta(dpjr::dpjr_data("penguins.dta"))
```

SAS 文件的等效代码如下：

```r
haven::read_sas(dpjr::dpjr_data("penguins.sas"))
```

以下是读取同一数据文件 SPSS “`.sav`” 格式并将其分配给 R 对象 `penguins_sav` 的代码：

```r
penguins_sav <- haven::read_sav(dpjr::dpjr_data("penguins.sav"))

penguins_sav
```

\# 一个 tibble：344 × 8

列：`species` `<dbl+lbl>`, `island` `<dbl+lbl>`, `bill_length_mm` `<dbl>`, `bill_depth_mm` `<dbl>`, `flipper_length_mm` `<dbl>`, `body_mass_g` `<dbl>`, `sex` `<dbl+lbl>`, `year` `<dbl>`

| # | `species` | `island` | `bill_length_mm` | `bill_depth_mm` |
|---|---------|--------|----------------|---------------|
| 1 | 1 [Adelie] | 3 [Torgersen] | 39.1 | 18.7 |
| 2 | 1 [Adelie] | 3 [Torgersen] | 39.5 | 17.4 |
| 3 | 1 [Adelie] | 3 [Torgersen] | 40.3 | 18 |
| 4 | 1 [Adelie] | 3 [Torgersen] | NA | NA |
| 5 | 1 [Adelie] | 3 [Torgersen] | 36.7 | 19.3 |
| 6 | 1 [Adelie] | 3 [Torgersen] | 39.3 | 20.6 |
| 7 | 1 [Adelie] | 3 [Torgersen] | 38.9 | 17.8 |
| 8 | 1 [Adelie] | 3 [Torgersen] | 39.2 | 19.6 |
| 9 | 1 [Adelie] | 3 [Torgersen] | 34.1 | 18.1 |
| 10 | 1 [Adelie] | 3 [Torgersen] | 42 | 20.2 |

… 还有 334 行，以及 4 个更多变量：`flipper_length_mm` `<dbl>`, `body_mass_g` `<dbl>`, `sex` `<dbl+lbl>`, `year` `<dbl>`

你会注意到 `.sav` 版本的企鹅数据框中变量的值与从 `.csv` 版本读取的值不同。所有变量，包括那些原本为字符字符串的变量，都是数值。

例如，在变量 `species` 中，值是一列“1”、“2”和“3”，而不是物种名称。

还请注意，在变量描述中，对于那些带有 SPSS 标签的变量，它包含 `<S3: haven_labelled>`。

### 7.1.1 `{labelled}`

一旦我们使用其中一个 `{haven}` 函数将 SAS、SPSS 或 Stata 数据读入 R，包 `{labelled}`（Larmarange, 2022）就为我们提供了处理变量标签、值标签和定义缺失值的强大工具。

```r
library(labelled)
```

我们将使用的第一个函数是 `look_for()`，它返回我们数据中变量的标签、列类型和值。

| pos | variable | label | col_type | missing | values |
|-----|----------|-------|----------|---------|--------|
| 1 | species | – | dbl+lbl | 0 | [1] Adelie, [2] Chinstrap, [3] Gentoo |
| 2 | island | – | dbl+lbl | 0 | [1] Biscoe, [2] Dream, [3] Torgersen |
| 3 | bill_length_mm | – | dbl | 2 | |
| 4 | bill_depth_mm | – | dbl | 2 | |
| 5 | flipper_length_mm | – | dbl | 2 | |
| 6 | body_mass_g | – | dbl | 2 | |
| 7 | sex | – | dbl+lbl | 11 | [1] female, [2] male |
| 8 | year | – | dbl | 0 | |

在此视图中，我们可以在“values”列中看到物种名称。还请注意，“col_type”列显示“`dbl+lbl`”：双精度和标签。在此数据框中，未定义任何标签。

函数 `var_label()` 允许我们为变量添加描述性标签。在下一个代码块中，我们为 `species` 变量添加标签：

```r
var_label(penguins_sav$species) <- "Penguin species"
```

我们可以使用 `look_for()` 函数看到标签现在已纳入数据框：

```r
look_for(penguins_sav)
```

| pos | variable | label | col_type | missing | values |
|-----|----------|-------|----------|---------|--------|
| 1 | species | Penguin species | dbl+lbl | 0 | [1] Adelie, [2] Chinstrap, [3] Gentoo |
| 2 | island | – | dbl+lbl | 0 | [1] Biscoe, [2] Dream, [3] Torgersen |
| 3 | bill_length_mm | – | dbl | 2 | |
| 4 | bill_depth_mm | – | dbl | 2 | |
| 5 | flipper_length_mm | – | dbl | 2 | |
| 6 | body_mass_g | – | dbl | 2 | |
| 7 | sex | – | dbl+lbl | 11 | [1] female, [2] male |
| 8 | year | – | dbl | 0 | |

也可以添加多个标签。请注意，在此示例中，为“`dbl+lbl`”和“`dbl`”类型都添加了标签。

```r
var_label(penguins_sav) <- list(island = "Island of record",
    body_mass_g = "Weight, in grams")
```

```r
look_for(penguins_sav)
```

| pos | variable | label | col_type | missing | values |
|-----|----------|-------|----------|---------|--------|
| 1 | species | Penguin species | dbl+lbl | 0 | [1] Adelie, [2] Chinstrap, [3] Gentoo |
| 2 | island | Island of record | dbl+lbl | 0 | [1] Biscoe, [2] Dream, [3] Torgersen |
| 3 | bill_length_mm | – | dbl | 2 | |
| 4 | bill_depth_mm | – | dbl | 2 | |
| 5 | flipper_length_mm | – | dbl | 2 | |
| 6 | body_mass_g | Weight, in grams | dbl | 2 | |
| 7 | sex | – | dbl+lbl | 11 | [1] female, [2] male |
| 8 | year | – | dbl | 0 | |

#### 7.1.1.1 使用标签

`{haven}` 创建的数据框中的标签可以使用 `unlabelled()` 函数转换为因子类型。

如果我们使用来自 SPSS 文件的 penguins 数据框统计每个物种的企鹅数量，我们会看到以下内容：

```r
penguins_sav |>
  group_by(species) |>
  tally()
```

```text
## # A tibble: 3 x 2
##   species       n
##   <dbl+lbl> <int>
## 1 1 [Adelie]   152
## 2 2 [Chinstrap] 68
## 3 3 [Gentoo]   124
```

在这个版本中，“`species`” 变量保留了数值。

通过应用 `unlabelled()` 函数，“`haven_labelled`” 类型的变量被转换为因子类型，并且标签（即物种名称）现在显示在我们的汇总表中：

```r
penguins_sav |>
  unlabelled() |>
  group_by(species) |>
  tally()
```

```text
## # A tibble: 3 x 2
##   species       n
##   <fct>    <int>
## 1 Adelie   152
## 2 Chinstrap 68
## 3 Gentoo   124
```

另一种方法是显式更改变量类型，在 `mutate()` 和 `mutate_if()` 中的一个 `mutate` 函数内部使用 `to_factor` 转换。在此第一个示例中，变量 `species` 从 labelled 转换为因子类型。

```r
penguins_sav |>
  mutate(species = as_factor(species)) |>
  group_by(species) |>
  tally()
```

```text
## # A tibble: 3 x 2
##   species       n
##   <fct>     <int>
## 1 Adelie      152
## 2 Chinstrap    68
## 3 Gentoo      124
```

在这个第二个变体中，`mutate_if(is.labelled)` 函数转换了所有标记的变量。

```r
penguins_sav |>
  mutate_if(is.labelled, to_factor) |>
  group_by(species, island) |>
  tally()
```

```text
## # A tibble: 5 x 3
## # Groups:   species [3]
##   species island       n
##   <fct>   <fct>    <int>
## 1 Adelie  Biscoe      44
## 2 Adelie  Dream       56
## 3 Adelie  Torgersen   52
## 4 Chinstrap Dream     68
## 5 Gentoo  Biscoe     124
```

### 7.1.2 读取 SPSS 调查文件：“Video”

标记数据框的功能在处理调查数据时非常有益。数据框可以包含表单中捕获的变量代码、与这些值关联的值，以及标签中的问题文本。

本示例中使用的文件来自谢菲尔德大学数学与统计帮助中心的“教学数据集”²

²https://www.sheffield.ac.uk/mash/statistics/datasets

![img](img/b86622d1e9ca82b3cbec45faaffaaf26_104_0.png)

*图 7.2 SPSS 变量视图。*

![img](img/b86622d1e9ca82b3cbec45faaffaaf26_104_1.png)

*图 7.3 SPSS 变量标签。*

