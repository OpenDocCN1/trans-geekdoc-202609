
在第二次分析中，我们可能感兴趣的是判断加拿大劳动力是否存在季节性变化：

```
lfs_canada_employment |>
  group_by(month(REF_DATE)) |>
  summarize(mean(VALUE))
```

```
## # A tibble: 12 x 2
##  `month(REF_DATE)` `mean(VALUE)`
##                 <dbl>         <dbl>
## 1                1        17841.
## 2                2        17960.
## 3                3        17907.
## 4                4        17848.
## 5                5        18255.
## 6                6        18539.
## 7                7        18514.
## 8                8        18514.
## 9                9        18423.
## 10              10        18458.
## 11              11        18421.
## 12              12        18369.
```

## 12.3 清理字符串

> “字符串不是 R 中光彩夺目、高调的组成部分，但它们在许多数据清理和准备任务中确实发挥着重要作用。” ——{stringr} 参考页

R 提供了一些处理字符串的强大工具。尤其是 {stringr}（Wickham, 2019b）包非常灵活。但在那之前，我们需要先了解一下正则表达式。

### 12.3.1 正则表达式

> “有些人在遇到问题时想：‘我知道了，我会用正则表达式。’现在他们有了两个问题。” —— 杰米·扎温斯基

正则表达式是一种指定字符模式的方式。这种模式可以是特定的字母或数字（“abc”或“123”），也可以是字符类型（字母、数字、空白等），或者是两者的组合。

学习基础知识的一个绝佳资源是 {stringr} 包网站上名为“正则表达式”的指南，网址为 stringr.tidyverse.org¹。

下面是一些有用的正则表达式匹配函数。请注意，方括号括起正则表达式以标识单个字符。在下面的示例中，三组方括号“[a][b][c]”包含三个独立的字符位置，而“[abc]”则标识一个单个字符。

| 字符 | 作用 |
|---|---|
| “abc” | 匹配“abc” |
| “[a][b][c]” | 匹配“abc” |
| “[abc]” | 匹配“a”、“b”或“c” |
| “[a-c]” | 匹配“a”到“c”中的任意一个（即匹配“a”、“b”或“c”） |
| “[ ^abc]” | 匹配除“a”、“b”、“c”以外的任意内容 |
| “^” | 匹配字符串开头 |
| “$” | 匹配字符串结尾 |
| “.” | 匹配任意字符串 |

| 字符 | 匹配频率 |
|---|---|
| “?” | 0 或 1 次 |
| “+” | 1 次或多次 |
| “*” | 0 次或多次 |
| “{n}” | 恰好 n 次 |
| “{n,}” | n 次或更多次 |
| “{n,m}” | n 次到 m 次之间 |

这些也需要转义：

| 字符 | 含义 |
|---|---|
| “”” | 双引号 |
| “‘” | 单引号 |
| “\” | 反斜杠 |
| “\d” | 任意数字 |
| “\n” | 换行符（换行） |
| “\s” | 任意空白字符（空格、制表符、换行） |
| “\t” | 制表符 |
| “\u…” | Unicode 字符* |

¹ https://stringr.tidyverse.org/articles/regular-expressions.html

Unicode 字符²的一个例子是“interrobang（问叹号）”，它是问号和感叹号的组合。

```
interrobang <- "\u2048"
interrobang
```

## [1] "?!"

加拿大邮政编码遵循一致的格式：

- 字母-数字-字母，后跟一个空格或连字符，然后是数字-字母-数字

与之对应的正则表达式如下所示，其组成部分如下：

- ^ : 字符串开头
- [A-Za-z] : 所有字母，包括大写和小写
- \d : 任意数字
- [ -]? : 空格或连字符；使用“?”可让这两者之一成为可选项（即可能存在，也可能不存在）
- $ : 字符串结尾

```
# regex for Canadian postal codes
# ^ : start of string
# [A-Za-z] : all the letters upper and lower case
# \d : any numerical digit
# [ -]? : space or hyphen,
#         ? to make either optional (i.e. it may be there or not)
# $ : end of string

postalcode <- "^[A-Za-z]\\d[A-Za-z][ -]?\\d[A-Za-z]\\d$"
```

> “如果你的正则表达式变得过于复杂，试着把它拆分成更小的部分，给每个部分命名，然后用逻辑运算将这些部分组合起来。” ——Wickham

