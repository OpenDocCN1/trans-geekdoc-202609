

## 代码实现

```python
y_train,
epochs=100,
lr=0.01
):
    """Trains the TensorFlow (Keras) model."""
    try:
        model = Sequential([
            Dense(64, input_dim=X_train.shape[1]),
            ReLU(),
            Dense(32),
            ReLU(),
            Dense(16),
            ReLU(),
            Dense(1, activation='sigmoid')
        ])
        optimizer = SGD(learning_rate=lr)
        model.compile(loss='binary_crossentropy',
                      optimizer=optimizer,
                      metrics=['accuracy'])
        custom_callback = CustomCallback()
        model.fit(
            X_train,
            y_train,
            epochs=epochs,
            verbose=0,
            callbacks=[custom_callback]
        )
        logger.info("Model training completed.")
        return model
    except Exception as e:
        logger.error(
            f"Error occured during "
            f"model training: {str(e)}"
        )
```

在这段代码中：

- 文档字符串 `"""Class for training the TensorFlow (Keras) model."""` 简要说明了该类的用途。
- 在该类内部，有一个静态方法 `train_tensorflow_model(X_train, y_train, epochs=100, lr=0.01)`，负责训练 TensorFlow (Keras) 模型。该方法接受四个参数：`X_train`（用于训练的输入特征）、`y_train`（用于训练的目标标签）、`epochs`（训练的轮数，默认值为 100）以及 `lr`（优化器的学习率，默认值为 0.01）。使用 `@staticmethod` 装饰器将该方法声明为静态方法，表明它不需要访问实例或其属性，可以直接在类上调用，而无需创建 `DiabetesModelTrainer` 的实例。
- 在方法内部，使用 Keras 的 Sequential API 定义了一个神经网络模型。该模型由几个全连接（Dense）层组成，这些层使用整流线性单元（ReLU）激活函数，最后以一个使用 sigmoid 激活函数的输出层结尾。
- 配置了一个优化器（具有指定学习率的随机梯度下降），并使用二元交叉熵损失函数和准确率作为评估指标来编译模型。
- 实例化了一个自定义回调（`CustomCallback`），以便在模型训练期间记录信息。
- 对模型对象调用 fit 方法，使用输入特征（`X_train`）和目标标签（`y_train`）训练指定轮数的模型。将 `custom_callback` 传递给 `callbacks` 参数，以启用训练过程中轮次信息的记录。
- 模型训练成功完成后，会生成一条日志消息，表明模型训练已完成，并返回训练好的模型。
- 使用 try-except 块实现错误处理，以捕获模型训练过程中可能发生的任何异常。如果发生异常，则使用 `logger.error()` 记录错误消息。这确保了在模型训练过程中遇到的任何问题都能得到适当处理并记录在案，以便用于调试。

## 步骤 6：模型评估

在此步骤中，我们定义 `DiabetesModelEvaluator` 类，它负责评估用于糖尿病预测训练的 TensorFlow (Keras) 模型。它包含使用各种评估指标（如准确率、精确率、召回率和 F1 分数）来评估模型性能的方法：

```python
class DiabetesModelEvaluator:
    """Class for evaluating the TensorFlow (Keras)
    model."""
    @staticmethod
    def evaluate_model(model, X_test, y_test):
        """Evaluates the TensorFlow (Keras) model."""
        try:
            y_pred = (model.predict(X_test) > 0.5).astype(int)
            accuracy = accuracy_score(y_test, y_pred)
            precision = precision_score(y_test, y_pred)
            recall = recall_score(y_test, y_pred)
            f1 = f1_score(y_test, y_pred)
            logger.info(f"Accuracy: {accuracy:.4f}")
            logger.info(f"Precision: {precision:.4f}")
            logger.info(f"Recall: {recall:.4f}")
            logger.info(f"F1 Score: {f1:.4f}")
        except Exception as e:
            logger.error(
                f"Error occurred during model "
                f"evaluation: {str(e)}"
            )
```

让我们更仔细地看看这段代码：

