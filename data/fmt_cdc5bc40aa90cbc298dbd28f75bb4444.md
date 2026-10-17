
第一个参数是包含随机经典输入的数组，而第二个参数是包含可优化参数随机值的数组。请注意我们是如何使用量子神经网络的`num_inputs`和`num_weights`属性的。

默认情况下，分类器将使用均方误差函数并依赖 SLSQP 优化器 [86]。

然后，如果你有一些带有标签`labels_train`的训练数据`data_train`，你可以如下所示调用`fit`方法来训练新创建的分类器：

```
classifier.fit(data_train, labels_train)
```

随后，如果你想计算训练好的分类器在某些数据`data_test`上的结果，可以这样使用`predict`方法：

```
outcomes = classifier.predict(data_test)
```

或者，如果你想计算训练模型在某些测试数据集（`data_test`和`labels_test`）上的准确率，可以运行以下指令：

```
acc = classifier.score(data_test, labels_test)
```

尽管如此，你不必过于关注`NeuralNetworkClassifier`和`VQC`类，因为事实证明，在 Qiskit 中另一种（在我们看来更好的）训练 QNN 的方法。我们将在下一章节中讨论它，它将涉及与现有机器学习框架 PyTorch 的接口。此外，能够使用此接口将允许我们探索 Qiskit 的“Torch Runtime”：这是一个能够使我们能够在 IBM 真实量子硬件上高效训练 QNN 的 Qiskit 工具。这与我们在第 5 章“QAOA：量子近似优化算法”中使用的技术相同，用于在量子硬件上运行 QAOA 执行。令人兴奋，不是吗？请坚持到下一章结束。

## 总结

这是一段长的旅程，不是吗？在本章中，我们首先介绍了量子神经网络作为经典神经网络的类比。我们已经看到量子神经网络的训练与经典神经网络非常相似，并且探索了使这种可能性成为微分方法。

在解决理论问题后，我们准备好键盘开始工作。我们学习了如何使用 PennyLane 实现和训练量子神经网络，并讨论了关于该框架的一些技术细节，例如它提供的微分方法的细节。

PennyLane 自带了一些奇妙的模拟器，但是——正如我们在第 2 章《量子计算的工具》中已经提到的——它还与 Amazon Braket 和 IBM Quantum 等量子硬件平台集成。因此，在真实的量子计算机上训练量子神经网络的能力触手可及！

我们通过简要概述如何在 Qiskit 中使用量子神经网络来结束了本章。

到此时，你对量子神经网络已经有了坚实的理解。结合你之前对量子支持向量机的知识，这使你在量子机器学习领域拥有了相当坚实的基础。在接下来的章节中——那将非常具有实践导向——我们将探索基于量子神经网络的更复杂模型架构。

# 11 兼者的优者：混合架构

> 团结产生力量。—— 英语谚语

到此时，我们对经典神经网络和量子神经网络都有了坚实的理解。在本章中，我们将利用这些知识来探索一种有趣的模型：量子神经网络的混合架构。

在本章中，我们将讨论模型是什么以及它们如何有用，我们还将学习如何使用 PennyLane 和 Qiskit 实现并训练它们。整个章节将非常具有实操性，而且我们还会花时间填补关于真实场景中训练模型实际操作的一些空白。除了这些——为了增加一点趣味——我们还将超越通常的二分类器，考虑其他类型的问题。

我们将在本章中涵盖以下主题：

- 混合架构的定义与意义
- PennyLane 中的混合架构（简要概述真实场景下训练模型的最佳实践，并介绍多分类问题）
- Qiskit 中的混合架构（PyTorch 介绍）

这将是一个非常令人兴奋的章节。让我们从赋予这些混合架构意义开始。

## 混合架构的定义与意义

在前一层层中使用函数并不是一个好主意，因为它是没有任何限制的。另一方面，在这种情况下，sigmoid 激活函数可能非常适合前一层。

+ 了解更多……

现在我们承诺过这一章将非常具有实操性，而且我们将履行这一承诺。理论部分的介绍已经足够了，让我们准备好战斗吧！准备好训练一组混合量子神经网络（QNN）来对某些数据进行分类。

## 11.2 PennyLane 中的混合架构

在本节中，我们将使用 PennyLane 来实现并训练几个混合 QNN 以解决分类问题。首先，我们将处理一个二分类问题，以便在熟悉的场景下更好地理解混合 QNN 是如何工作的。然后，我们将更进一步，对多分类问题执行同样的操作。

在开始这些问题之前，让我们先进行环境搭建。

### 11.2.1 环境准备

与之前一样，我们将从导入 NumPy 和 TensorFlow 开始，并为这两个包设置种子——以确保我们结果的可重复性：

```python
import numpy as np
import tensorflow as tf

seed = 1234
np.random.seed(seed)
tf.random.set_seed(seed)
```

