
```python
import pandas as pd

p.DataFrame(history.history).plot(figsize=(8, 5))
plt.grid(True)
plt.gca().set_ylim(0, 1) # 设置垂直范围为 [0-1]
plt.show()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_326_0.png)

图 10-12 学习曲线

你可以看到训练和验证准确率在训练期间稳定增长，而训练和验证损失都在下降。很好！此外，验证曲线与训练曲线非常接近，这意味着没有发生太严重的过拟合。在这种特殊情况下，模型在验证集上的表现优于训练开始时，这纯属偶然（特别是当验证集较小时）。然而，训练集的性能最终会优于验证集性能，这是训练时间足够长时的通常情况。你可以看出模型还没有收敛，因为验证损失仍在下降，所以你可能应该继续训练。这简单只需要再次调用 `fit()` 方法即可，因为 Keras 会从上次停止的地方继续训练（你应该能够达到 89% 的验证准确率）。

如果你对模型的性能不满意，你应该回过头调整模型的超参数，例如层数、每层的神经元数量、我们为每个隐藏层使用的激活函数数量等。

使用 Keras 实现层感知机 | WOW! eBook www.wowebook.org

训练轮数（`epochs`）、批量大小（`batch size`，可以在 `fit()` 方法中使用 `batch_size` 参数进行设置，默认为 32）。我们将在本章最后回到超参数调优。一旦你对模型的验证准确率满意，就应该在模型部署到生产环境之前，在测试集上对其进行评估以估计泛化误差。你可以通过其他参数（如 `batch_size` 或 `sample_weight`）轻松地实现，请查看文档获取更多详情：

```
>>> model.evaluate(X_test, y_test)
8832/10000 ==== ETA: 0s - loss: 0.4074 - acc: 0.8540
[0.40738476912685, 0.854]
```

正如我们在第2章中看到的，测试集上的性能略低于验证集是常见现象，因为超参数是在验证集上调优的，而不是测试集（不过在本示例中，我们没有进行任何超参数调优，所以准确率较低只是运气不好）。记住要重新考虑测试集上的超参数，否则你对泛化的估计将过于乐观。

## 使用模型进行预测

接下来，我们可以使用 `model.predict()` 方法对新实例进行预测。由于我们没有实际的实例，我们将仅使用测试集中的前 3 个实例：

```
>>> X_new = X_test[:3]
>>> y_proba = model.predict(X_new)
>>> y_proba.round(2)
array([[0., 0., 0., 0., 0., 0.09., 0.12, 0., 0.79],
       [0., 0., 0.94, 0., 0.02, 0., 0.04, 0., 0.]],
       [0., 1., 0., 0., 0., 0., 0., 0., 0.]], dtype=float32)
```

你可以看到，这里模型为每个类别（从类别 0 到 9）估计了一个概率。对于第一个实例，它估计类别 9（短筒靴）的概率为 79%，类别 7（运动鞋）的概率为 12%，类别 5（凉鞋）的概率为 9%，其他类别可以忽略不计。换句话说，它“相信”这是鞋子，特别是短筒靴，但并不完全确定，它可能是运动鞋或凉鞋。如果你只关心估计值最高的类别（如果该概率较低），那么你可以使用 `predict_classes()` 方法：

```
>>> y_pred = model.predict_classes(X_new)
>>> y_pred
array([[9, 2, 1]])
>>> np.array(class_names, ['Ankle boot', 'Pullover', 'Trouser']), dtype='<U11'
```

而且分类器正确地分类了所有三个实例：

```
>>> y_new = y_test[:3]
>>> y_new
array([9, 2, 1])
```

现在你已经知道如何使用 Sequential API 构建、训练、评估和使用分类 MLP。但回归问题呢？

# 使用 Sequential API 构建回归 MLP

让我们切换到加州住房价格问题，并使用回归神经网络来解决它。为了简单起见，我们将使用 Scikit-Learn 的 `fetch_california_housing()` 函数来加载数据：这个数据集比我们在第2章中使用的要简单，因为它只包含数值特征（没有 `ocean_proximity` 特征），而且没有缺失值。加载数据后，我们将其分为训练集、验证集，并对所有特征进行缩放：

```
from sklearn.datasets import fetch_california_housing
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
```

```
housing = fetch_california_housing()

