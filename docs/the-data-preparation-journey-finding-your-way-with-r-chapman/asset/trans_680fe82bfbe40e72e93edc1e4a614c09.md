
**表10.2：5条记录**

| name | n |
|---|---|
| Delta Air Lines Inc. | 1213 |
| United Air Lines Inc. | 1117 |
| Alaska Airlines Inc. | 714 |
| JetBlue Airways | 514 |
| American Airlines Inc. | 365 |

这些连接（join）使用的术语与你在{dplyr}中熟悉的术语类似。这个左连接将返回flights表中的所有记录，以及airlines表中与之匹配的变量。

为了指定连接的关键变量，我们使用SQL术语ON。请注意，我们指定的表名和变量名之间用句点分隔。

如需了解更多关于使用SQL（尤其是SQLite）的信息，强烈推荐托马斯·尼尔德（Thomas Nield）的《SQL入门》（Nield, 2016）。

### 10.3 使用{tidylog}包

任何表连接的重要环节都是检查结果，看它是否符合我们的预期。{tidylog}包（Elders and Oldoni, 2020）

该包的作者承认，这一功能会为处理过程增加一些计算和时间开销，但这可能是值得的。如果使用得当，它返回的信息可以立即指示代码是否正常工作。这在编写代码的早期阶段尤其如此——当你确信得到预期结果时，可以移除这些函数。

```r
library("tidylog")
```

运行library(tidylog)函数后，结果会自动生成。

美国职业棒球大联盟（Major League Baseball）的球队在美国和加拿大的城市进行比赛（目前只有多伦多！），但吸引了来自世界各地的顶尖球员。在这个示例中，代码创建了一个汇总表，显示2001赛季击球手的出生国家。为此，我们将使用R包中存储的数据，该数据包含Lahman棒球数据库（以最初创建该数据库的肖恩·拉赫曼[Sean Lahman]的名字命名）（Friendly et al., 2020）。

此轮运行完成后，{tidylog}包会生成关于连接、分组和计数（tally）函数的一些汇总信息。

```r
## start with the Batting table
Lahman::Batting |>
  ## filter for year
  filter(yearID == "2001") |>
  ## join to People table (where the birth country is recorded)
  left_join(Lahman::People, by = "playerID") |>
  ## now group_by and tally
  group_by(birthCountry) |>
  tally() |>
  arrange(desc(n)) |>
  slice_head(n = 10)
```

```
## filter: removed 110,845 rows (99%), 1,339 rows remaining

## left_join: added 25 columns (birthYear, birthMonth, birthDay, birthCountry, birthState, ...)

##          > rows only in x          0

##          > rows only in y  (19,456)

##          > matched rows     1,339

##          >                 ========

##          > rows total       1,339

## group_by: one grouping variable (birthCountry)

## tally: now 22 rows and 2 columns, ungrouped

## slice_head: removed 12 rows (55%), 10 rows remaining
```

```
## # A tibble: 10 x 2
##   birthCountry     n
##   <chr>        <int>
```

| birthCountry | n |
|---|---|
| USA | 1002 |
| D.R. | 120 |
| P.R. | 57 |
| Venezuela | 54 |
| Mexico | 19 |
| Cuba | 16 |
| CAN | 14 |
| Japan | 14 |
| Panama | 11 |
| Australia | 6 |

## 11 探索与验证策略

在本章中：

- 探索性数据分析以识别问题，包括{skimr}包
- 使用{validate}包进行结构化测试

### 11.1 识别脏数据

在第2章前面，我们介绍了与“脏数据”相关的挑战。

**第一个挑战：** 我们如何发现数据中存在的问题？

**第二个挑战：** 我们能够并且应该如何处理这些问题？

“数据验证”一词有时指在数据收集时应用的验证（例如，在基于网络的调查工具中），在其他情况下，它指确保数据满足指定条件的编程方法。在这两种情况下，我们都可以将数据验证视为一种质量控制形式，从快速的健全性检查到严格的编程测试。（White et al., 2013）

收集过程中的数据验证可以通过使用下拉框来消除拼写错误，或通过要求输入的文本匹配特定模式的输入字段来实现。例如，加拿大邮政编码始终遵循以下模式：大写字母（但并非所有字母）、0到9的数字、大写字母、空格、数字、大写字母和数字。邮政编码的第一个字母指定一个地区；在纽芬兰与拉布拉多省，邮编以字母“A”开头，而在育空地区以“Y”开头，这为可能的验证增加了另一个维度。电子数据收集还可以强制要求在提交前完成某项内容的填写。

这些强加的验证规则带有风险，需要深思熟虑地实施。强迫一个人填写字段可能会导致捏造的值，这可能比缺失字段更糟糕。想象一下强迫某人报告他们的收入——他们可能不乐意分享这些信息，为了满足字段要求，可能会输入“1”或一个荒谬的大数字，两者都不准确。在这种情况下，表单最好提供一个“不愿回答”的选项，让受访者有一个不会扭曲最终结果的选项。

在这里的工作中，我们将重点放在数据收集后的检查和验证上。分析人员可以在数据提供给下一步骤之前指定参数。这些参数可以表示为规则或假设，并基于对主题的了解。（van der Loo and de Jonge, 2018，第6章：数据验证）

我们可能评估的内容包括：

- 字段必须以特定方式结构化；例如邮政编码和日期字段。
- 值可能有一定的范围或有限数量的类别。
- 某些值（如年龄）必须为正数。
- 两个或多个变量之间可能存在已知关系。

现在我们来讨论评估数据中值的方法。

### 11.2 探索性数据分析

识别脏数据的一种方法是通过*探索性数据分析*（EDA）过程。（Tukey, 1977）EDA过程首先旨在帮助指导我们的分析，但它还有一个额外的好处，即提供关于数据污染方式的线索。

EDA由两类技术组成：

- 汇总统计
- 数据可视化

在此阶段，我们要查找的内容包括：

- 变量类型
- 缺失值
- 无效值和异常值，包括哨兵值
- 过宽或过窄的数据范围
- 数据的单位

（改编自（Zumel and Mount, 2019，第54页））

在此示例中，我们将查看一些关于公司员工的合成数据。数据存储在Excel文件的多个工作表中；我们将探索“df_HR_train”工作表中的数据，该工作表记录某人是否已完成强制培训课程。

```r
readxl::excel_sheets(dpjr::dpjr_data("cr25/cr25_human_resources.xlsx"))
```

```
## [1] "readme"      "df_HR_main"      "df_HR_transaction"
## [4] "df_HR_train"
```

一旦将数据读入我们的环境，我们就可以使用一些EDA方法来检查数据。

```r
df_HR_train <- readxl::read_excel(dpjr::dpjr_data("cr25/cr25_human_resources.xlsx"), sheet = "df_HR_train")
```

我们可以使用dplyr::glimpse()函数开始调查。此函数返回数据框的维度、变量类型以及每个变量的前几个值。

```r
glimpse(df_HR_train, width = 65)
```

```
## Rows: 999
## Columns: 5
## $ emp_id       <chr> "ID001", "ID002", "ID003", "ID004", "ID0~
## $ train_security <chr> "TRUE", "FALSE", "TRUE", "FALSE", "FALSE~
## $ train_crm    <chr> "TRUE", "FALSE", "TRUE", "TRUE", "FALSE"~
## $ train_qc     <chr> "NA", "FALSE", "FALSE", "FALSE", "FALSE"~
## $ train_history <chr> "TRUE", "TRUE", "TRUE", "TRUE", "TRUE", ~
```

