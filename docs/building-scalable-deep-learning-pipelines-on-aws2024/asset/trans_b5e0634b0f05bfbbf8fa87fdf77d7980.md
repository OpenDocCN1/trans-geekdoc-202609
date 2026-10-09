

```python
train_df, test_df = df.randomSplit([0.8, 0.2],
        seed=42)

train_features, train_labels = utils.spark_df_to_tensor(
        train_df
    )
test_features, test_labels = utils.spark_df_to_tensor(
        test_df
    )
train_loader = create_data_loader(
    train_features,
    train_labels,
    batch_size=batch_size
    )
test_loader = create_data_loader(
    test_features,
    test_labels,
    batch_size=batch_size
    )
input_size = train_features.shape[1]
output_size = 1
model = nn.Sequential(
    nn.Linear(input_size, 64),
    nn.ReLU(),
    nn.Linear(64, 32),
    nn.ReLU(),
    nn.Linear(32, 16),
    nn.ReLU(),
    nn.Linear(16, output_size)
)

criterion = nn.MSELoss()
optimizer = optim.Adam(
    model.parameters(),
    lr=learning_rate
)

train_model(
    model,
    train_loader,
    criterion,
    optimizer,
    num_epochs
)

evaluate_model(model, test_loader, criterion)

torch.save(model.state_dict(), 'trained_model.pth')

except FileNotFoundError:
    logger.error(f"Data file not found at {data_file_path}")

if __name__ == "__main__":
    data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(data_file_path)
```

## 第 8 章：使用 Apache Airflow 构建可扩展的深度学习管道

代码首先导入了 PyTorch 模块（`torch.optim`、`torch.nn`）、PySpark DataFrame（`pyspark.sql.DataFrame`）以及自定义模块（`data_processing`、`model_training`、`model_evaluation` 和 `utils`）。这些导入对于数据处理、模型训练和评估至关重要。随后，配置日志以显示 INFO 级别的消息，并初始化一个名为 `name` 的记录器。

在下一步中，模块定义了主函数。该函数接受几个参数，例如 `data_file_path`、`num_epochs`、`batch_size` 和 `learning_rate`。在此函数内部，执行以下步骤：

- 数据加载与预处理：该函数从由 `data_file_path` 指定的 CSV 文件加载数据，进行预处理，然后将其划分为训练集和测试集。
- 数据转换：使用自定义函数 `utils.spark_df_to_tensor` 将 Spark DataFrame 的特征和标签转换为 PyTorch 张量。
- 模型定义：使用 `nn.Sequential` 定义前馈神经网络模型。该模型由多个带有 ReLU 激活函数的线性层组成。
- 损失函数与优化器：使用均方误差（MSE）损失作为训练模型的准则，并采用 Adam 优化器来优化模型参数。
- 模型训练：调用 `train_model` 函数，使用训练数据加载器、准则、优化器和指定的迭代次数来训练模型。
- 模型评估：训练完成后，使用 `evaluate_model` 函数和测试数据加载器对训练好的模型进行评估。
- 模型保存：最后，将训练好的模型的状态字典保存到一个名为 `trained_model.pth` 的文件中。

最后，`__name__ == "__main__"` 块确保主函数仅在脚本直接运行时执行，而在作为模块导入到其他脚本中时不执行。它将 `data_file_path` 变量设置为特斯拉股票 CSV 文件的路径，并以该路径作为参数调用主函数。

为了运行代码，我们首先激活了“myenv”环境，然后导航到 EC2 实例上存储代码的目录“home/ubuntu/airflow/dags”，并执行“main.py”模块以编排特斯拉股价预测工作流：

```text
[In]: source activate myenv
[In]: cd home/ubuntu/airflow/dags
[In]: python3 main.py
```

代码的第一个输出是特斯拉股价预测模型训练过程中每个迭代周期的损失值：

| 迭代周期 (Epoch) | 损失 (Loss) |
|---|---|
| 1 | 49250.46 |
| 2 | 55661.49 |
| 3 | 24399.93 |
| 4 | 10579.51 |
| 5 | 2365.65 |
| 6 | 1972.29 |
| 7 | 1864.98 |
| 8 | 1288.25 |
| 9 | 736.96 |
| 10 | 625.62 |
| ... | ... |
| 100 | 9.70 |

