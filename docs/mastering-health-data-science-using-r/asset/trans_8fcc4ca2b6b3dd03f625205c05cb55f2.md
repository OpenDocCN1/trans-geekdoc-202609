

### 5.2.1 练习题

筛选数据，仅保留教育程度高于 HS 且报告饮酒的数据。然后，仅选择舒张压变量，并显示第四行和第十行。你的结果应与图 5.1 中的结果一致。

A data.frame: 2 × 4

| DBP1 | DBP2 | DBP3 | DBP4 |
|---|---|---|---|
| <dbl> | <dbl> | <dbl> | <dbl> |
| 68 | 68 | 70 | NA |
| 72 | 64 | 66 | NA |

图 5.1：筛选和选择数据。

```r
# Insert your solution here:
```

## 5.3 更新行和列

接下来我们将介绍的几个函数允许我们更新数据中的行和列。例如，`rename()` 函数允许我们更改列名。在以下代码中，我们将 `INCOME` 的名称更改为 `PIR`，因为该变量是贫困收入比率，同时还将 `SMOKE` 的名称更新为 `SMOKE_STATUS`。在指定这些名称时，新名称位于 `=` 的左侧，旧名称位于右侧。

```r
nhanes_df <- nhanes_df %>% rename(PIR = INCOME, SMOKE_STATUS = SMOKE)
names(nhanes_df)
#>  [1] "AGE"          "SEX"          "RACE"         "EDUCATION"
#>  [5] "PIR"          "SMOKE_STATUS" "YEAR"         "LEAD"
#>  [9] "BMI_CAT"      "HYP"          "ALC"          "DBP1"
#> [13] "DBP2"         "DBP3"         "DBP4"         "SBP1"
#> [17] "SBP2"         "SBP3"         "SBP4"
```

在上一章中，我们使用 `ifelse()` 函数基于吸烟状态变量创建了一个名为 `EVER_SMOKE` 的新变量。回想一下，该函数允许我们指定一个条件，然后根据是否满足该条件指定两个备选值。我们看到，我们的数据中约有 15,000 名从未吸烟的受试者。

```r
ifelse(nhanes_df$SMOKE_STATUS == "NeverSmoke", "No", "Yes") %>%
  table()
#> .
#>     No  Yes
#> 15087 16178
```

**tidyverse** 中另一个有用的函数是 `case_when()` 函数，它是 `ifelse()` 函数的扩展，但允许指定多于两个情况。我们演示此函数以展示如何重新标记 SMOKE_STATUS 列的级别。对于每个条件，我们使用 `~` 的右侧来指定该条件为 TRUE 时要分配的值。

```r
case_when(nhanes_df$SMOKE_STATUS == "NeverSmoke" ~ "Never Smoked",
          nhanes_df$SMOKE_STATUS == "QuitSmoke" ~ "Quit Smoking",
          nhanes_df$SMOKE_STATUS ==
             "StillSmoke" ~ "Current Smoker") %>%
  table()
#>
#> Current Smoker   Never Smoked   Quit Smoking
#>       7317           15087          8861
```

在前面的示例中，我们没有存储创建的列。要做到这一点，我们可以使用 `$` 运算符或 `cbind()` 函数。tidyverse 还包含一个名为 `mutate()` 的替代函数来添加列。该函数接收一个数据框和一组带有关联名称的列，以添加到数据中或更新数据。在随后的示例中，我们创建列 EVER_SMOKE 并更新列 SMOKE_STATUS。在 `mutate()` 函数中，我们不必使用 `$` 运算符来引用列 SMOKE_STATUS。相反，我们可以只指定列名，函数会将其解释为该列。

```r
nhanes_df <- nhanes_df %>%
  mutate(EVER_SMOKE = ifelse(SMOKE_STATUS == "NeverSmoke",
                             "No", "Yes"),
         SMOKE_STATUS =
             case_when(SMOKE_STATUS == "NeverSmoke" ~ "Never Smoked",
                       SMOKE_STATUS == "QuitSmoke" ~ "Quit Smoking",
                       SMOKE_STATUS == "StillSmoke" ~ "Current Smoker"))
```

本节我们演示的最后一个函数是 arrange() 函数，它接收一个数据框和一个用于排序数据的列向量（数据按第一列排序，并列项按第二列排序，以此类推）。默认情况下，arrange() 函数按递增顺序排序数据，但我们可以使用 desc() 函数来按降序排序。例如，以下代码在按收缩压和舒张压降序排序之前，先将数据筛选为男性吸烟者。也就是说，DBP1 的值用于对收缩压值相同的行进行排序。

```r
nhanes_df %>%
  select(c(YEAR, SEX, SMOKE_STATUS, SBP1, DBP1, LEAD)) %>%
  filter(SEX == "Male", SMOKE_STATUS == "Current Smoker") %>%
  arrange(desc(SBP1), desc(DBP1)) %>%
  head(8)
#>   YEAR SEX    SMOKE_STATUS SBP1 DBP1 LEAD
#> 1 2011 Male Current Smoker  230  120 5.84
#> 2 2015 Male Current Smoker  230   98 1.56
#> 3 2009 Male Current Smoker  220   80 4.84
#> 4 2001 Male Current Smoker  218  118 3.70
#> 5 2017 Male Current Smoker  212  122 2.20
#> 6 2003 Male Current Smoker  212   54 4.00
#> 7 2011 Male Current Smoker  210   92 5.37
#> 8 2007 Male Current Smoker  210   80 2.18
```

