

5. 你也可以使用 renv 包管理器通过运行以下命令来安装 Bioconductor 软件包：

```
renv::install("bioc::<package name>")
```

6. 例如，要安装 Biobase 包，你需要运行此命令：

```
renv::install("bioc::Biobase")
```

7. 你可以使用 renv 从 GitHub 安装开发包，如下所示： 

```
renv::install("<user name>/<repo name>")
```

例如，要安装用户 danmaclean 的 rbioinfcookbook 包，你将运行以下命令：

```
renv::install("danmaclean/rbioinfcookbook")
```

这里是一些其他关于安装的提示：

- 你也可以通过逗号分隔多个包名来同时安装多个包，renv 会自动处理你安装的包所需的任何依赖项。
- 在 renv 下，所有包都将安装在本地项目目录中，而不是主中央库，这意味着你可以为同一个包拥有多个版本，每个项目对应一个特定的版本。
- 该包所需的所有示例数据都在 GitHub 上专门创建的数据包中：danmaclean/rbioinfcookbook。安装该数据包后，数据将在你的项目中可用。

对于本章节，我们需要以下包：

- 常规包：
  - ggplot2
  - knitr
  - palmerpenguins
  - rmarkdown
  - tidyverse
- GitHub:
  - danmaclean/rbioinfcookbook

这些应该都能轻松安装，然后我们就可以开始了。

# 更多信息

在教程的替代方案中，我们通常从普通的命令行（Bash 或 Windows）中调用 Quarto。RStudio IDE 包含渲染按钮，quarto 包中也有可在 R 控制台中使用的函数。请随时使用任何对你有效的方法。

在 R 中，加载库并直接通过名称使用函数是通常的做法。虽然这在短的交互式会话中很棒，但当同时加载许多共享函数名的包时，可能会引起混淆。为了明确我在特定时刻使用的是哪个包和哪个函数，我会偶尔使用 `packageName::functionName()` 约定。

有时在教程中间，我会中断对某些中间输出的深入或者查看对象的结构。当这种情况发生时，你会看到一个代码块，其中每行都以 ##（双井号符号）开头。考虑以下命令：

```
letters [1:5]
```

这将给你以下输出：

```
## a b c d e
```

注意，输出行以 ## 为前缀。

# 使用 Markdown 和 Quarto 进行文学化计算

生物信息学中的一项常见任务是写出我们的结果以便与同事交流，或者在我们的实验笔记本（电子或其他）中留下良好的记录。一项关键技能是使工作尽可能具有可重复性，这样当我们需要重新查看它或他人需要复制该过程时，我们可以重新运行它。解决此问题的一种流行方法是使用文学化编程技术和可执行笔记本，它们将人类可读的文本、分析代码和计算输出混合在单个文档中。在 R 中，Markdown 语法的 Markdown 扩展以及 Quarto 命令行工具（以及 R 包）允许我们在创建各种格式的输出文档时将代码和文本结合。在本教程中，我们将查看典型文档的大型结构，该文档可以使用 Quarto 渲染成多种格式。

# 准备工作

我们需要章节开头提到的 Quarto 命令行工具和一个文本编辑器。可选，你可以安装 R quarto 包。我们在这里创建的 Markdown 应该保存为具有 .qmd 扩展的文件——例如，example_quarto.qmd。

# 如何操作...

可以使用以下步骤开发可重用的工作流和报告：

1. 在 example_quarto.qmd 文件中，添加 YAML header：

```
---
title: "R Markdown in Quarto Report"
author: "AN Rizard"
date: "17 April, 2023"
output: html document
---
```

2. 然后，添加一些要解释的文本和代码：

你正在阅读一个用 Rmarkdown 创建并在 Quarto 中渲染的文档。
此文档包含了文本和代码的混合。下面的代码封装在反引号中，在渲染时代码将被执行，结果将插入到文档中

```````{r}
library(palmerpenguins)
x <- penguins$bill_length_mm
y <- penguins$bill_depth_mm

lmm(y - x)
```````
```

3. 使用 Markdown 的最小标记标记格式化文本：

我们可以使用 Markdown 格式化任何文本，简单的内联文本元素即可传达格式

## 行开头的 ## 使其标题。

两个井号给出二级标题，三个井号给出三级标题。标题从一级（最大）到六级（最小）

我们可以创建文本格式，包括 _斜体_ 和 **粗体**。

我们可以创建列表：
1. 第一项
2. 第二项

我们可以创建超链接 [一个一个指向 Google 的链接](https://www.google.com)

早些应用更多选项并在代码块之间传递对象状态

整个文档作为一个单一 R 会话运行 - 因此在早期块中创建的对象以后可以使用。

图表被插入到文档中。

- 设置一些选项并在代码块之间传递对象状态：

```{r}
# fig-width: 6
# fig-cap: "A caption"
```

- 保存后，我们渲染文档：

```bash
quarto render example_quarto.qmd
```

- 整个文档作为一个单一 R 会话运行 - 因此在早期块中创建的对象以后可以使用。

图表被插入到文档中。

- 设置一些选项并在代码块之间传递对象状态：

```{r}
# fig-width: 6
# fig-cap: "A caption"
```

- 保存后，我们渲染文档：

```bash
quarto render example_quarto.qmd
```

# 工作原理...

Quarto 系统基于多功能且强大的 Pandoc 来转换不同的文档。它最实用的功能之一是在各种标记语言之间（例如 HTML 和 LaTeX，以及 Markdown 和 Microsoft Office）之间进行翻译，使其成为作家、研究人员和开发者的有用工具。这意味着如果你有一个以一种格式编写的文档，可以轻松地将其转换为另一种格式，而无需手动重新格式整个文档。Pandoc 还可以执行各种转换，例如添加脚注、表格和图像，使其成为格式化和为出版准备文档的绝佳工具。例如，如果你需要准备提交期刊的报告，可以使用 Pandoc 将你的 R Markdown 转换为 PDF 或 Word，添加图像，并根据期刊的规范进行格式化。格式是由 YAML header 中的选项或配置文件指定的，而不是在标记本身中，因此将文档准备为从相同源渲染成多种格式仅需正确设置配置。在本教程中，我们将查看如何操作，特别是针对 HTML、PDF 和 Word 文档输出。

