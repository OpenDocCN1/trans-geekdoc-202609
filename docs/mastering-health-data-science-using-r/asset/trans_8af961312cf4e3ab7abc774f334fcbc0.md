

```r
rw2 <- function(n){
  v <- rep(0, n)
  for (i in 2:n){
    v[i] <- v[i-1] + rbinom(1, 1, 0.5)
  }
}

microbenchmark(rw1(10000), rw2(10000), unit="ms")
#> Unit: milliseconds
#>       expr  min  lq mean median   uq   max neval
#> rw1(10000) 5.10 5.25 5.84   5.36 5.92 10.64   100
#> rw2(10000) 4.27 4.35 4.68   4.39 4.58  9.32   100
```

这也适用于数据框或矩阵。在以下代码块中，我们以三种方式生成随机矩阵。第一种用一行代码创建矩阵，第二种初始化一个空矩阵然后逐行填充，最后一种在每次迭代时动态更新矩阵大小。

```r
random_mat1 <- function(n){
  m <- matrix(sample(1:3, n^2, replace = TRUE), nrow = n)
  return(m)
}

random_mat2 <- function(n){
  m <- matrix(nrow = n, ncol = n)
  for (i in 1:n){
    m[i,] <- sample(1:3, n, replace = TRUE)
  }
}

random_mat3 <- function(n){
  m <- NULL
  for (i in 1:n){
    m <- rbind(m, sample(1:3, n, replace = TRUE))
  }
  return(m)
}

microbenchmark(random_mat1(100),
               random_mat2(100),
               random_mat3(100),
               unit = "ms")
#> Unit: milliseconds
#>   expr      min       lq     mean   median       uq      max neval
#>  random_mat1(100) 0.226 0.244 0.265 0.249 0.256 1.59   100
#>  random_mat2(100) 0.494 0.508 0.544 0.521 0.536 2.52   100
#>  random_mat3(100) 1.075 1.163 1.384 1.189 1.233 5.01   100
```

这表明，如果需要更新向量、矩阵或数据框的值，应尽量一次性完成尽可能多的重新赋值。例如，一次性更改整列比逐个更改单个值更好。这可以避免额外的副本。

### 20.2.1 练习题

以下代码为每个种族群体拟合线性模型并记录系数。请重写此代码，以预分配结果向量，并使用 **microbenchmark** 包比较两种方法的效率。

```r
coefs <- c()
pat_races <- unique(pain$PAT_RACE)
for (r in pat_races){
  df <- pain[pain$PAT_RACE == r, ]
  if (nrow(df) > 3){
    new_coef <- lm(PROMIS_DEPRESSION ~ PROMIS_ANXIETY,
                   data = df)$coefficients[2]
    coefs <- c(coefs, new_coef)
  }
}
```

## 20.3 并行编程

使代码更高效的另一种方法是使用并行处理。在 R 中运行循环时，每次只能运行一次迭代。例如，以下代码串行运行 100 次随机游走。并行处理允许我们同时执行多次对该函数的调用。这是通过在机器上的独立核心（或处理器）上运行这些进程来实现的。例如，如果有六个核心可用，我们可以在每个处理器上运行 1/6 的复制次数，从而减少总体计算时间。**parallel** 包（R Core Team 2024）包含用于在不同操作系统上实现并行处理的函数。不幸的是，此功能通常在 RStudio 中不受支持，且本书未涉及。我们建议使用 **parallel** 包中的 `mclapply()` 函数通过分叉实现并行处理。这在 Windows 上不适用，但实现起来简单得多。对于 Windows 上的并行处理，我们建议使用 **parallel** 包中的 `parLapply()` 函数查看套接字方法。

```r
replicate(100, rw1(1000))
```

## 20.4 练习

- 1. 以下代码块包含四次尝试，向 pain 数据添加新列 LOWER_BACK。请注意，第二次和第三次尝试是向量化的，而第一次和第四次不是。对每种方法计时，并按从快到慢的顺序排列这些方法。

  ```r
  # Attempt 1: loop
  pain$LOWER_BACK <- vector(mode="logical", length=nrow(pain))
  for (i in 1:nrow(pain)) { # for every row
    if ((pain$X218[i] == 1) | (pain$X219[i] == 1)) {
      pain$LOWER_BACK[i] <- TRUE
    } else {
      pain$LOWER_BACK[i] <- FALSE
    }
  }

  # Attempt 2: logic
  pain$LOWER_BACK <- ((pain$X218 == 1) |
                      (pain$X219 == 1))

  # Attempt 3: which
  pain$LOWER_BACK <- FALSE
  true_ind <- which((pain$X218 == 1) | (pain$X219 == 1))
  pain$LOWER_BACK[true_ind] <- TRUE

  # Attempt 4: apply
  back_pain <- function(x){
    if((x['X218'] == 1) | (x['X219'] == 1)){
      return(TRUE)
    }
    return(FALSE)
  }
  pain$BACK_PAIN <- apply(pain, 1, back_pain)
  ```

