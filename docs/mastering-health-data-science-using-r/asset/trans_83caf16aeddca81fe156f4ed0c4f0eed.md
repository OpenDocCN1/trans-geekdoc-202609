

```r
add_x_seq <- function(x){
  # Adds x to 1:10 and returns
  add_x <- function(y){
    return(y + x)
  }

  return(add_x(1:10))
}

add_x_seq(3)
#>  [1]  4  5  6  7  8  9 10 11 12 13
#add_x(3) # would return an error
```

如果我们想使用创建的函数，可以将其返回。在更新后的示例中，我们返回一个匿名函数。这样做，我们为每个 x 值创建了一个唯一的函数。

```r
add_x <- function(x){
  # Returns a function to add x to any value
  return(function(y) y + x)
}

add2 <- add_x(2)
add2(1:10)
#>  [1]  3  4  5  6  7  8  9 10 11 12

add10 <- add_x(10)
add10(1:10)
#>  [1] 11 12 13 14 15 16 17 18 19 20
```

## 18.2 函数文档

我们编写的函数只有最少的注释或文档。在创建函数时，我们应该为它们编写文档，包括有关输入和输出格式的任何信息。我们通过在函数前添加以 '#' 开头的注释来实现这一点。这种函数文档风格称为 roxygen。下面的代码块展示了我们的欧氏距离函数的一个示例。您可以看到我们提供了关于两个参数和返回值的信息。roxygen 风格是已发布的 R 包所使用的风格。

```r
#' Euclidean distance
#'
#' @description Calculates the Euclidean distance between two points
#'
#' @param pt1 numeric vector
#' @param pt2 numeric vector
#' @return the Euclidean distance from pt1 to pt2
euclidean_dist <- function(pt1, pt2){
  return((sum((pt1 - pt2)^2))^0.5)
}
```

每条注释应以井号和撇号开头。第一组行是简介，注释块的第一行保留给标题。这是我们希望用户了解函数的第一条信息，并且应该是一行。对于除标题外的所有其他信息，我们使用某些标签。

- `@description` 此标签应放在首位，是您可以在标题之外简要放置有关函数的更多信息的地方。您还可以使用 `@details` 标签添加更多细节。
- `@param` 此标签位于每个输入参数描述之前。对于每个参数，我们希望包含名称和类型，但也可能包含有关如何使用该参数的信息。
- `@return` 此标签记录返回的对象并指定类型。如果我们返回一个列表，那么我们可能会包含有关列表中每个对象的信息。

### 18.2.1 练习题

为以下抛硬币函数编写文档。

```r
#' Insert your solution here:
coin_flips <- function(prob, n = 10){
  results <- rbinom(n = n, size = 1, prob = prob)
  return(list(percent_heads = sum(results)/n, results = results))
}
```

## 18.3 调试与测试

当我们编写更复杂的代码和函数时，我们希望学习如何测试代码。在测试代码时，一个好的口头禅是“尽早测试，经常测试”。因此，避免在运行并检查结果是否符合预期之前编写太多代码。以下是一些适用于任何环境下调试的简单原则。

- 从简单开始，逐步构建。
- 通过检查所有圆括号 ()、方括号 [] 和花括号 {} 是否如您预期地匹配来检查语法。
- 检查对象名称是否正确，是否有意外的拼写错误，或者是否不小心对不同对象使用了相同的名称。
- 重启 R 会话并重新运行所有代码。
- 检查是否对不同对象使用了相同的对象名称。
- 通过在各阶段打印对象值或在 R 中使用断点来定位错误。
- 一次只修改一段代码，并重新检查所有测试值，以避免引入新错误。

例如，假设我们想编写一个函数，用于查找绝对 Pearson 相关系数高于某个阈值的数值列对。我们希望代码结构合理、灵活满足需求，并避免不必要的工作。要开始构建此函数，我们首先需要考虑我们想要的输入和输出。这称为_自顶向下方法_。在编写任何代码之前，大致勾勒出代码需要完成的整体步骤，有助于改进结构，避免重写大量代码。

