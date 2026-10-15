

荷兰统计局，并为我们提供了编写结构化验证测试的工具。

我们将在此包中研究的第一个函数是 `check_that()`，使用 {palmerpenguins}（Horst 等，2022；Horst，2020）中的数据。我们知道包中的数据是整洁干净的——它们已经经过验证过程。

```
library(tidyverse)

library(palmerpenguins)
library(validate)
```

### 数值范围：

作为企鹅专家，我们知道巴布亚企鹅（Pygoscelis papua）是企鹅物种中第三大的，体重可达 8.5 千克。因此我们可能想看看是否有任何记录的企鹅体重超过 8500 克。`check_that()` 函数将这个问题反过来了；我们确保所有记录中的企鹅体重值都小于或等于 8500 克。如果值低于该值，则返回“通过”。

```
check_penguins <- check_that(penguins, body_mass_g <= 8500)

summary(check_penguins)
```

对 `check_that()` 函数创建的对象使用 `summary()` 函数，结果显示所有企鹅的体重都小于或等于 8500 克，并且数据中有 2 个“NA”值。

### 关系：

虽然最重的巴布亚企鹅可达 8.5 千克，但体重超过 5 千克的阿德利企鹅或帽带企鹅非常罕见。如果我们将体重阈值改为 5000 克会怎样？

```
check_penguins <- check_that(penguins, body_mass_g <= 5000)

summary(check_penguins)
```

除了告诉我们有 61 条记录的 `body_mass_g` 变量值大于 5000 克之外，它还让我们知道有 2 个 NA 值。

我们可以添加一个 `if()` 语句来过滤掉巴布亚企鹅，然后检查体重。

```
check_penguins <- check_that(
  penguins,
  if (species != "Gentoo") body_mass_g <= 5000
)

summary(check_penguins)
```

现在所有记录（除了那一个“NA”）都通过了。发生了什么？首先是我们排除了所有巴布亚企鹅——如果是巴布亚企鹅，就会被标记为“通过”。所有剩余的企鹅（即帽带企鹅和阿德利企鹅）都会根据 5000 克的体重值进行评估。而且它们都通过了。

让我们进一步探索数据。如果我们按体重超过 5000 克的企鹅进行筛选，会发现什么？

```
penguins |>
  filter(body_mass_g > 5000) |>
  distinct(species)
```

```
## # A tibble: 1 x 1
##   species
##   <fct>
## 1 Gentoo
```

因此，这证实了所有较重的企鹅都是巴布亚企鹅，符合我们的预期。

### 范围：

我们知道 {palmerpenguins} 数据来自 2007-2009 年三个季度的测量。我们可以编写一个验证测试，确保 year 变量在该范围内。

```
check_penguins <- check_that(penguins, year >= 2007 & year <= 2009)
summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| V1 | 344 | 344 | 0 | 0 | FALSE | FALSE | year - 2007 >= -1e-08 & year - 2009 <= 1e-08 |

如果我们只检查某一年呢？

```
check_penguins <- check_that(penguins, year == 2009)
summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| V1 | 344 | 120 | 224 | 0 | FALSE | FALSE | abs(year - 2009) <= 1e-08 |

输出在“通过”列中给出了该年份的案例数，在“失败”列中给出了不在该年份的案例数。

### 关系：

我们知道有些物种只在三个岛屿之一上被测量过。巴布亚企鹅只在比斯科岛上取样，而我们样本中的帽带企鹅只来自梦想岛。数据是否反映了这一点？

在第一个测试（标记为 g，代表巴布亚企鹅）中，如果不是巴布亚企鹅，就会被纳入通过；如果是巴布亚企鹅，则必须在比斯科岛才能通过。在 c（代表帽带企鹅）测试中，我们将对帽带企鹅做同样的操作，它们应该都在梦想岛上。

```
check_penguins <-
  check_that(penguins,
             g = if (species == "Gentoo") island == "Biscoe",
             c = if (species == "Chinstrap") island == "Dream")

summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| g | 344 | 344 | 0 | 0 | FALSE | FALSE | species != "Gentoo" | (island == "Biscoe") |
| c | 344 | 344 | 0 | 0 | FALSE | FALSE | species != "Chinstrap" | (island == "Dream") |

输出现在包含两个测试的结果。两个测试的所有案例都通过，没有失败。

我们本来可以编写代码生成汇总表来检查这一点。然而，在许多数据集中，组合太多，无法以这种方式进行可靠调查。

```
penguins |>
  group_by(species, island) |>
  tally()
