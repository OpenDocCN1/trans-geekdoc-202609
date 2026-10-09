`

```python
返回：
    - tuple: 包含训练集和测试集 DataFrame 的元组。
"""
df = self.spark.read.csv(
        file_path,
        header=True,
        inferSchema=True
)
 assembler = VectorAssembler(
        inputCols=feature_cols,
        outputCol='features'
)
df = assembler.transform(df)
scaler = StandardScaler(
        inputCol='features',
        outputCol='scaled_features',
        withMean=True,
        withStd=True
)
scaler_model = scaler.fit(df)
df = scaler_model.transform(df)
train_df, test_df = df.randomSplit(
        [train_ratio, 1-train_ratio],
        seed=seed
)
return train_df, test_df
```

```python
[In]: def convert_to_numpy(self, train_df, test_df):
"""
将 Spark DataFrame 转换为 numpy 数组。

参数：
    - train_df (DataFrame):
        包含训练数据的 Spark DataFrame。
    - test_df (DataFrame):
        包含测试数据的 Spark DataFrame。

返回：
    - tuple:
        包含训练集和测试集的 numpy 数组，
        对应于
        特征和标签。
"""
train_features = np.array(
    train_df.select('scaled_features')
    .rdd.map(lambda x: x.scaled_features.toArray())
    .collect()
)
train_labels = np.array(
    train_df.select('Close')
    .rdd.map(lambda x: x.Close).collect()
)
test_features = np.array(
    test_df.select('scaled_features')
    .rdd.map(lambda x: x.scaled_features.toArray())
    .collect()
)
test_labels = np.array(
    test_df.select('Close')
    .rdd.map(lambda x: x.Close).collect()
)
return train_features, train_labels, \
test_features, test_labels
```

```python
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
        """
        创建并训练神经网络模型。

        参数：
        - train_features (ndarray): 训练特征。
        - train_labels (ndarray): 训练标签。
        - epochs (int): 训练的 epoch 数量。
        - batch_size (int): 训练的批次大小。

        返回：
        - None
        """

        self.input_shape = (train_features.shape[1],)
        self.model = Sequential([
            Dense(64, activation='relu',
                  input_shape=self.input_shape),
            Dense(32, activation='relu'),
            Dense(16, activation='relu'),
            Dense(1)
        ])
        self.model.compile(optimizer='adam', loss='mse')
        self.model.fit(
            train_features,
            train_labels,
            epochs=epochs,
                batch_size=batch_size
            )
```

```python
[In]: def evaluate_model(self, test_features, test_labels):
            """
            评估训练好的模型。

            参数：
                - test_features (ndarray): 测试特征。
                - test_labels (ndarray): 测试标签。

            返回：
                - float: 测试损失值。
            """
            test_loss = self.model.evaluate(
                test_features,
                test_labels
            )
            return test_loss
```

```python
[In]: def predict_and_evaluate(self, test_features,
                                test_labels):
            """
            预测并评估神经网络模型。

            参数：
                - test_features (ndarray): 测试特征。
                - test_labels (ndarray): 测试标签。

            返回：
                - float: R2 分数。
            """
test_predictions = self.model.predict(
      test_features
)
r2_score_value = r2_score(
    test_labels,
    test_predictions
)
return r2_score_value
```

```python
In: def plot_actual_vs_predicted(
    tsla_regressor,
    test_features,
    test_labels
):
    """
    绘制实际值与预测值的对比图。

    参数：
      - tsla_regressor (TLSARegressor):
          TLSARegressor 类的实例。
      - test_features (ndarray): 测试特征。
      - test_labels (ndarray): 测试标签。

    返回：
      - None
    """

    test_predictions = tsla_regressor.model.predict(
        test_features
    )

    print("Actual    Predicted")
    for actual, predicted in zip(
test_labels, test_predictions
): 
    print(f"{actual:.2f}  {predicted[0]:.2f}")
plt.figure(figsize=(10, 6))
plt.scatter(test_labels, test_predictions,
            color='blue')
plt.plot(
    [test_labels.min(), test_labels.max()],
    [test_labels.min(), test_labels.max()],
    'k--', lw=3
)
plt.xlabel('Actual')
plt.ylabel('Predicted')
plt.title('Actual vs. Predicted Values')
plt.show()
```

```python
[In]: def main(file_path):
        """
        主函数，用于协调整个工作流。
        
        参数：
            - file_path (str): CSV 文件的路径。
            
        返回：
            - None
        """
        try:
            tsla_regressor = TLSARegressor()
            train_df, test_df = tsla_regressor.
                preprocess_data(
                file_path
                )
	train_features, train_labels, test_features, \
	test_labels = tsla_regressor.convert_to_numpy(
		train_df,
		test_df
	)
	tsla_regressor.create_and_train_model(
		train_features,
		train_labels
	)
	test_loss = tsla_regressor.evaluate_model(
		test_features,
		test_labels
	)
	r2_score_value = tsla_regressor.predict_and_evaluate(
		test_features,
		test_labels
	)

	logging.info("Test Loss: {}".format(test_loss))
	logging.info("R2 Score: {}".format(r2_score_value))

	plot_actual_vs_predicted(
		tsla_regressor,
		test_features,
		test_labels
	)

except Exception as e:
	logging.error(f"An error occurred: {e}")
```

```python
[In]: if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

## 摘要

在本章中，我们继续探索用于回归任务的深度学习模型。我们构建、训练并评估了一个 TensorFlow 深度学习模型，利用它来预测特斯拉的每日股价。虽然该深度学习回归模型并非旨在用于商业用途，但它展示了显著的性能，实现了超过 99% 的 R 平方值。这一性能与上一章使用 PyTorch 进行预测所获得的结果相当。

在下一章中，我们将把重点转向分类任务。我们将深入研究如何利用 PyTorch 对分类变量进行分类，这标志着我们在深度学习探索中的一个新阶段。

## 第 6 章

# 使用 PyTorch 进行深度学习的分类

在第 *4* 章和第 *5* 章中，我们探索了用于回归任务的深度学习。在本章和下一章中，我们将把重点转向分类，这是深度学习的另一个基本任务。回归和分类是两种不同类型的机器学习任务：回归旨在根据输入特征预测连续的数值，例如前面章节中演示的预测特斯拉股价。相比之下，分类则涉及将输入数据分配到预定义类别或类中。本章的目标是根据诸如怀孕次数、血糖水平、血压、身体质量指数（BMI）、年龄以及糖尿病家族史（也称为糖尿病遗传函数）等属性，预测一名女性被诊断为糖尿病的概率。

我们利用 Spark 进行数据预处理，以展示其在处理大型数据集时的分布式计算能力。虽然我们的数据集相对较小，但这些概念和代码适用于更大的数据集，这使得本练习在生产环境中具有很高的价值。小型数据集允许我们深入探讨诸如数据增强、迁移学习、重采样、模型复杂度、数据质量和数据表示等重要主题——这些都是深度学习的关键方面。

在开发本项目代码时，我们遵循了关键的建模步骤：数据预处理、模型定义、模型训练和模型评估。我们还 incorporated 了额外的功能，例如将数据从 S3 桶复制到 EC2 上的本地目录以进行处理，并在建模过程中处理错误和日志消息，以便于调试和监控。此外，我们使用 K 折交叉验证来评估模型，以确保我们的结论不依赖于单一的测试数据集。

本章首先检查糖尿病数据集，随后构建、训练和评估 PyTorch 分类模型。然后我们介绍 K 折交叉验证，整合本章中讨论的各个代码片段，最后以对关键要点的总结作为结束。

## 数据集

本项目使用的数据集是著名的 Pima 印第安人糖尿病数据集。Pima 指的是 Pima 人，他们是一群原产于美国西南部的原住民部落，主要居住在现在的亚利桑那州。

该数据集包含 768 条记录。每条记录代表一名 Pima 印第安女性，并包含各种与健康相关的属性，以及一个目标变量（结果），指示该女性是否患有糖尿病。该数据集适用于旨在根据明确定义的特征（如怀孕次数、血糖水平、血压、身体质量指数（BMI）、年龄以及糖尿病家族史（糖尿病遗传函数））预测糖尿病结果的分类任务。

`