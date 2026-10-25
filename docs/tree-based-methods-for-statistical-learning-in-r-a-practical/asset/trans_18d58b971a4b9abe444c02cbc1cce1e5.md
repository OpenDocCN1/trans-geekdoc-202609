

![](img/2c227bfb3620dc3d159fa5e6598afa30_32_0.png)

图 1.3：具有四个分割的基本（二元）决策树。

five available features; parch is the only variable not selected to partition the data. The terminal nodes (nodes 6–11) each contain a node summary giving the proportion of surviving passengers in that node. As we’ll see in later chapters, these proportions can be used as class probability estimates.

五个可用特征；parch 是未被选中用于划分数据的唯一变量。终端节点（节点 6–11）各包含一个节点摘要，给出该节点中幸存乘客的比例。如我们在后续章节中将看到的，这些比例可用作类概率估计。

For example, the tree diagram estimates that first and second class female passengers had a 93% chance of survival; the percentage displayed in the bottom of each node corresponds to the fraction of training observations used to define that node. Given what you know about the ill-fated Titanic, does the tree diagram make sense to you? Does it appear that women and children were given priority and had a higher chance of survival (i.e., “women and children first”)? Perhaps, unless you were a third-class passenger.

例如，树图估计一等舱和二等舱女性乘客的生存概率为 93%；每个节点底部显示的百分比对应于用于定义该节点的训练观测值的比例。根据你对不幸的泰坦尼克号的了解，这个树图对你来说合理吗？看起来女性和儿童是否获得了优先权并且生存机会更高（即“妇女和儿童优先”）？也许吧，除非你是三等舱乘客。

In Part I of this book, I’ll look at how several popular decision tree algorithms choose which variables to split on (splitters) and how each split condition is determined (e.g., age < 9.5). Part II of this book will then look at how to improve the accuracy and generalization performance of a single tree by combining several hundred or thousand individual trees together.

在本书第一部分中，我将探讨几种流行的决策树算法如何选择要分割的变量（分割器）以及如何确定每个分割条件（例如，age < 9.5）。本书第二部分将探讨如何通过将几百或几千棵单独的树组合在一起，来提高单棵树的准确性和泛化性能。

![](img/2c227bfb3620dc3d159fa5e6598afa30_33_0.png)

图 1.4：总结不幸泰坦尼克号上生存概率的决策树图。

## 1.3 为什么选择 R？

### 为什么不？

### 1.3.1 说真的，为什么选 R？