```

| 物种 | 岛屿 | 数量 |
|---------|--------|---|
| Adelie | Biscoe | 44 |
| Adelie | Dream | 56 |
| Adelie | Torgersen | 52 |
| Chinstrap | Dream | 68 |
| Gentoo | Biscoe | 124 |

可以使用“与”运算符 `&` 编写单个 `check_that()` 测试。

```
check_penguins <-
  check_that(penguins,
    if (species == "Gentoo") island == "Biscoe" &
    if (species == "Chinstrap") island == "Dream")
```

```
summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| V1 | 344 | 344 | 0 | 0 | FALSE | FALSE | species != "Gentoo" | (island == "Biscoe" & (species != "Chinstrap" | (island == "Dream"))) |

### 图 11.1 check_penguins。

我们还可以根据一个已定义的列表进行测试。如果我们需要评估数据的列表非常庞大，这种策略会很有效。想象一下检查你所在地区每个城镇的名称拼写。如果你在现有数据文件中预定义了这些名称的列表，该列表可以被读入你的 R 环境，并针对该列表运行测试。在这个简短的示例中，创建了一个名为 island_list 的对象，并针对该列表的内容运行验证检查。

```
island_list <- c("Biscoe", "Dream", "Torgersen")

check_penguins <-
  check_that(penguins,
    if (species == "Adelie") island %in% island_list)

summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| V1 | 344 | 344 | 0 | 0 | FALSE | FALSE | species != "Adelie" | (island %in% island_list) |

_如果我们没有将梦想岛包括在发现阿德利企鹅的岛屿列表中，会怎样？_

{validator} 还允许我们在 `check_that()` 函数中检查变量类型。由于 R 将数据框列存储为单一类型，因此只会返回一个通过/失败评估。

```
summary(check_that(penguins, is.integer(year)))
```

![](img/b86622d1e9ca82b3cbec45faaffaaf26_167_0.png)

**图 11.2** _summary(check_that(penguins))_.

## 11.3.2 badpenguins

“badpenguins.rds” 文件向原始的 “penguins” 表添加了五只虚构的企鹅，包括测量数据。让我们加载数据文件 “badpenguins.rds”（一个 R 数据文件），并运行之前使用过的一些测试：

```
badpenguins <- read_rds(dpjr_data("badpenguins.rds"))
```

```
tail(badpenguins)
```

```
## # A tibble: 6 x 8
##   species island bill_length_mm bill_depth_mm flipper_length_mm body_mass_g
##   <fct>   <fct>       <chr>          <chr>           <chr>            <chr>
## 1 Chin... Dream      50.2           18.7            198              3775
## 2 Penguin Gotham     <NA>           <NA>            <NA>             90
## 3 Pingu  Antar~     <NA>           <NA>            <NA>             <NA>
## 4 Pinga  Antar~     <NA>           <NA>            <NA>             <NA>
## 5 Opus   Bloom~     <NA>           <NA>            <NA>             <NA>
## 6 Gunter Ice K~     <NA>           <NA>            <NA>             <NA>
## # i 2 more variables: sex <fct>, year <chr>
```

```
check_penguins <- check_that(badpenguins, year >= 2007 & year <= 2009)

summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| V1 | 349 | 344 | 5 | 0 | FALSE | FALSE | year >= 2007 & year <= 2009 |

```
check_penguins <- check_that(badpenguins, island %in% island_list)

summary(check_penguins)
```

| 名称 | 项目数 | 通过 | 失败 | 缺失值 | 错误 | 警告 | 表达式 |
|------|-------|--------|-------|-----|-------|---------|------------|
| V1 | 349 | 344 | 5 | 0 | FALSE | FALSE | island %in% island_list |

在这两种情况下，我们都会得到 5 个“失败”。

## 11.3.3 调查失败

我们如何检查哪些记录失败了？

{validate} 还提供了另外两个函数，`validator()` 和 `confront()`，它们让我们能够

- 同时运行多项检查，以及

