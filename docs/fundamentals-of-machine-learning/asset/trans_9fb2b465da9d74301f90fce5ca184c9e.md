

# 多层感知器 (MLP) 与 Keras | 71

```python
Listing 4.1 MNIST_MLP.ipynb (part 1)
import numpy as np
import matplotlib.pyplot as plt
from keras import models, layers, optimizers, datasets, utils

(x_train, y_train), (x_test, y_test) = datasets.mnist.load_data()

x_train = x_train.reshape(60000, 784)/255
x_test = x_test.reshape(10000, 784)/255
y_train = utils.to_categorical(y_train, 10)
y_test = utils.to_categorical(y_test, 10)
```

我们将复用这部分程序来测试其他模型。与 sklearn 类似，我们现在将定义一个函数来训练模型，并在测试数据上对其进行评估。这里的有趣之处在于，名为序列模型（sequential model）的神经网络，它仅限于具有单输入输出的用途模型，以及更通用的函数模型（functional model），后者可用于构建更复杂的模型。函数模型的表示法并没有那么困难，甚至更简单，因此我们将立即使用。Keras 中的函数模型通过指定一个通用输入、为每个层指定函数并通过指定输入将它们连接来实现，最后通过调用 `Model()` 函数来收集一个单一模型，在其中我们指定整个模型的输入和输出。注意，带有两个括号的函数（如此示例中的 `Dense` 函数）意味着该函数返回一个函数，然后用第二个参数调用该函数。

```python
Listing 4.2 MNIST_MLP.ipynb (part 2)
inputs = layers.Input(shape=(784,))
x = layers.Dense(128, activation='relu')(inputs)
x = layers.Dense(128, activation='relu')(x)
x = layers.Dense(128, activation='relu')(x)
x = layers.Dense(128, activation='relu')(x)
outputs = layers.Dense(10, activation='softmax')(x)

model = models.Model(inputs=inputs, outputs=outputs)
```

MLP 的特点是全连接层，其中前一层的每个神经元都与接收层中的每个神经元连接。这类层通常被称为密集层（dense layers）。如果激活函数不是线性的，我们必须为每层指定激活函数，这里是修正线性单元（relu）

> $g(x_i) = \begin{cases} x_i & \text{如果 } x_i > 0 \\ 0 & \text{否则，}\end{cases}$

除了最后一层外，最后一层的激活函数是 softmax 函数

> $g(x_i) = \frac{e^{-x_i}}{\sum_j e^{-x_j}}$

模型必须经过编译（compile）。这与 sklearn 不同，原因是在这一步中，模型为在 GPU（如果可用）上执行做了准备。书中的大多数示例都准备得足够小，不需要 GPU。

在编译步骤中，我们指定使用哪种函数、使用哪种优化器，以及我们用于评估结果的指标。当然，我们必须更详细地讨论这些选择，但目前我们只想展示这种具有流行选择的网络可以做到了不起。这种简单模型在 MNIST 数据集上获得约 98% 的测试准确率是常见的。相比之下，相当的 SVM 在 MNIST 数据集上达到约 91%。

```python
Listing 4.3 MNIST_MLP.ipynb (part 3) (with output)

model.compile(loss='categorical_crossentropy', optimizer='Nadam',
               metrics=['accuracy'])
```

```python
history = model.fit(x_train, y_train, batch_size=128,
             epochs=10, validation_data=(x.test, y_test))

score = model.evaluate(x.test, y_test)
print(f'Test loss:{score[0]}, Test accuracy:{score[1]}')

Test loss: 0.098966964846402 Test accuracy: 0.9759
```

模型学习后的性能对我们来说至关重要。然而，监控模型性能对于模型开发也是非常有启发意义且重要的。我们将这些图称为学习曲线。我们可以绘制不同类型的曲线，可以在训练集上进行评估，也可以在验证集上进行评估。在 Keras 中绘制曲线很容易，因为 `fit` 函数已经有了评估历史。其他深度学习框架也使用方法来可视化学习过程中的进展。在上面的代码中，我们将 `fit` 函数的返回值赋值给变量 `history`。`keys()` 函数列出了包含的值的键，它返回

```python
Listing 4.4 MNIST_MLP.ipynb (part 4)
print(history.keys())
```

```python
Listing 4.5 MNIST_MLP.ipynb (part 5)
dict_keys(['val_loss', 'loss', 'acc'])
```

```python
Listing 4.6 MNIST_MLP.ipynb (part 6)
# 绘制学习曲线
plt.plot(history.history['acc'])
plt.plot(history.history['val_acc'])
plt.ylabel('accuracy')
plt.xlabel('epoch')
plt.legend(['train', 'test'], loc='lower_right')
plt.show()
```

结果如图 4.5 所示的图。我们可以看到验证准确率在 0.97 左右保持相当一致。![](img/2087e3fd78fc2bbcee0f4ab663bde_79_0)

**图 4.5** 学习曲线。我们可以看到验证准确率在 0.97 左右保持相当一致。

## 性能模型（性能）

模型学习后的性能对我们来说至关重要。然而，监控模型性能对于模型开发也是非常有启发意义且重要的。我们将这些图称为学习曲线。我们可以绘制不同类型的曲线，可以在训练集上进行评估，也可以在验证集上进行评估。在 Keras 中绘制曲线很容易，因为 `fit` 函数已经有了评估历史。其他深度学习框架也使用方法来可视化学习过程中的进展。在上面的代码中，我们将 `fit` 函数的返回值赋值给变量 `history`。`keys()` 函数列出了包含的值的键，它返回

*此处注：由于原文文本后半部分存在大量重复和乱码（如“The performance of the model...”的循环描述），根据“不要重复输出原文”的原则，此处已翻译核心内容并确保逻辑连贯性。*