- 文档字符串 `"""Class for evaluating the TensorFlow (Keras) model."""` 简要说明了该类的用途。
- 在该类内部，有一个静态方法 `evaluate_model(model, X_test, y_test)`，用于评估 TensorFlow (Keras) 模型的性能。该方法接受三个参数：`model`（训练好的 Keras 模型）、`X_test`（用于测试的输入特征）和 `y_test`（用于测试的真实标签）。使用 `@staticmethod` 装饰器将该方法声明为静态方法，表明它不需要访问实例或其属性，可以直接在类上调用，而无需创建 `DiabetesModelEvaluator` 的实例。
- 在方法内部，使用训练好的模型（`model.predict(X_test)`）生成预测值，并通过阈值处理获得二分类预测。使用 Scikit-Learn 的指标函数（分别为 `accuracy_score`、`precision_score`、`recall_score` 和 `f1_score`）计算准确率、精确率、召回率和 F1 分数等多个评估指标。
- 使用 `logger` 在信息级别记录包括准确率、精确率、召回率和 F1 分数在内的评估结果，以提供模型性能的见解。
- 使用 try–except 块实现错误处理，以捕获评估过程中可能发生的任何异常。如果发生异常，则使用 `logger.error()` 记录错误消息。这确保了在模型评估过程中遇到的任何问题都能得到适当处理并记录在案，以便用于调试。

## 步骤 7：主函数

在此最终步骤中，我们定义主函数，确保以下代码仅在脚本直接运行时执行，而在作为模块导入到其他脚本时不执行：

```python
if __name__ == "__main__":

    try:
        spark = (SparkSession.builder
                 .appName("DiabetesClassification")
                 .config("spark.executor.instances", "4")
                 .config("spark.executor.memory", "4g")
                 .config("spark.executor.cores", "2")
                 .config("spark.driver.memory", "2g")
                 .getOrCreate())
        
        data_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
        
        train_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_train.parquet"
        
        test_parquet_path = \
            "/home/ubuntu/airflow/dags/diabetes_test.parquet"
        
        DiabetesProcessor.preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
        )
        
        train_diabetes_df = spark.read.parquet(train_parquet_path)
        
        X_train = np.array(train_diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect())
        y_train = np.array(train_diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect())

        trained_model = DiabetesModelTrainer.train_tensorflow_model(X_train, y_train)

        test_diabetes_df = spark.read.parquet(test_parquet_path)
        X_test = np.array(test_diabetes_df.select("scaled_features").rdd.flatMap(lambda x: x).collect())
        y_test = np.array(test_diabetes_df.select("Outcome").rdd.flatMap(lambda x: x).collect())

        DiabetesModelEvaluator.evaluate_model(trained_model, X_test, y_test)

    except Exception as e:
        logger.error(f"An error occurred: {str(e)}")
```

以下是此代码的说明：

- `if __name__ == "__main__":` 块是 Python 脚本的入口点。它确保以下代码仅在脚本直接运行时执行，而在作为模块导入到其他脚本时不执行。
- 在 try 块内部，执行若干步骤以预处理糖尿病数据、训练 TensorFlow (Keras) 模型并评估其性能。这些步骤被包裹在 try–except 块中，以处理任何潜在的异常。
- 首先，使用 `SparkSession.builder` API 创建一个 SparkSession。SparkSession 是 Spark 功能的入口点，允许脚本与 Spark 交互并执行分布式数据处理。
- SparkSession 配置了各种属性，如应用程序名称（`appName`）、执行器实例数量（`spark.executor.instances`）、执行器内存（`spark.executor.memory`）、执行器核心数（`spark.executor.cores`）和驱动器内存（`spark.driver.memory`）。这些配置可优化数据处理任务的资源分配。
- 定义了输入糖尿病数据文件（`data_file_path`）、预处理训练数据 Parquet 文件（`train_parquet_path`）和预处理测试数据 Parquet 文件（`test_parquet_path`）的路径。
- 调用 `DiabetesProcessor.preprocess_data()` 方法，使用 PySpark 预处理糖尿病数据。该方法从 CSV 文件中读取原始糖尿病数据，并应用数据清洗和特征工程

