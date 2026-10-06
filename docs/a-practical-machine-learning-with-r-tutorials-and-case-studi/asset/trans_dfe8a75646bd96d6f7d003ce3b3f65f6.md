

## 9.3 数据

使用 `import()` 命令导入格式。文件可以从用户的本地硬盘或互联网加载。

- * 使用 `janitor` 包 (Firke (2023)) 将变量名重命名为大驼峰命名法（Upper-Camel），并替换变量名中的空格和特殊字符。
- * 使用 `tidymodels` 包 (Kuhn and Wickham (2020)) 来简化数据工程和机器学习任务。
- * 使用 `tableExtra` (Zhu (2021)) 包来支持表格的渲染。
- * 使用 `learner` 包 (Aden-Buie et al. (2022))，它需要配合 `shiny` 包 (Chang et al. (2022)) 用于本书中的交互式练习。
- * 使用 `shiny` 包 (Chang et al. (2022))，它需要配合 `learner` 包 (Aden-Buie et al. (2022)) 用于本书中的交互式练习。
- * 使用 `met` 包 (Venables and Ripley (2002)) 来创建和优化 MLP 神经网络。
- * 使用 `brute` 包 (Kuhn and Fabel (2022)) 基于 Python 库 PyTorch 创建并优化 MLP 神经网络。关于 `brute` 包，需要注意的是，在安装该包后需要安装 PyTorch 软件。安装 PyTorch 软件非常简单：当首次使用该包时（即执行 `library(brute)` 时），会弹出的窗口请求下载并安装所需的软件。点击“Yes”确认后，软件将安装。

## 9.3 数据

为了训练和测试，我们使用了著名的 `diamonds` 数据集。`diamonds` 数据集包含 53940 颗钻石的信息，包含在 R 包 `ggplot2` (Wickham (2016))。你可以在 R 控制台中输入 `?diamonds` 来了解更多关于该数据集的信息。`ggplot2` 会随 `tidymodels` 包自动加载，不需要执行 `library(ggplot2)`。

在下面的代码块中，我们首先加载 `tidymodels` 和 `janitor` 库。然后，我们将 `diamonds` 数据框中的列名转换为大驼峰命名法，选择 `Price`（价格）、`Carat`（克拉）、`Clarity`（净度）、`Cut`（切工）和 `Color`（颜色）变量进行分析，并将结果保存到数据框 `DataDiamonds` 中。之后，我们使用 `str()` 命令查看数据框结构：

```r
library(tidymodels); library(janitor)
DataDiamonds <- diamonds |
  clean_names("upper_camel") %>%
  select(Price, Clarity, Cut, Color)
str(DataDiamonds)
```

```r
## title [53940 x 5] (stbl: tbl/df/data.frame)
## $ : Int [1:53940] 0.23 0.21 0.23 0.29 0.31 0.24 0.24 0.26 0.22
## $ Clarity : num [1:53940] "SI1"<..."SI2"<...: 5 4 2 4 2 3 3 3 1
## $ Cut : Ord. w with 8 levels "Fair"<..."Good"<...: 2 2 6 2 7 6 6 5
## $ Color : Ord. w with 7 levels "F"<..."G"<......
```

`str()` 命令的输出显示，数据框 `Diamonds` 包含 53,940 个观测值和五个不同的变量（列），它们描述了钻石的属性以及价格（美元）。
被选为预测变量的 *Clarity, Cut, and Color* 也被称为钻石评估的“4C”属性：

1. Carat（克拉）：用于描述钻石重量的测量单位。以公克为单位（1 克拉等于 0.2 克），是比较钻石时最直观的因素。
2. Clarity（净度）：衡量钻石内部自然微观包裹体和缺陷可见性的测量标准。内含极少或无内含物的钻石被认为是稀有且极具价值的。钻石的净度分为八个等级，衡量钻石的清澈程度（II 最差，SI, SSI, VS1, VS2, VVS1, IF (最好)）。
3. Cut（切工）：针对钻石切面、对称性和反射光质。钻石的切工直接与其整体火彩和美感相关。钻石的切工分为五个等级：*Fair, Good, Ideal, and Super Ideal*。
4. Color（颜色）：钻石中可见的自然颜色或光色。钻石越接近“无色”，价格越贵。颜色分为七个等级，从 *D*（最好）到 *J*（最差）。

从上面的 `str()` 命令输出中，你可以看到 *Clarity, Cut, and Color* 分别存储为具有 8、7 和 6 个水平的 *R 因子类型（factor-type）*。

> ^4 以下描述提取自 Brilliant Earth 网站（https://www.brilliantearth.com/diamond/buying-guide/）。
> 5 `diamonds` 数据集中的净度分级与美国宝石学院（https://4cs.gia.edu/en-us/diamond-clarity/）的评级标准一致，但无暇（IF）和内含（I）类别未包含在具体等级中。

## 9.4 神经网络模型背后的思想

由于分析需要数值值，我们在下方的代码块中使用 `as.integer()` 命令提取因子水平作为数值：

```r
DataDiamonds=DataDiamonds |>
  mutate(Clarity=as.integer(Clarity)) |>
  mutate(Cut=as.integer(Cut)) |>
  mutate(Color=as.integer(Color))

head(DataDiamonds)
```

| | Price | Clarity | Cut | Color |
|---|---|---|---|---|
| | | <int> | <int> | <int> |
| 1 | 326.21 | 2 | 5 | 2 |
| 2 | 326.21 | 3 | 4 | 2 |
| 3 | 327.23 | 5 | 2 | 2 |
| 4 | 334.29 | 4 | 4 | 6 |
| 5 | 335.31 | 2 | 2 | 7 |
| 6 | 336.24 | 6 | 3 | 7 |

