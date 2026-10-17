
# use the exclamation mark to filter those that don't match

`filter(!str_detect(`Series ID`, "CEU0210"))`

```
```

## # A tibble: 6 x 3

##   `Series ID`   `Annual 2019` `Annual 2020`

##   <chr>                 <dbl>         <dbl>

## 1 CEU1021100001          144.          130.

## 2 CEU1021200001          190.          176.

## 3 CEU1021210001           50.5          39.8

## 4 CEU1021220001           42.2          41.4

## 5 CEU1021230001           97.8          95.1

## 6 CEU1021300001          344           247.

```
```

这不起作用，因为它保留了从 2121 开始的四位数行业。

解决方案可以通过关注层次结构中区分层级的字符找到。

让我们在第二个过滤器前面加上 1 到 9 的数字（字符串的第 8 个字符），并将下一个字符（第 9 个字符）保留为零。这应该能找到“CEU1021200001”但省略“CEU1021210001”。

```
# NAICS 212

bls_employment_naics21 |>

  # remove the ones that have a zero in the 5th spot from the end

  # - add any digit from 1-9, leave the following digit as 0

  filter(str_detect(`Series ID`, "[1-9]00001$"))
```

```
## # A tibble: 3 x 3

## `Series ID` `Annual 2019` `Annual 2020`

## <chr>       <dbl>         <dbl>

## 1 CEU1021100001 144. 130.

## 2 CEU1021200001 190. 176.

## 3 CEU1021300001 344 247.
```

另一个选项是使用否定零 “[ˆ0]”。你会注意到它使用了插入符号“ˆ”。因为它在方括号内，所以它具有否定命名值的作用。这与它在方括号外时的行为不同，在方括号外它表示“字符串的开始”。

```
# NAICS 212

bls_employment_naics21 |>

  # remove the ones that have a zero in the 6th spot from the end

  # - add any digit that is not a zero

  filter(str_detect(`Series ID`, "[^0]00001$"))
```

```
## # A tibble: 3 x 3

## `Series ID` `Annual 2019` `Annual 2020`

## <chr>       <dbl>         <dbl>

## 1 CEU1021100001 144. 130.

## 2 CEU1021200001 190. 176.

## 3 CEU1021300001 344 247.
```

这里还有一个最终选项，使用 `str_sub()` 在 `str_detect()` 函数内部指定位置。

在继续之前，让我们单独查看 `str_sub()` 函数的结果。在此代码中，该函数从“Series ID”变量的第 8 和第 9 个位置提取所有字符字符串，结果是长度为两个字符的字符串。

```r
# extract the character strings in the 8th & 9th position

str_sub(bls_employment_naics21$`Series ID`, start = 8, end = 9)
```

```text
## [1] "00" "10" "20" "21" "22" "23" "30"
```

从括号内部开始，我们有 `str_sub()` 函数来创建这些两字符字符串。接下来是带有正则表达式的 `str_detect()`，它识别第一位为非零数字、第二位为零的那些。表格随后会被过滤，只保留检测到的那些行。

```r
# NAICS 212

bls_employment_naics21_3digit <- bls_employment_naics21 |>

  # filter those that match the regex in the 8th & 9th position

  filter(str_detect(

    str_sub(`Series ID`, start = 8, end = 9),

    "[^0][0]"
  ))

bls_employment_naics21_3digit
```

| `Series ID` | `Annual 2019` | `Annual 2020` |
|---|---:|---:|
| CEU1021100001 | 144. | 130. |
| CEU1021200001 | 190. | 176. |
| CEU1021300001 | 344 | 247. |

清理此表格的最后一步是将它放入整洁的结构中。目前它违反了整洁数据的第二原则，即每个观测值构成一行。 (Wickham, 2014, p.4) 在这种情况下，每一年都应有自己的行，而不是为每一年分别设置一列。

我们可以使用 `{tidyr}` (Wickham, 2021b) 包的 `pivot_longer()` 函数来实现：

```r
bls_employment_naics21_3digit |>

  pivot_longer(

    cols = contains("Annual"),

    names_to = "year",

    values_to = "employment")
```

| `Series ID` | year | employment |
|---|---:|---:|
| CEU1021100001 | Annual 2019 | 144. |
| CEU1021100001 | Annual 2020 | 130. |
| CEU1021200001 | Annual 2019 | 190. |
| CEU1021200001 | Annual 2020 | 176. |
| CEU1021300001 | Annual 2019 | 344 |
| CEU1021300001 | Annual 2020 | 247. |

## 12.3.4 示例：NOC：从标题中拆分代码

