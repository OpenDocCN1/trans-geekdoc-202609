

- **召回率**：PyTorch 模型的召回率 (0.66) 高于 TensorFlow 模型 (0.59)。这表明 PyTorch 模型能捕获更大比例的实际正例，对于需要尽可能识别出更多正例的任务可能更有利。

- **F1 分数**：PyTorch 模型的 F1 分数 (0.66) 略高于 TensorFlow 模型 (0.64)。F1 分数平衡了精确率和召回率，表明 PyTorch 模型在精确率和召回率之间提供了略好的整体平衡。

总体而言，TensorFlow 和 PyTorch 模型在准确率、精确率、召回率和 F1 分数方面都表现出可比的性能。尽管模型之间存在细微差异，但这些差异属于误差范围内，或者可能源于优化策略或随机初始化的变化。尽管性能很高，但仍存在改进空间。提高数据质量、采用重采样和数据增强技术、探索迁移学习、调整模型复杂度、改善数据表示以及微调超参数，都可以进一步优化模型性能。

## 通过超参数调优优化模型性能

目前获得的结果来自使用固定超参数的模型。考虑到输入样本较小，这些结果是合理的。TensorFlow 提供了一个强大的工具来改进模型性能：超参数调优。通过利用 `keras_tuner`，我们可以系统地搜索最佳的超参数组合，将模型优化到超越手动选择所能达到的水平。

为了增强我们的模型，我们将使用 `keras_tuner` 的超参数调优过程替换固定的超参数。这种方法允许我们探索更广泛的模型配置，并找出表现最好的那一个。

### 步骤 1：必要的导入

在进行超参数调优之前，我们需要确保已导入必要的模块。来自 `keras_tuner` 的 `HyperModel` 类将帮助我们定义具有可调整超参数的模型架构，而 `RandomSearch` 将促进寻找这些超参数的最佳组合：

```python
[In]: from keras_tuner import HyperModel, RandomSearch
```

### 步骤 2：定义 DiabetesHyperModel 类

接下来，我们创建 `DiabetesHyperModel` 类，该类扩展了来自 `keras_tuner` 的 `HyperModel` 类。这个类允许我们定义模型架构，特别是指定哪些参数是可调整的。在此情况下，我们指定每个全连接层（dense layer）的单元数量和学习率是要调整的超参数。

在 `build` 方法中，我们定义了一个包含三个全连接层的基本顺序模型。对于每个全连接层，单元数量由 `hp.Int` 决定，它允许 `keras_tuner` 在指定范围内探索不同的值。同样，学习率使用 `hp.Float` 设置，提供调优器可探索的范围。模型使用标准的二元交叉熵损失函数和准确率作为指标进行编译：

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
        model.compile(loss='binary_crossentropy',
                      optimizer=optimizer,
                      metrics=['accuracy'])
        return model
```

### 步骤 3：将调优器集成到 DiabetesModelTrainer 中

定义了 `DiabetesHyperModel` 类后，我们现在将 `keras_tuner` 集成到模型训练过程中。我们修改 `DiabetesModelTrainer` 类中的 `train_tensorflow_model` 方法，使用 `RandomSearch`，这是一种系统地探索 `DiabetesHyperModel` 类中定义的超参数空间的调优器。

在此方法中，我们实例化调优器，指定参数，如试验次数 (`max_trials`) 和每次试验的执行次数 (`executions_per_trial`)。然后，调优器通过迭代不同的超参数组合来搜索最佳模型配置。找到最佳模型后，它会被返回，并可进一步训练和评估：

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
            logger.info("Best model training completed.")
            return best_model
        except Exception as e:
            logger.error(
                f"Error occurred during model training: "
                f"{str(e)}"
            )
```

**注意** 在此代码中，我们选择使用 Keras Tuner 进行超参数调优，因为它是 TensorFlow 生态系统内的原生工具，专门设计用于与 TensorFlow 模型无缝配合工作。Keras Tuner 提供了简单且灵活的接口来定义和搜索超参数，使其成为调优使用 TensorFlow 构建的深度学习和模型的理想选择。

或者，我们也可以使用 Scikit-Learn 库中的 `GridSearchCV`，这是一种广泛用于各种机器学习模型超参数调优的方法。虽然 `GridSearchCV` 强大且通用，但我们在此示例中选择了 Keras Tuner，因为它与 TensorFlow 的原生集成简化了调优过程，并确保与 TensorFlow 特定功能和函数的兼容性。对于感兴趣的用户，我们在 *Distributed Machine Learning with PySpark: Migrating Effortlessly from Pandas and Scikit-Learn*（Apress，2023 年 11 月）中详细介绍了 `GridSearchCV`。

下表比较了调优后的模型与固定超参数模型的结果。如所示，具有调优超参数的模型在多个指标上显示出改进的性能，证实了超参数调优在优化模型性能方面的有效性：

| 指标 | 调优模型 | 固定超参数模型 |
| :--- | :--- | :--- |
| 准确率 | 0.7863 | 0.7692 |
| 精确率 | 0.7500 | 0.7059 |
| 召回率 | 0.5854 | 0.5854 |
| F1 分数 | 0.6575 | 0.6400 |

超参数调优只是提高模型性能的一种方式。在第 9 章中，我们将进一步深入探讨调优，并探索提高模型性能的其他方法，从而更深入地理解如何有效地优化深度学习模型。

## 将所有部分结合在一起

在本节中，我们将构建、训练和评估用于糖尿病预测的 TensorFlow (Keras) 模型（带和不带 Keras Tuner）的各个代码片段整合起来。

## 使用固定超参数构建和训练 TensorFlow 模型

```python
[In]: import logging
[In]: from pyspark.sql import SparkSession
[In]: from pyspark.ml.feature import VectorAssembler, StandardScaler
[In]: from pyspark.sql.functions import col
[In]: from sklearn.metrics import (
    accuracy_score,
    precision_score,
    recall_score,
    f1_score
)
[In]: from tensorflow.keras.models import Sequential
[In]: from tensorflow.keras.layers import Dense, ReLU
[In]: from tensorflow.keras.optimizers import SGD
[In]: from tensorflow.keras.callbacks import Callback
[In]: import numpy as np
```

