
我们使用 `str_split_1()` 函数。然后我们再次确认返回的结果确实是一个向量，并打印结果。

```r
sample_str_words <- str_split_1(sample_str, " ")
class(sample_str_words)
#> [1] "character"

sample_str_words
#> [1] "A"             "systematic"    "search"
#> [4] "will"          "be"            "performed"
#> [7] "in"            "PubMed,"       "Embase,"
#> [10] "and"           "the"           "Cochrane"
#> [13] "Library,"      "using"         "the"
#> [16] "following"     "search"        "query:"
#> [19] "('out-of-hospital" "cardiac"      "arrest'"
#> [22] "OR"            "'OHCA')"       "AND"
#> [25] "('MIRACLE"     "2'"            "OR"
#> [28] "OHCA"          "OR"            "CHAP"
#> [31] "IC-GRAPH"      "OR"
#> [34] "SOFA"          "OR"            "APACHE"
#> [37] "OR"            "SAPS"          "OR"
#> [40] "SWAP"          "OR"            "TTM')."
```

现在我们希望识别这个向量中带有起始和/或结束括号的单词。函数 `grepl()` 接收一个字符向量 `x` 和一个要搜索的模式。它返回一个逻辑向量，指示 `x` 的每个元素是否与该模式匹配。

```r
grepl(sample_str_words, ")")
#> Warning in grepl(sample_str_words, ")"): argument 'pattern' has
#>   length
#> 1 and only the first element will be used
#> [1] FALSE
```

这并不符合我们的预期。我们期望输出多个 TRUE/FALSE 值，每个单词对应一个。让我们再读一下文档。

## 21.3 解读错误消息和警告

前面的警告消息为我们提供了很好的线索，说明哪里出了问题。它说输入的 pattern 长度大于 1。然而，我们给出的 pattern 却并非如此。这些注释是为了帮助解释步骤，但你可能还想打印输出来弄清楚它在做什么。

```r
sample_strA <- " A systematic search will be performed in PubMed,
Embase, and the Cochrane Library, using the following search query:
('out-of-hospital cardiac arrest' OR 'OHCA') AND ('MIRACLE 2' OR
'OHCA' OR 'CAHP' OR 'C-GRAPH' OR 'SOFA' OR 'APACHE' OR 'SAPS' OR
'SWAP' OR 'TTM')."

sample_strB <- "Searches will be conducted in MEDLINE via PubMed, Web
of Science, Scopus and Embase. The following search strategy will be
used:(child OR infant OR preschool child OR preschool children OR
preschooler OR pre-school child OR pre-school children OR pre school
child OR pre school children OR pre-schooler OR pre schooler OR pre
scholar OR pre scholars OR children OR adolescents OR adolescent OR
children)AND(attention deficit disorder with hyperactivity OR ADHD OR
attention deficit disorder OR ADD OR hyperkinetic disorder OR minimal
brain disorder) Submitted "
```

```r
sample_str <- sample_strB

# 分离括号，去除多余空白，并拆分为单词
sample_str <- str_replace(sample_str, "\\)", "")
sample_str <- str_replace(sample_str, "\\(", "")
sample_str <- str_squish(sample_str)
sample_str_words <- str_split_1(sample_str, " ")

# 查找带括号的索引
end_ps <- grepl(x = sample_str_words, pattern = "\\)")
start_ps <- grepl(x = sample_str_words, pattern = "\\(")

# 查找第一个和最后一个括号之间的单词
search_query <- sample_str_words[which(end_ps)[1]:which(start_ps)[1]]
search_query <- paste(search_query, collapse=" ")
search_query
#> [1] ") adolescents OR adolescent OR children OR schooler pre OR pre-schooler OR children school pre OR child school pre OR children pre-school OR child pre-school OR preschooler OR children preschool OR child preschool OR infant OR child ("

# 查找检索词
search_terms <- str_replace_all(search_query, "\\)", "")
search_terms <- str_replace_all(search_query, "\\(", "")
sample_terms <- str_squish(search_query)
```

