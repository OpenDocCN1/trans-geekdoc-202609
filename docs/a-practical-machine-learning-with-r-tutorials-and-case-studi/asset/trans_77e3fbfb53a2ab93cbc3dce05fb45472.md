
## 8 逻辑回归 — 处理不平衡数据

少数类中的观测值现在是通过相似的观测值进行增强的，而不是现有观测值的完全复制。

在随后的 8.6 节中，你可以尝试这里介绍的平衡方法，例如 `step_downsample()`、`step_upsample()` 和 `step_smote()`，并根据意愿组合它们。

对于下采样和上采样命令 `step_downsample()`、`step_upsample()`、`step_smote()`，你也可以设置多数类和少数类之间的所需比例。

下采样命令使用 `under_ratio=` 来设置所需的比例。`under_ratio` 定义为：

其中：$N_{major} :=$ 多数类的最终观测数量，$N_{minor} :=$ 少数类的观测数量

例如，`under_ratio=1`（默认值）意味着在完成下采样后，少数类和多数类的观测数量将相同。`over_ratio=1.2` 意味着当多数类观测数量比少数类观测数量多 20% 时停止下采样。

对于两个上采样命令 `step_upsample()` 和 `step_smote()`，所需的比例由参数 `over_ratio` 决定，其定义为：

```
$over_ratio = \frac{N_{minor}}{N_{major}}$
```

其中：$N_{minor} :=$ 少数类的最终观测数量，$N_{major} :=$ 多数类的观测数量

例如，`over_ratio=1`（默认值）意味着在完成上采样后，少数类和多数类的观测数量将相同。`over_ratio=0.9` 意味着当少数类观测数量达到多数类数量的 90% 时停止上采样。

## 8.6 使用平衡数据重复流失分析

### 交互式章节

在本节中，你将找到内容以及可以在 RStudio 中执行、修改和重新运行的 R 代码。

阅读和学习本节的最佳方式是使用 RStudio 打开它。这样你就可以在网络浏览器中交互式地进行代码练习和 R 项目了。通过这种方式，你可以应用目前为止学到的知识并扩展你的知识。你也可以选择继续阅读书籍或在线内容，但你将无法从交互式学习体验中受益。

在 RStudio 的交互式环境中处理本节，请遵循以下步骤：

- 1. 确保已安装 `R` 和 `shiny` 包。如果没有，请从 RStudio 的主菜单（Tools -> Install Packages ...）安装。
- 2. 下载用于交互会话的 R 文件并保存到你的项目文件夹中。你将在下方找到下载链接。
- 3. 在 RStudio 中打开下载的文件，并位于窗口顶部中间的 Run Document 按钮。

有关运行练习（包括 Windows 和 Mac 用户的视频）的帮助，请参考：https://blog.lang-analytics.com/exc/2024/01/intersections.html

不要跳过这个交互式章节，除了提供已学概念的应用，它还将扩展你目前为止学的内容。

以下是下载交互式章节的链接：
https://ai.lang-analytics.com/exc/?file=09-LogRegExerc200.Rmd

在第 8.4 节中为电信公司进行分析时，你的结果在预测不流失的客户（Churn = No）方面存在偏差。这是因为电信数据集中观测值的数量偏向于不流失的客户（负类）。

作为提醒，由于数据集不平衡，特异性（负类的预测质量）为 90%，而灵敏度（正类的预测质量）仅为 43%。

在本节中，你将重复第 8.4 节的分析，但在执行逻辑回归分析之前，你将平衡训练数据以改进结果。你将使用相同的训练/测试数据和相同的命令（recipe 定义除外）。

为了让你了解如何修改 recipe，我们展示了第一次尝试

## 8 逻辑回归 — 处理不平衡数据

我们如何使用下面的代码块。我们使用 `step_downsample(Churn, over_ratio=2)` 和 `step_smote(Churn, over_ratio=0.75)`：

```
set.seed(789)
RecipeChurn=recipe(Churn-, data=DataTrain) |>
    step_dummy(Gender) |>
    step_downsample(Churn, over_ratio=2) |>
    step_smote(Churn, over_ratio=0.75)
```

```
DataTrainBal=RecipeChurn |>
    prep() |>
    juice() |>
count(Churn, Churn)
```

| tibble: 2 x 2 |
| Churn | n |
| <int> | <int> |
| 1 Yes | 1962 |
| 2 No | 2616 |

我们是如何得到 `DataTrainBal` 数据的？首先，`step_downsample(Churn, over_ratio=2)` 从训练数据框（DataTrain）的多数类中随机删除观测值，直到多数类的观测数量减少到少数类大小的两倍（Churn = Yes 有 1308 个观测值，Churn = No 有 2616 个观测值）；最初，`step_smote(Churn, over_ratio=0.75)` 为少数类创建新的观测值，直到少数类的数量达到多数类数量的 75%。

（注：原文中存在大量重复的 OCR 错误，已根据提供的内容进行了去重和清理）
