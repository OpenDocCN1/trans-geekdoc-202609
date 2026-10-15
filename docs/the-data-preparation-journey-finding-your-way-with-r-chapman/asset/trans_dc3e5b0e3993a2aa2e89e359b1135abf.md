
## 7.1.1.1 使用标签

{haven} 创建的数据框中的标签可以使用 unlabelled() 函数转换为因子类型。

如果我们使用来自 SPSS 文件的 penguins 数据框统计每个物种的企鹅数量，我们会看到以下内容：

```
penguins_sav |>
  group_by(species) |>
  tally()
```

```
## # A tibble: 3 x 2
##   species       n
##   <dbl+lbl> <int>
## 1 1 [Adelie]   152
## 2 2 [Chinstrap] 68
## 3 3 [Gentoo]   124
```

在这个版本中，“species” 变量保留了数值。

通过应用 unlabelled() 函数，“haven_labelled” 类型的变量被转换为因子类型，并且标签（即物种名称）现在显示在我们的汇总表中：

```
penguins_sav |>
  unlabelled() |>
  group_by(species) |>
  tally()
```

```
## # A tibble: 3 x 2
##   species       n
##   <fct>    <int>
## 1 Adelie   152
## 2 Chinstrap 68
## 3 Gentoo   124
```

另一种方法是显式更改变量类型，在 mutate() 和 mutate_if() 中的一个 mutate 函数内部使用 to_factor 转换。在此第一个示例中，变量 species 从 labelled 转换为因子类型。

```
penguins_sav |>
  mutate(species = as_factor(species)) |>
  group_by(species) |>
  tally()
```

## # A tibble: 3 x 2
##   species       n
##   <fct>     <int>
## 1 Adelie      152
## 2 Chinstrap    68
## 3 Gentoo      124

在这个第二个变体中，mutate_if(is.labelled) 函数转换了所有标记的变量。

```
penguins_sav |>
  mutate_if(is.labelled, to_factor) |>
  group_by(species, island) |>
  tally()
```

## # A tibble: 5 x 3
## # Groups:   species [3]
##   species island       n
##   <fct>   <fct>    <int>
## 1 Adelie  Biscoe      44
## 2 Adelie  Dream       56
## 3 Adelie  Torgersen   52
## 4 Chinstrap Dream     68
## 5 Gentoo  Biscoe     124

## 7.1.2 读取 SPSS 调查文件：“Video”

标记数据框的功能在处理调查数据时非常有益。数据框可以包含表单中捕获的变量代码、与这些值关联的值，以及标签中的问题文本。

本示例中使用的文件来自谢菲尔德大学数学与统计帮助中心的“教学数据集”²

²https://www.sheffield.ac.uk/mash/statistics/datasets

## 7.1 统计软件

![](img/b86622d1e9ca82b3cbec45faaffaaf26_104_0.png)

## 图 7.2 SPSS 变量视图。

![](img/b86622d1e9ca82b3cbec45faaffaaf26_104_1.png)

## 图 7.3 SPSS 变量标签。

![](img/b86622d1e9ca82b3cbec45faaffaaf26_105_0.png)

## 图 7.4 SPSS 值标签。

R 包 {haven} 允许我们捕获所有这些信息。

## 7.1.2.1 将 SPSS 数据读入 R

第一步，我们将使用默认参数从 SPSS 文件中读取数据。

```
df_video <- read_spss(dpjr::dpjr_data("Video_SPSS.sav"))

# display the data in the console
df_video
```

## # A tibble: 20 x 17
##   Person Gender Heardofcondition Set `@1st`
##   <dbl> <dbl+lbl> <dbl+lbl> <dbl> <dbl+lbl>
## ## 1 1 1 [Male] 1 [Yes] 1 4 [Demonst~
## ## 2 2 2 [Female] 1 [Yes] 1 4 [Demonst~
## ## 3 3 2 [Female] 2 [No] 1 4 [Demonst~
## ## 4 4 2 [Female] NA 1 4 [Demonst~
## ## 5 5 2 [Female] 2 [No] 1 4 [Demonst~
## ## 6 6 2 [Female] 1 [Yes] 11 1 [General~
## ## 7 7 2 [Female] 1 [Yes] 11 1 [General~
```
##  8        8 1 [Male]     1 [Yes]               11 1 [General~
##  9        9 2 [Female] NA                     11 1 [General~
## 10       10 2 [Female] NA                     11 1 [General~
## 11       11 1 [Male]    NA                     24 3 [Old vid~
## 12       12 2 [Female] NA                     24 3 [Old vid~
## 13       13 1 [Male]    NA                     24 3 [Old vid~
## 14       14 2 [Female] NA                     24 3 [Old vid~
## 15       15 2 [Female] NA                     24 3 [Old vid~
## 16       16 1 [Male]    2 [No]                 10 2 [Medical~
## 17       17 1 [Male]    2 [No]                 10 2 [Medical~
## 18       18 2 [Female] 1 [Yes]                 10 2 [Medical~
## 19       19 2 [Female] 1 [Yes]                 10 2 [Medical~
## 20       20 1 [Male]    1 [Yes]                 10 2 [Medical~
## ## i 12 more variables: `@2nd` <dbl+lbl>,
## ##     `@3rd` <dbl+lbl>, `@4th` <dbl+lbl>,
## ##   Combination <dbl>,
## ##   VideoAGenUnderstandingCONDITION <dbl+lbl>,
## ##   VideoBdoctorUnderstandingCONDITION <dbl+lbl>,
## ##   VideoCOldUnderstandingCONDITION <dbl+lbl>,
## ##   DEMOUnderstandingCONDITION <dbl+lbl>, ...
```