以下是表中两列的解释：

- Epoch（迭代周期）：此列指示训练迭代周期的数量，即对整个训练数据集进行迭代的次数。
- Loss（损失）：此列表示每个迭代周期的训练损失。训练损失衡量模型预测值与训练数据中实际值之间的匹配程度。在训练初期，由于模型以随机的权重和偏置开始，并逐渐调整以最小化损失，因此损失值较高是预期之中的。

以下是训练损失随迭代周期变化的过程：

- 在初始迭代周期（例如第 1 和第 2 个周期），损失值极高（即 49,250 和 55,661），表明模型预测存在显著误差。这是训练开始时的预期现象，此时模型参数是随机初始化的。
- 随着训练的推进，损失值稳步下降。例如，到第 10 个迭代周期时，损失已降至 625.6，表明模型的预测值正在接近特斯拉的实际股价。

到第 100 个迭代周期时，训练损失已显著降低至 9.7，这表明模型很好地学习了训练数据中的模式。这种较低的训练损失表明模型在训练数据上的预测值与实际特斯拉股价紧密吻合。

第二个输出是测试损失和 R 平方值，如下所示：

| 指标 (Metric) | 数值 (Value) |
| :--- | :--- |
| 测试损失 (Test Loss) | 25.3015 |
| R 平方 (R-squared) | 0.9976 |

在此表中，我们提供了评估特斯拉股价预测模型性能的关键指标：

- 测试损失：此指标表示模型在独立测试数据集上进行预测时的误差。在特斯拉股价预测模型的背景下，25.3 的测试损失意味着，平均而言，模型的预测值与实际特斯拉股价偏差约为 25.3 美元。较低的测试损失值通常表明性能更好，因为这意味着模型的预测值更接近实际价格。
- R 平方得分：R 平方得分也称为决定系数，用于衡量模型预测值解释实际特斯拉股价方差的程度。0.9976 的 R 平方得分表明，模型解释了特斯拉股价约 99.76% 的变异性。换句话说，模型在预测特斯拉股价方面非常准确，因为它可以解释实际价格中观察到的大部分变异性。

训练损失的下降趋势表明，模型在训练迭代周期过程中已经学习并改进了其预测能力。测试损失和 R 平方指标表明，特斯拉股价预测模型表现优异，具有较低的测试损失和较高的 R 平方得分，这表明预测准确，且对特斯拉股价变异性的解释能力很强。

## 使用 Airflow DAG 进行特斯拉股价预测

现在，我们来到了本章的核心：将工作流编排为 Airflow DAG，而不是使用带有 `main()` 函数的独立脚本。在上一小节中，我们通过 `main()` 函数手动执行特斯拉股价预测代码，该函数编排了各种任务（预处理、模型训练和模型评估）的执行。当将代码集成到 Airflow DAG 中时，不再需要单独的 `main()` 函数以相同的方式编排任务。相反，任务被显式地定义为 Airflow DAG 的一部分，使用诸如 `PythonOperator` 或 `BashOperator` 等算子。每个算子对应一个特定任务，并使用 DAG 定义中的 `>>` 运算符指定任务之间的依赖关系。

为了演示如何将上一小节中的确切相同代码作为 DAG 运行，我们将按照以下步骤定义和编排 `tesla_stock_prediction` DAG：

- 导入：导入必要的库和模块。
- 默认参数：定义 DAG 的配置设置，如所有者、开始日期和重试次数。
- DAG 定义：创建具有唯一标识符、描述和其他设置的 DAG 对象。
- 预处理数据任务：定义执行 `preprocess_data_task` 函数以加载和预处理特斯拉股票数据的 `PythonOperator(preprocess_data_task)`。
- 训练模型任务：定义执行 `train_model_task` 函数以使用预处理数据训练深度学习回归模型的 `PythonOperator(train_model_task)`。
- 评估模型任务：定义执行 `evaluate_model_task` 函数以评估训练好模型的 `PythonOperator(evaluate_model_task)`。
- 任务依赖：使用 `>>` 运算符设置任务之间的依赖关系，指示任务应执行的顺序。

让我们一步步了解代码，从导入必要的模块开始：

### 步骤 1：导入

在此部分，我们导入工作流所需的各个库和模块：

512