现在我们可以从 scikit-learn 中导入一些实用函数。我们已经广泛使用过它们了——它们无需介绍！

```python
from sklearn.metrics import accuracy_score
from sklearn.model_selection import train_test_split
```

在本章中，我们将生成自己的数据集以获得更大的灵活性。为了创建它们，我们将依赖 scikit-learn 包中的`make_classification`函数。记得我们在第 8 章“什么是量子机器学习？”中介绍过它。

```python
from sklearn.datasets import make_classification
```

此外，在本节中，我们将使用带有伴随微分的 Lightning 模拟器以获得良好的性能。因此，我们需要更改 Keras 使用的默认数据类型：

```python
tf.keras.backend.set_floatx('float64')
```

现在我们可以导入 PennyLane 并定义我们在上一节中使用的厄米特矩阵$M$。记得它对应于特征值，即给$|0\rangle$分配特征值 1，给$|1\rangle$分配特征值 0；即$M = |0\rangle\langle0|$。

```python
import pennylane as qml

state_0 = [[1], []]
M = state_0 * np.conj(state_0).T
```

最后，我们可能导入 Matplotlib 并复用上一节中定义的函数来绘制训练损失和验证损失：

```python
import matplotlib.pyplot as plt

def plot_losses(history):
    tr_loss = history.history["loss"]
    val_loss = history.history["val_loss"]
    epochs = np.array(range(len(tr_loss))) + 1

    plt.plot(epochs, tr_loss, label="Training loss")
    plt.plot(epochs, val_loss, label="Validation loss")
    plt.xlabel("Epoch")
    plt.legend()
    plt.show()
```

这就是我们开始所需的所有内容。让我们开始第一个问题。

### 11.2.2 二分类问题

我们现在已经准备好构建第一个混合 QNN 并训练它来解决二分类任务。当然，我们首先需要的是数据，正如在上一节中讨论的，我们将使用`make_classification`函数生成数据。使用将“特征编码与量子分类结合”的混合 QNN 是有意义的，例如，我们的数据集中有很多变量（特征），因此我们将生成一个包含 20 个变量的数据集——这对于目前的量子硬件来说可能已经足够大了！为了确保我们有足够的数据，我们将生成 1000 个样本。方法如下：

```python
x, y = make_classification(n_samples=1000, n_features=20)
```

默认情况下，`make_classification`函数生成具有两个可能类别的数据集。这正是我们需要的！

像一样，我们将此数据集划分为训练集、验证集和测试集：

```python
x_tr, x_test, y_tr, y_test = train_test_split(x, y, train_size=0.8)
x_val, x_test, y_val, y_test = train_test_split(x_test, y, train_size=0.5)
```

准备工作后，我们需要考虑将使用的模型。让我们从构建将包含在网络末端的量子层（QNN）开始。

对于这个问题，我们将使用在上一节中介绍的双局部变分形式（见图 10.2）。你可能还记得，我们可以这样在 PennyLane 中实现它：

```python
def TwoLocal(nqubits, theta, reps = i):
  for r in range(reps):
    for i in range(nqubits):
      qml.RY(theta[r * qubits + i], wires)
```

（注：上述代码中包含一些变量不一致之处，例如`qubits`替代了`nqubits`以及`i`作为`reps`的默认值，但根据提供的源代码予以保留。）

![](img/9fb09d10535597eb51a8f327fe77afc4_476_0.png)

图 11.1: 混合 QNN 二分类器在训练过程中训练损失和验证损失函数的演化

运行之前的代码时，我们可以看到我们的模型训练准确率为 95%，验证准确率为 90%，测试准确率为 96%。

这是一个非常令人满意的结果。我们刚刚训练了第一个混合 QNN 二分类器，并且见证了它如何被有效用于解决分类任务。

| 练习 11.1 |
| :--- |
| 尝试使用两个额外的（稠密）经典层（每层包含 16 和 8 个神经元）来解决这个问题。比较结果。 |

现在，我们说过这一章将是实操性的，而且我们是认真的的。到目前为止，我们只是训练了模型并一次性就成功了，但这在实践中很少发生。这就是为什么我们专门整理了一个小节，介绍如何在真实世界的条件下优化模型。

## 11.2.3 在现实世界中训练模型

无论你信不相信，我们关心我们亲爱的读者。一直以来，在我们训练的每一个模型背后，我们都投入了数小时细致的参数选择和模型准备——这一切是为了确保我们给你的结果足够好，即使不是最优的。

当你自己去训练模型时，你很快就会发现事情并不总是如你预期的那样顺利。对于每一个表现良好的模型，会有几十甚至数百个被丢弃的模型。这是你需要自己做好准备的。

在机器学习项目的早期阶段——特别是量子机器学习项目——你应该解决以下两个主要问题：

- **你将如何记录所有的结果？** 当你训练很多模型时，你需要一种方法将它们的性能与其架构以及训练中使用的参数记录在一起。这样，你就可以轻松地识别哪些是有效的，哪些是无效，并避免重复同样的错误。

