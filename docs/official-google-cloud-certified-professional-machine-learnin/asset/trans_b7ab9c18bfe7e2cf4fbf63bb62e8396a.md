

## 模型类型

**表 14.2** 模型类型

| 模型类型 | 可解释性方法 | 说明 |
| --- | --- | --- |
| 线性回归和逻辑回归 | Shapley 值、标准误、p 值 | 这是对所有可能联盟的所有边际贡献的平均值。 |
| 提升树 | Tree SHAP、基于基尼系数的特征重要性 | 针对基于决策树的模型优化的 Shapley 值。 |
| 深度神经网络和宽深模型 | 集成梯度 | 一种基于梯度的方法，能高效计算特征归因，具有与 Shapley 相同的公理属性。 |
| `Arima_PLUS` | 时间序列分解 | 如果时间序列中存在多个分量，则将其分解为多个分量。 |

为预测添加可解释性会产生计算成本。对于 Shapley 等方法尤其如此，其复杂度会随特征数量呈指数级增长。

在以下 SQL 代码中，我们使用的是 `EXPLAIN_PREDICT` 而非 `PREDICT` 函数。我们从名为 `dataset1.credit_card_test` 的表中选择所有列，且仅选择一行。结果如 **图 14.7** 所示。

![图 14.7 预测结果](images/c14f007.png)

**图 14.7** 预测结果

```sql
SELECT *
FROM ML.EXPLAIN_PREDICT(
    MODEL `creditcard_model1`,
    (
        SELECT * FROM
        `dataset1.credit_card_test` LIMIT 1
    ),
    STRUCT(5 AS top_k_features)
)
```

在本例中，预测值为 –1.281。现在让我们看看作为查询结果一部分报告的前五个特征（**图 14.8**）。值得注意的是，这些单个特征贡献比基线低两个数量级。

![图 14.8 预测的顶部特征归因](images/c14f008.png)

**图 14.8** 预测的顶部特征归因

分析完解释后，您可能还希望将全局解释作为元数据的一部分进行记录。在模型层面，您可以始终预留一个数据集专门用于运行解释。将每次预测的特征归因与预测结果一起存储。

## BigQuery ML 与 Vertex AI Tables

BigQuery ML 处理表，Vertex AI 也是如此。这两个产品有相似之处，但存在关键差异，因为它们面向不同类型的用户。BigQuery 是一款无服务器数据仓库，其用户是 SQL 专家，习惯用表、连接、`GROUP-BY` 语句等概念思考问题。部分 BigQuery 客户编写了数千个查询，其中一些非常复杂，通过 `BigQuery_scheduled queries` 自动化，并使用 Looker 和 Looker Studio 等可视化工具。

Vertex AI 的客户非常熟悉 Kubeflow，且精通 Java 或 Python。这类数据科学家每天使用 Jupyter Notebook，主要使用 Pandas DataFrame 处理数据。这类机器学习工程师构建有趣的新神经网络，有时编写自定义 TensorFlow 操作，并考虑使用 TPU。这类用户希望对数据流和训练过程拥有细粒度的控制。

总之，尽管这两个产品功能大体相似，但其界面以及训练和预测的方法截然不同，面向的受众也不同。

## 与 Vertex AI 的互操作性

尽管 Vertex AI 和 BigQuery ML 是截然不同的产品，但它们在机器学习流水线的每个环节都被设计为可互操作。至少有六个集成点，使得将这两个产品无缝结合使用变得轻而易举。

### 访问 BigQuery 公共数据集

BigQuery 拥有 200 多个公共数据集，通过 Google Cloud 公共数据集计划向公众开放。Google 承担数据集的存储费用，您可以通过自己的 GCP 项目访问它们。您只需为在这些数据集上运行的查询付费。

您也可以从 Vertex AI 访问这些数据集，以训练 ML 模型或增强现有数据。例如，假设您要预测某地的交通状况；您可以将自己的数据集与 BigQuery 的公共天气数据集结合，以改进模型。

### 将 BigQuery 数据导入 Vertex AI

在 Vertex AI 中创建数据集时，您需要提供源网址作为起点。您可以直接提供指向 BigQuery 数据集的 BigQuery 网址，以创建 Vertex AI 数据集。您可以在控制台中通过几个步骤完成此操作，或在 Python 中按如下方式操作：

```python
from google.cloud import aiplatform
dataset = aiplatform.TabularDataset.create(
    display_name="my-tabular-dataset",
    bq_source="bq://project.dataset.table_name",
)
```

请注意，我们并未将数据从 BigQuery 导出再导入 Vertex AI。得益于此集成，您现在可以无缝连接 BigQuery 中的数据。

### 从 Vertex AI Workbench Notebook 访问 BigQuery 数据

当您在 Vertex AI Workbench 的托管笔记本实例中使用 Jupyter Notebook 时，可以直接浏览 BigQuery 数据集、运行 SQL 查询，或下载为 Pandas DataFrame。

这对于使用 Jupyter Notebook 进行探索性分析、创建可视化、试验机器学习模型，或使用不同数据集进行特征工程的数据科学家来说非常有用。

### 在 BigQuery 中分析测试预测数据

此功能与数据集创建集成类似，但方向相反。训练模型时，您提供训练集和测试集，作为流程的一部分，您会获得测试集的预测结果。您可以将这些结果直接导出到 BigQuery。当您想使用各种 SQL 方法进一步分析测试预测时，这非常有用。

### 导出 Vertex AI 批量预测结果

在 Vertex AI 中进行批量预测时，您可以直接指向 BigQuery 表作为输入数据，此外，还可将预测结果发回 BigQuery 并存储为表。如果您已使用 Vertex AI 标准化 MLOps，但数据在 BigQuery 中，这非常有用。

### 将 BigQuery 模型导出到 Vertex AI

在 BigQuery 中构建模型后，您可以将模型从 BigQuery 导出到 GCS，然后导入 Vertex AI。这使您能完全自由地在任何地方训练和使用模型。展望未来，如果您使用 Vertex AI Model Registry，可以直接将 BigQuery ML 模型注册到其中。此步骤省去了将模型文件导出到 GCS 的额外工作，实现了无缝衔接。支持 BigQuery 内置模型和 TensorFlow 模型。目前导出 `ARIMA_PLUS` 模型、`XGBoost` 模型以及使用了 transform 的模型存在限制。

## BigQuery 设计模式

在数据科学和机器学习中，有几种情况频繁出现，足以被视为一种模式，针对这些情况有一些巧妙且经过深思熟虑的解决方案，称为设计模式。因为 BigQuery ML 是一项从新视角切入机器学习的革命性技术，所以针对一些老问题出现了一些优雅的新解决方案。

### 哈希特征

此解决方案解决了分类变量面临的三个问题：

*   **词汇表不完整**：输入数据可能不包含分类变量可能取值的完整集合。如果数据直接输入 ML 模型，这会造成问题。
*   **基数高**：邮政编码是基数高的分类变量示例，这在 ML 中会造成一些扩缩问题。
*   **冷启动问题**：分类变量可能会新增训练数据集中不存在的值——例如，新员工入职时创建新的员工 ID。

