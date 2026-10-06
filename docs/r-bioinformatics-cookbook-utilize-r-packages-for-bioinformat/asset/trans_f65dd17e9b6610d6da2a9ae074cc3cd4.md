

## 324 使用 purr 和 base R 进行函数式编程

步骤 4 转移到 Bioconductor，我们对 `ExpressionSet` 对象使用了 Biobroom 版本的 `tidy()`。这会将表达值的方矩阵转换为整洁（tidy）的数据框（dataframe），并带有样本数据和其他类型的列。额外参数 `addPhen` 是该类型对象特有的，它会插入对象中的表型元数据。请注意，生成的数据框超过了 200 万行——生物数据集可能非常大，并生成巨大的数据框。

## 使用嵌套数据框进行函数式编程

函数式编程是一种关注于使用函数来解决问题的编程风格。它避免了编写清晰、可重用、易理解且行为可预测的代码。

数据框是整洁工作法的核心，我们打算将其视为类似于电子表格的矩形容器，每个单元格仅有一个值。事实上，数据框是可以嵌套的——它们可以在单个单元格中包含其他数据框。这在内部是通过数据框的列表列（list column实现的，使得每个单元格变成列表的成员，任何类型的对象都可以存储在外部数据框现概念上的单个单元格中。

在本教程中，我们将查看如何创建嵌套数据框，以及使用函数式风格对其进行操作的方法，旨在简化大型或多维度数据处理工作。

## 准备工作

我们将使用 `tidyr`、`dplyr`、`purrr` 和 `broom` 库。我们还将使用内置的 `mtcars` 数据。

## 如何实现...

可以通过以下步骤使用嵌套数据框：

- 1. 创建嵌套数据框：

```r
library(tidyr)
nested_mt <- nest(mtcars, -cyl)
```

- 2. 添加一个新的列表列，存储线性模型的结果：

```r
library(dplyr)
library(purrr)
nested_mt_cols <- nested_mt |>
mutate(
  model = map(data, ~ lm(mpg ~ wt, data = .x))
)
```

- 3. 添加一个新的列表列，存储线性模型整理后的结果：

```r
library (broom)
nested_mt_list_cols <- nested_mt_list_cols |>
mutate (tidy_model = map(model, tidy))
```

- 4. 解嵌套数据框：

```r
simple_df <- unnest(nested_mt_list_cols, tidy_model)
```

这就是我们处理嵌套数据框的方式。

## 运行原理...

首先，我们在步骤 1 中创建了一个嵌套数据框。我们使用 `tidyr` 中的 `nest()` 函数对 `mtcars` 数据框进行嵌套。`-` 选项告诉函数哪些列不要被折叠进数据框的嵌套部分。这实际上将 `cyl` 列变成了一个因子，并据此创建子集。这在概念上与你可能已经熟悉的 `dplyr::group_by()` 函数相似。通过检查对象类可以看到发生了什么：

```
## A tibble: 3 x 2
## cyl data
## <dbl> <list>
## 1 6 <tibble [7 x 10]>
## 2 4 <tibble [11 x 10]>
## 3 8 <tibble [14 x 10]>
```

嵌套数据框包含一个名为 `data` 的新列，嵌套数据已折叠其中。每个嵌套数据框包含了原始数据框中具有每个 `cyl` 值的行。

在步骤 2 中，我们通过 `mutate()` 在嵌套数据框上创建了一个新列。在 `mutate()` 调用内部，我们使用 `purrr` 中的 `map()` 函数来遍历命名列中的每个子数据框，并应用命名函数。`map` 接收 `data lm(...)`，因此我们遍历较大数据框中的每个微型数据框，并将 `lm()` 应用于该微型数据框。在函数内部，新的 `.x` 是非常地道的写法，表示我们当前正在处理的对象——即那个微型数据框。嵌套数据框看起来如下所示：

```
## A tibble: 3 x 3
## cyl data
## <dbl> <list>
## 1 6 <tibble [7 x 10]> <lm>
## 2 4 <tibble [11 x 10]> <lm>
## 3 8 <tibble [14 x 10]> <lm>
```

一个名为 `model` 的新列在每个 `cyl` 取值处都包含一个 `lm` 对象。

## 使用 purr 和 base R 进行函数式编程

已经建立了使用 `mutate` 和 `map()` 将复杂对象整理为数据框的模式。在步骤 3 中，我们使用 `broom::tidy()` 将 `lm()` 对象转换为 `tibble`（一种数据框）。嵌套数据框看起来如下：

```
## A tibble: 3 x 4
## model tidy_model
## cyl data <list>
## <dbl> <list>
## #1 6 <tibble [7 x 10]> <lm> <tibble [2 x 5]>
## #2 4 <tibble [11 x 10]> <lm> <tibble [2 x 5]>
## #3 8 <tibble [14 x 10]> <lm> <tibble [2 x 5]>
```

步骤 4 使用 `unnest()` 函数将所有内容返回到更简单的数据框；第二个参数 `tidy_model` 是我们想要解包的列。我们得到了如下结果：

```
## A tibble: 6 x 8
## model term estimate std.error
## cyl data p.value
## <dbl> <list> <dbl> <dbl>
## <chr>
1 6 <tibble [7 x
<lm> (Intercept) 28.4 4.18 6.79 0.00105
2 6 <tibble [7 x
<lm> wt -2.78 1.33 -2.08 0.0918
3 4 <tibble [11 x 10]>
<lm> (Intercept) 39.6 4.35 9.10 0.00077
4 4 <tibble [11 x 10]>
<lm> wt -5.65 1.85 -3.05 0.0137
5 8 <tibble [14 x 10]>
<lm> (Intercept) 23.9 7.94 0.00405
6 8 <tibble [14 x 10]>
<lm> wt -2.19 .037
```

我们现在有了一个解包了 model 的数据框。注意（此处省略了后续重复的说明文字）。

