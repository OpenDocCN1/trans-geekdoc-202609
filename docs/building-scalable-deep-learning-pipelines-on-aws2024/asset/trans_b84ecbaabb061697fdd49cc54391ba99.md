

```python
logger.error(
    f"Error occurred during data preprocessing: "
    f"{str(e)}"
)
```

```python
[In]: class DiabetesHyperModel(HyperModel):
    """用于调优 Keras 模型的 HyperModel。"""
    def build(self, hp):
        model = Sequential()
        model.add(
            Dense(
                units=hp.Int('units_1',
                             min_value=32,
                             max_value=128,
                             step=32
                             ),
                input_dim=X_train.shape[1]
                )
        )
        model.add(ReLU())
        model.add(
            Dense(
                units=hp.Int(
                    'units_2',
                    min_value=16,
                    max_value=64,
                    step=16
                    )
            )
        )
        model.add(ReLU())
        model.add(
            Dense(
                units=hp.Int(
                    'units_3',
                    min_value=8,
                    max_value=32,
                    step=8
                )
            )
        )
        model.add(ReLU())
        model.add(Dense(1, activation='sigmoid'))
        optimizer = SGD(
            learning_rate=hp.Float(
                'lr',
                1e-4,
                1e-2,
                sampling='log'
            )
        )
        model.compile(loss='binary_crossentropy', optimizer=optimizer, metrics=['accuracy'])
        return model
```

```python
[In]: class DiabetesModelTrainer:
    """用于训练 TensorFlow (Keras) 模型的类。"""
    @staticmethod
    def train_tensorflow_model(
        X_train,
        y_train,
        X_test,
        y_test,
        epochs=50
    ):
        """使用 keras_tuner 训练 TensorFlow (Keras) 模型。"""
        try:
            tuner = RandomSearch(
                DiabetesHyperModel(),
                objective='val_accuracy',
                max_trials=5,
                executions_per_trial=3,
                directory='tuner_dir',
                project_name='diabetes_tuning'
            )
            tuner.search(
                X_train,
                y_train,
                epochs=epochs,
                validation_data=(X_test, y_test),
                verbose=1
            )
            best_model = tuner.get_best_models(num_models=1)[0]
            logger.info("最佳模型训练完成。")
            return best_model
        except Exception as e:
            logger.error(
                f"模型训练过程中发生错误: "
                f"{str(e)}"
            )
```

```python
[In]: class DiabetesModelEvaluator:
    """用于评估 TensorFlow (Keras) 模型的类。"""
    @staticmethod
    def evaluate_model(model, X_test, y_test):
        """评估 TensorFlow (Keras) 模型。"""
        try:
            y_pred = (model.predict(X_test) > 0.5).astype(int)
            accuracy = accuracy_score(y_test, y_pred)
            precision = precision_score(y_test, y_pred)
            recall = recall_score(y_test, y_pred)
            f1 = f1_score(y_test, y_pred)
            logger.info(f"准确率: {accuracy:.4f}")
            logger.info(f"精确率: {precision:.4f}")
            logger.info(f"召回率: {recall:.4f}")
            logger.info(f"F1 分数: {f1:.4f}")
        except Exception as e:
            logger.error(
                f"模型评估过程中发生错误: "
                f"{str(e)}"
            )
```

```python
[In]: if __name__ == "__main__":
    try:
        spark = (
            SparkSession.builder
            .appName(
                "DiabetesProcessingAndTensorFlowTraining"
            )
            .config("spark.executor.instances", "4")
            .config("spark.executor.memory", "4g")
            .config("spark.executor.cores", "2")
            .config("spark.driver.memory", "2g")
            .getOrCreate()
        )

        data_file_path = "/home/ubuntu/airflow/dags/diabetes.csv"
        train_parquet_path = ("/home/ubuntu/airflow/dags/diabetes_train.parquet")
        test_parquet_path = ("/home/ubuntu/airflow/dags/diabetes_test.parquet")

        DiabetesProcessor.preprocess_data(
            spark,
            data_file_path,
            train_parquet_path,
            test_parquet_path
        )

        train_diabetes_df = spark.read.parquet(
            train_parquet_path
        )
        X_train = np.array(
            train_diabetes_df
            .select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )
        y_train = np.array(
            train_diabetes_df
            .select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        test_diabetes_df = spark.read.parquet(
            test_parquet_path
        )
        X_test = np.array(
            test_diabetes_df
            .select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )
        y_test = np.array(
            test_diabetes_df
            .select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        best_model = DiabetesModelTrainer.train_tensorflow_model(
            X_train,
            y_train,
            X_test,
            y_test
        )

        DiabetesModelEvaluator.evaluate_model(
            best_model,
            X_test,
            y_test
        )

    except Exception as e:
        logger.error(f"发生错误: {str(e)}")
```

