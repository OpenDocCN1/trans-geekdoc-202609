
这两个算符都代表对量子比特的测量，但它们关联到不同输出的特征值不同。第一个算符将特征值 1 和 0 分别关联到比特值为 0 和 1，而第二个观测量将特征值 1 和 -1 关联到这些结果。

**练习 10.1**

练习的目的是让你更熟悉狄拉克符号。证明之前的两个海米特算符可以分别写为 $|0\rangle\langle0| + |1\rangle\langle1|$ 和 $|0\rangle\langle0| - |1\rangle\langle1|$。

> 提示：记住 ket（列向量）和 bra（行向量）的积是一个矩阵。我们在第 7.2.1 节中见过这个例子。

正如我们在章节之后看到的，像 PennyLane 这样的框架允许你使用由海米特算符定义的测量操作。这在定义量子神经网络的测量操作时可以提供很大的灵活性。例如，Shalev-Shwartz 和 Shai Ben-David [65, 20.6] 讨论了这些用于经典神经网络的技术。

- **参数位移规则（parameter shift rule）：** 标准的自动微分技术只能在模拟器上使用。幸运的是，在真实硬件上执行量子神经网络时，还有另一种计算梯度的方法：使用**参数位移规则**。顾如其名，这种技术使我们能够通过在量子网络中使用相同的电路，但偏移可优化参数的值来计算梯度。参数位移规则并非总是适用，但它在许多常见情况下都有效，并且可以与其他技术（如数值近似）结合使用。

我们不会深入探讨这种方法的工作原理，但你可以查阅 Maria Schuld 等人的研究论文 [80] 以获取更多信息。例如，如果你有一个由单个旋转门 $R_X(\theta)$ 组成的电路，以及对其期望值 $E(\theta)$ 的测量，你将能够计算其关于 $\theta$ 的导数：

$$\nabla_{\theta}E(\theta) = \frac{1}{2}\left(E\left(\theta+\frac{\pi}{2}\right)-E\left(\theta-\frac{\pi}{2}\right)\right)$$

这与三角函数的情况类似：例如，你可以用同一个正弦函数的位移值来表示正弦函数的导数。

对于我们的目的来说，只需要知道它存在并且可以使用足够了。当然，参数位移规则也可以在模拟器上使用！

## 重要说明

当在模拟器上运行量子神经网络时，可以使用类似于经典机器学习的自动微分技术来计算梯度。当它们运行在真实硬件或模拟器上时，这些梯度也可以——至少在许多情况下——使用参数位移规则来计算。

另一种方法是数值近似，它始终是计算梯度的有效方法。

正如我们所提到的，所有这些方法在 PennyLane 中都已完全实现，我们将在接下来的章节中尝试所有的它们。

## 了解更多信息...

一切看起来都很良好且充满前景，但量子神经网络在训练方面也面临一些挑战。最值得注意的是，它们容易受到**贫瘠高原（barren plateaus）**的影响：即训练梯度消失，从而导致训练无法进行（有关进一步解释请参阅 McClean 等人的论文 [81]）。众所周知，使用的测量操作类型以及 QNN 的深度也会影响发现这些贫瘠高原的概率。这在 Cerezo 及其合作者的论文 [82] 中被研究过。无论如何，在训练你的 QNN 时，你应该保持警惕，如果贫瘠高原威胁到你的模型，请遵循文献寻找可能的解决方案。

我们已经拥有了构建和训练量子神经网络所需的所有要素。但在实践中执行这些之前，我们将讨论一些技巧和建议，这些技巧将帮助你充分利用我们全新的量子机器学习模型。

### 10.1.5 量子神经网络的实际用法

以下是在设计和训练 QNN 模型时应该记住的观点汇锦。你可以将其视为前几个章节的总结，并辅以第 8 章“什么是量子机器学习？”中的几个亮点。

