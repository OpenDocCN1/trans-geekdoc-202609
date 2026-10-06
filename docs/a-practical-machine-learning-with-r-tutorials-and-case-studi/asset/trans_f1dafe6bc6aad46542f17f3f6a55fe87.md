

## 3.9 使用 tidyverse 包进行数据清洗

这是命令所处理的数据框。然后，通过一个或多个条件指定应该选择哪些观测值。

在下面的示例中，我们演示了 `filter()` 的几种应用。为此，我们使用了通过 `select()` 命令创建的数据框 `TitanicNarrow`：

### 仅分析男性乘客：

如果我们想分析男性乘客并将结果保存在一个新数据框 `TitanicMen` 中，可以使用：

```R
TitanicMen=filter(TitanicNarrow, Sex=="male")
head(TitanicMen)
```

| | Survived | Class | Sex | Age | FareInPounds |
|---|---|---|---|---|---|
| 1 | 0 | male | 22 | 7.250 |
| 2 | 0 | male | 35 | 8.050 |
| 3 | 0 | male | 27 | 8.458 |
| 4 | 0 | male | 54 | 51.862 |
| 5 | 0 | male | 22 | 21.075 |
| 6 | 0 | male | 28 | 8.050 |

在上面的代码块中，当我们过滤男性乘客时，我们使用 `Sex=="male"` 作为条件。这个条件可以翻译为：“变量名 `Sex.x` 要求等于 'male'”。

请注意以下两个技巧：

- 1. 我们使用 `==` 而不是 `=`。这在 R 以及大多数其他编程语言中都是必须的，因为 `==` 表示一个条件而不是赋值。在条件中漏掉第二个 `-` 号是一个常见的错误。幸运的是，当这种情况发生时，R 会给出明显的错误。
- 2. 单词 "male" 必须写在引号中，因为条件要求变量 `Sex.x` 等于字符值 "male" 而不是对象 `male`。

### 仅分析低票价乘客：

为了筛选出票价低于 7 英镑的乘客数据框，并将结果保存到新数据框 `TitanicLowFare` 中，你可以使用以下 R 代码：

```R
TitanicLowFare=filter(TitanicNarrow, FareInPounds<7)
head(TitanicLowFare)
```

## 3 R 和 RStudio 简介

```R
## Survived Pass Class Sex Age FareInPounds
## 1 0 3 male 45 6.975
## 2 0 3 male 19 6.750
## 3 0 3 male 36 0.000
## 4 0 3 male 34 6.496
## 5 0 1 male 40 0.000
## 6 1 3 male 25 0.000
```

如果你仔细观察输出结果，你会发现它包含了票价为 0 的情况。这些可能是票价缺失的观测值。理想情况下，这些 `FareInPounds` 条目应该是 `NA`（不可用），但在该数据集中它们是 0。我们可以通过 `&` 组合这两个条件来剔弃这些观测值；

```R
TitanicLowFare=filter(TitanicNarrow, FareInPounds<7 & FareInPounds>0)
head(TitanicLowFare)
```

```R
## Survived Pass Class Sex Age FareInPounds
## 1 0 3 male 45 6.975
## 2 0 3 male 19 6.750
## 3 0 3 male 34 6.496
## 4 0 3 male 61 6.237
## 5 0 3 male 18 6.496
## 6 0 3 male 20 4.013
```

现在你现在看到输出中不再包含票价为 0 的观测值了。

### 仅分析 60 岁及以上的乘客（老年人）：

为了只分析年龄在 60 岁或以上的乘客，并将结果保存到新数据框 `TitanicSeniors` 中，我们可以使用以下 R 代码：

```R
TitanicSeniors=filter(TitanicNarrow, Age>=60)
head(TitanicSeniors)
```

```R
## Survived Pass Class Sex Age FareInPounds
## 1 0 2 male 66.0 10.50
## 2 0 1 male 65.0 61.98
## 3 0 1 male 64.0 27.72
## 4 0 1 male 71.0 54.65
## 5 0 3 male 70.5 7.75
## 6 0 1 male 60.0 25.93
```

注意，输出仅包含年龄为 60 岁及以上的乘客。我们在条件中使用 `>=` 而不是 `>` 来实现这一点。这确保了年龄为 60 的乘客包含在输出中。

### 3.9.3 在数据框中变（计算）新变量

`mutate()` 命令提供了与我们在 Excel 中经常的操作非常的功能：我们有一个包含数据的 Excel 表格，并根据一或多列添加一个额外的列。

**基于数据框，`mutate()` 根据现有的变量（列）计算出一个新的变量（列）。** 如果使用 *calculate*（计算）而不是 *mutate* 可能会更清楚地显示该命令的作用，但它的名称是 —— *mutate()*。

这是一个例子：Titanic 数据集中的 `FareInPounds` 反映了1912 年的价格。这些价格转换为2023 年的美元是多少？我们需要将1912 年的英镑价格乘以108.5。

以下是详细步骤：

- 我们需要基于 `TitanicNarrow` 创建一个新的数据框 `DataTitanicFare`，其中包含变量 `Fare2023Dollars`。
- 新变量 `Fare2023Dollars` 定义为：108.5 * FareInPounds。
- 之后删除 `FareInPounds` 列也是不错的，因为它不再有用。
- 我们可以通过 `mutate()` 命令完成这一切：
- `mutate()` 命令的第一个参数再次是操作的数据（TitanicNarrow）。
- 随后的参数决定了如何计算新变量并更新现有变量。
- 后续定义用逗号分隔。

相关的 R 代码和输出：

1912 年的汇率约为 108.5。

```R
DataTitanicFare=mutate(TitanicNarrow, Fare2023Dollars=108.5*FareInPounds, FareInPounds=NULL)
head(DataTitanicFare)
```

### 3.9.4 使用管道链接命令

管道（Piping）是一种链接一个或多个命令的过程。管道操作符将一个命令的输出作为下一个命令的输入。我们将通过一个示例来演示管道的工作原理：假设在数据框上，我们想要创建一个 `DataFinalResult` 的数据框，包含：

- 变量 `Survived`、`Sex`、`Age` 和 `FareInPounds`
- 仅女性乘客
- 票价应以2023美元表示

正如你所学的，对于第一个条件，使用 `select()` 命令选择所需的变量；为了确保结果仅包含女性乘客，使用 `filter()` 过滤观测值；最后，为了确保票价以2023美元表示，我们将使用 `mutate()`。

正如第3.8节所介绍的，大多数 R 命令具有以下结构，第一个参数是：数据：

```
Data More Arguments
command(Arg1, Arg2, Arg3, ..., ArgN)
命令参数用逗号分隔
```

