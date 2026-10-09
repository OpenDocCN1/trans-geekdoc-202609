
learning_rate（float）：优化器的学习率。默认值为 0.001。

num_workers（int）：用于数据加载的子进程数量。默认值为 4。

Raises: 引发 FileNotFoundError：如果找不到指定的数据文件。

```python
"""
try:
    subprocess.run([
        "aws", "s3", "cp",
        "s3://instance1bucket/TSLA_stock.csv",
        "/home/ubuntu/airflow/dags/"
    ])
    
    df = load_data(data_file_path)
    df = preprocess_data(df)
    
    train_df, test_df = df.randomSplit([0.8, 0.2], seed=42)
    
    train_features, train_labels = \
        spark_df_to_tensor(train_df)
    test_features, test_labels = spark_df_to_tensor(test_df)
    
    train_loader = create_data_loader(
        train_features,
        train_labels,
        batch_size=batch_size,
        num_workers=num_workers
    )
    
    test_loader = create_data_loader(
        test_features,
        test_labels,
        batch_size=batch_size,
        num_workers=num_workers
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
```

让我们来探讨该函数的作用，并将其分解为单独的操作，包括数据加载、预处理、模型初始化、训练、保存和评估：

- 主函数协调特斯拉股价预测的整个过程，从数据加载到模型评估。它充当机器学习流水线的中央协调者。
- 主函数首先使用 `subprocess.run` 方法从 AWS S3 存储桶将数据复制到 EC2 上的本地目录。这是数据加载的前置步骤。接下来，它使用 `load_data` 函数从 CSV 文件中加载特斯拉股价数据，并将文件路径作为参数传入。
- 在数据加载之后，主函数使用 PyTorch 初始化神经网络模型。它定义了模型架构，指定输入特征的数量（从数据集中动态推断）以及输出大小（固定为 1，用于预测单个值（即股价））。此外，模型包含三个隐藏层，分别包含 64、32 和 16 个神经元，每个层后面都跟随一个整流线性单元（ReLU）激活函数。
- 初始化完成后，主函数使用 `train_model` 函数开始训练模型。它指定了诸如 epoch 数、批次大小、学习率、损失函数和优化器等参数。在训练过程中，模型参数会根据训练数据迭代更新，以最小化损失函数。
- 训练完成后，主函数使用 `torch.save` 方法将训练好的模型参数保存到文件中。这使得模型可以重复使用或部署以对新数据进行预测，而无需重新训练。
- 随后，主函数使用 `evaluate_model` 函数在测试数据上评估训练好的模型的性能。它计算测试损失和 R-squared 分数等指标，以评估模型在未见数据上的泛化能力。
- 主函数包含错误处理机制，例如使用 `try-except` 块捕获数据加载期间未找到文件的错误。这确保了代码能够处理意外问题，并提供有用的错误信息以便调试。

通过在 main 函数中封装这些阶段，代码实现了模块化和结构化的设计，使其更容易理解和维护。主函数作为中央协调者，整合了机器学习流水线的不同组件，以完成特斯拉股价预测的任务。在第 8 章中，我们将通过部署代码通过 Apache Airflow 来探索对此流程的进一步增强。

### 步骤 9：辅助函数 (spark_df_to_tensor)

在这一步中，我们创建 **spark_df_to_tensor** 辅助函数，它将 Spark DataFrame 列转换为 PyTorch 张量：

```python
[In]: def spark_df_to_tensor(
        df: DataFrame
    ) -> Tuple[torch.Tensor, torch.Tensor]:
        """
        Converts Spark DataFrame columns to PyTorch tensors.
        """
        features = torch.tensor(
            np.array(
                df.rdd.map(lambda x: x.scaled_features.toArray())
                .collect()
            ),
            dtype=torch.float32
        )
        labels = torch.tensor(
            np.array(
                df.rdd.map(lambda x: x.Close).collect()
            ),
            dtype=torch.float32)
        return features, labels
```

**spark_df_to_tensor** 函数用于将 Spark DataFrame 列转换为 PyTorch 张量。这种转换是必要的，因为 PyTorch 张量是在神经网络模型中表示和操作数据的主要数据结构。

该函数接受一个包含预处理特征和标签的 Spark DataFrame 作为输入。它从 DataFrame 中提取特征向量和标签，并使用 DataFrame 的 RDD（弹性分布式数据集）的 **collect** 方法将它们转换为 NumPy 数组。

然后，使用 torch.tensor 构造函数将这些 NumPy 数组转换为 PyTorch 张量，该构造函数可以从类数组对象创建张量。最后，该函数以元组形式返回特征张量和标签张量，准备好作为训练或评估神经网络模型的输入。

关于 spark_df_to_tensor 函数的实现细节：

- 在函数内部，通过使用 lambda 函数将每一行映射到其对应的特征向量数组，从 DataFrame 中提取特征向量。
- 使用 `toArray()` 方法将 Spark 向量列转换为 NumPy 数组。
- 同样，使用 `collect` 方法从 DataFrame 中提取标签并转换为 NumPy 数组。
- 然后，使用 `torch.tensor` 构造函数将特征数组和标签数组转换为 PyTorch 张量。
- 最后，以元组形式返回特征张量和标签张量。

通过提供将 Spark DataFrame 列转换为 PyTorch 张量的便捷接口，spark_df_to_tensor 函数促进了基于 PySpark 的数据处理流水线与基于 PyTorch 的机器学习模型的集成。这使得数据可以在数据预处理阶段（使用 PySpark 执行）和模型训练/评估阶段（使用 PyTorch 执行）之间流动，而无需手动转换或兼容性问题。此外，将数据转换为张量确保了与 PyTorch 基于张量的操作和自动微分功能的兼容性，这对于训练神经网络模型至关重要。最后，这种将 Spark DataFrame 列转换为 PyTorch 张量的机制简化了数据处理工作流，并支持在大规模数据集上高效训练和评估神经网络模型。

# 步骤 10：执行

此步骤中的代码通常位于脚本末尾，作为直接运行脚本时执行代码的入口点。它调用 main 函数，并传入指定的数据文件路径作为参数，启动使用 PyTorch 机器学习技术进行特斯拉股价预测的整个过程：

```python
[In]: if __name__ == "__main__":
        data_file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
        main(data_file_path)
```

在第 8 章中，我们展示了如何使用 Apache Airflow 优化此代码部署过程，Apache Airflow 是一个强大的工作流管理平台。我们强调了 Airflow 高级的任务调度和编排能力，这些能力消除了对传统 main 函数的需求。相反，我们利用 Airflow 的有向无环图（DAG）方法，其中每个节点代表数据管道中的特定任务。Airflow 自动化任务依赖关系，支持并行执行，促进重试，并提供全面的监控和日志记录功能。这增强了可扩展性并提高了运营效率，为简化和自动化的管道铺平了道路。

为了运行代码，我们将文件保存为 "tesla_stock_price_prediction.py"，并在 JupyterLab 终端中执行（或者我们也可以直接在 EC2 实例上运行）。由于我们创建了一个名为 "myenv" 的环境，因此按以下方式激活它：

```bash
[In]: source /home/ubuntu/myenv/bin/activate
```