- **做出明智的选择：** 当你开始设计 QNN 时，你有三个重要的决定要做出：你必须选择一个特征映射（feature map）、一个变分形式（variational form）和一个测量操作。对这些选择要有目的，并考虑你正在处理的问题和数据。例如，你的决定可能会影响你发现贫瘠高原的概率。一个很好的建议是查阅类似问题的文献，并在此基础上构建。

- **尺寸至关重要：** 当你使用设计良好的变分形式时，通常，生成的量子神经网络的能力将与它拥有的可优化参数的数量直接相关。使用过多的参数，你可能会得到一个过拟合的模型。使用非常少的参数，你的模型最终可能会欠拟合（注：原文此处可能误为 fitting，根据语境应为 underfitting）。

- **优化很重要：** 对于大多数问题，Adam 优化器是你在训练量子神经网络时的首选。

- **正确喂数据：** 喂给量子神经网络的数据应该根据要求进行归一化。

### 10.2.1 为 QNN 准备数据

正如我们之前提过的，我们将训练一个 QNN 模型来实现一个二分类器。我们反复使用二分类器并非偶然，因为二分类器是可能是最容易训练的机器学习模型。然而，在书的后面部分，我们将探索更有趣的案例和架构。

对于我们的示例问题，我们将使用 scikit-learn 包提供的玩具数据集之一：“乳腺癌威斯星数据集” [78]。该数据集包含 569 个样本，每个样本有 30 个数值变量。这些变量描述了可以表征乳腺是恶性还是良性的特征。每个样本的标签可以是 0 或 1，分别对应恶性或良性。你可以在网上找到该数据集的文档：https://scikit-learn.org/stable/datasets/toy_dataset.html#breast-cancer-dataset（该数据集的原始文档也可以 https://archive.ics.uci.edu/ml/datasets/breast-cancer-wconsin+(diagnostic) 找到）。我们可以通过调用 `sklearn.datasets` 中的 `load_breast_cancer` 函数来获取，并设置可选参数 `return_X_y` 以便获取样本之外的标签。为此，我们可以使用以下指令：

```python
from sklearn.datasets import load_breast_cancer

x, y = load_breast_cancer(return_X_y = True)
```

当我们训练 QSVM 时，由于我们不需要对模型之间进行任何比较，因此一个训练集和一个测试集就足够了。但在我们的这种情况下，我们将通过对验证损失进行早停（early stopping）来训练模型。这意味着——如果你不记得的话——我们将跟踪验证损失，并且一旦它不再提高，我们就会停止训练——取决于我们定义的某些标准。此外，我们将保留最能最小化验证损失的模型配置。为了此目的使用测试集不是良好的做法，因为那样测试集就会在训练中发挥作用，它将无法对真实误差提供良好的估计；这就是为什么我们需要一个单独的验证集。

我们可以如下所示将数据集拆分为训练集、验证集和测试集：

```python
from sklearn.model_selection import train_test_split

x_tr, x_test, y_tr, y_test = train_test_split(
    x, y, train_size = 0.8)

x_val, x_test, y_val, y_test = train_test_split(
    x_test, y_train, train_size = 0.5)
```

数据集中的所有变量都是非零的，但它们没有归一化。为了与我们的任何特征映射配合使用，我们应该使用 `MaxAbsScaler` 将训练数据归一化在 0 和 1 之间：

```python
from sklearn.preprocessing import MaxAbsScaler

scaler = MaxAbsScaler()
x_tr = scaler.fit_transform(x_tr)
```

然后我们按照训练数据集相同的比例归一化测试集和验证集：

```python
x_test = scaler.transform(x_test)
x_val = scaler.transform(x_val)

# 限制所有值在 0 到 1 之间。
x_test = np.clip(x_test, 0, 1)
x_val = np.clip(x_val, 0, 1)
```

就像我们在上一章节中训练 QSVM 时做的一样！

