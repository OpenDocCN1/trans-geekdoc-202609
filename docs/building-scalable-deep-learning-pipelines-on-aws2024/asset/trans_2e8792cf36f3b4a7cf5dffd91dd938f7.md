
## 模块 2：model_training.py

```python
train_diabetes_df = spark.read.parquet(train_parquet_file_path)

X_train = np.array(
    train_diabetes_df.select("scaled_features")
    .rdd.flatMap(lambda x: x)
    .collect()
)

y_train = np.array(
    train_diabetes_df.select("Outcome")
    .rdd.flatMap(lambda x: x)
    .collect()
)

model = Sequential()
model.add(Dense(
    64,
    input_dim=X_train.shape[1],
    activation='relu'
))
model.add(Dense(32, activation='relu'))
model.add(Dense(1, activation='sigmoid'))

optimizer = SGD(learning_rate=0.01)
model.compile(
    loss='binary_crossentropy',
    optimizer=optimizer,
    metrics=['accuracy']
)

custom_callback = CustomCallback()
model.fit(
    X_train,
    y_train,
    epochs=100,
    verbose=0,
    callbacks=[custom_callback]
)

model.save(model_save_path)

logger.info("Model training completed successfully.")
except Exception as e:
    logger.error(
        f"Error occurred during model training: {str(e)}"
    )
```

我们来拆解一下这段代码：

- **导入所需库**：该模块导入了必要的库，例如 NumPy、来自 PySpark 的 SparkSession，以及 TensorFlow 的各个组件，包括用于创建顺序模型的 Sequential、用于添加全连接层的 Dense、用于随机梯度下降优化的 SGD、用于创建自定义回调的 Callback，以及用于记录日志的 logging。
- **自定义回调**：定义了一个名为 CustomCallback 的自定义回调，它继承自 TensorFlow 的 Callback 类。此回调用于在训练过程中每个 epoch 结束时打印 epoch 信息。
- **train_tensorflow_model 函数**：此函数是训练 TensorFlow 模型的主入口点。它接受两个参数：
  - train_parquet_file_path：预处理后的 Parquet 格式训练数据的路径
  - model_save_path：保存训练好的 TensorFlow 模型的路径
- **SparkSession 设置**：创建一个名为 “TensorFlowTraining” 的 SparkSession。
- **加载数据**：将 Parquet 训练数据加载到名为 train_diabetes_df 的 PySpark DataFrame 中。
- **数据转换**：将 PySpark DataFrame 转换为 NumPy 数组（X_train 和 y_train），作为 TensorFlow 模型的输入和输出使用。
- **模型定义**：定义了一个包含三层的全连接顺序模型——两个带有 ReLU 激活函数的全连接层，以及一个带有 sigmoid 激活函数的全连接层。
- **模型编译**：使用二元交叉熵损失函数、指定学习率的 SGD 优化器以及准确率作为评估指标来编译模型。
- **回调设置**：创建之前定义的自定义回调实例（custom_callback）。
- **模型训练**：使用自定义回调打印 epoch 信息，将模型拟合到训练数据上，训练 100 个 epoch。
- **模型保存**：将训练好的模型保存到指定路径。
- **日志记录**：记录一条消息，指示模型训练成功完成。如果在训练过程中发生任何异常，则记录包含异常详情的错误消息。

### 模块 3：model_evaluation.py

该模块负责使用预处理后的测试数据评估 TensorFlow 分类模型的性能：

```python
import numpy as np
from pyspark.sql import SparkSession
from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score
from tensorflow.keras.models import load_model
import logging

logger = logging.getLogger(__name__)

def evaluate_model(
    test_parquet_file_path,
    model_load_path
):
    """
    Evaluate a TensorFlow model.
    
    Args:
        test_parquet_file_path (str):
            Path to the preprocessed testing data.
        model_load_path (str):
            Path to load the trained model.
    """
    try:
        spark = SparkSession.builder \
                .appName("ModelEvaluation") \
                .getOrCreate()

        model = load_model(model_load_path)

        test_diabetes_df = spark.read.parquet(
            test_parquet_file_path
        )

        X_test = np.array(
            test_diabetes_df.select("scaled_features")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

        y_test = np.array(
            test_diabetes_df.select("Outcome")
            .rdd.flatMap(lambda x: x)
            .collect()
        )

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
            f"Error occurred during model evaluation: {str(e)}"
        )
```