- 2. 检查以下代码并确定正在计算什么。然后，重写代码以使其更高效。使用 **microbenchmark** 包比较执行时间，并解释为什么你的方法更高效。

  ```r
  n <- 100000
  x1 <- rnorm(n, 10, 1)
  x2 <- rbinom(n, 1, 0.2)
  y <- numeric(0)

  for (i in 1:n){
    if (x2[i] == 1){
      y[i] <- rnorm(1, 2 * x1[i], 0.7)
    } else{
      y[i] <- rnorm(1, 1 + 3 * x1[i], 0.2)
    }
  }
  df <- data.frame(x1 = x1, x2 = x2, y = y)
  ```

- 3. 假设我们想要按种族群体找出报告频率最高的五个疼痛区域。请编写你的解决方案：(a) 使用至少一个循环；(b) 对身体区域列进行数据透视，然后使用 **dplyr** 函数进行汇总。比较两种方法的效率。

## 第 VI 部分

### 额外主题

![](img/58a554e865d49ca347d9a3f76f8f0812_338_0.png)

泰勒与弗朗西斯

泰勒与弗朗西斯集团

http://taylorandfrancis.com

## 21 提升你的 R 技能

在本书中，我们介绍了一些流行的包以及这些包中的许多特定函数。然而，不可能涵盖 R 中可用的所有包、函数和选项。在本章中，我们将讨论如何使用新包、解释错误消息、调试以及整体良好的编程实践，以帮助你将 R 编程提升到新水平。

### 21.1 阅读新包的文档

当你开始将本书中的工具应用到自己的工作或新环境中时，可能需要安装和使用新包，或遇到一些意外错误。练习阅读包文档并响应错误消息，有助于你超越本书涵盖的主题来扩展 R 技能。我们使用 **stringr** 包（Wickham 2022）来演示这些技能，该包是 **tidyverse** 的一部分，并拥有多个用于处理文本数据的函数。

```r
library(tidyverse)
library(HDSinRdata)
```

每个已发布的包都有一个 CRAN 网站。该网站包含参考手册，其中包含包中可用函数和数据的文档。通常，该网站还包括有用的 vignette，提供如何使用包中函数的示例。该网站还会告诉你使用包的要求、包的作者是谁，以及包上次更新的时间。例如，请查看 **stringr**¹ 的 CRAN 网站并阅读 vignette “stringr 简介”²。

我们使用 **stringr** 包来演示清理与系统综述 PubMed 搜索查询相关的文本。以下代码块中给出了一个示例搜索查询，摘自 Gue et al. (2021)。我们的第一个目标是从文本中提取实际搜索查询以及查询中使用的所有术语。我们可以假设，搜索查询要么完全包含在括号中，要么是由 AND 或 OR 连接的一系列括号短语。我们的目标是提取搜索查询以及查询中使用的所有单独搜索词，但我们需要分步完成。

```r
sample_str <- " A systematic search will be performed in PubMed,
Embase, and the Cochrane Library, using the following search query:
('out-of-hospital cardiac arrest' OR 'OHCA') AND ('MIRACLE 2' OR
'OHCA' OR 'CAHP' OR 'C-GRAPH' OR 'SOFA' OR 'APACHE' OR 'SAPS' OR
'SWAP' OR 'TTM')."
```

我们想对文本做的第一件事是清理空白，删除任何尾随、前导或重复的空格。在我们的示例中，字符串以尾随空格开头，搜索查询前也有多个空格。在 stringr 参考手册中搜索“空白”，我们找到了 str_trim() 和 str_squish() 函数。阅读这两个函数的文档。你会发现 str_squish() 是我们要找的函数，并且它接受一个参数。

```r
sample_str <- str_squish(sample_str)
sample_str
#> [1] "A systematic search will be performed in PubMed, Embase, and
↵ the Cochrane Library, using the following search query:
↵ ('out-of-hospital cardiac arrest' OR 'OHCA') AND ('MIRACLE 2' OR
↵ 'OHCA' OR 'CAHP' OR 'C-GRAPH' OR 'SOFA' OR 'APACHE' OR 'SAPS' OR
↵ 'SWAP' OR 'TTM')."
```

### 21.2 尝试简单示例

在单个字符串上测试函数的前提是从简单示例开始的一个好例子。与其立即将函数应用到完整数据集上，不如先确保你理解它在简单示例中的工作原理，并能预期结果应该是什么样子。我们的下一个任务是将文本拆分为单词，并将其存储为字符向量。阅读文档以确定为什么

