

# 使用 API 数据

可以使用 `httr` 包下载相同的数据。以下代码下载了 `indicator_id = 1001`、`location_id = 86` 且 `year = 2019` 的指标数据。

我们可以使用 `GET()` 函数配合 URL `https://api.healthdata.org/sdg/v1/GetResultsTsByIndicator?indicator_id=1001&location_id=86&year=2019`：

```r
headers <- c("Authorization" = "YOUR-KEY")
res <- GET(url,
  add_headers(headers))
```

```r
res$content %>% rawToChar() %>% fromJSON(res)
```

在 {hmsidWR} 包中可以找到 `gbd_get_data()` 函数的高级版本。`hmsidWR::gbd_get_data()` 函数允许使用端点自定义（endpoint customization），而不是在长查询中使用 `sdg` 参数；通过 `GetResultsByIndicator`，可以指定查询的起点。然后，用户可以指定 `indicator_id`、`location_id` 和 `year` 来下载特定指标、位置和年份的数据。

该函数要求参数带有引号：

```r
hmsidWR::gbd_get_data(
  url = "https://api.healthdata.org/sdg/v1",
  key = "YOUR-KEY",
  endpoint = "GetResultsByIndicator",
  indicator_id = "1001",
  location_id = "86",
  year = "2019"
)
```

输出结果与上示例中的图 A.4 相同。

# A.3.2 包引用

{hmsidWR} 包可以在 https://github.com/Fgazzelloni/hmsidWR 获取。该包提供了支持本书的数据和函数。

从 CRAN 下载该包，或通过 GitHub 下载开发版本：

```r
# 从 CRAN 下载
install.packages("hmsidWR")

# 从 GitHub 下载
install.packages("devtools")
devtools::install_github("Fgazzelloni/hmsidWR")
```

# 本书使用的工具

本附录提供了复现书中使用的环境和代码的全面指南。要开始，您需要安装 R 编程语言以及 RStudio IDE。此外，我们将介绍设置 Quarto 项目、将其与 GitHub 集成进行版本控制，以及使用 {renv} 包确保可复现性的步骤。这将允许您准确恢复到与书籍创建期间完全相同的项目环境，确保所有代码示例都能无缝运行。

# B.1 RStudio 安装

首先，您需要访问以下链接下载并安装 RStudio Desktop。

Quarto 是 RMarkdown 的下一代版本，旨在各种发布任务，包括创建笔记、演示文稿和网站。本书使用 Quarto 开发，并在 GitHub 上进行版本控制。设置您的项目：

1. 在 RStudio 中创建一个新项目（Project）。
2. 启用 Git 版本控制。
3. 选择 "Quarto Book" 作为项目类型。这将自动生成具有以下结构的 `_quarto.yml` 文件：

```yaml
project:
  type: book
```
4. 要预览书籍，使用终端运行 `quarto preview`。此命令将生成一个包含编译后书籍文件的 `docs` 目录。

# 如何使用 Quarto 设置此项目

## B.2.1 有用命令

您可以在 RStudio 中直接通过 GitHub 或通过命令行管理项目。要将您的项目与 GitHub 连接：

- 初始化 Git 仓库：
```bash
git init
git remote add origin https://github.com/username/repo.git
```
- 提交文件并将其推送到仓库：
```bash
git branch -M main
git push -u origin main
```

## B.2.2 在 GitHub Pages 上发布您的书籍

要在 GitHub Pages 上发布您的书籍：

- 修改 `_quarto.yml` 文件以指定输出目录：
```yaml
---
project:
  type: book
  output-dir: docs
---
```
- 添加 `.gitignore` 文件以防止 GitHub Pages 忽略文件：
```bash
touch .gitignore
```
- 使用以下命令渲染书籍：
```bash
quarto render
```
此命令将创建一个 `docs` 文件夹，编译后的书籍将存储在其中。

## B.2.3 添加包

如果您想向项目添加自定义包，请遵循这些步骤：

- 使用 `devtools` 创建新包：
```r
devtools::create("yourpkg")
```
- 添加原始数据处理脚本：
```r
usethis::use_raw()
```
此命令会创建一个 `data-raw` 目录用于处理数据。
- 保存处理过的数据供包使用：
```r
usethis::use_data(yourdata)
```
- 为包函数和数据集编写文档：
```r
usethis::use_r("dataset")
devtools::document()
```
- 使用摘要（vignettes）提供额外文档：
```r
vignette("other")
vignette("rd")
```
- 最后，构建您的包以包含所有数据和函数：
```r
devtools::load_all(".")
```

## B.2.4 使用 renv 确保可复现性

为了确保书中所有的分析和代码示例都是可复现的，我们使用了 `renv` 包。该包捕获项目中使用的所有 R 包的具体版本，并将它们存储在 `renv.lock` 中。

要将项目环境恢复到书籍创建期间完全相同的状态：

1. 克隆项目仓库。
2. 在 R 控制台运行以下命令：
```r
renv::restore()
```
此命令将读取 `renv.lock` 文件并重装所有包，确保代码示例能够按预期工作。

# 转换为 Python 的提示

将 R 代码转换为 Python 在正确的引导下可以平滑过渡。让我们从基础开始，并比较 R 和 Python 之间的等价物。

## C.1 包与库

1. 安装包：
- R：`install.packages("package_name")`
- Python (使用 pip)：`pip install package_name`
- Python (使用 conda)：`conda install package_name`

2. 加载库：
- R：`library(package_name)`
- Python：`import package_name`

## C.2 Tidyverse 及其 Python 等价物

- tidyverse (R)：是一系列为数据科学设计的 R 包集合，包括用于数据处理的 `dplyr`、用于数据可视化的 `ggplot2`、用于整理数据的 `tidyr` 等。`library(tidyverse)`
- Python 等价物：
   - pandas：类似于 `dplyr`，提供了强大的数据处理工具。`import pandas as pd`
   - matplotlib/seaborn：类似于 `ggplot2`，这些库用于数据可视化。`import matplotlib.pyplot as plt`, `import seaborn as sns`
   - numpy：虽然不是 `tidyr` 的直接等价物，但 numpy 提供了数组操作和数值计算的功能，对于数据整理任务非常。`import numpy as np`
   - scikit-learn：提供了数据预处理、建模和评估工具，类似于 tidyverse 中的某些包（如 `modelr`）。`from sklearn import ...`

## C.3 创建数据统计

1. 创建基础数据：
- R：
```r
data <- data.frame(
  x = c(1, 2, 3, 4, 5),
  y = c(2, 3, 4, 5, 6)
)
```
- Python (使用 pandas)：
```python
import pandas as pd
data = pd.DataFrame({
  'x': [1, 2, 3, 4, 5],
  'y': [2, 3, 4, 5, 6]
})
```
2. 基础统计：
- R：
```r
# 汇总统计
summary(data)
```