```r
search_terms <- str_split_1(search_terms, " AND | OR ")
search_terms
#> [1] ")" adolescents" "adolescent" "children"
#> [4] "schooler pre" "pre-schooler" "children school pre"
#> [7] "child school pre" "children pre-school" "child pre-school"
#> [10] "preschooler" "children preschool" "child preschool"
#> [13] "infant" "child "
```

## 21.4 通用编程技巧

当你编写更复杂的代码和函数时，我们希望注重实践良好的编程原则。这有助于你在需要共享或更新代码时，或者在你不可避免地遇到错误或意外行为时。以下是一些通用编程技巧，以及它们与沟通和调试的关系。

- 1. 命名一致。为你的对象和函数使用一致且信息丰富的名称。例如，你可以看到在本文中，我们只在名称中使用了小写字母、下划线（_）和偶尔的数字。这些名称还应该具有信息性且唯一。这使得在调试时更容易检查拼写错误或重复名称。调试时，检查你是否对不同的对象使用了相同的名称，或对同一个对象使用了不同的名称。你可以使用 `ls()` 函数查找所有当前对象，或者检查你的环境窗格来完成此操作。

```r
# 推荐
ages <- c(65, 33, 27, 88)
age_mean <- mean(ages)

# 不推荐
x <- c(65, 33, 27, 88)
x1 <- mean(ages)
```

```r
#' 查找向量的唯一元素
#'
#' @param x 向量
#' @return 移除重复项后的新向量
own_unique <- function(x){
  # 检查空向量
  if (length(x) == 0){
    return(NULL)
  }

  # 否则 y 将是唯一值
  y <- c()

  for(i in 1:length(x)){
    # 如果 x 中的值不在 y 中，则添加它
    if(!(x[i] %in% y)){
      y <- c(y, x[i])
    }
  }

  return(y)
}
```

- 3. 不要重复自己。重复代码会增加出错的可能性。此外，它会使我们以后难以更新代码。当我们发现自己重复代码时，应该使用函数。如果你发现自己重复常量，应该将这些值定义为一个对象。后续代码使用一行代码将分类变量转换为因子，并存储哪些列是分类变量的向量。

```r
dry_df <- data.frame(age = ages,
                     tb = c(1, 0, 0, 0),
                     heart_rate = c(60, 82, 76, 72),
                     gender = c("Female", "Male", "Nonbinary",
                                "Female"))

# 转换因子变量
cat_vars <- c("tb", "gender")
dry_df[cat_vars] <- lapply(dry_df[cat_vars], factor)
```

- 4. 练习阅读文档。每当你使用一个新函数时，你应该先阅读文档。调试时，你应该检查函数的输入参数是否符合预期，并查看示例。阅读这些示例也有助于你编写自己的文档，以便更好地理解如何与受众沟通。

- 5. 从简单开始，逐步构建。如果我们一次性编写大量代码，然后它无法运行，就很难理解哪里出了问题。相反，我们应该以小步骤构建代码或函数，并在每一步之后进行检查。在测试代码时，一个好的口号是尽早测试，经常测试。因此，尽量避免在运行并检查结果是否符合预期之前编写太多代码。如果你最终写了一大批代码，你可以通过检查不同位置的对象值来定位错误。

- 6. 学会寻求帮助。在软件工程中，有一个众所周知的技巧：在办公桌上放一只橡皮鸭（或其他可爱的物品），用来对着它讲解你的代码。必须口头表达和解释你的方法对调试非常有帮助。R 的错误消息有时可以提示错误可能源于何处，但它们并不总是直接的。搜索你不理解的错误消息可能会让你更好地理解问题。

## 21.5 练习

这些练习侧重于阅读函数文档和调试。

- 1. 假设我们想将以下字符串中的单词“Thank you”替换为“Thanks”。为什么以下代码会失败？我们如何纠正它？

```r
string <- "Congratulations on finishing the book!
Thank you for reading it."
str_sub(string, c(35, 42)) <- "Thanks"
string
#> [1] "Congratulations on finishing the bThanks"
#> [2] "Congratulations on finishing the book! \nTThanks"
```

- 2. 后续代码使用了 HDSin-