I grew up on R (and SAS), but I've chosen it for this book primarily for one reason: it currently provides the best support and access to a wide range of tree-based methods (both classic and modern-day). For example, I'm not aware of any non-R open source implementation of tree-based methods that provides full support for nominal categorical variables without requiring them to be encoded numerically. Another good example is conditional inference trees [Hothorn et al., 2006c], the topic of Chapter 3, which are only implemented in R (as far as I'm aware). Nonetheless, there is at least one Python example included in this book!

我从小使用 R（和 SAS），但我为本书选择它主要出于一个原因：它目前为广泛的基于树的方法（经典和现代）提供了最佳支持和访问。例如，据我所知，没有任何非 R 的开源基于树的方法实现能够完全支持名义类别变量，而无需将其数值编码。另一个很好的例子是条件推断树 [Hothorn et al., 2006c]，即第 3 章的主题，据我所知，它们仅在 R 中实现。尽管如此，本书中至少包含一个 Python 示例！

This book was also written in R (and LaTeX) using the wonderful knitr package Xie [2021].

本书还使用了出色的 knitr 包 Xie [2021]，以 R（和 LaTeX）编写。

There's been some progress in areas of scikit-learn and other open source software that will be discussed in Chapter 8.

scikit-learn 和其他开源软件的某些领域已取得一些进展，将在第 8 章中讨论。

While I have a strong appreciation for the power of base R (i.e., the core language), I'm extremely appreciative of, and often rely on, the amazing ecosystem of contributed packages. Nonetheless, I've decided to keep the use of external packages to a minimum (aside from those packages related to the core tree-based methods discussed in this book), and instead rely on vanilla R programming as much as possible. This choice was made for several (highly opinionated) reasons:

虽然我非常欣赏基础 R（即核心语言）的强大功能，但我非常感激，并且经常依赖于，令人惊叹的贡献包生态系统。尽管如此，我决定将外部包的使用降至最低（除了与本书讨论的核心基于树的方法相关的包之外），并尽可能多地依赖原生 R 编程。出于几个（非常主观的）原因，做出了这一选择：

- it will make the book easier to maintain going forward, as the code examples will (hopefully) continue to work for many years to come without much modification;
- using standard R programming constructs (e.g., `for` loops and their apply-style functional replacements, like `lapply()`) will make the material easier to comprehend for non-R programmers, and easier to translate to other open source languages, like Julia and Python;
- it emphasizes the basic concepts of the methods being introduced, rather than focusing on current best coding practices and cool packages, of which there are many. (Please don't send me hate mail for using `sapply()` instead of `vapply()` or the family of map functions available in `purrr` [Henry and Wickham, 2020].)

- 这将使本书未来更易于维护，因为代码示例（希望）在未来多年内无需太多修改即可继续工作；
- 使用标准 R 编程结构（例如，`for` 循环及其 apply 风格的函数式替代品，如 `lapply()`）将使非 R 程序员更容易理解材料，并更容易将其转译为其他开源语言，如 Julia 和 Python；
- 它强调所介绍方法的基本概念，而不是关注当前的最佳编码实践和众多酷炫包。（请不要因为我使用 `sapply()` 而不是 `vapply()` 或 `purrr` [Henry and Wickham, 2020] 中可用的 map 函数系列而给我发仇恨邮件。）

Note that I've tried to be as aggressive as possible in terms of commenting upon the various code snippets scattered throughout this book and the online supplementary material. You should pay careful attention to these comments as they often link a particular line or section of code to a specific step in an algorithm, try to explain a hacky approach I'm using, and so on.

请注意，我尽可能积极地对本书和在线补充材料中散布的各种代码片段进行了注释。你应该仔细关注这些注释，因为它们通常将代码的特定行或部分与算法中的特定步骤联系起来，试图解释我使用的 hacky 方法，等等。

Each chapter includes one or more software sections, which highlight both R and non-R implementations of the relevant algorithms under discussion. Additionally, each chapter also contains R-specific software example sections (usually at the end of each chapter), which demonstrate use of relevant tree-specific software on actual data (either simulated or real).

每章包含一个或多个软件部分，突出显示所讨论的相关算法的 R 和非 R 实现。此外，每章还包含 R 特定的软件示例部分（通常在每章末尾），演示在实际数据（模拟或真实数据）上使用相关的树特定软件。

There are many great resources for learning R, but I would argue that the online manual, “An Introduction to R”, which can be found at https://cran.r-project.org/doc/manuals/r-release/R-intro.html, is a great place to start. Book-wise, I think that Matloff [2011] and Wickham [2019] are some of the best resources for learning R (note that the latter is freely available to read online). If you're interested in a more hands-on introduction to statistical and machine learning with R, I'll happily self-promote Boehmke and Greenwell [2020].

有很多学习 R 的优秀资源，但我认为在线手册“R 语言入门”（可在 https://cran.r-project.org/doc/manuals/r-release/R-intro.html 找到）是一个很好的起点。就书籍而言，我认为 Matloff [2011] 和 Wickham [2019] 是学习 R 的一些最佳资源（注意后者可免费在线阅读）。如果你有兴趣获得更实用的 R 统计和机器学习入门，我很乐意自我推广 Boehmke 和 Greenwell [2020]。

### 1.3.2 软件信息和约定

Each chapter contains at least one software section, which points to relevant implementations of the ideas discussed in the corresponding chapter. And while this book focuses on R, these sections will also allude to additional implementations in other open source programming languages, like Python and Julia. Furthermore, several code snippets are contained throughout the book to help solidify certain concepts (mostly in R).

每章至少包含一个软件部分，指向相应章节中讨论的想法的相关实现。虽然本书侧重于 R，但这些部分也将提及其他开源编程语言（如 Python 和 Julia）中的其他实现。此外，本书中包含多个代码片段，以帮助巩固某些概念（主要是 R）。

Be warned, I occasionally use dots in variable and function names—old R programming habits die hard. Package names are in bold text (e.g., **rpart**), inline code and function names are in typewriter font (e.g., `apply()`), and file names are in sans serif font (e.g., path/to/filename.txt). In situations where it may not be obvious which package a function belongs to, I'll use the notation `foo::bar()`, where `bar()` is the name of a function in package `foo`.

请注意，我偶尔会在变量名和函数名中使用点号——老的 R 编程习惯很难改。包名使用粗体文本（例如，**rpart**），内联代码和函数名使用等宽字体（例如，`apply()`），文件名使用无衬线字体（例如，path/to/filename.txt）。在不明显函数属于哪个包的情况下，我将使用 `foo::bar()` 表示法，其中 `bar()` 是包 `foo` 中的函数名。

I often allude to the documentation and help pages for specific R functions. For example, you can view the documentation for function `foo()` in package `bar` by typing `?foo::bar` or `help("foo", package = "bar")` at the R console. It's a good idea to read these help pages as they will often provide more useful details, further references, and example usage. For base R functions—that is, functions available in R's `base` package—I omit the package name (e.g., `?kronecker`). I also make heavy use of R's `apply()`-family of functions throughout the book, often for brevity and to avoid longer code snippets based on `for` loops. If you're unfamiliar with these, I encourage you to start with the help pages for both `apply()` and `lapply()`.

我经常提及特定 R 函数的文档和帮助页面。例如，你可以在 R 控制台中输入 `?foo::bar` 或 `help("foo", package = "bar")` 来查看包 `bar` 中函数 `foo()` 的文档。阅读这些帮助页面是个好主意，因为它们通常会提供更多有用细节、进一步参考和示例用法。对于基础 R 函数——即 R 的 `base` 包中可用的函数——我省略包名（例如，`?kronecker`）。我还在全书中大量使用 R 的 `apply()` 函数族，通常是为了简洁并避免基于 `for` 循环的更长代码片段。如果你不熟悉这些，我建议你从 `apply()` 和 `lapply()` 的帮助页面入手。

R package vignettes (when available) often provide more in-depth details on specific functionality available in a particular package. You can browse any available vignettes for a CRAN package, say `foo`, by visiting the package's homepage on CRAN at

https://cran.r-project.org/package=foo.

R 包 vignettes（如有）通常会提供特定包中特定功能的更深入细节。你可以通过访问 CRAN 上包的主页来浏览任何可用的 CRAN 包（例如 `foo`）的 vignettes，

https://cran.r-project.org/package=foo.

You can also use the `utils` package to view package vignettes during an active R session. For example, the vignettes accompanying the R package `rpart` [Therneau and Atkinson, 2019], which is heavily used in Chapter 2, can be found at https://CRAN.R-project.org/package=rpart or by typing `utils::vignette("bar", package = "foo")` at the R console.

你还可以使用 `utils` 包在活动 R 会话期间查看包 vignettes。例如，R 包 `rpart` [Therneau and Atkinson, 2019]（在第 2 章中大量使用）的 vignettes 可在 https://CRAN.R-project.org/package=rpart 找到，或在 R 控制台中输入 `utils::vignette("bar", package = "foo")`。

There's a myriad of R packages available for fitting tree-based models, and this book only covers a handful. If you're unfamiliar with CRAN's task views, you should be. They provide useful guidance on which packages on CRAN are relevant to a certain topic (e.g., machine learning). The task view on statistical and machine learning, for example, which can be found at

https://cran.r-project.org/web/views/MachineLearning.html,

lists several R packages useful for fitting tree-based models across a wide variety of situations. For instance, it lists **RWeka** [Hornik, 2021] as providing an open source interface to the J4.8-variant of C4.5 and M5 (see the online supplementary material on the book website). A brief description of all available task views can be found at https://cran.r-project.org/web/views/.

有大量可用于拟合基于树模型的 R 包，而本书仅涵盖其中一小部分。如果你不熟悉 CRAN 的任务视图，那么你应该熟悉。它们提供了有关哪些 CRAN 包与某个主题（例如，机器学习）相关的有用指导。例如，统计和机器学习任务视图（可在 https://cran.r-project.org/web/views/MachineLearning.html 找到）列出了几种适用于各种情况拟合基于树模型的 R 包。例如，它列出了 **RWeka** [Hornik, 2021]，作为 C4.5 和 M5 的 J4.8 变体的开源接口（参见书籍网站上的在线补充材料）。所有可用任务视图的简要描述可在 https://cran.r-project.org/web/views/ 找到。

Keep in mind that the focus of this book is to help you build a deeper understanding of tree-based methods, it is not a programming book. Nonetheless, writing, running, and experimenting with code is one of the best ways to learn this subject, in my opinion.

请记住，本书的重点是帮助你更深入地理解基于树的方法，它不是一本编程书。尽管如此，在我看来，编写、运行和实验代码是学习这门学科的最佳方式之一。

This book uses a couple of graphical parameters and themes for plotting that are set behind the scene. So don’t fret if your plots don’t look exactly the same when running the code. This book uses a mix of base R and **ggplot2** [Wickham et al., 2021a] graphics, though, I think there’s a **lattice** [Sarkar, 2021] graphic or two floating around somewhere. For **ggplot2**-based graphics, I use the **theme_bw()** theme, which can be set at the top level (i.e., for all plots) using **theme_set(theme_bw())**. Most of the base R graphics in this book use the following **par()** settings (see **?graphics::par** for details on each argument):

本书在绘图时使用了一些在幕后设置的图形参数和主题。因此，如果运行代码时你的图形看起来不完全一样，请不要担心。本书使用基础 R 和 **ggplot2** [Wickham et al., 2021a] 图形的混合，不过，我想某处还有一两个 **lattice** [Sarkar, 2021] 图形。对于基于 **ggplot2** 的图形，我使用 **theme_bw()** 主题，可以使用 **theme_set(theme_bw())** 在顶层（即所有图形）上设置。本书中大多数基础 R 图形使用以下 **par()** 设置（有关每个参数的详细信息，请参见 **?graphics::par**）：

```
par(
  mar = c(4, 4, 0.1, 0.1), # may be different for a handful of figures
  cex.lab = 0.95,
  cex.axis = 0.8,
  mgp = c(2, 0.7, 0),
  tcl = -0.3,
  las = 1
)
```

Some of the base R graphics in this book use a slightly different setting for the **mar** argument (e.g., to make room for plots that also have a top axis, like Figure 8.12 on page 349).

本书中的一些基础 R 图形对 **mar** 参数使用略有不同的设置（例如，为同时带有顶部轴的图形腾出空间，如第 349 页的图 8.12）。

## 1.4 示例数据集

The examples in this book make use of several data sets, both real and simulated, and both small and large. Many of the data sets are available in the **treemisc** package that accompanies this book (or another R package), but many are also available for download from the book’s website:

https://bgreenwell.github.io/treebook/datasets.html.

本书中的示例使用了多个数据集，包括真实和模拟数据，以及小型和大型数据。许多数据集可在伴随本书的 **treemisc** 包（或另一个 R 包）中找到，但许多也可从本书网站下载：

https://bgreenwell.github.io/treebook/datasets.html.

In this section, I’ll introduce a handful of the data sets used in the examples throughout this book. Some of these data sets are pretty common, and are

在本节中，我将介绍本书示例中使用的一些数据集。其中一些数据集非常常见，并且