我们来拆解一下这段代码：

- **导入所需库**：该模块导入了必要的库，例如 NumPy、来自 PySpark 的 SparkSession、来自 sklearn.metrics 的各种评估指标、来自 TensorFlow 的 load_model 以及 logging。
- **evaluate_model 函数**：此函数是评估 TensorFlow 模型的主入口点。它接受两个参数：
  - test_parquet_file_path：预处理后的 Parquet 格式测试数据的路径
  - model_load_path：加载训练好的 TensorFlow 模型的路径
- **SparkSession 设置**：创建一个名为 “ModelEvaluation” 的 SparkSession。
- **加载模型**：使用 load_model 从指定路径加载训练好的 TensorFlow 模型。
- **加载测试数据**：将 Parquet 测试数据加载到名为 test_diabetes_df 的 PySpark DataFrame 中。
- **数据转换**：将 PySpark DataFrame 转换为 NumPy 数组（X_test 和 y_test），用于模型评估。
- **模型预测**：使用加载的模型对测试数据的结果（y_pred）进行预测。应用 0.5 的阈值将概率转换为二元预测。
- **计算评估指标**：使用来自 sklearn.metrics 的 accuracy_score、precision_score、recall_score 和 f1_score 计算准确率、精确率、召回率和 F1 分数等评估指标。
- **日志记录**：记录评估指标，包括准确率、精确率、召回率和 F1 分数。
- **错误处理**：如果在模型评估过程中发生任何异常，则记录包含异常详情的错误消息。

## 模块 4：main.py

我们现在来到了主模块。这个脚本是协调糖尿病预测的 TensorFlow 分类模型预处理、训练和评估工作流的主入口点（main.py）：

```python
import logging
from preprocessing import preprocess_data
from model_training import train_tensorflow_model
from model_evaluation import evaluate_model

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def main():
    preprocess_data(
        "/home/ubuntu/airflow/dags/diabetes.csv",
        "/home/ubuntu/airflow/dags/diabetes_train.parquet",
        "/home/ubuntu/airflow/dags/diabetes_test.parquet"
    )
    logger.info("Data preprocessing completed.")
    
    train_tensorflow_model(
        "/home/ubuntu/airflow/dags/diabetes_train.parquet",
        "/home/ubuntu/airflow/dags/diabetes_model.h5"
    )
    logger.info("Model training completed.")
    
    evaluate_model(
        "/home/ubuntu/airflow/dags/diabetes_test.parquet",
        "/home/ubuntu/airflow/dags/diabetes_model.h5"
    )
    logger.info("Model evaluation completed.")

if __name__ == "__main__":
    main()
```

我们来拆解一下这段代码：

- **导入所需库**：该脚本导入了用于记录日志的 logging，以及来自相应模块的 `preprocess_data`、`train_tensorflow_model` 和 `evaluate_model` 函数。
- **日志设置**：配置日志以显示级别为 INFO 的消息。
- **主函数**：此函数是协调工作流的主入口点。它执行以下步骤：
  - 调用 preprocess_data 函数预处理糖尿病数据，将预处理后的训练和测试数据保存为 Parquet 文件。
  - 记录一条消息，指示数据预处理完成。
  - 调用 train_tensorflow_model 函数，使用预处理后的训练数据训练 TensorFlow 模型，并保存训练好的模型。
  - 记录一条消息，指示模型训练完成。
  - 调用 evaluate_model 函数，使用预处理后的测试数据评估训练好的模型。
  - 记录一条消息，指示模型评估完成。
- **__name__ == "__main__" 检查**：此检查确保只有在直接运行脚本时才执行主函数，而不是在将其作为模块导入到其他脚本中时执行。

该脚本协调了从数据预处理到模型训练和评估的整个工作流，并记录消息以指示每个步骤的完成。提供给预处理、训练和评估函数的路径指示了输入数据和训练好的模型的存储或检索位置。

要运行代码，我们首先激活了 “mynv” 环境，然后导航到存储代码的 EC2 实例上的目录 “home/ubuntu/airflow/dags”，并执行 “main.py” 模块以协调糖尿病预测工作流。

