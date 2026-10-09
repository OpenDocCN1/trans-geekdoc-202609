

## 第 9 章 提高模型性能的技巧

```python
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

接下来，我们有 `convert_to_numpy` 方法，该方法通过从 Spark DataFrame 中提取并收集缩放后的特征和标签到 NumPy 数组，从而将 Spark DataFrame 转换为 NumPy 数组：

```python
def convert_to_numpy(self, train_df, test_df):
    """
    将 Spark DataFrame 转换为 numpy 数组。

    参数:
        - train_df (DataFrame):
            包含训练数据的 Spark DataFrame。
        - test_df (DataFrame):
            包含测试数据的 Spark DataFrame。

    返回:
        - tuple:
            包含特征和标签的
            训练集和测试集 numpy
            数组的元组。
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
    return (train_features,
        train_labels,
        test_features,
        test_labels
    )
```

过渡到下一个方法，我们有 `create_and_train_model` 方法，该方法用于创建并训练神经网络模型：

- 定义一个具有多个全连接层（Dense layers）的顺序神经网络模型
- 使用 Adam 优化器和均方误差（Mean Squared Error）损失函数编译模型
- 在训练数据上训练模型

```python
def create_and_train_model(
    self,
    train_features,
    train_labels,
    epochs=100,
    batch_size=32
):    
    """
    创建并训练神经网络模型。

    参数:
    - train_features (ndarray): 训练特征。
    - train_labels (ndarray): 训练标签。
    - epochs (int): 训练的轮数。
    - batch_size (int): 训练的批量大小。

    返回:
    - History:
    包含每个
    轮次的损失值的
    训练历史记录。
    """
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
        Dense(
            64,
            activation='relu',
            input_shape=self.input_shape
        ),
        Dense(
            32,
            activation='relu'
        ),
        Dense(
            16,
            activation='relu'
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```

继续进入下一步，我们有 `evaluate_model` 方法。该方法通过使用模型的 `evaluate` 方法计算测试损失，从而在测试数据上评估训练好的模型：

```python
def evaluate_model(self, test_features, test_labels):
    """
    评估训练好的模型。

    参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

    返回:
        - float: 测试损失。
    """
    test_loss = self.model.evaluate(
        test_features,
        test_labels
    )
    return test_loss
```

继续下一个方法，我们有 `predict_and_evaluate` 方法，该方法通过以下方式在测试数据上预测特斯拉（Tesla）股价并评估模型：

- 对测试特征进行预测
- 计算 R2 分数以评估模型的性能

```python
def predict_and_evaluate(
        self,
        test_features,
        test_labels
    ):
    """
    预测并评估神经网络模型。

    参数:
        - test_features (ndarray): 测试特征。
        - test_labels (ndarray): 测试标签。

    返回:
        - float: R2 分数。
    """
    test_predictions = self.model.predict(test_features)
    r2_score_value = r2_score(test_labels, test_predictions)
    return r2_score_value
```

在下一步中，我们过渡到主函数，该函数协调整个工作流。该函数位于 `TSLARegressor` 类之外，它实例化一个 `TSLARegressor` 对象，然后调用方法来预处理数据、将数据转换为 NumPy 数组、创建并训练模型，以及评估模型。它还记录测试损失和 R2 分数，并使用 Matplotlib 绘制每轮的训练损失：

```python
def main(file_path):
    """
    协调整个工作流的主函数。

    参数:
        - file_path (str): CSV 文件的路径。

    返回:
        - None
    """
    try:
        tsla_regressor = TSLARegressor()
        train_df, test_df = tsla_regressor.preprocess_data(
            file_path
        )
        train_features, train_labels, test_features, \
        test_labels = tsla_regressor.convert_to_numpy(
            train_df,
            test_df
        )
        history = tsla_regressor.create_and_train_model(
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

        plt.plot(history.history['loss'])
        plt.title('Model Loss')
        plt.xlabel('Epoch')
        plt.ylabel('Loss')

        plt.show()

    except Exception as e:
        logging.error(f"An error occurred: {e}")
```

在最后一步，我们有主函数，它作为脚本工作流的入口点：

```python
if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO)
    file_path = "/home/ubuntu/airflow/dags/TSLA_stock.csv"
    main(file_path)
```

该函数配置日志级别为 INFO，定义 CSV 数据的文件路径，并在脚本作为主模块执行时，使用文件路径调用 main 函数。

函数的执行流程如下：

- 数据预处理：读取并处理 CSV 数据，缩放特征，并将其拆分为训练集和测试集
- 数据转换：将 Spark DataFrame 转换为 NumPy 数组，以便与 TensorFlow 兼容
- 模型训练：创建神经网络模型，在训练数据上训练它，并记录训练损失
- 模型评估：在测试数据上评估训练好的模型，并计算 R2 分数
- 日志记录和绘图：记录评估指标并绘制训练损失

要使用 Python 3 从 `/home/ubuntu/airflow/dags` 目录运行脚本，并考虑到名为 `myenv` 的虚拟环境，我们遵循了以下步骤：

激活名为 `myenv` 的虚拟环境：

```bash
source /path/to/myenv/bin/activate
```

更改目录到 `/home/ubuntu/airflow/dags`：

```bash
cd /home/ubuntu/airflow/dags
```

使用 Python 3 运行脚本，指定脚本名称 `predict_tsla_stock.py`：

```bash
python3 predict_tsla_stock.py
```

此命令使用 Python 3 从 `/home/ubuntu/airflow/dags` 目录执行 `predict_tsla_stock.py` 脚本。

代码作为整个 TSLA 股价回归工作流的一部分，产生两个主要输出。第一个输出是评估指标（测试损失和 R2 分数），使用 `logging.info` 方法打印：

```python
logging.info("Test Loss: {}".format(test_loss))
logging.info("R2 Score: {}".format(r2_score_value))
```

以下是输出：

```text
Test Loss: 15.5924
R2 Score: 0.9987
```

测试损失使用 `evaluate_model` 方法计算并记录：

```python
test_loss = tsla_regressor.evaluate_model(
    test_features, test_labels
)
```

R2 分数使用 `predict_and_evaluate` 方法计算并记录：

```python
r2_score_value = tsla_regressor.predict_and_evaluate(
    test_features, test_labels
)
```

相对较低的测试损失（15.5924）和非常高的 R2 分数（0.9987）的组合表明模型在测试数据上表现非常出色。低测试损失表明预测值接近实际值，而高 R2 分数表明模型解释了数据中几乎所有的变异性。