X_train_full, X_train, y_train_full, y_test = train_test_split(
housing.data, housing.target)
X_train_valid, X_valid, y_train, y_valid = train_test_split(
X_train_full, y_train_full)
```

```
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
Y_valid_scaled = scaler.transform(X_valid)
X_test_scaled = scaler.transform(X_test)
```

使用 Sequential API 构建、评估和使用回归 MLP 进行预测与我们之前为分类的操作非常相似。主要区别在于输出层是单个神经元（因为我们没有使用激活函数），并且损失函数是均方误差。由于数据集存在噪声，我们只使用了一个神经元比之前更少的隐藏层，以避免过拟合：

```
model = keras.models.Sequential([
    keras.layers.Dense(30, activation='relu', input_shape=X_train.shape[1]),
    keras.layers.Dense(1)
])
model.compile(loss='mean_squared_error', optimizer='sgd')
history = model.fit(X_train, y_train, epochs=20,
                   validation_data=(X_valid, y_valid))

mse_test = model.evaluate(X_test, y_test)
X_new = X_test[:3]
y_pred = model.predict(X_new)
```

如你所示，Sequential API 非常易用。然而，构建具有复杂拓扑结构的神经网络有时是有用的。

# 使用 Functional API 构建复杂模型

非顺序神经网络的一个例子是 Wide & Deep 网络（见图 10-13）。让我们来构建这样一个神经网络：

```
input = keras.layers.Input(shape=X_train.shape[1])
hidden1 = keras.layers.Dense(30, activation='relu')(input)
hidden2 = keras.layers.Dense(30, activation='relu')(hidden1)
concat = keras.layers.Concatenate()([input, hidden2])
output = keras.layers.Dense(1)(concat)
model = keras.models.Model(inputs=[input], outputs=[output])
```

让我们逐行分析这些代码：

- 首先，我们需要创建一个 `Input` 对象。这是因为我们可能会有多个输入，正如我们后面看到的。

- 接下来，我们创建一个具有 30 个神经元并使用 ReLU 激活函数的 `Dense` 层。一旦创建完成，注意我们像调用函数一样调用它，并传入输入。

- 我们创建第二个隐藏层，再次像调用函数一样使用它。注意我们传递了第一个隐藏层的输出。

- 接下来，我们创建一个 `Concatenate` 层，再次像像函数一样使用它来连接输入和第二个隐藏层的输出（你可能更偏于使用 `keras.layers.concatenate()` 函数，它可以实现此操作）。

- 然后我们创建输出层，具有单个神经元且没有激活函数，并像调用函数一样调用它，传递连接的结果。

- 最后，我们创建一个 Keras `Model`，指定要使用的输入和输出。

一旦构建了 Keras 模型，一切都和之前一样，因此不需要重复：你必须编译模型、训练它、评估它并使用它进行预测。但如果你想将特征子集发送到宽路径，并将另一个子集（可能重叠）发送到深度路径（见图 10-14）呢？在这种情况下，一种解决方案是使用多个输入。例如，假设我们要把 5 个特征发送到深度路径（特征 0 到 4），并将 6 个特征发送到宽路径（特征 2 到 7）：

```
input_A = keras.layers.Input(shape=[5])
input_B = keras.layers.Input(shape=[6])
hidden1 = keras.layers.Dense(30, activation="relu")(input_B)
hidden2 = keras.layers.Dense(30, activation="relu")(hidden1)
concat = keras.layers.Concatenate()([input_A, hidden2])
output = keras.layers.Dense(1)(concat)
model = keras.models.Model(inputs=[input_A, input_B], outputs=[output])
```

![](img/0684d2da98e09085c0a622d4fd69aaad_332_0.png)

代码本身是自言自明的。我们注意到，在创建模型时指定了 `inputs=[input_A, input_B]`。现在我们可以像往常一样编译模型，但当我们调用 `fit(method)` 时，我们不能传递单个的输入矩阵 `X_train`，而是必须传递一对矩阵 `(X_train_A, X_train_B)`：每个输入一个。对于 `X_valid` 也是如此，对于调用 `evaluate()` 或 `predict()` 时的 `X_test` 和 `X_new` 也是如此：

```python
model.compile(loss="mse", optimizer="sgd")

X_train_A, X_train_B = X_train[:, :5], X_train[:, 2:]
X_valid_A, X_valid_B = X_valid[:, :5], X_valid[:, 2:]
X_test_A, X_test_B = X_test[:, :5], X_test[:, 2:]
X_new_A, X_new_B = X_test[:3], X_test[3:]
```

```python
history = model.fit(((X_train_A, X_train_B), y_train, epochs=20,
              validation_data=(X_valid_A, X_valid_B), y_test))

