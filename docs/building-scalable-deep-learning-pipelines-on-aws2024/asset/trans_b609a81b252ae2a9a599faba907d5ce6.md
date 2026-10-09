

## 使用交叉验证增强模型评估

K折交叉验证对于获得模型性能的可靠估计至关重要，尤其是在数据有限的情况下。通过将数据集划分为K个折，并在这些折上迭代执行训练和测试过程，该技术确保了每个数据点都被用于训练和验证。这种方法通过平均多个子集的性能来降低过拟合和欠拟合的风险，从而实现更均衡的评估。此外，K折交叉验证最大化了可用数据的使用，有助于超参数调整，并帮助解决诸如类别不平衡等问题，最终使模型在未见数据上具有更好的泛化能力。

要在原始代码中实现K折交叉验证，我们遵循以下步骤：

- **步骤 1：导入 KFold**

```python
from sklearn.model_selection import KFold
```

此导入启用了 Scikit-Learn 中的 KFold 类，这是实现K折交叉验证所必需的。

- **步骤 2：定义折数**

```python
k_folds = 5
kfold = KFold(n_splits=k_folds, shuffle=True, random_state=42)
```

这设置了五折的K折交叉验证，在划分前对数据进行洗牌，并使用随机种子以确保可重复性。

- **步骤 3：遍历每个折**

```python
fold_results = []

for fold, (train_idx, test_idx) in enumerate(kfold.split(X_np)):
    logging.info(f"Training fold {fold + 1}/{k_folds}")

    X_train, X_test = X_np[train_idx], X_np[test_idx]
    y_train, y_test = y_np[train_idx], y_np[test_idx]

    # Convert to PyTorch datasets
    train_dataset = TensorDataset(
        torch.tensor(X_train),
        torch.tensor(y_train)
    )
    test_dataset = TensorDataset(
        torch.tensor(X_test),
        torch.tensor(y_test)
    )

    # Create DataLoaders
    train_loader = DataLoader(
        train_dataset,
        batch_size=64,
        shuffle=True
    )
    test_loader = DataLoader(
        test_dataset,
        batch_size=64,
        shuffle=False
    )

    # Initialize the model, criterion, and optimizer
    input_size = X_train.shape[1]
    output_size = 1
    model = DiabetesClassifierModel(input_size, output_size)
    criterion = nn.BCEWithLogitsLoss()
    optimizer = optim.Adam(model.parameters(), lr=0.01)

    # Train the model
    model_trainer = ModelTrainer(
        model,
        criterion,
        optimizer,
        train_loader
    )
    model_trainer.train()

    # Evaluate the model
    model_evaluator = ModelEvaluator(
        model,
        test_loader,
        y_test
    )
    results = model_evaluator.evaluate()

    # Append results to the fold_results list
    fold_results.append(results)
```

在这段代码中，K折交叉验证在主函数中实现。数据集首先经过预处理并转换为 NumPy 数组（X_np 用于特征，y_np 用于标签）。使用 Scikit-Learn 中的 KFold 类创建K折划分，其中 k_folds = 5，意味着数据集被划分为五个折。

在循环内部，使用K折划分确定训练和测试索引。然后将相应的数据划分为训练集和测试集。为训练数据和测试数据创建 PyTorch 数据集，然后将其加载到 DataLoaders 中，以便在模型训练期间促进批处理。

对于每个折，初始化模型，使用 ModelTrainer 类进行训练，并使用 ModelEvaluator 类进行评估。计算每个折的评估指标——如准确率、精确率、召回率、F1 分数和 ROC-AUC 分数——并将它们存储在列表中。

- **步骤 4：聚合各折的结果**

```python
avg_accuracy = np.mean([result['accuracy'] for result in fold_results])
avg_precision = np.mean([result['precision'] for result in fold_results])
avg_recall = np.mean([result['recall'] for result in fold_results])
avg_f1 = np.mean([result['f1'] for result in fold_results])
avg_roc_auc = np.mean([result['roc_auc'] for result in fold_results])

logging.info(f"Average Accuracy: {avg_accuracy:.4f}")
logging.info(f"Average Precision: {avg_precision:.4f}")
logging.info(f"Average Recall: {avg_recall:.4f}")
logging.info(f"Average F1 Score: {avg_f1:.4f}")
logging.info(f"Average ROC-AUC Score: {avg_roc_auc:.4f}")
```

在所有折处理完成后，对结果进行平均，以提供模型性能的更稳健的估计。然后记录这些平均性能，提供模型在不同数据子集上泛化能力的全面视图。K折交叉验证确保模型的评估不依赖于单一的训练-测试划分，从而提供对其能力更均衡、更准确的评估。

下表显示了K折交叉验证的结果：

| 折 | 准确率 | 精确率 | 召回率 | F1 分数 | ROC-AUC 分数 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 折 1 | 0.7586 | 0.5833 | 0.6512 | 0.6154 | 0.8347 |
| 折 2 | 0.7103 | 0.6774 | 0.3962 | 0.5000 | 0.7966 |
| 折 3 | 0.7586 | 0.6078 | 0.6739 | 0.6392 | 0.8048 |
| 折 4 | 0.8000 | 0.7826 | 0.6545 | 0.7129 | 0.8711 |
| 折 5 | 0.7569 | 0.7297 | 0.5192 | 0.6067 | 0.8242 |
| **平均值** | **0.7569** | **0.6762** | **0.5790** | **0.6148** | **0.8263** |

结果显示，模型在各折中表现一致，平均准确率为 75.69%，鉴于小型糖尿病数据集，这表明性能合理。其他指标——精确率、召回率、F1 分数和 ROC-AUC——也提供了关于模型预测能力的见解，其中 ROC-AUC 分数平均为 0.8263，表明具有良好的判别能力。

## 综合所有内容

在本节中，我们将本章中讨论的用于探索 Pima 糖尿病数据集以及构建、训练和评估 PyTorch 深度学习模型（带或不带K折交叉验证）的各个独立代码片段进行整合。

### 探索 Pima 糖尿病数据集

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import col, sum as pyspark_sum
import boto3

class PimaDatasetExplorer:
    """
    Class for exploring and analyzing a Pima Indian Diabetes
    dataset using PySpark.
    """
    
    def __init__(self, file_path):
        """
        Initializes the PimaDatasetExplorer object.
        
        Args:
            file_path (str): The path to the dataset file.
        """
        self.file_path = file_path
        self.data = None

    def load_data(self):
        """
        Loads the dataset from the specified file path into a PySpark DataFrame.
        """
        try:
            self.data = spark.read.csv(
                self.file_path,
                header=True,
                inferSchema=True
            )
            self.data.cache()
        except Exception as e:
            print(
                "An error occurred while loading the data:",
                str(e)
            )
            self.data = None

    def preprocess_data(self):
        """
        Performs preprocessing steps on the dataset.
        """
        self.load_data()

    def handle_missing_values(self):
        """
        Counts the number of missing values for each column
        in the dataset and displays the counts.
        """
        if self.data is not None:
            missing_counts = self.data.select([
                pyspark_sum(col(c).isNull()).cast("int").alias(c)
                for c in self.data.columns
            ])
            print("Missing Value Counts:")
            missing_counts.show()
```

