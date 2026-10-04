

-   [Pipeline](https://mng.bz/LyX8)
-   [ColumnTransformer](https://mng.bz/BXM8)
-   [FeatureUnion](https://mng.bz/DX20)

`Pipeline` 命令允许你创建一个 Scikit-learn 类序列，从而对数据进行一系列转换，并最终得出预测。通过这种方式，你可以将任何模型与其对数据所需的变换整合在一起，并一次性处理所有相关的参数——变换的参数以及模型本身的参数。`Pipeline` 命令是 Scikit-learn 软件包中将表格数据从源移动到预测的核心命令。在实例化时，你只需要提供一个元组列表，每个元组组包含流水线中步骤的名称以及要执行的 Scikit-learn 类或模型。一旦实例化，你就可以按照 Scikit-learn 的通用 API 规范（`fit`/`predict`）来后续操作。`Pipeline` 将按顺序执行所有预定义的步骤，自然地，你可以检查并调优流水线序列中的单个步骤以获得更好的结果和性能，但你也可以将流水线视为一个单一的宏命令处理。

然而，列可能具有不同的类型并需要完全不同的转换序列，或者你可能设计了两种处理数据的方法并希望将其合并。`ColumnTransformer` 和 `FeatureUnion` 是 Scikit-learn 命令，可以帮助你将特定的变换或变换流水线应用于某些列（你可以通过它们在列序列中的名称或位置来定义）。该命令接收一个元组列表，与 `Pipeline` 命令一样，但它需要变换的名称、执行该变换的 Scikit-learn 类，以及应用该变换的列名或索引列表。由于它是一个转换命令，其理想的用法是在流水线内部，在那里它的变换可以作为模型数据馈送的一部分。相比之下，`FeatureUnion` 只是连接两个不同流水线结果的一种方法。你也可以使用简单的 NumPy 命令如 `np.hstack`（https://mng.bz/IkJD）来实现相同的结果。然而，使用 `FeatureUnion` 的优势在于该命令可以分入 Scikit-learn 流水线中，从而自动作为模型数据馈送的一部分使用。

Scikit-learn 及其 `Pipeline` 提供的操作模块化和 API 一致性将允许你创建复杂的数据转换并将其作为单一命令处理，使你的代码具有高度的可读性、紧凑性和易于维护性。在下一节中，我们将回到 Airbnb NYC 数据集。我们将在 Scikit-learn 中创建一系列转换序列，这将允许我们演示 Scikit-learn 及其流水线功能为何处理表格数据问题的正确选择。我们还将指出，得益于定义良好的流水线，你可以轻松地在表格数据机器学习的不同选项之间切换。

## 探索和处理 Airbnb NYC 数据集的特征

## 4.2 探索和处理 Airbnb NYC 数据集的特征

之前介绍的 Airbnb NYC 数据集是一个演示的完美示例，因为它是一个代表真实世界问题及其各种类型列的数据集。我们需要携带并组合流水线来处理不同的特征，接下来的章节将让我们有机会展示比此处你找到的更高级的处理技术。

目前，我们将要处理的特征放入一个列表 `excluding_list` 中。它们是某些特征，例如纬度和经度或最后一次评论的数据（`last_review`），这些特征需要特殊的临时处理。此外，数据集还展示了几列可能作为目标：价格（`price`）、列出物业的可用性（`availability_365`）以及评论数量（`number_of_reviews`）。对于我们的目的，我们更倾向于使用价格，因为它是大于零的连续值集，我们可以立即将其作为回归目标。此外，通过对平均值或中位数进行拆分，或将值分入十桶，我们可以快速地将价格转换为二分类或多分类目标。除了价格之外，我们将使用所有其他特征作为预测或用于更高级的特征工程。

在接下来的小节中，我们将演示一种逐步的方法来探索数据集，根据有用的列过滤数据集，并设置我们的目标变量。原则上，在进行探索性数据分析（EDA）时，我们将遵循第 2 章提供的提示和示例。在下一节中，我们将利用发现并准备合适的流水线，这些流水线将在随后的段落中修订表格数据机器学习的不同选项时被重复使用。

### 4.2.1 数据集探索

作为探索数据集的第一步，我们导入相关的包（NumPy 和 pandas），定义排除的特征列表，并根据我们在上一章中建立的先验知识将分类特征和连续特征分开，并从当前工作目录加载数据。要执行的代码是：

```python
import numpy as np
import pandas as pd
excluding_list = ['price', 'id', 'latitude',
  'longitude', 'host_id',
  'last_review', 'name',
  'host_name']
categorical = ['neighbour_group',
  'neighborhood',
  'room_type']
continuous = ['minimum_nights',
  'number_of_reviews',
  'reviews_per_month',
  'calculated_listings_count']
data = pd.read_csv('Airbnb_NYC_2019.csv')
```