到为止，我们完成了一些相当标准的数据预处理，不需要过多思考未来量子神经网络的实际架构。但现在情况改变了。我们有一个问题要解决：我们的数据集有 30 个变量，对于目前的量子硬件来说，这是一个相当大的数字。由于我们无法使用具有 30 个比特的量子计算机，我们可能考虑以下选择：

- 在 5 个比特上使用振幅编码（amplitude encoding）特征映射，它可以容纳高达 $2^5 = 32$ 个变量
- 使用我们用过的其他特征映射，但结合降维技术

我们将采用后一种选择。你可以自己尝试另一种可能性：如果你使用我们在第 9 节*量子支持向量机*中学习过的 `qml.AmplitudeEmbedding` 模板，这非常简单。

**练习 10.2**

在你学习这一章节时，请尝试使用所有原始变量并在五个量子比特上使用振幅编码来实现一个 QNN。请记住，当通过 `features` 参数向 `qml.AmplitudeEmbedding` 对象馈送数据时，不要使用 `inputs` 变量，而应该使用 `a for i in inputs`。这是因为 PennyLane 需要执行某些内部类型操作。

在模拟器上训练量子神经网络是一项非常计算密集型的任务。我们不希望任何人的计算机崩溃，所以为了确保每个人都能顺畅运行此示例，我们将限制使用 4 比特电路。然后，我们将使用降维技术将变量数量减少到 4，并设置一个接收这 4 个输入变量的 QNN。

正如我们在上一章节中所做的那样，我们将使用主成分分析将数据集中的变量减少到 4：

```python
from sklearn.decomposition import PCA

pca = PCA(n_components = 4)

xs_tr = pca.fit_transform(x_tr)
xs_test = pca.transform(x_test)
```

## 构建网络

现在我们收集了实现量子神经网络所需的所有部分，我们将将其构建为一个具有两个参数的量子节点：`inputs` 和 `theta`。第一个参数是强制性的：为了让 PennyLane 能够使用 TensorFlow 训练量子神经网络，它的第一个参数必须接受包含网络所有输入的数组，且该参数的名称必须是 `inputs`。在这个参数之后，我们可以添加任意数量的参数。这些参数可以对应电路的任何参数，并且需要包含变分形式中的优化参数。

因此，我们可以如下实现我们的量子神经网络：

```python
nqubits = 4
dev = qml.device("default.qubit", wires=nqubits)

def qnn_circuit(inputs, theta):
    ZZFeatureMap(nqubits, inputs)
    TwoLocal(nqubits = nqubits, theta = theta, reps = 1)
    return qml.expval(qml.Hermitian(M, wires=[0]))

qnn = qml.Node(qnn_circuit, dev, interface="tf")
```

为了保持简单，我们选择只使用变分形式的一次重复。如果你的数据集更复杂，你可能想要增加这个数字，以便获得更多的可训练参数。

顺便注意一下，我们如何在量子节点初始化器中添加 `interface = "tf"` 参数。这样做是为了让量子节点能够处理数组列表中的张量（TensorFlow 的数据对象），以便 PennyLane 能与 TensorFlow 进行顺畅通信。如果我们使用了 `@qml.node` 装饰器，就必须在调用它时包含该参数。

这定义了实现我们量子神经网络的量子节点。现在，我们需要弄清楚如何训练它，为此，我们将依靠 TensorFlow。我们将在下一个小节中执行此操作。

### 10.2.3 在 PennyLane 中使用 TensorFlow

在第 8 章“什么是量子机器学习？”中，我们已经学习了如何使用 TensorFlow 来训练经典神经网络。得益于 PennyLane 出色的互操作性，我们现在几乎可以像训练经典模型一样使用 TensorFlow 来训练我们的量子神经网络。

> **了解更多...**
> PennyLane 还可以与 PyTorch 等其他经典机器学习框架集成。此外，它还提供了自己的基于 NumPy 包的训练工具，但这些工具更为有限。

还记得我们如何使用 Keras 层构建 TensorFlow 模型并将它们连接到顺序模型中吗？看这里：

