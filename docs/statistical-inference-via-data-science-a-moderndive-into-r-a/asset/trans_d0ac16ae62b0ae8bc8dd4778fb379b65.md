

## 4.4 数据导入与整洁数据

```r
library(ggplot2)
library(dplyr)
library(readr)
library(tidyr)
```

请记住，ggplot2 用于数据可视化，dplyr 用于数据清洗，readr 用于将电子表格数据导入 R，而 tidyr 用于将数据转换为“整洁”（tidy）格式。与其逐个安装和加载这些包，有一种更快的方法可以加载这些包，即安装并加载 tidyverse 包。tidyverse 包充当“伞型”包，安装/加载它会一次性为你安装/加载多个包。

在按照第 1.3 节所示安装普通包一样安装 tidyverse 包后，运行：

```r
library(tidyverse)
```

等同于运行：

```r
library(ggplot2)
library(dplyr)
library(readr)
library(tidyr)
library(purr)
library(tibble)
library(stringr)
library(forcats)
```

purrr、tibble、stringr 和 forcats 留给了更高级的书籍；请查阅 [R for Data Science12](https://r4ds.had.co.nz/) 来了解这些包。

在本书的剩余部分，我们每章开始时都会运行 `library(tidyverse)`，而不是逐个加载各种组件包。tidyverse“伞型”包的名称源于其所有包中的所有函数都被设计为具有共同输入和输出：“整洁”格式的数据框。这种输入输出数据框的标准化使得不同包之间不同函数之间的切换尽可能无缝。需更多信息，请查看该包的 [tidyverse.org13](https://www.tidyverse.org/) 网页。

12 http://r4ds.had.co.nz/ 
13 https://www.tidyverse.org/

## 4.5 结论

### 4.5.1 其他资源

所有学习检查（Learning checks）的解答可以在本书在线版的附录中找到。附录从 https://moderndrive.com/v2/appendixa 开始。

本章使用的所有 R 代码的 R 脚本文件可以在 https://www.modernrive.com/v2/scripts/04-tidy.R 获取。

如果你想学习更多关于 readr 和 tidyr 包的知识，我们建议你查阅 RStudio 的“数据导入备忘表”（Data Import Cheat Sheet）。在 2024 年版本的 RStudio 中，你可以通过 RStudio 菜单栏 -> Help -> Cheat Sheets... 进入此备忘表。向下滚动到“Data import with reader, readxl, and googlesheets4”获取有关使用 readr、readxl 和 googlesheets4 包导入数据的信息，以及“Data tidying with tidyr”获取有关使用 tidyr 包“整洁”数据的信息。

### 4.5.2 未来何方？

恭喜你！你已经完成了本书的“使用 tidyverse 进行数据科学”部分。现在我们将第 5 章和第 6 章进入本书的“使用 moderndrive 进行统计建模”部分，在那里，你将利用数据可视化和清洗技能来掌握数据框中不同变量之间的关系。

然而，我们将第 10 章的“回归推断”留到我们在第 7、8、9 章涵盖了统计推断之后再进行。如图 4.6 所示，让我们向着统计/数据建模迈进！

![](img/445742518041017e8f01f11b0c3190d9_145_0.png)

图 4.6：ModernDive 流程 —— 进入第二部分！

![](img/445742518041017e8f01f11b0c3190d9_146_0.png)

## 第二部分

## 使用 moderndive 进行统计建模

## 简单线性回归

我们在第 2 章介绍了数据可视化，在第 3 章介绍了数据清洗，在第 4 章介绍了数据导入和“整洁”数据。在本章中，我们将处理回归，这种方法可以帮助我们研究结果变量（或响应变量）与一个或多个解释变量（或回归变量）之间的关系。该方法首先提出一个统计模型。收集数据并用于估计系数，结果通常用于两个目的：

1. **为了解释（For explanation）**：当我们想要描述一个或多个回归变量的变化与响应的变化相关、量化这些变化、确定哪些回归变量确实与响应相关，或者确定描述响应与解释变量之间关系的模型是否合适时。
2. **为了预测（For prediction）**：当我们想要根据回归变量的观测值来确定响应的值将会是多少。我们并不关心所有回归变量之间以及它们与响应之间如何相互作用，我们只需要尽可能好的预测。

作为一个示例，假设我们想研究血压与潜在风险因素（如每日盐摄入量、年龄和活动水平）之间的关系。响应是血压，回归变量是风险因素。如果我们使用线性回归进行解释，我们想要确定减少盐分摄入对血压是否有真实影响，或者个人在减少盐分摄入时血压会下降多少。

最基本且最常用的回归类型是线性回归。线性回归涉及一个数值响应和一个或多个可以是数值或分类的回归变量。它被称为线性，是因为描述响应和回归变量的统计模型被假设是线性的。线性回归是几乎任何其他类型回归的基础。

