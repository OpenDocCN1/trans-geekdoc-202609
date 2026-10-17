
这将使得 Optuna 仅尝试 `0.001`、`0.003`、`0.005`、`0.008` 和 `0.01` 这几个值，不再尝试其他值。

如果你想了解这些采样器是如何运作的，可以查看一下它们的[在线文档](https://optuna.readthedocs.io/en/stable/reference/sam/index.html)。

当 `Study` 对象准备好后，我们需要做的就是调用 `optimize` 方法，并指定目标函数以及让 Optuna 运行的试验次数：

```
study.optimize(objective, n_trials=6)
```

运行此操作（这可能需要一段时间），你将得到类似下面的输出：

```
Trial 0 完成，值为：0.9，参数为：
{'learning_rate': 0.01996042558751034}
最佳是 trial 0，值为：0.9。
```

```
Trial 1 完成，值为：0.9，参数为：
{'learning_rate': 0.06258876833294336}
最佳是 trial 1，值为：0.9。
```

```
Trial 2 完成，值为：0.9，参数为：
{'learning_rate': 0.04433504616170433}
最佳是 trial 2，值为：0.9。
```

```
Trial 3 完成，值为：0.91，参数为：
{'learning_rate': 0.07875049978766316}
最佳是 trial 3，值为：0.91。
```

```
Trial 4 完成，值为：0.92，参数为：
{'learning_rate': 0.07821760500376156}
最佳是 trial 4，值为：0.92。
```

```
Trial 5 完成，值为：0.9，参数为：
{'learning_rate': 0.02798666792298152}
最佳是 trial 4，值为：0.92。
```

通过我们考虑的这些参数变化，我们没有看到性能上的任何显著差异。但尽管如此，我们至少学会了如何使用 Optuna！

### 练习 11.2

使用 Optuna 同时优化模型的学习率和批大小（batch size）。

最后，请注意在目标函数中，我们使用了验证准确率（validation accuracy）而不是测试准确率（test accuracy）。记住，测试数据集应该只在我们选出最佳模型后才使用。否则，它的独立性就会受到破坏。例如，如果我们在每次 Optuna 试验后都保存模型，那么现在我们在 trial 4 模型上计算测试准确率就有意义了，以确保我们具有较低的泛化误差。

### 练习 11.3

Optuna 可以用于任何框架，而不仅仅是 TensorFlow —— 它可以优化你为了任何目的所需的任何参数！你只需要构建一个合适的目标函数。为了进一步说明这一点，请使用 Optuna 找到函数 $f(x) = (x-3)^2$ 的最小值。

# PennyLane 中的混合架构

> **了解更多...**
> 在接下来的几页中，我们无法涵盖关于 Optuna 的所有知识。
> 如果你想学习更多，应该查看它的在线文档。
> 你可以在此处找到它：https://optuna.readthedocs.io/en/stable/index.html。

以上是关于如何在真实世界场景中训练（量子）机器学习模型的简要概述。在接下来的小节中，我们将离开舒适区，使用 PennyLane 为我们解决一个新问题：多类分类任务。

## 1.2.4 多类分类问题

这将是一个令人兴奋的小节，因为我们将考虑一种可以应用我们 QML 知识的新类型问题。然而，任何旅程都始于第一步，我们的第一步是重置 NumPy 和 TensorFlow 的集合，以便于提高复现性：

```
np.random.seed(seed)
tf.random.set_seed(seed)
```

我们正准备考虑一个多类分类问题，当然，我们首先需要的是数据。我们的 `make_classification` 函数可以帮助我们，我们可以传递参数 `n_classes = 3` 来生成一个具有 3 个不同类别的数据集，这些类别将被标记为 0、1 和 2。但有一个陷阱：增加类别的数量意味着我们需要调整一些默认参数；通过将 `clusters_per_class` 设置为 1，可以达到有效的配置。因此，我们可以如下生成数据集：

```
x, y = make_classification(n_samples=1000, n_features=20, n_classes=3, clusters_per_class=1)
```

现在我们有了数据，是时候考虑模型了。我们正在面对的是一种新类型的问题，所以我们需要回到基础。现在，让我们忘记网络组件，尝试思考如何设计一个能够解决三分类（ternary classification）的量子神经网络（QNN）。

## 多类分类的通用视角

在这方面，查看经典神经网络如何处理这类问题是有用的。我们知道，在解决二分类问题时，神经网络在最后一层中有一个具有界限激活函数的神经元；通过这种方式，我们根据输出更接近 0 还是 1 来分配标签。这种方法在具有多个类别时可能并不普遍有效。

在处理 $k$ 类分类问题时，神经网络通常被设计为最后一层有 $k$ 个神经元 —— 同样使用使得值位于 0 和 1 之间的激活函数。每个神经元与一个标签相关，所以我们只需要分配输出最高的神经元的标签即可。从直觉上看，你可以将最后一层中的这 $k$ 个神经元中的每一个看作灯泡 —— 其亮度由输出决定 —— 指示输入属于某个类别的概率。

将这个想法转化为量子神经网络是很容易的。与其获取观测值 $M$ 在第一个比特上的期望值，不如返回一个包含 $k$ 个比特的数组——$M$ 在 $k$ 个比特上的期望值——为每个比特分配一个标签。

> **了解更多...**
> 构建多类问题分类器还有其他的方法。例如，两种流行的方法是**全对一（one-vs-all）**和**一对一（one-vs-one）**方法。它们涉及训练多个分类器并结合它们的结果。如果你好奇，邀请你查看 Geron 书的第 3 章。

## PennyLane 中的混合架构

这解决了设计处理我们任务的 QNN 问题，但我们仍然面临一个问题：对于这类问题还没有合适的损失函数。在二分类中，我们可以依靠二交叉熵函数，但它不适用于多类别问题。幸运的是，有一种可以泛化二交叉熵的损失函数。请让我们介绍交叉熵。

让我们考虑一个任意神经网络 $N$，它对于任何参数 $\theta$ 和任何输入 $x$，返回一个具有 $k$ 个元素的数组 $N_\theta(x)$，所有元素都在 0 到 1 之间。交叉熵损失函数取决于神经网络的参数 $\theta$、输入 $x$ 和目标 $y$，但有一个重要的细节：损失函数期望目标是**独热形式（one-hot format）**。这意味着 $y$ 不应该是代表标签 $(0,1,...,k-1)$ 的数字。它应该是一个具有 $k$ 个元素的向量（数组），除标签位置以外的所有元素都设置为 0，该位置应设置为 1。因此，如果 $y=0$，我们将得到 $y=(1,0,...,0)$，或者如果 $y=k-1$，我们将得到 $y=(0,...,0,1)$。根据这些假设，交叉熵定义如下：

> $H(\theta; x, y) = \sum_{j=1}^{k} y_j \log(N_\theta(x)_j).$

当然，我们在 $y$ 和 $N_\theta(x)$ 中使用索引 $j$ 来表示第 $j$ 个元素。注意，在这个定义中，我们隐含地假设最后一层的第一个神经元与标签 0 相关，第二个神经元与标签 1 相关，以此类推。

### 练习 11.4

证明二交叉熵损失是 $k=2$ 时交叉熵损失的一个特例。

当然，交叉熵函数是多类分类的一个合理的损失函数，并且与二交叉熵损失函数共享一些良好的属性。例如，如果分类器完全正确输出（它分配了 1），则损失为 0；对于正确输出并将其余部分设为 0，但如果分类器将错误的输出分配为 1 而其余部分设为 0，它就会产生偏差。

到目前为止，我们已经知道如何实现我们的 QNN 并且有了一个损失函数，因此我们只需要完善架构的细节了。关于量子层，我们已经知道将使用哪种观测值，所以这不是问题。对于特征映射，我们将依赖角编码（angular encoding），对于变分形式，我们将使用双局部变分形式（two-local variational form）。为了保持一定的效率，我们将 QNN 设置为四个量子比特，并让混合架构的其他部分与上一个小节保持一致。

目前的抽象思考足够了；让我们进入代码阶段。做好准备，因为接下来的内容会非常精彩。

# 为三分类问题实现 QNN

根据我们的计划，我们需要做的第一件事是将目标数组 `y` 编码为独热（one-hot）格式。

### 练习 11.5

分类交叉熵损失有一种变体，它不需要目标必须为独热格式。它就是稀疏分类交叉熵损失（sparse categorical cross entropy loss）。尝试使用此损失函数和未编码的目标来复制以下操作。你可以通过 `tf.keras.losses.SparseCategoricalcrossentropy` 访问它。

我们可以实现自己的独热编码器，但没有必要。scikit-learn 包——再次为我们提供了帮助！——已经实现了一个 `OneHotEncoder` 类，你可以从 `sklearn.preprocessing` 导入它。你可以像使用其他熟悉的 scikit-learn 类（如 `MaxAbsScaler`）一样使用这个类工作。

为了对目标数组进行独热编码，你需要一个 `OneHotEncoder` 对象；只需将数组传递给 `fit_transform` 方法即可。但有一个限制：数组应该是一个列向量！我们的目标数组 `y` 是一维的，因此在将其喂给 `fit_transform` 方法之前，我们必须对其进行变形。因此，我们可以这样对目标数组进行独热编码：

```python
from sklearn.preprocessing import OneHotEncoder

hot = OneHotEncoder(sparse = False)
y_hot = hot.fit_transform(y.reshape(-1,1))
```

注意我们添加了参数 `sparse = False`。这个布尔值（默认值为 `True`）决定了编码器是否返回稀疏矩阵。稀疏矩阵在存储包含大量零的矩阵时（如独热编码数组）是内存高效型的数据类型。本质上，稀疏矩阵不是记录矩阵中每个条目的数值，而是只跟踪非零条目。在处理大型矩阵时，它可以节省大量内存，但遗憾的是，使用稀疏矩阵会导致训练过程中出现问题，因此我们需要独热编码器为我们一个普通的数组。

# PennyLane 中的混合架构

> **了解更多...**
> `OneHotEncoder` 类的奇妙之处在于，一旦我们使用 `fit_transform` 用来自每个类别的代表元素编码了目标数组，我们就可以对任何目标数组使用 `transform` 方法。在我们的案例中，`hot` 对象将记住我们的数据中有 3 个类，因此 `hot.transform` 将正确地编码任何目标：即使给的是一个全零的输入，它仍将它们编码为长度为 3 的数组。

我们不需要对数据做任何其他处理，现在可以将其划分为训练集、验证集和测试集：

```python
x_tr, x_test, y_tr, y_test = train_test_split(
    x, y_hot, train_size = 0.8)

x_val, x_test, y_val, y_test = train_test_split(
    x_test, y_test, train_size = 0.5)
```

现在我们可以实现将构成我们模型量子层的 QNN 了。事实上，这个量子神经网络并没有特别之处，仅仅它返回的是一个值数组而不是单个值。根据之前的规范，我们可以将其定义如下：

```python
nqubits = 4

dev = qml.device("lightning.qubit", wires = nqubits)

@qml.qnode(dev, interface="tf")
def qnn(inputs, theta):
    qml.AngleEmbedding(inputs, range(nqubits))
    qml.StronglyEntanglingVariationalLayer(theta, reps = 2)
    return qml.expval(qml.PauliZ(wires=0)), \
           qml.expval(qml.PauliZ(wires=1)), \
           qml.expval(qml.PauliZ(wires=2))

weights = {"theta": qml.random.random(shape=(2, nqubits, 3), requires_grad=True)}
```

权重准备就绪后，我们可以使用以下内容来定义模型……在这种情况下，我们需要输出到 Keras 层中。要让输出是一个概率分布。为了确保这一点，我们可以使用 softmax 函数，它的定义为：

$\sigma(x) = \frac{e^{x_i}}{\sum_{j=1}^n e^{x_j}}$

可以很容易检查出 $\sigma$ 是一个受限在 0 和 1 之间的向量。除了这些修改外，我们还添加了一个额外的经典层：

```python
model = tf.keras.models.Sequential([
    tf.keras.layers.Input(shape=(n_features,)),
    tf.keras.layers.Dense(8, activation="relu"),
    qml.layers.KerasLayer(qnn, weights, output_dim=3),
    tf.keras.layers.Activation("softmax")
])
```

我们现在可以使用 Adam 优化器和分类交叉熵损失函数来编译模型，并在使用 `fit` 方法进行训练之前完成此操作；这里特别令人兴奋。作为一个有趣的事实，如果你忘记告诉 TensorFlow 使用二分类熵损失而不是分类交叉熵损失，它仍然会使用分类交叉熵损失（别看我们）；我们不是凭经验这么说的。

```python
opt = tf.keras.optimizers.Adam(learning_rate=0.001)
model.compile(opt, loss=tf.keras.losses.CategoricalCrossentropy())
```

```python
history = model.fit(x_tr, y_tr, 
    epochs=50, 
    shuffle=True,
    validation_data=(x_val, y_val),
    batch_size=10,
    callbacks=[earlystop])
```

训练几分钟后，我们可以通过以下指令获得训练和验证损失的演化图：

```python
plot_losses(history)
```

结果图表可以在图 11.2 中找到，它展示了两种损失的演化。

![图 11.2](img/9fb09d10535597eb51a8f327fe77afc4_490_0.png)

图 11.2：混合神经网络多分类器训练过程中训练和验证损失函数的演化

我们现在可以计算新训练模型的训练、验证和测试准确率，但为了做到这一点，`accuracy_score` 函数需要预测标签和实际标签以数字表示，而不是编码为数组的独热格式。因此，我们需要使用独热编码。为此，我们可以使用 `argmax` 方法，它返回数组中最大值的条目，并且可以给出一个可选的 `axis` 参数以便其仅应用于一个轴。因此，我们可以这样计算准确率：

```python
tr_acc = accuracy_score(
    model.predict(x_tr).argmax(axis=1),
    y_tr.argmax(axis = 1)
)
```

# PennyLane 中的混合架构

```python
val_acc = accuracy_score(
    model.predict(x_val).argmax(axis = 1),
    y_val.argmax(axis = 1))

test_acc = accuracy_score(
    model.predict(x_test).argmax(axis = 1),
    y_test.argmax(axis = 1))
```

```python
print("Train accuracy:", tr_acc)
print("Validation accuracy:", val_acc)
print("Test accuracy:", test_acc)
```
