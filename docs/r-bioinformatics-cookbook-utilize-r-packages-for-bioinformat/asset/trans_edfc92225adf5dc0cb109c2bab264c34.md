

# bio3d 中的 3D 结构蛋白质对齐

步骤。你也可以使用整个序列。`getPredictionProfile()` 函数需要内核和模型对象才能工作。

在第 6 步中，我们绘制预测谱图（prediction profile）。该谱图显示了每个氨基酸对整体决策的贡献，并增加了学习结果的可解释性。在这里，第四个残基 D 对该谱图所做的决策做出了巨大贡献。通过检查许多序列中的这种情况，可以阐明有助于决策的模式。值得注意的是，你得到的图像可能与图 8.9 略有不同——由于此配方和算法的随机性部分——因此你应该在分析中考虑到这一点：确保任何差异都不是由于运行代码时的随机选择造成的。在这个例子中，最大的贡献应该仍然来自 D：

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_253_0.png)

此预测谱图是对重要氨基酸的一种简单而有效的显示。

# bio3d 中的 3D 结构蛋白质对齐

两个分子模型之间的三维结构对齐可以揭示蛋白质共有的或特有的结构属性。这些属性可能暗示进化或功能上的共同点。在这个配方中，我们将学习如何在维度上获取两个蛋白质序列的对齐，并在 3D 中查看它们。

# 准备工作

对于这个配方，我们需要安装一个序列对齐器。我们将利用 msa 包自带的 MUSCLE 版本并安装它。你也可以使用 conda 单独安装它。

我们还需要安装一个查看器。我们将使用 PyMOL，它可以通过以下方式安装到 conda 环境中：

```
conda install -c conda-forge -c schrodinger pymol-bundle
```

# 搜索基因和蛋白质序列的结构域和基序

我们还将使用 `bio3d` 包以及 `rbioinfcookbook` 包中的数据文件。

# 如何操作...

我们可以通过执行以下步骤来预测结构：

- 1. 加载必要的库和文件：

```
library (bio3d)

flxwc.pdb <- fs::path_package(
  "extdata",
  "1xwc.pdb",
  package="rbioinfcookbook"
)
f3trx.pdb <- fs::path_package(
  "extdata",
  "3trx.pdb",
  package="rbioinfcookbook"
)

a <- read.pdb(flxwc.pdb)
b <- read.pdb(f3trx.pdb)
```

- 2. 执行对齐：

```
pdbs <- pdbaln(list("1xwc"=a,"3trx"b), fit=TRUE, exfile="msa")
```

- 3. 在 PyMol 中启动并渲染对齐：

```
env_path <- function(env, program = "") {
  df <- reticulate::conda_list(
  b <- df$python[which($dfname == env)]

  if (length(b) == 0) {
    stop("未找到名为该的环境")
  }

  file.path(dirname(b), program)
}

pymol_path <- env_path("informatics_project", "pymol")

pymol(pdbs, exfile = pymol_path, type = "launch", as="cartoon")
```

这些都是为了获得预测结构的渲染视图我们需要执行的所有步骤。

# 工作原理...

与通常一样，步骤 1 是使用 `read.pdb()` 函数加载库和输入数据——两个不同的蛋白质数据库（PDB）文件。在第 2 步中，我们使用 `pdaln()` 函数进行对齐。我们将所有想要对齐的 PDB 放入一个具有适当名称的列表对象中。`fit` 参数设置为 `TRUE`，以便根据所有对齐序列执行结构叠加。`exefile` 参数告诉函数去哪里寻找对齐器——在这里，`msa` 值告诉它去我们安装的 `msa` 包中查找。

一旦我们有了对齐，就想在 PyMOL 中将其可视化。可执行文件安装在 conda 环境中，因此我们可以使用第 3 步开头定义的自定义 `env_path()` 函数提取路径并将其作为参数传递给 `pymol()`。PyMOL 将会启动并渲染对齐结果。

# 更多...

如果你不想在 msa 中使用 MUSCLE，可以在第 2 步中使用指向替代可执行文件的路径，或者将 `exefile` 替换为 `web.args="your.email@something.org"` 以通过 EBI 网页进行对齐。

在第 3 步中省略 `type` 参数将导致写入 PyMOL 脚本，你可以在单独的 PyMOL 会话中使用它。

# 系统发育学分析与可视化

系统发育学是研究物种或其他生物群之间进化关系的学科。它涉及使用分子和计算技术来构建系统发育树，这些树描绘了所研究生物的进化史。

在生物信息学中，使用各种计算工具和方法研究系统发育学，包括序列对齐、基于距离的方法、极大似然法和贝叶斯推断。这些方法允许研究人员比较不同生物的 DNA 或蛋白质序列，并根据遗传成分的相似性和差异推断它们的进化关系。系统发育学在生物学中有许多应用，用于帮助理解物种的进化历史，研究疾病的起源和传播（系统发育分析可用于追踪传染疾病的起源和传播），并通过识别进化上独特的物种或种群为保护工作提供信息。

# 技术要求

我们将以项目特定的方式使用 `renv` 管理包。要使用 `renv` 安装包首先需要 `renv` 包。你可以通过控制台运行以下命令来实现：

- 1. 安装 renv：

```
install.packages("renv")
```

- 2. 创建一个新的 renv 环境：

```
renv::init()
```

这会在你的项目中创建一个名为 .renv 的目录。

- 3. 随后可以使用以下命令安装包：

```
renv::install()
```

- 4. 你还可以使用 renv 包管理器通过运行以下命令安装 Bioconductor 包：

```
renv::install("bioc::package name")
```

- 5. 例如，安装 Biobase 包，你需要运行：

```
renv::install("bioc::Biobase")
```

- 6. 你可以这样使用 renv 安装 GitHub 上的开发包：

```
renv::install("user name/repo name")
```

- 7. 例如，安装 damnaclean 用户 rbioinfcookbook 包，你需要运行：

```
renv::install("damnaclean/rbioinfcookbook")
```

逗号分隔包名分开安装多个包。renv 会自动处理你安装的包所需的任何依赖项。

在 renv 下，所有包都将安装在本地项目目录中，而不是主库中，这意味着每个项目可以拥有同一个包的不同版本。

该包所需的所有示例数据都在 GitHub 上专门创建的数据包 damnaclean/rbioinfcookbook 中。安装该包后，这些数据将在你的项目中可用。

对于本章，我们需要以下包：

- 常规包：
  * adographics
  * ape
  * cowplot
  * data.table
  * dplyr
  * fs
  * ggplot2
  * pangorn
  * readr
  * reticulate
  * treespace
- GitHub:
  * damnaclean/rbioinfcookbook
  * evolvedmicrobe/dotplot
- Bioconductor:
  * Biostrings
  * dotplot
  * ggtree
  * msa
  * treeio

除了这些包之外，我们还需要一些 R 工具，例如 conda。所有这些将在需要时进行说明。

