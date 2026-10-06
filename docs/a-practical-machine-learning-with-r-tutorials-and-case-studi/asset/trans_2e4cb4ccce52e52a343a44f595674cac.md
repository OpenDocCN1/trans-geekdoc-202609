

# 30 R 和 RStudio 简介

它并不适用于计算。然而，如果我们认为将小数点向右移动等同于乘以 10，移动两位等同于乘以 100，移动三位等同于乘以 1000，以此类推。那么我们可以将 GDP 写为：

```
GDP = 2.55 \cdot 10^{000,000,000,000}
GDP = 2.55 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10
GDP = 2.55 \cdot 10^{13}
```

最后一个方程使用科学计数法写出了巨大的 GDP 数字。
我们对非常小的数字也可以同样的操作。例如，被雷击中的概率。在这种情况下，由于我们处理的是非常小的数字，我们将小数点向左移动。这可以通过除以 10 移动一位、除以 100 移动两位以此类推来实现：

```
ProbLight = 3.65; 将小数点向左移动 9 位
ProbLight = 3.65 / 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10 \cdot 10
ProbLight = 3.65 / 10^9
ProbLight = 3.65 \cdot 10^{-9}
```

总之，我们可以像下面所示用科学计数法写出 GDP 和 ProbLight：

```
GDP = 2.15 \cdot 10^{13}
ProbLight = 3.422 \cdot 10^{-9}
```

当我们向 R 呈现这些非常大和非常小的数字时，它会做什么？

```
GDP=215000000000000
ProbLight=0.000000000365
cat("GDP", GDP)

## GDP: 2.15e+13
```

# 3.8 R 命令的结构

```r
cat("ProbLight", "ProbLight")
```

## ProbLight: 3.65e-09

R 几乎使用了科学计数法，只是用小写字母 e 替换了“10 的 ... 次方”。这种表示法并不美观，而且在数学上也是显然是不正确的，但几乎所有的统计程序都使用这种伪科学计数法.¹¹²

你学到了什么？当你看到 R 对非常大或非常小的数字的输出时，你现在知道如何解释字母 e 之后的数字了。这个数字告诉你要将小数点向右（当数字为正时）或向左（当数字为负时）移动多少位。

# 3.8 R 命令的结构

在处理 R 命令时，特别是当组合多个 R 命令时（管道；第 3.9.4 节），理解 R 的原理至关重要。

正如你已经看到的，在像 `mean()` 或 `sum()` 等命令中，一个 R 命令由名称后跟一对括号组成。在括号内部，用户可以为命令的一个或多个参数提供信息。

在下例示例中，我们再次从数据框 `Titanic` 中提取出泰坦尼克号乘客的年龄，并将其存储在 R 向量 `VecAge` 中（更多细节见第 3.5.2 节）。然后我们使用 `mean()` 和 `median()` 命令计算泰坦尼克号乘客的平均年龄和中位数：

```r
library(rio)
Titanic=import("https://ai.lang-analytics.com/data/Titanic.csv")
VecAge=Titanic$Age
cat("Mean:
```

## Mean: 29.47

## Median: 28

> ¹¹² 在数学上正确的情况下不写出“10 的 ... 次方”，源于电子计算器显示器只能显示非常简单符号的时代。

# 3 R 和 RStudio 简介

上面的两个示例已经揭示了关于 R 命令结构的一些重要属性：

- 命令中的每个参数都有一个名称。例如，在 `mean()` 和 `median()` 命令中，数据参数的名称是 `x`，就像许多其他命令一样。请注意，`x` 和 `data` 是 R 命令中数据参数的常用名称。`x<-VecAge` 将 R 向量 `VecAge` 中的数据分配给参数 `x`。
- R 不要求用户使用参数名称，只要按正确顺序提供参数值即可。例如，`x` 是 `mean()` 和 `median()` 命令的第一个参数。因此，`median(VecAge)`。
- 所有的 R 命令都有多个参数，每个参数都有唯一的名称。对于 `mean()` 和 `median()` 命令也是如此。然而，你可以看到在上面的两个示例中只提供了一个参数。这是因为如果用户没有为所有参数提供值，R 将使用默认值。