本示例取自一个表格，显示了不列颠哥伦比亚省住宿行业不同职业的工作人数。在此表中，加拿大国家职业分类（NOC）代码与代码的标题在同一列中。

```r
noc_table <- read_rds(dpjr::dpjr_data("noc_table.rds"))

gt(head(noc_table))
```

| noc_occupation_title | certification_training_requirements | employment |
|---|---|---:|
| 063: Accommodation service managers | A university degree or college diploma in hotel management or other related discipline or equivalent job experience | 6,479 |
| 652: Occupations in travel and accommodation | Related post-secondary diploma; On the job training | 5,771 |
| 673: Cleaners | On the job training | 5,083 |
| 631: Food service supervisors | Post-secondary training in restaurant management or food service admin, or; Equivalent job experience | 3,479 |
| 632: Chefs and cooks | Cook’s apprenticeship program and training; Chef’s Red Seal Certification | 1,542 |
| 112: Human resources professionals | Related post-secondary degree or diploma | 1,271 |

**图 12.1 NOC 表格：步骤 1。**

此表在三列中有四个变量，每一个都至少有一个数据清理挑战。

### noc_occupation_title

此变量结合了两个值：三位 NOC 代码和职业的标题。

我们将使用 `{tidyr}` 函数 `separate_wider_delim()` 将其拆分为两个变量。该函数为我们提供了命名分离后产生的新列的参数，以及用于识别分离点的字符字符串，在本例中为“：”。**不要忘记空格！**

此函数还具有参数 `cols_remove =`。默认设置为 TRUE，会删除原始列。设置为 FALSE 时会保留原始列；我们这里不会使用，但可能有用。

还有基于固定宽度位置和正则表达式的 `separate_wider_*()` 函数。

```r
noc_table_clean <- noc_table |>

  tidyr::separate_wider_delim(

    cols = noc_occupation_title,

    delim = ": ",

    names = c("noc", "occupation_title")

  )

gt(head(noc_table_clean))
```

| noc | occupation_title | certification_training_requirements | employment |
|---:|---|---|---:|
| 063 | Accommodation service managers | A university degree or college diploma in hotel management or other related discipline or equivalent job experience | 6,479 |
| 652 | Occupations in travel and accommodation | Related post-secondary diploma; On the job training | 5,771 |
| 673 | Cleaners | On the job training | 5,083 |
| 631 | Food service supervisors | Post-secondary training in restaurant management or food service admin, or; Equivalent job experience | 3,479 |
| 632 | Chefs and cooks | Cook’s apprenticeship program and training; Chef’s Red Seal certification | 1,542 |
| 112 | Human resources professionals | Related post-secondary degree or diploma | 1,271 |

**图 12.2** *NOC 表格：步骤 2。*

### certification_training_requirements

此变量在开头有一个被表示为方块的字符，并且方块与第一个字母之间还有一个空格。

这里我们可以使用 `{stringr}` 函数 `str_remove_all()`。（请记住，`str_remove()` 函数只删除该字符的第一个实例。）

```r
noc_table_clean <- noc_table_clean |>

  mutate(

    certification_training_requirements =

      str_remove_all(certification_training_requirements, "□ ")
  )

gt(head(noc_table_clean))
```

| noc | occupation_title | certification_training_requirements | employment |
|:---|:---|:---|:---|
| 063 | Accommodation service managers | A university degree or college diploma in hotel management or other related discipline or equivalent job experience | 6,479 |
| 652 | Occupations in travel and accommodation | Related post-secondary diploma; On the job training | 5,771 |
| 673 | Cleaners | On the job training | 5,083 |
| 631 | Food service supervisors | Post-secondary training in restaurant management or food service admin, or; Equivalent job experience | 3,479 |
| 632 | Chefs and cooks | Cook’s apprenticeship program and training; Chef’s Red Seal Certification | 1,542 |
| 112 | Human resources professionals | Related post-secondary degree or diploma | 1,271 |

**图 12.3 NOC 表格：步骤 3。**

### employment

此变量应为数字，但却是字符类型。这是因为

- 使用逗号作为千位分隔符
- 最小的类别用 "-*" 表示以指示表格注释。

为了清理它，我们需要三个步骤：

- 1. 删除逗号
- 2. 将 “-*” 替换为 NA
- 3. 转换为数值

```r
noc_table_clean <- noc_table_clean |>

  # remove commas

  mutate(

    employment =

      str_remove_all(employment, ",")
  ) |>

  # replace with NA

  mutate(

    employment =

      str_replace_all(employment, "-\\*", replacement = NA_character_)
  ) |>

  # convert to numeric

  mutate(

    employment =

      as.numeric(employment)
  )

gt(head(noc_table_clean))
```
