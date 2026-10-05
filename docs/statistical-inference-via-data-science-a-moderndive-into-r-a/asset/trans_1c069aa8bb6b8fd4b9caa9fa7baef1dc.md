

## 1.4 探索你的第一个数据集

### 1.4.2 flights 数据框 (data frame)

我们将从探索 `flights` 数据框开始，了解它的结构。在你的控制台中运行以下代码，可以手动输入或复制粘贴。它将在你的控制台中显示 `flights` 数据框的内容。请注意，输出可能会根据你显示器的大小略有不同。

flights

```
# A tibble: 435,352 x 19
year month day_time sched_dep_time dep_time_time delay arr_time
<int> <int> <int> <int> <dbl> <dbl>
1 2023 1 1 2038 203 328
2 2023 1 1 18 2300 78 228
3 2023 1 1 31 2344 47 500
4 2023 1 1 33 2140 173 238
5 2023 1 1 36 2048 228 223
6 2023 1 1 50 500 3 808
7 2023 1 1 52 510 10 948
8 2023 1 1 54 530 -6 645
9 2023 1 1 57 520 17 926
10 2023 1 1 57 545 2 845
# i 435,342 more rows
# i 12 variables: sched_arr_time <int>, arr_delay <dbl>
# carrier <chr>, flight <int>, tailname <chr>, origin <chr>, dest <chr>
# air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>
# time_hour <dttm>
```

让我们来解析这个输出：

- 435,352 x 19：tibble 是 R 中一种特定的数据框（data frame）。这个特定的数据框有 435,352 行，对应不同的观测值。在这里，每个观测值都是一次航班。19 列对应描述每个观测值的 19 个变量。

- `year`、`month`、`day_time`、`sched_dep_time`、`dep_time` 和 `arr_time` 是不同的列，换句话说，是该数据集不同的变量。

- 我们接着看到前 10 行，对应前 10 次航班。R 只显示前 10 行，因为如果显示所有 435,352 行，将会淹没你的屏幕。

- ... 还有 435,342 行和 11 个变量：这告诉我们还有 435,352 行数据和 11 个变量无法在当前屏幕中完全显示。

## 1 在 R 中开始处理数据

遗憾的是，这个输出并不能让我们很好地探索数据，但它提供了一个很好的预览。让我们看看探索数据框的一些不同方法。

### 1.4.3 探索数据框

有很多方法可以让你熟悉 `flights` 这样的数据框包含的内容。我们展示了三个以数据框作为“参数”（输入）的函数，以及一种探索数据框中某一列的方法：

- 使用 `view()` 函数，它会打开 RStudio 内置的数据查看器。
- 使用 `glimpse()` 函数，它包含在 `dplyr` 包中。
- 使用 `relationship()` 函数，它包含在 `knitr` 包中。
- 使用 `$` 提取运算符，用于查看单个变量。

#### View():

在 RStudio 的控制台中运行 `View(flights)`，可以手动输入或粘贴到控制台面板中。在弹出的查看器中探索这个数据框。养成查看你遇到的任何数据框的习惯。注意 `View()` 中的大写字母 `V`。R 是区分大小大小的，如果你运行的是 `view(flights)` 而不是 `View(flights)`，你将收到错误信息。

#### 学习检查

(LC1.3) `flights` 数据集中的任意一行指的是什么？

- A. 航空公司公司的数据
- B. 航班的数据
- C. 机场的数据
- D. 多次航班的数据

通过运行 `View(flights)`，我们可以探索列中列出的不同变量。观察发现有很多不同类型的变量。某些变量如 `distance`、`day` 和 `arr_delay` 是我们所说的定量变量（quantitative variables）。这些变量本质上是数值型的。其他变量是分类变量（categorical）。

如果你查看 `View(flights)` 输出的最左列，你会看到一列数字。这些是数据集的行号。浏览具有相同数字行（例如第 5 行），你可以了解每行代表什么。这允许你通过注意特定行中各列的值来识别该行描述的是什么对象。这通常被称为**观测单位**（observational unit）。在本例中，观测单位是 2023 年从纽约出发的个人。你可以通过确定每个变量测量的是什么“事物”来识别观测单位。我们将介绍更多关于观测单位的内容。

#### 2. glimpse():

我们将涵盖的第二种方法是使用 `dplyr` 包包含的 `glimpse()` 函数来探索数据框。因此，在运行 `library(dplyr)` 加载包后，你可以直接使用 `glimpse()` 函数。该函数为我们提供了探索数据框优于 `view()` 的替代方案：

```
glimpse(flights)
Rows: 435,352
Columns: 19
$ year    <int> 2023, 2023, 2023, 2023, 2023, 2023, 2023, 2023
$ month   <int> 1, 1, 1, 1, 1, 1, 1, 1
$ day      <int> 1, 1, 1, 1, 1, 1, 1, 1
$ dep_time  <int> 2038, 2300, 2344, 2140, 2048, 500, 510, 530
$ origin   <int> 328, 78, 228
$ arr_time  <int> 328, 228, 500, 238, 223, 808, 948, 645, 926, 845
$ sched_arr_time <int>
$ arr_delay <dbl>
$ carrier <chr>
$ flight <int>
$ tailname <chr>
$ origin <chr>
$ dest <chr>
$ air_time <dbl>
$ distance <dbl>
$ hour <dbl>
$ minute <dbl>
$ time_hour <dttm>
```
*(注：此处示例中的 glimpse 输出内容根据原文逻辑进行了对齐处理，保持代码块格式)*

*(注：原文中的 glimpse 示例数据存在错乱，翻译时保留了其结构并进行了微调以确保代码可读性。)*