- 正如前面提到的，我们可以嵌套命令。在上面的示例中，你可以看到 `mean()` 和 `median()` 命令嵌套在 `cat()` 命令中。R 允许嵌套命令到任何深度。但嵌套命令可能会使代码非常难以阅读。

让我们详细查看 `median()` 命令。当我们在 RStudio 的控制台中输入 `? median()` 时，RStudio 的 Help（帮助）选项卡会显示一个帮助文件。除了其他帮助主题外，我们还获得了关于命令参数、顺序和默认值的信息：

```r
median(x, na.rm = FALSE)
```

在这种情况下，`median()` 命令有两个参数：第一个参数是 `x`，第二个参数是 `na.rm`。它决定是否自动删除缺失值。默认情况下 `na.rm=FALSE` 意味着不删除缺失值。然而，用户可以设置 `na.rm=TRUE`，例如：

```r
median(VecAge, na.rm = TRUE)
```

或者，用户可以省略参数名称，只要参数的顺序正确：

```r
median(VecAge, TRUE)
```

根据经验，在大多数 R 命令中，数据参数是第一个参数。这个经验有助于我们之后连接多个命令（第 3.9.4 节）。

# 3.9 使用 tidyverse 进行数据整理

# 3.9 使用 tidyverse 进行数据整理

正如数据框一样，它们是为了保持整齐（organized）而设计的。tidyverse 的目标是清理和整理数据。tidyverse 包是 R 中使用最频繁的包，包括 dplyr、ggplot2、tidyr 和 tibble。tidyverse 是一组为数据科学设计的包集合。tidyverse 中的所有包共享共同的设计理念和编程结构。

接下来的章节将介绍 tidyverse 的主要部分。

# 3.9.1 选择数据

通过 `select()` 命令，你可以从数据框中选择变量（列）。如果你不需要所有的变量，这非常有用。

`select()` 命令的第一个参数是你正在处理的数据框名称。其他参数（用逗号分隔）是你想要选择的变量。

在示例中，我们加载了 tidyverse 并导入了 Titanic 数据集，然后使用 `select()` 创建了一个名为 `TitanicNarrow` 的数据框。

```r
library(tidyverse)
library(rio)
Titanic=import("https://ai.lang-analytics.com/data/Titanic.csv")
TitanicNarrow=select(Titanic, Survived, ...)
```

正如你所看到的，我们成功了。`TitanicNarrow` 只包含所选的列。

我们还重命名变量。由于变量 `PClass` 不符合我们的命名标准，我们使用 `PasClass=PClass` 先选择 `PClass` 并将其重命名为 `PasClass`。

你可以使用 `select()` 命令覆盖现有的数据框，如下例：

```r
library(tidyverse)
library(rio)
Titanic=import("https://ai.lang-analytics.com/data/Titanic.csv")
Titanic=select(Titanic, Survived, PasClass=PClass, Sex, Age, FareInpounds)
```

在大多数情况下，覆盖数据框是不希望的。你可以看到这个问题：如果由于某种原因 `select()` 命令被执行了第二次，我们将收到错误消息，因为我们尝试选择并重命名 `PClass`，但 `PClass` 在 `Titanic` 中已经不存在了。它在我们第一次执行 `select()` 命令时就被重命名了。

# 3.9.2 过滤数据

当我们使用 `select()` 命令时，我们选择的是包含在数据框中的变量（列）。相比之下，`filter()` 命令用于过滤数据框中符合特定标准的观测值（行）。

与 `select()` 命令一样，`filter()` 命令的第一个参数是你处理的数据框名称。其他参数是决定保留哪些行的逻辑表达式。