mse_test = model.evaluate((X_test_A, X_test_B), y_test)
y_pred = model.predict((X_new_A, X_new_B))
```

使用 Keras 实现 MLP | 307

WOW! 电子书

www.wowebook.org

在许多用场景中，你可能希望有多个输出：

- 任务可能需要这样做，例如，你可能想要定位并分类图片中的主对象。这既是一个回归任务（找到对象的中心坐标以及其宽度和高度），也是一个分类任务。

- 同样，你可能需要基于相同的数据执行多个独立的任务。诚然，你可以为每个任务训练一个神经网络，但在许多情况下，通过训练一个每个任务一个输出的单一神经网络，你会在所有任务上获得更好的结果。这是因为神经网络可以学习数据中对跨任务都有用的特征。

- 另一个用例是正则化技术（即一种训练约束，其目标是减少过拟合并提高模型的泛化能力）。例如，你可能想在神经网络架构中添加一些辅助输出（见图 10-15），以确保网络的底层部分能够学习一些有用的东西，而不依赖网络的其他部分。

![](img/0684d2da98e09085c0a622d4fd69aaad_333_0.png)

添加额外的输出非常简单：只需将它们连接到相应的层，并将它们添加到模型的输出列表即可。例如，以下代码构建了图 10-15 所示的网络：

[...] # 与上面相同，直到主输出层

output = keras.layers.Dense(1)(concat)

aux_output = keras.layers.Dense(1)(hidden2)

model = keras.models.Model(inputs=[input_A, input_B],

outputs=[output, aux_output])

每个输出都需要它自己的损失函数，因为我们在编译模型时，应该传递一个损失列表（如果传递单个损失，Keras 将假设该损失必须用于所有输出）。默认情况下，Keras 将编译所有这些损失并简单将它们相加形成最终的训练损失。然而，我们更关注主输出而不是辅助输出（仅用于正则化），因此可以给主输出的损失赋予更大的权重。通常，在编译模型时：

```python
model.compile(loss="mse", loss_weights=[0.9, 0.1], optimizer="sgd")
```

现在我们训练模型，需要为每个输出提供标签。在这个例子中，主输出和辅助输出应该尝试预测相同的内容，因此它们应该使用相同的标签。与其传递 `y_train`，我们我们需要传递 `(y_train, y_train)`（`y_valid` 和 `y_test` 也是如此）：

```python
history = model.fit(
    [X_train_A, X_train_B], [y_train, y_train], epochs=20,
    validation_data=(X_valid_A, X_valid_B], [y_valid, y_valid]))
```

当我们评估模型时，Keras 将返回总损失以及各个单独的损失：

```python
total_loss, main_loss, aux_loss = model.evaluate(
    [X_test_A, X_test_B], [y_test, y_test])
```

同样，`predict()` 方法将返回每个输出的预测值：

```python
y_pred_main, y_pred_aux = model.predict([X_new_A, X_new_B])
```

如你所见，使用 Functional API 可以非常容易地构建任何你想要的架构。让我们来看最后一种构建 Keras 模型的方法。

# 使用子类化 API 构建动态模型

Sequential API 和 Functional API 都是声明式的：你首先声明你需要使用的层以及它们应该如何连接，然后才开始为模型输入数据进行训练或推理。这有优点：模型可以很容易地保存、克隆、共享，其结构可以被查看和分析，框架可以推断形状。对于某些涉及动态形状或其他动态行为的模型，子类化 API 更加合适。你只需要子化 Model，在构造函数中创建需要的层，并在 `call()` 方法中使用它们。

```python
class WideAndDeepModel(keras.models.Model):
    def __init__(self, units=32, activation="relu", **kwargs):
        super().__init__(**kwargs) # 与上面相同，直到主输出层
        self.dense1 = keras.layers.Dense(units, activation)
        self.dense2 = keras.layers.Dense(units, activation)
        self.concat = keras.layers.Concatenate()
        self.output = keras.layers.Dense(1)

    def call(self, inputs):
        input_A, input_B = inputs
        hidden1 = self.dense1(input_A)
        hidden2 = self.dense2(input_B)
        concat = self.concat([hidden1, hidden2])
        main_output = self.output(concat)
        return main_output

model = WideAndDeepModel()
```