## 摘要

在本章中，我们继续探索深度学习分类的话题，继上一章使用 PyTorch 之后，这次我们使用了 TensorFlow。我们演示了如何复制在 PyTorch 中使用的相同步骤，包括数据加载、预处理、定义模型架构、训练和评估。此外，我们还整合了额外的功能，例如将数据从 S3 存储桶复制到 EC2 本地目录进行处理，展示了与 AWS 服务的集成，并在整个建模过程中处理错误和日志消息，用于调试和监控。

为了实现两个模型性能的公平比较，我们使用了与 PyTorch 相同的皮马（Pima）糖尿病数据集。主要结论是，两个模型（PyTorch 和 TensorFlow）的性能相当。

我们还介绍了使用 keras_tuner 进行超参数调优，这有助于提高 TensorFlow 模型的性能。通过自动搜索最佳配置，我们获得了比手动选择超参数更好的结果。

在下一章中，我们将转向另一个同样重要的话题：如何使用 Apache Airflow 简化 AWS 上的管道流程。

# 第 8 章

## 使用 Apache Airflow 构建可扩展的深度学习管道

在前几章中，我们构建了可扩展的深度学习管道，并在 AWS EC2 实例上手动执行它们。虽然这种非自动化的方法在行业中很常见，但它并不总是最高效的。一方面，它缺乏对工作流状态和进度的可见性，需要单独实现监控和日志记录。另一方面，在修改或扩展工作流时也可能带来挑战。确实，如果没有专门的编排框架，将工作流扩展以管理大量数据或计算资源可能是令人生畏的。此外，如果没有标准化的方法，确保实验的可重复性变得具有挑战性，主要依赖于版本控制和文档。

采用 Apache Airflow 运行工作流可以有效解决这些问题。它促进了基于预定义时间表或触发的自动化执行，最大限度地减少了手动干预的需求。此外，它开箱即用地提供了全面的监控和日志记录功能使用户能够轻松跟踪工作流进度并排查出现的问题。当你在 Airflow 中运行 DAG（有向无环图）时，你可以确保任务根据其依赖关系以正确的顺序执行。Airflow 专门设计用于随着工作流的规模和复杂性的增长而扩展，有效地管理大量数据和计算资源。此外，它通过将工作流封装为代码、促进版本控制，并使团队成员能够分享以进行实验复现和随时间跟踪变更，从而促进可重复性。

在本章中，我们将演示如何使用 Apache Airflow 构建可扩展的数据处理管道。我们将创建完整的 AWS 工作流，包括使用 PySpark 预处理数据，使用 PyTorch 和 TensorFlow 开发深度学习模型，以及使用 Airflow 运行代码。更具体地说，我们将分别使用第 4 章和第 7 章中的特斯拉股票和糖尿病数据集，以及那些章节中的独立回归和分类脚本。这将允许我们演示如何通常运行 Python 脚本，并将其与作为 Apache Airflow DAG 更高效地执行进行对比。

我们将首先创建一个用于使用 PySpark 和 PyTorch 预测特斯拉股价的 Apache Airflow 管道，然后继续对使用 PySpark 和 TensorFlow 进行糖尿病分类执行相同的操作。

### 用于特斯拉股价预测的 Airflow 管道

在本节中，我们演示如何使用 Apache Airflow 构建可扩展的数据处理工作流。我们将创建一个 AWS 管道，包括使用 PySpark 预处理数据，使用 PyTorch 开发深度学习模型，以及使用 Airflow 运行代码。

为了实现这一点，我们将使用与第 4 章相同的特斯拉数据集。代码也将与该章节保持一致，主要区别在于本章采用更模块化的方法。一个模块化的