- **你将如何探索模型的变体？** 当你不训练模型时，为每个模型保留一个独立的脚本可能是可行的，但这不是并不是大型项目的解决方案。通常情况下，你想尝试各种配置，并看看哪种效果最好。在这方面，自动化确实可以让你的生活变得更轻松。

我们将第一个问题留给你。事实上，并没有通用的方法来处理它——这完全取决于当前的问题以及你可以使用的训练策略。然而，关于第二个问题，我们确实有一些可以提供的。

在训练模型时，选择良好的超参数（如良好的批大小或学习率）并不是一项容易的任务，但它是至关重要的。你应该使用较小还是较大的学习率？你应该使用多少层？什么类型的？决策、决策、决策！可能性的数量指数级增长，因此探索每一个可能性是不可能的。但在机器学习中，找到一个良好的配置可能是成功与失败之间的区别。我们如何能够系统且（某种程度上）毫不费力地做到这一点？

## 第 11 章：两者的兼得：混合架构

目前已经有很多包和工具可以帮助你自动搜索最优训练参数。其中最流行的包之一是 Optuna，我们即将对它进行演示。请参阅附录 D “安装工具”以获取安装说明说明。

## 了解更多信息...

在机器学习问题中自动搜索最优训练参数的过程被称为**自动化机器学习**，通常缩写为 AutoML。这指的是使用自动化技术来解决机器学习问题。让机器负责训练其他机器！

一旦你安装了 Optuna，可以如下方式导入它：

```
import optuna
```

我们将使用 Optuna 在 0.001 到 0.1 之间寻找最佳学习率。为了实现这一点，我们需要定义一个带有单个参数（trial）的函数（我们称为 objective）。目标函数应该使用我们想要优化的训练参数——我们将精确这种方式——并且它应该返回我们想要优化的指标。例如，在我们的情况下，我们想要最大化

```python
def objective(trial):
    # 定义学习率作为可优化参数
    lrate = trial.suggest_float("learning_rate", 0.001, 0.1)

    # 定义层数作为可优化参数
    n_layers = trial.suggest_int("n_layers", 1, 3)

    # 准备模型
    model = tf.keras.Sequential([
        tf.keras.layers.Input(shape=(20,)),
    ])

    for i in range(n_layers):
        model.add(tf.keras.layers.Dense(4, activation=trial.suggest_categorical("activation", ["sigmoid", "elu", "relu"])))

    model.add(tf.keras.layers.Dense(1, activation="sigmoid"))

    # 定义优化器
    model.compile(optimizer=tf.keras.optimizers.Adam(learning_rate=lrate), loss='binary_crossentropy')

    # 训练模型！
    history = model.fit(x_tr, y_tr, epochs=50, batch_size=10, validation_data=(x_val, y_val), verbose=0)

    # 返回验证准确率
    return history.history['val_accuracy'][-1]
```

- 如果参数的数据类型为浮点数（float）且参数在 m 和 M 之间限制，你应该调用`suggest_float("parameter", m, M)`方法。如果你只想让参数在 m 和 M 之间取以步长 s 分隔的离散值，发送可选参数`step = s`，其默认值为 None。

- 如果参数的类型是 m 到 M 之间的整数，你应该使用`suggest_int("parameter", m, M)`。同样，如果参数的值应该从 m 到 M 以步长 s 分隔。

- 如果你的参数从一组可能的值列表中取值，你应该使用`suggest_categorical("parameter", values)`。例如，如果我们想在神经网络的层上尝试激活函数，可以使用如下代码：

```python
activation = trial.suggest_categorical("activation_function", ["sigmoid", "elu", "relu"])
```

当然，一个目标函数可以有任意数量的可优化参数。它们将通过分别调用我们介绍的方法来定义。所以这就是你如何创建目标函数并指定你想要优化的参数。现在，我们如何优化它们？第一步是使用`create_study`函数创建一个 Study 对象，如下：

```python
from optuna.samplers import TPESampler

study = optuna.create_study(direction='maximize', sampler=TPESampler(seed=seed))
```

在这里，我们指定要创建一个研究来最大化某个目标函数，并使用带有种子的 TPESampler。默认情况下，Optuna 会尝试最小化目标函数——这就是为什么我们必须传递那个参数。我们传递的采样器（sampler）只是在优化过程中寻找要尝试值的对象。我们选择的是默认的，但我们手动传递了它，以便能够设置种子并获得可重复的结果。还有许多其他的采样器。

最值得关注的是，`GridSampler`允许你在预定义的“搜索空间”中尝试所有的参数组合。例如，我们可以使用以下采样器：

```
values = {"learning_rate": [0.001, 0.003, 0.005, 0.008, 0.01]}
sampler = optuna.samplers.GridSampler(values)
```