如果我们只按 SBP1 排序，那么收缩压值相同的行将保持其原始顺序。你可以在以下输出中看到差异。

```r
nhanes_df %>%
  select(c(YEAR, SEX, SMOKE_STATUS, SBP1, DBP1, LEAD)) %>%
  filter(SEX == "Male", SMOKE_STATUS == "Current Smoker") %>%
  arrange(desc(SBP1)) %>%
  head(8)
#>   YEAR SEX    SMOKE_STATUS SBP1 DBP1 LEAD
#> 1 2011 Male Current Smoker  230  120 5.84
#> 2 2015 Male Current Smoker  230   98 1.56
#> 3 2009 Male Current Smoker  220   80 4.84
#> 4 2001 Male Current Smoker  218  118 3.70
#> 5 2003 Male Current Smoker  212   54 4.00
#> 6 2017 Male Current Smoker  212  122 2.20
#> 7 2007 Male Current Smoker  210   80 2.18
#> 8 2011 Male Current Smoker  210   92 5.37
```

### 5.3.1 练习题

创建一个名为 DBP_CHANGE 的新列，其值等于患者第一次和第四次舒张压读数之差。然后，按此新列以递增顺序对数据框进行排序，并打印前四行。生成的数据框的 head 中的前四个 DBP_CHANGE 值应为 -66、-64、-64 和 -62。

```r
# Insert your solution here:
```

## 5.4 总结和分组

如果我们想了解每个给定种族类别有多少个观测值，可以使用我们在前面章节中描述的 table() 函数。另一个类似的函数是 count() 函数。该函数接收一个数据框和一个或多个列，并计算这些列中唯一值的每个组合的行数。如果未指定列，则计算数据框中的总行数。在以下代码中，我们找到观测值的总数（31,265）以及按种族和年份划分的数量。我们可以看到，每个组的数量波动相当大！

```r
count(nhanes_df)
#> n
#> 1 31265
count(nhanes_df, RACE, YEAR)
#> RACE YEAR n
#> 1 Mexican American 1999 713
#> 2 Mexican American 2001 674
#> 3 Mexican American 2003 627
#> 4 Mexican American 2005 634
#> 5 Mexican American 2007 639
#> 6 Mexican American 2009 672
#> 7 Mexican American 2011 322
#> 8 Mexican American 2013 234
#> 9 Mexican American 2015 287
#> 10 Mexican American 2017 475
#> 11 Other Hispanic 1999 181
#> 12 Other Hispanic 2001 129
#> 13 Other Hispanic 2003 80
#> 14 Other Hispanic 2005 96
#> 15  Other Hispanic 2007  395
#> 16  Other Hispanic 2009  367
#> 17  Other Hispanic 2011  337
#> 18  Other Hispanic 2013  167
#> 19  Other Hispanic 2015  214
#> 20  Other Hispanic 2017  313
#> 21 Non-Hispanic White 1999 1401
#> 22 Non-Hispanic White 2001 1882
#> 23 Non-Hispanic White 2003 1785
#> 24 Non-Hispanic White 2005 1818
#> 25 Non-Hispanic White 2007 1940
#> 26 Non-Hispanic White 2009 2169
#> 27 Non-Hispanic White 2011 1463
#> 28 Non-Hispanic White 2013  917
#> 29 Non-Hispanic White 2015  685
#> 30 Non-Hispanic White 2017 1413
#> 31 Non-Hispanic Black 1999  463
#> 32 Non-Hispanic Black 2001  542
#> 33 Non-Hispanic Black 2003  576
#> 34 Non-Hispanic Black 2005  679
#> 35 Non-Hispanic Black 2007  728
#> 36 Non-Hispanic Black 2009  661
#> 37 Non-Hispanic Black 2011  876
#> 38 Non-Hispanic Black 2013  357
#> 39 Non-Hispanic Black 2015  351
#> 40 Non-Hispanic Black 2017  808
#> 41     Other Race 1999   76
#> 42     Other Race 2001   88
#> 43     Other Race 2003  109
#> 44     Other Race 2005  122
#> 45     Other Race 2007  123
#> 46     Other Race 2009  175
#> 47     Other Race 2011  475
#> 48     Other Race 2013  223
#> 49     Other Race 2015  209
#> 50     Other Race 2017  595
```

像我们之前那样查找计数是我们数据的一种汇总统计形式。tidyverse 中的 summarize() 函数用于计算数据的汇总统计量，并允许我们计算多个统计量：该函数接收一个数据框和基于给定列名的一个或多个汇总函数。在随后的示例中，我们找到观测值的总数以及非西班牙裔黑人的收缩压均值和中位数。请注意，n() 函数是

