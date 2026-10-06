

```r
server: shiny
```

2. 为输入小部件创建一个面板：

```r
# panel: sidebar
num_vars <- c("bill_length_mm", "flipper_length_mm", "body_mass_g")
cat_vars <- c("species", "island", "sex")

selectInput("x", "X轴上的变量", num_vars)
selectInput("y", "Y轴上的变量", num_vars)
selectInput("colour", "按颜色分类", cat_vars)
```

3. 为动态图表创建一个面板：

```r
# panel: fill
plotOutput("scatter_plot")
```

4. 编写服务器代码：

```r
# context: server

library(ggplot2)
library(palmerpenguins)
output$scatter_plot <- renderPlot({

  ggplot(penguins) + 
    aes(string(input$x, input$y)) + 
    geom_point(aes_string(colour = input$colour)) +
    theme_minimal() + 
    scale_color_brewer(palette = "Set2")

})
```

5. 启动服务器：

```bash
quarto serve shiny.qmd
```

这将在我们的浏览器窗口中启动一个交互式文档。

# 工作原理...

该配方从第 1 步开始，通过创建一个 YAML 头部，让 Quarto 知道此页面中的代码用于在 Shiny 小部件运行所需的服务器环境中运行。YAML 头部设置了标题和输出格式（必须是 html 且服务器类型）。

在第 2 步中，我们设置了布局。Quarto 文档中的 R 块采用了哈希管道符号 (`#`) 之后的特殊选项，告诉 Quarto 这部分代码将放在侧边栏布局（sidebar layout）中。随后的 R 代码定义了两个向量，这两个向量存储了我们将作为动态图表选项使用的变量名称。接下来，我们使用 Shiny 函数 `selectInput()` 创建动态输入下拉选择器。每个函数的第一个参数是代码中引用该元素的名称，第二个参数是该元素在渲染页面中的标签，第三个参数是该元素在渲染页面中显示的值列表——注意，我们使用了 `num_vars` 和 `cat_vars` 中的值。

第 3 步我们进一步设置了布局，添加了一个将包含渲染图表的面板。我们使用 `plotOutput()` 函数声明此处最终将渲染一个图表；该函数的唯一参数是 `scatter_plot` 名称，它将用于在代码中引用该元素。

第 4 步中，我们进入了实际的处理和绘图代码。`# context: server` 选项告诉 Quarto 这必须在服务器端运行，而不是在本地，并且每当元素更新时都需要运行。这使得操作变得简单；在加载数据和绘图的库后，我们使用 `renderPlot()` 函数创建一个动态图表。唯一的参数是绘图代码——这是多行代码，因此必须封装在使用 `}` 的匿名代码块中以使其成为整体。该代码块使用 `ggplot` 创建图表。注意，内置的 Shiny 输入对象 `input` 是输入元素值的所在地；`input` 对象的每个成员对应于我们在第 2 步在侧边栏中创建的元素。我们使用 `aes_string` 来绕过 ggplot 的非标准评估以及存储在变量中的值，而不是变量名。一旦创建了图表，我们使用第 3 步中选择的名称 (`scatter_plot`) 将其分配给内置的 Shiny 输出对象。

一旦我们的文档被创建并保存（例如，命名为 `shiny.qmd` 的文件），在第 5 步中，我们可以提供服务。这一步在命令行中完成。输出是本地机器上的地址，有时可以点击或复制粘贴到网络浏览器地址栏以查看运行中的交互式页面。

# 更多...

如果你需要获取此配方的完整示例文件，可以这样从 `rbioinfcookbook` 包中提取它：

```r
qmd_path <- fs::path_path("extdata", "shiny.qmd",
package="rbioinfcookbook")
file.copy(qmd_path, 'somewhere/on/your/system/shiny.qmd')
```

这样，你可以轻松地看到文档的结构，并有望节省一些打字时间。

# 参见

这些页面无法托管在 GitHub Pages 等平台上，因为它们需要活跃的 Web 服务器来处理动态服务器端更新。请查看 shinyapps.io 或 RStudio 的托管选项。

# 使用线性模型轻松进行 5 统计检验

线性模型是一种用于建模因变量与一个或多个自变量之间关系的统计工具。它们基于变量之间的关系是线性的假设，这意味着因变量的变化与自变量的变化成正比。

线性模型广泛应用于许多领域，包括生物信息学。在生物信息学中，线性模型可以用于分析大型数据集，例如基因表达数据。例如，线性模型可以用于识别不同实验条件之间的差异基因，或根据其他变量（如临床数据）预测基因的表达。

线性模型与统计检验（如 t 检验和方差分析 ANOVA）密切相关。事实上，t 检验和 ANOVA 可以被看作线性模型的特例。例如，双样本 t 检验等同于一个具有二值化自变量的线性模型，该二值变量表示正在比较的两个组。同样，ANOVA 是 t 检验的推广，其中涉及比较的组多于两个。在本章中，我们将学习如何采用统一的方法，教授一种理解和应用的通用方法。

在本章中，我们将涵盖以下内容：

- 使用线性模型进行建模
- 使用线性模型比较差异
- 使用线性模型进行 ANOVA
- 使用线性模型处理交互
- 使用线性模型进行预测
- 使用线性模型进行检验
- 使用线性模型进行分类

# 技术要求

我们将使用 renv 来管理项目特定的包。要使用 renv，首先需要安装该包：

- 1. 安装 renv：

```r
install.packages("renv")
```

- 2. 创建一个新的 renv 环境：

```r
renv::init()
```

这将创建一个 .renv 目录。

- 3. 随后可以通过以下安装包：

```r
renv::install()
```

- 4. 我们也可以使用 renv 包管理器安装 Bioconductor 包：

```r
renv::install("bioc::package")
```

- 5. 例如，要安装 Biobase 包，运行：

```r
renv::install("bioc::Biobase")
```

- 6. 你可以使用以下命令从 GitHub 安装开发版版包：

```r
renv::install("user/repo")
```

- 7. 例如，要安装 danmaclean/rbioinfcookbook 包，运行：

```r
renv::install("danmaclean/rbioinfcookbook")
```

你也可以通过逗号分隔包名一次安装多个包。renv 会自动处理你安装的包的依赖关系。在 renv 下，所有包将安装到本地目录而不是中央库，这意味着你可以拥有包的多个版本。

此包所需的所有数据都在 GitHub 上的特殊包 danmaclean/rbioinfcookbook 中。安装该包后，数据将在项目中可用。

对于本章，我们需要以下包：

- 常规包：
  - dplyr
  - ggplot2
  - multcomp
  - rcompanion
- GitHub 包：
  - danmaclean/rbioinfcookbook