在这种情况下，我们对此函数的输入是一个数据框，其中可能包含数值列和分类列的混合，以及一个默认值为 0.6 的阈值相关系数。我们想要返回一个包含列对及其相关系数的数据框。这为我们的文档提供了模板。

```r
#' Find pairs of columns with strong correlation
#'
#' @description Finds all pairs of numeric columns with strong Pearson
#' correlation and returns the pairs in a data frame
#'
#' @param df data frame
#' @param threshold positive numeric threshold value to define a
#' strong correlation as one with absolute value above the threshold
#' @return data frame with one row for each pair of columns
#' with high correlation containing the names of the columns
#' and the corresponding correlation
high_cor <- function(df, threshold = 0.6){
  return()
}
```

接下来，为了从简单开始，我们想创建一些人工数据来测试我们的函数。我们使用 **MASS** 包中的 `mvrnorm()` 函数（Venables 和 Ripley，2002）来控制列之间的相关性，并添加一个应被我们的函数忽略的分类列。

```r
set.seed(4)
cor_mat <- matrix(c(1, 0.9, 0.4, 0,
                    0.9, 1, 0.3, 0,
                    0.4, 0.3, 1, 0,
                    0, 0, 0, 1.0), nrow = 4)
m <- round(MASS::mvrnorm(100, c(0,0,0,0), Sigma = cor_mat), 3)
test_df <- as.data.frame(m)
test_df$V5 <- sample(c("A", "B", "C"), 100, replace = TRUE)
high_cor(test_df)
#> NULL
```

我们可以使用 `cor()` 函数来查找 Pearson 相关系数。

```r
cor(test_df[,-5])
#>         V1      V2      V3      V4
#> V1  1.0000  0.9006  0.324  -0.0797
#> V2  0.9006  1.0000  0.291  -0.0702
#> V3  0.3241  0.2912  1.000  -0.2306
#> V4 -0.0797 -0.0702 -0.231  1.0000
```

很好，现在让我们大致勾勒出需要完成的步骤。

- 1. 将数据子集化为仅包含数值列。
- 2. 找出所有列对的相关系数。
- 3. 检查一对列是否具有强相关性。
- 4. 如果是，则将其添加到我们的结果中。

让我们从第 1 步开始。在将代码放入函数之前，我们要在示例数据上测试我们的步骤。为此，我们使用 **dplyr** 包中的 `select_if()` 函数。

```r
df_numeric <- select_if(test_df, is.numeric)
head(df_numeric)
#>
#>   V1    V2    V3    V4
#> 1 -0.656 0.417 1.188 0.685
#> 2  0.117 -0.336 -1.611 -0.115
#> 3  1.229  0.617  0.241 -0.356
#> 4  0.478  0.121  1.176 -0.106
#> 5  1.546  1.914  0.366  0.045
#> 6  0.416  0.110  1.630 -1.726
```

这起作用了。接下来我们需要找出强相关性。现在，我们可以使用相关函数来查找相关系数。然后我们想遍历所有列对，检查相关系数的绝对值是否高于我们的阈值。我们为此使用循环。在第一次尝试中，我们创建了一个嵌套的 for 循环，其中 i 是列对中第一列的索引，j 是第二列的索引。我们可以看到一定是有些错误，因为我们得到了 i 和 j 相同的列对，而且我们还得到了零。注意我们如何使用 print 语句。这有助于我们识别需要为第一个 for 循环添加括号，并且需要将 j 更新为从 i+1 开始。

```r
cor_mat <- cor(df_numeric)
for (i in 1:nrow(cor_mat) - 1){
for (j in (i:nrow(cor_mat))){
print(paste(i, j)))
}
}
#> [1] "0 0"
#> [1] "0 1"
#> [1] "0 2"
#> [1] "0 3"
#> [1] "0 4"
#> [1] "1 1"
#> [1] "1 2"
#> [1] "1 3"
#> [1] "1 4"
#> [1] "2 2"
#> [1] "2 3"
#> [1] "2 4"
#> [1] "3 3"
#> [1] "3 4"
```

让我们再试一次。这次我们创建一个变量 n，代表列数。