```python
weights = {"theta": 8}
qlayer = qml.qnn.KerasLayer(qnn, weights, output_dim=1)
```

这就是你如何创建一个包含我们量子神经网络的 Keras 层——就像它是经典模型中的任何层一样！为了实现这一点，我们必须调用 `qml.qnn.KerasLayer`，并向它传递一些内容。首先，当然我们已经看到了带有神经网络的量子节点。然后，通过所有接收可优化参数的节点参数名称索引字典，并为这些参数中的每一个指定所需的参数数量。由于我们只有一个参数 `theta`，且它应该包含 8 个可优化参数（也就是说它是一个长度为 8 的数组），因此我们发送了 (`theta: 8`)。最后，我们必须指定量子节点的输出维度；由于它只返回一个数值期望值，因此该维度为 1。

一旦有了量子层，我们就可以轻松地创建 Keras 模型：

```python
model = tf.keras.models.Sequential([qlayer])
```

以这种灵活程度将量子节点集成到神经网络中的能力将使我们能够在下一章节中轻松地构建更复杂的模型架构。

准备好模型后，我们现在需要选择一个优化器和损失函数，然后就像编译任何经典模型一样编译模型。在我们的情况下，我们将使用二分类交叉熵损失（因为我们最终正在训练一个二分类器），并将依赖于学习率设为 0.005 的 Adam 优化器。对于优化器的其余参数，我们将使用默认值。我们的代码如下：

```python
opt = tf.keras.optimizers.Adam(learning_rate = 0.005)
model.compile(opt, loss=tf.keras.losses.BinaryCrossentropy())
```

此外，我们将使用以下指令对验证损失使用早停法（early stopping），容忍度为两个轮次（epochs）：

```python
earlystop = tf.keras.callbacks.EarlyStopping(
    monitor = "val_loss", patience = 2, verbose = 1,
    restore_best_weights = True)
```

现在我们已经准备好发送最终指令来训练我们的模型。

## 了解更多...

你可能记得，在本章的某个地方，我们讨论了量子神经网络计算梯度的不同方式。你可能想知道我们为什么为了训练模型而处理这些问题。

结果显示 PennyLane 已经为我们选择了计算梯度的最佳微分方法。每个量子节点可以使用某些微分方法——例如，作为硬件的节点无法使用自动微分，但模拟器节点可以。在这一节的后续部分，我们将详细讨论 PennyLane 中使用的所有微分方法。

为了训练我们的模型，我们只需要调用 `fit` 方法。由于我们将使用早停，所以对轮次设置了宽松的 50。此外，我们将固定批大小为 20。对于这一点，我们可以使用以下代码：

```python
history = model.fit(xs_tr, y_tr, epochs = 50, shuffle = True,
    validation_data = (xs_val, y_val),
    batch_size = 20,
    callbacks = [earlystop])
```

运行此指令后得到的输出将类似于：

```
Epoch 1/50
23/23 [====] - 22s 944ms/step - loss: 0.8069 - val_loss: 0.7639
Epoch 2/50
23/23 [====] - 21s 932ms/step - loss: 0.7485 - val_loss: 0.7174
Epoch 3/50
23/23 [====] - 21s 930ms/step - loss: 0.7022 - val_loss: 0.6819
Epoch 4/50
23/23 [====] - 22s 957ms/step - loss: 0.6685 - val_loss: 0.6554
Epoch 5/50
23/23 [====] - 21s 925ms/step - loss: 0.6433 - val_loss: 0.6362
Epoch 6/50
23/23 [====] - 21s 915ms/step - loss: 0.6249 - val_loss: 0.6236
Epoch 7/50
23/23 [====] - 21s 916ms/step - loss: 0.6122 - val_loss: 0.6141
Epoch 8/50
23/23 [====] - 21s 931ms/step - loss: 0.6029 - val_loss: 0.6081
Epoch 9/50
```
