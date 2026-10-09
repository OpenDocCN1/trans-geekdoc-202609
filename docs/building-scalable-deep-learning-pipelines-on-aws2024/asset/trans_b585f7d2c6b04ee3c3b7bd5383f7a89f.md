

- epochs (int): 训练过程中的轮数（对完整数据集的迭代次数）。默认值设为 100。
- batch_size (int): 每次梯度更新处理的样本数。默认值设为 32。

返回：
- None

### 模型架构
- 该方法初始化了一个顺序模型（Sequential），这是一个线性的层堆栈。向模型中添加了四个具有不同配置的密集层（dense layers）：
    - 第一层（Dense(64, activation='relu', input_shape=self.input_shape)）拥有 64 个单元，使用 ReLU 激活函数，并接受由特征数量定义的输入形状。
    - 后续层（Dense(32, activation='relu'), Dense(16, activation='relu')）分别拥有 32 个和 16 个单元，均使用 ReLU 激活函数。
    - 最后一层（Dense(1)）拥有单个单元，代表输出层。

### 编译
- 使用 Adam 优化器（optimizer='adam'）和均方误差损失函数（loss='mse'）对模型进行编译。

### 训练
- 使用训练特征和标签对编译后的模型进行训练（self.model.fit）。训练过程运行指定的轮数（epochs），并使用指定的批次大小（batch_size）。

### 超参数选择
- 轮数（Epochs）：选择 100 轮是基于神经网络训练中的常见做法，旨在平衡学习数据模式与避免过拟合之间的关系。虽然没有进行大规模的实验，但 100 轮是一个合理的起点，通常允许模型收敛。
- 批次大小（Batch Size）：选择批次大小为 32，因为它是广泛接受的标准，在计算效率和模型准确性之间取得了平衡。这是一个常用的默认值，在大多数情况下表现良好，在训练速度和泛化能力之间提供了良好的权衡。

## 步骤 6：evaluate_model 方法定义

在此步骤中，我们在 TSLARegressor 类内创建 evaluate_model 方法，该方法负责使用测试数据评估已训练的神经网络模型：

```python
[In]: def evaluate_model(self, test_features, test_labels):
    """
    Evaluate the trained model.
    
    Parameters:
    - test_features (ndarray): Test features.
    - test_labels (ndarray): Test labels.
    
    Returns:
    - float: Test loss.
    """
    test_loss = self.model.evaluate(test_features, test_labels)
    return test_loss
```

evaluate_model 方法通过计算测试数据上的损失来评估已训练的神经网络模型。

以下是该方法的参数及其功能的解释：

### 参数
- test_features (ndarray)：包含测试特征的 NumPy 数组
- test_labels (ndarray)：包含相应测试标签的 NumPy 数组

### 返回
- float：测试损失，指示模型在测试数据上的表现

### 评估
- 该方法使用已训练模型（self.model）的 evaluate 函数来计算测试数据上的损失。
- 它向 evaluate 函数传入测试特征和标签，该函数根据模型的预测和真实标签计算损失。

### 测试损失
- 计算出的测试损失作为方法的输出返回。该值提供了关于模型在未见数据上表现的见解。测试损失越低，表明表现越好，因为这意味着模型的预测更接近真实标签。

## 步骤 7：predict_and_evaluate 方法定义

在此步骤中，我们创建 predict_and_evaluate 方法，该方法的作用是预测值使用已训练的神经网络模型，然后根据 R 平方分数评估其性能：

```python
[In]: def predict_and_evaluate(self, test_features, test_labels):
        """
        Predict and evaluate the neural network model.
        
        Parameters:
            - test_features (ndarray): Test features.
            - test_labels (ndarray): Test labels.
            
        Returns:
            - float: R2 score.
        """
        test_predictions = self.model.predict(test_features)
        r2_score_value = r2_score(test_labels, test_predictions)
        return r2_score_value
```

该方法使用已训练的神经网络模型（self.model）对测试特征进行预测，并使用 R 平方分数评估其性能。

让我们分解该方法的参数和功能：

### 参数
- test_features (ndarray)：包含测试特征的 NumPy 数组
- test_labels (ndarray)：包含相应测试标签的 NumPy 数组

### 返回
- float：R 平方分数，衡量因变量（测试标签）中方差中有多少比例可以由自变量（测试特征）在模型中预测

### 预测
- 该方法首先使用已训练模型（self.model）的 predict 函数对测试特征进行预测。
- 预测值存储在变量 test_predictions 中。

### 评估（R 平方分数）
- 然后，该方法通过将预测值（test_predictions）与真实测试标签（test_labels）进行比较来计算 R 平方分数。
- 使用 Scikit-Learn 库中的 r2_score 函数来完成此任务。

### R 平方分数计算
- R 平方分数指示因变量中方差有多大比例可以由自变量预测。
- 较高的 R 平方分数（接近 1）表明因变量中更大比例的方差可以由自变量预测，这意味着模型对数据的拟合更好。
- 计算出的 R 平方分数作为方法的输出返回，提供了模型在测试数据上预测性能的度量。

## 步骤 8：plot_actual_vs_predicted 函数定义

我们现在位于 TSLARegressor 类之外。我们创建 plot_actual_vs_predicted 函数，该函数使用 Matplotlib 绘制测试数据的实际值与预测值：

```python
[In]: def plot_actual_vs_predicted(tsla_regressor, test_features, test_labels):
    """
    Plot actual vs. predicted values.

    Parameters:
      - tsla_regressor (TSLARegressor):
        Instance of TSLARegressor class.
      - test_features (ndarray): Test features.
      - test_labels (ndarray): Test labels.

    Returns:
      - None
    """
    test_predictions = tsla_regressor.model.predict(test_features)

    print("Actual    Predicted")
    for actual, predicted in zip(test_labels, test_predictions):
        print(f"{actual:.2f}  {predicted[0]:.2f}")

    plt.figure(figsize=(10, 6))
    plt.scatter(test_labels, test_predictions, color='blue')
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

让我们分解该函数完成的内容：

### 参数
- tsla_regressor (TSLARegressor)：TSLARegressor 类的实例，包含已训练的神经网络模型（model）
- test_features (ndarray)：包含测试特征的 NumPy 数组
- test_labels (ndarray)：包含相应测试标签的 NumPy 数组

### 返回
- None

### 预测
- 该函数首先使用已训练的神经网络模型（tsla_regressor.model.predict(test_features)）预测测试特征的值。
- 预测值存储在变量 test_predictions 中。

### 打印实际值与预测值
- 该函数并排打印实际值和预测值以供比较。
- 它通过循环遍历每一对实际值和预测值，并将它们格式化为两位小数进行打印。

### 绘制实际值与预测值
- 该函数创建一个散点图，以可视化实际值和预测值之间的关系。
- 实际值绘制在 x 轴上（test_labels），预测值绘制在 y 轴上（test_predictions）。
- 此外，还绘制了一条对角虚线，代表实际值和预测值相同的理想场景。

### 图表定制
- 该函数通过设置 x 轴和 y 轴的标签以及提供标题来定制图表。
- 使用 plt.show() 显示图表。

### 可视化
- 此可视化允许直观地评估模型的预测值与实际值的匹配程度。
- 点沿对角虚线紧密聚集，表明实际值和预测值之间存在强相关性，意味着模型表现良好。

