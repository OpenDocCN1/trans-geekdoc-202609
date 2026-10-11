
## 初始数据概览

| country_population | country_gdp | continent | region |
| :--- | :--- | :--- | :--- |
| 185 | 2972 | 0 | 0 |

初始阶段涉及识别数据集中每列缺失值的数量或比例。这有助于理解缺失值在各列中的模式和范围。首先，让我们编写一个函数来创建 DataFrame，以显示 Gapminder 数据集的缺失值摘要。

### 显示缺失值摘要的函数

```r
# function to display the missing values summary
missing_values_df <- function(df) {

  # column wise missing values
  missing_values <- colSums(is.na(df))

  # percentage of missing values
  missing_values_percent <- 100 * colSums(is.na(df)) / nrow(df)

  # create a dataframe with the results
  missing_values_table <- cbind(missing_values, missing_values_percent)

  # rename the columns
  colnames(missing_values_table) <- c("Missing Values", "% of Total Values")

  # sort the table by percentage of missing descending
  missing_values_table <- missing_values_table[missing_values_table[, 2] != 0, ]
  missing_values_table <- missing_values_table[order(-missing_values_table[, 2]), ]
  missing_values_table <- round(missing_values_table, 1)

  # return the dataframe with missing values details
  return(missing_values_table)
}

gapminder_NA_summ <- missing_values_df(gapminder)

# print the result of gapminder_NA_summ
gapminder_NA_summ
```

### 缺失值统计结果

| | Missing Values | % of Total Values |
| :--- | :--- | :--- |
| country_gdp | 2972 | 28.2 |
| infant_mortality | 1453 | 13.8 |
| fertility | 187 | 1.8 |
| country_population | 185 | 1.8 |

## 使用 naniar 库可视化检测缺失数据

缺失值是数据分析中常见的现象，可能由多种原因引起，例如数据录入错误、设备故障或无响应。缺失值非常普遍，以至于很难找到一个没有缺失值的数据集。忽略或不当处理缺失值可能导致有偏或不准确的结果，后果可能很严重。幸运的是，有许多方法和技术可帮助您管理数据中的缺失值。这样，即使使用不完整的数据，也能确保分析可靠且有效。

您可以求助于 Nicholas Tierney 开发的 `naniar` 包来管理缺失值并深入了解数据。使用 `naniar`，您可以探索缺失值的模式，并可视化缺失数据对分析的影响。这些工具可以帮助您确保结果的可靠性，即使存在缺失数据。

```r
# load the naniar package
library(naniar)
```

为了深入了解缺失数据是否随机发生，您可以创建一个可视化图表，显示数据集中所有变量缺失值的位置。

您可以首先使用 `vis_miss()` 图开始探索缺失值。图 3.2 通过用黑色标示缺失值的位置，直观地展示了缺失数据的数量。此外，该图还包含数据集总体缺失值百分比（图例中显示）和每个变量缺失值百分比的详细信息。这种方法可以帮助您了解缺失值的模式，并确定其是随机发生的，还是背后存在系统性原因。

```r
# locations of missing values of each variable
vis_miss(gapminder)
```

![](images/Figure3.4.png)

**图 3.2：每列缺失值数量及总体缺失值百分比**

图 3.3 展示了 Gapminder 数据集中每个变量的缺失值数量：

```r
# number of missing values in each variable
gg_miss_var(gapminder)
```

![](images/Figure3.5.png)

**图 3.3：可视化每个变量的缺失值数量**

### 缺失值的原因

在处理缺失数据时，首先必须了解数据缺失的原因。不同类型的缺失数据会以不同方式影响您的结果。让我们将其分为三类：

*   **完全随机缺失**：当某变量中的缺失值与数据集中的任何其他变量或该变量本身完全无关时发生。换句话说，缺失性没有可辨别的模式，只是随机发生。
*   **随机缺失**：对于 MAR，缺失性并非随机，但可以通过数据集中具有完整信息的其他变量来预测，这意味着缺失性取决于数据集中的其他因素，但这些因素是已知的且可被考虑在内。
*   **非随机缺失**：当缺失性取决于未观测到的数据或缺失数据的实际值时发生。这比较棘手，因为缺失值可能与数据集中未包含的关键变量相关，从而导致有偏或不准确的结果。

通过了解不同类型的缺失数据，您可以就是如何处理它们以及它们如何影响分析做出明智的决定。

接下来，要可视化缺失模式或变量间缺失的组合，可以使用 `gg_miss_upset` 函数：

```r
# explore combinations of missingness among variables
gg_miss_upset(gapminder)
```

![](images/Figure3.6.png)

**图 3.4：可视化变量间的缺失模式**

上图 3.4 显示有 185 个案例中，所有四个变量（`country_gdp`、`infant_mortality`、`fertility`、`country_population`）同时存在缺失值。变量 `country_gdp` 和 `infant_mortality` 有 832 个案例同时缺失。

评估数据集中缺失数据量的一种方法是在检查分类变量时使用 `gg_miss_fct()` 函数。该函数显示数据集中按分类变量分组的每列缺失值百分比。

```r
# check heatmap of missingness of variables along the years
gg_miss_fct(x = gapminder, fct = year)
```

图 3.5 探索了 Gapminder 变量随年份的缺失情况：

![](images/Figure3.7.png)

**图 3.5：各列随年份的缺失值数量**

上述热力图显示，`infant_mortality` 和 `country_gdp` 的缺失值分布在所有年份中，但 2016 年 `country_gdp`、`country_population`、`fertility` 和 `infant_mortality` 均无数据可用。

图 3.4 提供了关于四个变量中 185 个缺失值的洞察。进一步检查数据，图 3.5 证实这些案例对应 2016 年。这一额外验证加深了我们对数据集中缺失值的理解，并为未来的分析提供了有用信息。

## 处理缺失值

在处理真实世界的数据集时，缺失数据是一个常见问题，根据问题的性质和程度，有不同的策略来处理缺失值。一些流行的方法包括删除法（移除不完整的观测值或整个变量）和插补法（用从可用信息得出的估计值替换缺失值）。这两种方法都有优缺点，选择正确的策略取决于缺失量和模式以及分析目标等因素。

### 删除法
