

### 3.3.2 指令列表

指令列表是一种描述性文本，用来描述各部分代码在做什么。

在《如何共享数据进行协作》中，Ellis 和 Leek（Ellis and Leek, 2017）提出，代码功能的高层级概要至关重要。以下是对他们前两个步骤的改写：

- 步骤 1：获取原始数据文件，使用参数 $a = 1, b = 2$ 运行汇总代码
- 步骤 2：分别对每个样本运行代码

接下来应用 Knuth 的“文学编程”（Literate Programming）理念，每一步后面都应该紧跟着实现该步骤的代码。R Markdown 格式非常适合这类工作；文本描述后面可以跟一段 R 代码，然后再跟另一对文本描述/R 代码块，以此类推。

在实践中，你可能会采取循序渐进的方法：

- 1. 为基本计划创建大纲，
- 2. 在该计划中添加你将在分析中执行的步骤，
- 3. 为每个步骤补充一些文本细节，
- 4. 编写代码。

### 3.3.3 带文档代码的示例

这些原则在实践中是什么样的？下面的示例展示了每个步骤可能的形式。

我们从大纲开始：

- 目标：找出世界上 10 个最大经济体的相对规模。
- 数据：将使用 `{gapminder}` 包，并使用最近一年的数据（2007 年）。
- 计算：人均 GDP * 人口 = 国家 GDP 总量。
- 表格：创建包含前 10 个国家的表格。

有了这个大纲，我们可以进入“数据”步骤

```
# DATA

gapminder_gdp <- gapminder::gapminder |>
  # filter for most recent year
  # use `slice_max()` function instead of hard-coding value
  # - make sure that it is the most recent data
  # note: this is a shorthand for `filter(year == max(year))`
  slice_max(year)
```

“计算”步骤：

```
# CALCULATION

gapminder_gdp <- gapminder_gdp |>
  # calculate total GDP
  mutate(gdpCountry = gdpPercap * pop) |>
  # divide by 10^12 to turn into trillions
  mutate(gdpCountry = gdpCountry/(10^12)) |>
  # select relevant variables
  select(country, gdpCountry)

head(gapminder_gdp)
```

```
## # A tibble: 6 x 2
##   country   gdpCountry
##   <fct>          <dbl>
## 1 Afghanistan    0.0311
## 2 Albania        0.0214
## 3 Algeria        0.207
## 4 Angola         0.0596
## 5 Argentina      0.515
## 6 Australia      0.704
```

最后，使用 {gt} 包创建表格并设置其格式（Iannone et al., 2023）

```
gapminder_gdp |>
  # use `slice_max()` with `n =` argument to get 10 largest economies
  # `slice_max()` has the added bonus of sorting in descending order
  slice_max(gdpCountry, n = 10) |>
  # create table with {gt} package
  gt::gt() |>
  # add table formatting
  fmt_number() |>
  # add table text
  tab_header(
    title = "Size of 10 largest national economies",
    subtitle = "Total GDP, 2007 (trillions of US$)"
  ) |>
  tab_source_note(
    source_note = "Source: {gapminder} package"
  )
```

10 个最大经济体的规模

2007 年 GDP 总量（万亿美元）

| 国家 | gdpCountry |
|---|---|
| 美国 | 12.93 |
| 中国 | 6.54 |
| 日本 | 4.04 |
| 印度 | 2.72 |
| 德国 | 2.65 |
| 英国 | 2.02 |
| 法国 | 1.86 |
| 巴西 | 1.72 |
| 意大利 | 1.66 |
| 墨西哥 | 1.30 |

来源：{gapminder} 包

```
# note: other table formatting to consider:
# - change variable names
# - add growth from 1957?
```

> > Benjamin D. Lee 的《记录科学软件的十条简单规则》（Lee, 2018）中的第一条是“边写代码边写注释。”

## 3.4 项目文档

项目文档中较高层级的一部分是项目文件的结构。

对于在学术环境中工作的人来说，Marwick、Boettiger 和 Mullen（Marwick et al., 2018）定义了研究汇编中应该包含的内容应遵循的三条通用原则。这些原则也可以适用于其他场景：

- 按照现行标准组织文件。
- 保持数据、方法和输出的清晰分离。
- 说明所使用的计算环境。