²完整的 Unicode 字符列表可以在维基百科网页上找到（Wikipedia contributors, 2022a）。

以及 Grolemund 所著的《R for Data Science》（Wickham and Grolemund, 2016, p.209）

加拿大邮政编码的正则表达式可以使用大小写敏感运算符“(?i)”来缩短。将它放在表达式开头，会应用于正则表达式中的所有字母标识符；可以通过“(?-i)”将其关闭。

```
# option: (?i) : make it case insensitive
#       (?-i) : turn off insensitivity
postalcode <- "(?i)^[A-Z]\\d[A-Z][ -]?\\d[A-Z]\\d$(?-i)"
```

不列颠哥伦比亚省金伯利镇的邮政编码是“V1A 2B3”。下面是一个包含该编码的一些变体的列表，我们将用其测试我们的正则表达式。

```
# list of postal codes
pc_kimberley <- c("V1A2B3", "V1A 2B3", "v1a 2B3xyz", "v1a-2b3")
```

### 12.3.2 使用 {stringr} 进行数据清理

借助正则表达式的强大功能，我们可以使用 {stringr} 包中的函数来筛选、选择并清理数据。

```
library(stringr)
```

与许多 R 包一样，参考页对包中的函数提供了很好的解释，并提供了展示这些函数实际示例的指南。{stringr} 的参考页是 stringr.tidyverse.org³。

让我们看看 {stringr} 中特别适合清理任务的一些函数。

³https://stringr.tidyverse.org/

### 12.3.2.1 字符串特征

| 函数 | 用途 |
|---|---|
| str_subset() | 字符型；返回包含匹配项的所有字符串 |
| str_which() | 数值型；返回匹配项在向量中的位置 |
| str_detect() | 逻辑型；若找到模式则返回 TRUE |

{stringr} 函数 str_subset() 和 str_which() 返回具有该模式的字符串，要么返回整个字符串，要么返回其位置。

```
# which strings have the postal code pattern?
str_subset(pc_kimberley, postalcode)
```

## [1] "V1A2B3"  "V1A 2B3" "v1a-2b3"

```
# which strings have the postal code pattern, by location?
str_which(pc_kimberley, postalcode)
```

## [1] 1 2 4

{stringr} 中的另一个函数 str_detect() 检测模式是否存在，并返回逻辑值（真或假）。在这里，我们使用包含加拿大邮政编码正则表达式的 postalcode 对象来测试这四个邮政编码的列表。

```
str_detect(string = pc_kimberley, pattern = postalcode)
```

## [1] TRUE TRUE FALSE TRUE

正如我们所见，第三个示例邮政编码——末尾包含一个额外数字——返回“FALSE”值。它可能在前 7 个字符中包含看起来像邮政编码的内容，但由于末尾有额外字母，它不是邮政编码。要查找在字符串任意位置匹配邮政编码的字符串，我们必须修改正则表达式，去掉开头的“^”和结尾的“$”指定：

```
# remove start and end specifications
postalcode <- "(?i)[A-Z]\\d[A-Z][ -]?\\d[A-Z]\\d(?-i)"
```

```
str_detect(string = pc_kimberley, pattern = postalcode)
```

## [1] TRUE TRUE TRUE TRUE

所有字符串中都有匹配加拿大邮政编码结构的部分。我们怎样才能提取匹配的部分呢？

如果我们重新运行 str_subset() 和 str_which() 函数，会看到现在四个字符串都被返回了。

```
# which strings have the pattern?
str_subset(pc_kimberley, postalcode)
```

## [1] "V1A2B3"  "V1A 2B3"  "v1a 2B3xyz" "v1a-2b3"

```
# which strings have the pattern ("e"), by location?
str_which(pc_kimberley, postalcode)
```

## [1] 1 2 3 4

借助这两个函数，我们可以识别哪些字符串包含我们要查找的字符。要获取特定的字符串，我们可以使用 str_extract()：

```
pc_kimberley_all <- str_extract(pc_kimberley, postalcode)
pc_kimberley_all
```

## [1] "V1A2B3"  "V1A 2B3" "v1a 2B3"  "v1a-2b3"

### 12.3.2.2 替换与拆分函数

我们怎样才能清理这个列表，使我们的邮政编码格式一致？

我们的目标是得到一个六字符字符串，包含大写字母，且既没有空格也没有连字符。

下表展示了我们将使用的函数。

