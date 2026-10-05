

## 446 11 用数据讲述你的故事

ModernDive 的合著者 Chester Ismay、Albert Y. Kim 以及 Jennifer Chunn 更进了一步，创建了 `fifteight` 包，该包可以在 R 中轻松访问这些数据集。有关 `fifteight` 包中包含的所有 129 个数据集的完整列表，请查看软件包网页：https://fivirthirtyeight.netlify.app/articles/fivirthirtyeight.html。

此外，可以使用此处¹¹ 提供的“vignettes”，使用 `dplyr`、`ggplot2` 以及 tidyverse 中的其他包对这些数据进行从头到尾完全可重复的静态分析。例如，此处¹⁴ 提供了一个如何重现 Bechtel 测试文章末尾图表之一的 vignette（快速指南/教程）。

### 11.3.2 1999 年美国的出生人数

`fifteight` 包中的 `US_births_1994_2003` 数据框提供了 1994 年至 2003 年间美国出生人数的信息。有关此数据的更多信息（包括指向 FiveThirtyEight.com 上原始文章的链接），请在控制台中运行 `?us_births_1994_2003` 来查看帮助文件。

通过 RStudio 的电子表格视图 `view()` 函数或使用 `dplyr` 包中的 `glimpse()` 来预览你的数据始终是一个好习惯：

```r
glimpse(US_births_1994_2003)
```

| Rows | 3,652 |
| :--- | :--- |
| Columns | 6 |

```r
$ year <int> 1994, 1994, 1994, 1994, 1994, 1994, 1994, 1994, 1994, 19~ 
$ month <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, ~ 
$ date_of_month <int> 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, ~ 
$ date <date> 1994-01-01, 1994-01-02, 1994-01-03, 1994-01-04, 19~ 
$ day_of_week <ord> Sat, Sun, Mon, Tue, Wed, Thurs, Fri, Sat, Mon-
$ births <int> 8096, 7772, 10142, 11428, 11053, 11406, 11251, 8653~
```

我们将关注1999年每天的出生人数。回第 3.2 节，我们可以使用 `dplyr` 包中的 `filter()` 函数来实现：

```r
US_births_1999 <- US_births_1994_2003 |> 
filter(year == 1999)
```

¹¹³ https://fivirthirtyeight.netlify.app/articles/
¹⁴ https://fivirthirtyeightdata.github.io/articles/bechtel.html

## 11.3 案例研究：有效的数据故事

正如第2.4节所述，由于日期是时间的概念并具有顺序，因此折线图比散点图更合适。换句话说，我们应该使用 `geom_line()` 而不是 `geom_point()`。

```r
ggplot(US_births_1999, aes(x = date, y = births)) +
  geom_line() +
  labs(x = "Date",
      y = "Number of births",
      title = "US Births in 1999")
```

![](img/44572518041017e8f011b0c19d481_0.png)

**图 11.9：1999 年美国的出生人数。** 我们看到在2000年1月之前出现了一个巨大的下降，很可能是由于假期季节导致的。然而，1999年10月1日之前出现了超过14000人出生的峰值？这种异常高值的原因是什么？让我们按出生人数的降序对 `US_births_1999` 进行排序。回想第3.6节，我们可以使用 `dplyr` 中的 `arrange()` 函数来实现此，确保按降序排序：

```r
US_births_1999 |>
arrange(desc(births))
```

| | month | date_of_month | day_of_week | births |
| :--- | :--- | :--- | :--- | :--- |
| <int> | <int> | <ord> | <int> |
| 1 | 1999 | 9 | 1999-09-09 | Thurs | 14540 |
| 2 | 1999 | 12 | 1999-12-21 | Tues | 13508 |
| 3 | 1999 | 9 | 1999-08-08 | Wed | 13437 |
| 4 | 1999 | 9 | 1999-09-21 | Tues | 13384 |
| 5 | 1999 | 9 | 1999-08-28 | Tues | 13358 |
| 6 | 1999 | 7 | 1999-07-07 | Wed | 13343 |
| 7 | 1999 | 7 | 1999-08-07 | Thurs | 13245 |
| 8 | 1999 | 8 | 1999-08-17 | Tues | 13201 |
| 9 | 1999 | 9 | 1999-09-10 | Fri | 13181 |
| 10 | 1999 | 12 | 1999-12-28 | Tues | 13158 |

# A tibble: 365 x 6
# 355 more rows

出生人数最多（14,540）的日期实际上是 1999-09-09。如果我们以月/日/年的格式（美国的标准格式）写下日期，出生人数最多的日期就是 9/9/99！全是9！难道是父母在这一天故意以更高的比例诱导分产吗？无论原因是什么，这都是一个有趣的故事！

学习检查 (LC11.5) 1994年至2003年间，美国出生人数最少的日期是哪一天？关于这种情况，你可以讲述什么样的故事？

是时候用数据思考并进一步用数据讲述你的故事了！统计建模在这里如何帮助你？什么类型的统计推断会有帮助？你还能发现什么？你可以将此分析带到何处？在这个分析中你哪些假设？我们将这些问题留给读者去探索和研究。

记得通过序言中的联系方式与我们联系。我们很想看到你的想法！请查看 https://moderndive.com/labs 额外的问题集和实验。

### 11.3.3 R 代码脚本

本章中使用的所有 R 代码脚本文件位于 https://www.moderndive.com/v2/scripts/11-tell-your-story-with-data.R。全书中相关章节保存为 *.R 文件的代码如下：

| 章节 | 链接 |
| :--- | :--- |
| 1 | https://moderndive.com/v2/scripts/01-getting-started.R |
| 2 | https://moderndive.com/v2/scripts/02-visualization.R |
| 3 | https://moderndive.com/v2/scripts/03-wrangling.R |
| 4 | https://moderndive.com/v2/scripts/04-tidy.R |
| 5 | https://moderndive.com/v2/scripts/05-regression.R |
| 6 | https://moderndive.com/v2/scripts/06-multiple-regression.R |
| 7 | https://moderndive.com/v2/scripts/07-sampling.R |
| 8 | https://moderndive.com/v2/scripts/08-confidence-intervals.R |
| 9 | https://moderndive.com/v2/scripts/09-hypothesis-testing.R |
| 10 | https://moderndive.com/v2/scripts/10-inference-for-regression.R |
| 11 | https://moderndive.com/v2/scripts/11-tell-your-story-with-data.R |

结语

现在你已经走这一步，积累了许多关于如何使用模拟技术的知识。我们希望你能够创建出精美的图表，以读者可以清晰理解的方式展示信息。希望这些技能在未来帮助你讲述故事。