这些信息也被称为项目的“元数据”（White et al., 2013）。

需要纳入文档的更详细内容列表包括：

- 项目、分析和研究目标的简要描述。
- 文件夹结构图。
- 关于数据来源的详细信息
  - 收集数据的组织名称。
  - 该组织中负责人的姓名和联系方式。
  - 下载或提取日期。
  - 网页链接。
  - 原始文件名。
  - 指向数据附加文档（如数据字典）的链接。
- 关于分析*如何*完成的高层级说明
  - 例如：“本分析使用了 2010 年至 2019 年的每日数据来计算每月平均量，随后将其用于 ARIMA 模型以生成 6 个月预测。”
- 关于分析和代码的详细信息：
  - 影响决策的事项（“我选择这种统计检验是因为……”或“出生日期变量被转换为‘截至 2020 年 7 月 1 日的年龄’，因为……”）
  - 指令列表——描述文件或代码块在做什么、但不描述如何实现的描述性文本。
  - 数据字典或代码簿。
- 所用软件和包的详细信息：
  - 版本和（如有）发布日期。

### 3.4.1 README 文件

> > Benjamin D. Lee 在《记录科学软件的十条简单规则》（Lee, 2018）中的第四条规则是“包含一个带有基本信息的 README 文件。”

在项目的根文件夹中放置一个 README 文件，是记录项目大量重要通用信息的好方法。在数据文件夹中再放一个 README 文件也无妨。

另一个介绍数据文件 README 的来源是康奈尔大学研究数据管理服务小组撰写的《编写“readme”风格元数据指南》（Research Data Management Service Group, 2021）。

SFBrigade 是一个旧金山的志愿者公民科技组织，它为他们的项目创建了一个数据科学专用的 README 大纲，托管在 github¹。

推荐的基本最小 README 结构是：

¹Project-README-template.md (https://github.com/sfbrigade/data-science-wg/blob/master/dswg_project_resources/Project-README-template.md)

- 项目介绍/目标
- 项目描述
  - 一个缺失的组件是“数据来源”。
- 团队（含联系方式）

对于一个已完成的分析型项目，你可能还希望包含高层级的结果。这可能类似于学术期刊文章中的摘要，或商业或政府报告中的执行摘要。

另一个技巧来源是《README 的艺术》²。虽然它面向的是编写计算机程序和模块的人，但这些经验同样适用于数据科学项目。README 的目的是：

- 1. 告诉他们它是什么（结合上下文）。
- 2. 向他们展示它在实际使用中的样子。
- 3. 向他们展示如何使用它。
- 4. 告诉他们任何其他相关细节。

一个例子是 R 包 {palmerpenguins}，它在 GitHub 页面上有一个全面的 README。³

### 3.4.2 记录目录结构

你的文档（可能作为 README 文件的一部分）可以包含一张显示目录结构的图。{fs} 包（Hester et al., 2020）有一个函数 dir_tree()，它可以生成项目文件夹中文件夹结构和文件的树状图。

```
```r
library(fs)
```
```

默认情况下，它会显示当前目录下的所有子文件夹和文件。

```
```r
fs::dir_tree(path = "project_template")
```
```

## project_template

```
## +-- data
## |   \-- readme.md
## +-- data-raw
## |   +-- readme.md
## |   \-- source_data.xlsx
## +-- figs
## |   \-- readme.md
## +-- output
## |   \-- readme.md
## +-- readme.md
## \-- scripts
##      \-- readme.md
```

recurse = 参数指定树状图将绘制的目录结构深度。指定 recurse = FALSE 会将显示内容限制为当前目录内的文件和子文件夹。

```
fs::dir_tree(path = "project_template", recurse = FALSE)
```

```
## project_template
## +-- data
## +-- data-raw
## +-- figs
## +-- output
## +-- readme.md
## \-- scripts
```

还可以通过使用整数（而不是 FALSE 或 TRUE）来指定层数。

```
fs::dir_tree(path = "project_template", recurse = 2)
```

```
## project_template
## +-- data
## |   \-- readme.md
## +-- data-raw
## |   +-- readme.md
## |   \-- source_data.xlsx
## +-- figs
## |   \-- readme.md
## +-- output
## |   \-- readme.md
```