其中一些变量名以 @（at 符号）开头——这会在后面给我们带来一些麻烦，因此让我们使用 {janitor} 包（Firke，2021）³ 中的 clean_names() 函数来清理它们。

```
df_video <- janitor::clean_names(df_video)
```

现在，我们可以使用 {labelled} 中的 look_for() 函数来查看数据框的内容：

```
look_for(df_video)
```

## 7.1.2.2 处理缺失值

非常经常，SPSS 文件会有“用户定义缺失值”。在视频调查文件中，它们被编码为“NA”。但通常，调查结果的分析会有多种类型的“缺失值”：

- 受访者留空问题
- 受访者因跳逻辑而未回答问题（换句话说，受访者未看到该问题）
- 分析人员在计算其他类别响应的百分比时，可能决定将“不知道”或“不适用”编码为“缺失”。

根据具体情况，你可能希望统计其中一些。例如，如果有大量“不知道”和“不适用”响应，你可能希望分析其中哪一个（它们意味着完全不同的事情！）如果它们都被编码为“NA”，你就失去了获得该见解的能力。

在下面的代码中，向 read_spss() 函数添加 user_na = TRUE 参数可保留原始值。

```
df_video <- read_spss(dpjr::dpjr_data("Video_SPSS.sav"), user_na = TRUE)

df_video <- janitor::clean_names(df_video)

df_video
```

```
## # A tibble: 20 x 17
##   person gender  heardofcondition  set x1st
##     <dbl> <dbl+lbl> <dbl+lbl>       <dbl> <dbl+lbl>
## 1     1 1 [Male] 1 [Yes]           1 4 [Demonst~
## 2     2 2 [Female] 1 [Yes]          1 4 [Demonst~
## 3     3 3 2 [Female] 2 [No]           1 4 [Demonst~
## 4     4 4 2 [Female] 0 (NA) [N/A]     1 4 [Demonst~
## 5     5 5 2 [Female] 2 [No]           1 4 [Demonst~
## 6     6 6 2 [Female] 1 [Yes]          11 1 [General~
## 7     7 7 2 [Female] 1 [Yes]          11 1 [General~
## 8     8 8 1 [Male]  1 [Yes]          11 1 [General~
## 9     9 9 2 [Female] 0 (NA) [N/A]    11 1 [General~
## 10   10 10 2 [Female] 0 (NA) [N/A]   11 1 [General~
## 11   11 11 1 [Male]  0 (NA) [N/A]   24 3 [Old vid~
## 12   12 12 2 [Female] 0 (NA) [N/A]   24 3 [Old vid~
## 13   13 13 1 [Male]  0 (NA) [N/A]   24 3 [Old vid~
## 14   14 14 2 [Female] 0 (NA) [N/A]   24 3 [Old vid~
## 15   15 15 2 [Female] 0 (NA) [N/A]   24 3 [Old vid~
## 16   16 16 1 [Male]  2 [No]          10 2 [Medical~
## 17   17 17 1 [Male]  2 [No]          10 2 [Medical~
## 18   18 18 2 [Female] 1 [Yes]        10 2 [Medical~
## 19   19 19 2 [Female] 1 [Yes]        10 2 [Medical~
## 20   20 20 1 [Male]  1 [Yes]        10 2 [Medical~
## # i 12 more variables: x2nd <dbl+lbl>, x3rd <dbl+lbl>,
```

```
## #   x4th <dbl+lbl>, combination <dbl>,
## #   video_a_gen_understanding_condition <dbl+lbl>,
## #   video_bdoctor_understanding_condition <dbl+lbl>,
## #   video_c_old_understanding_condition <dbl+lbl>,
## #   demo_understanding_condition <dbl+lbl>,
## #   total_a_gen <dbl>, total_bdoc <dbl>, ...
```

第一个版本中为“NA”的内容现在变为“0”。

## 7.1.2.3 探索数据

attributes() 函数为我们提供了一种查看变量详细信息的途径。

首先，我们可以查看整个数据框的属性。

```
attributes(df_video)
```

```
## $class
## [1] "tbl_df"      "tbl"         "data.frame"
##
## $row.names
## [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17
## [18] 18 19 20
##
## $names
## [1] "person"
## [2] "gender"
## [3] "heardofcondition"
## [4] "set"
## [5] "x1st"
## [6] "x2nd"
## [7] "x3rd"
## [8] "x4th"
## [9] "combination"
## [10] "video_a_gen_understanding_condition"
## [11] "video_bdoctor_understanding_condition"
## [12] "video_c_old_understanding_condition"
## [13] "demo_understanding_condition"
## [14] "total_a_gen"
## [15] "total_bdoc"
## [16] "total_c_old"
## [17] "total_ddemo"
```

³{janitor} 的参考页面在这里：http://sfirke.github.io/janitor/
