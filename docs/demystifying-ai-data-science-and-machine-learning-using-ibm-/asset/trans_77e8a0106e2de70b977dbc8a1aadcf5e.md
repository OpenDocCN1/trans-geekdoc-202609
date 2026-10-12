

## 变量重要性分析

由于神经网络作为“黑箱”运行且难以解释，我们可以通过检查变量重要性来理解预测变量的相对显著性。[图 9.12](#chapter9.xhtml#fig9_12) 显示了模型 MLP 3 的变量重要性图表。如图所示，**travel purpose** 是最重要的预测变量，其次是 **departure delay**、**age**、**airline status** 和 **arrival delay**。另一方面，**destination state** 和 **average number of flights per year** 属于最不重要的预测变量之一。

![FIGURE 9.12 Variable importance chart of the champion model—MLP 3. Return to text.⏎](images/fig9_12.jpg)

**图 9.12** 冠军模型——MLP 3 的变量重要性图表。[返回文本。⏎](#chapter9.xhtml#b9fig9_12)

这些结果与前几章讨论的回归模型和决策树模型的结果基本一致。

## 示例：使用神经网络的关联模型

![](images/ufig9_25.jpg)

对于此关联模型，我们使用 **Boston Housing** 数据集构建了多个神经网络模型。

*   **数据集**：`boston.sav`
*   **目标变量**：`Imv`（**连续型**——房屋中位数价值）

### 探索-采样-修改-分区

有关这些步骤的更多详细信息，请参阅前几章。

### 神经网络建模

鉴于该数据集样本量较小（506 条记录）且所有字段均为连续型，我们将使用之前完成的已插补、已归一化的数据。虽然神经网络可以处理缺失值和非归一化数据，但通常需要大型数据集才能有效训练。对于较小的数据集，使用完整的归一化数据更有可能产生拟合度更好的模型。此外，我们将数据按 60:40 的比例划分为训练样本和测试样本。

我们将使用 MLP 或 RBFN 方法及各种配置构建以下八个神经网络模型：

1.  **模型 MLP 1**：使用 MLP 算法；由软件自动选择隐藏层单元数。
2.  **模型 MLP 2**：使用具有两个隐藏层的 MLP 算法：
    *   第 1 层：10 个单元
    *   第 2 层：10 个单元
3.  **模型 MLP 3**：使用具有两个隐藏层的 MLP 算法：
    *   第 1 层：20 个单元
    *   第 2 层：20 个单元
4.  **模型 MLP 4**：使用具有两个隐藏层的 MLP 算法：
    *   第 1 层：30 个单元
    *   第 2 层：30 个单元
5.  **模型 RBF 1**：使用 RBFN 算法；由软件自动选择隐藏层单元数。
6.  **模型 RBF 2**：使用具有一个包含 20 个单元的隐藏层的 RBFN 算法。
7.  **模型 RBF 3**：使用具有一个包含 50 个单元的隐藏层的 RBFN 算法。
8.  **模型 RBF 4**：使用具有一个包含 100 个单元的隐藏层的 RBFN 算法。

你的流程应类似于下图所示。请注意，神经网络模型是在数据插补和归一化**之后**添加到 **Partition** 节点的。这使我们能够使用完整的归一化数据集来训练模型。

你应该获得如下所示的流程。请注意，我们在插补和归一化数据后将神经网络模型添加到了 Partition 节点。因此，我们可以使用完整的归一化数据来训练模型。

![](images/ufig9_26.jpg)

使用以下配置设置这九个神经网络模型。

#### MLP 1

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **MLP 1**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Multi-layer perceptron (MLP)**
    *   隐藏层：选择 **Automatically compute number of units**
3.  **停止规则**
    *   选择 **Use maximum training time** 并设置为 15 分钟
    *   选择 **Customize number of maximum training cycles** 并设置为 100
    *   选择 **Use minimum accuracy** 并设置为 90%
4.  **高级设置**
    *   将 **Overfit prevention set** 设为默认值 (30%)

#### MLP 2

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **MLP 2**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Multi-layer perceptron (MLP)**
    *   隐藏层：选择 **Custom number of units**
    *   将 **Hidden layer 1** 设为 10，**Hidden layer 2** 设为 10
3.  **停止规则**
    *   选择 **Use maximum training time** 并设置为 15 分钟
    *   选择 **Customize number of maximum training cycles** 并设置为 250
    *   选择 **Use minimum accuracy** 并设置为 90%
4.  **高级设置**
    *   将 **Overfit prevention set** 设为默认值 (30%)

#### MLP 3

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **MLP 3**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Multi-layer perceptron (MLP)**
    *   隐藏层：选择 **Custom number of units**
    *   将 **Hidden layer 1** 设为 20，**Hidden layer 2** 设为 20
3.  **停止规则**
    *   选择 **Use maximum training time** 并设置为 15 分钟
    *   选择 **Customize number of maximum training cycles** 并设置为 250
    *   选择 **Use minimum accuracy** 并设置为 90%
4.  **高级设置**
    *   将 **Overfit prevention set** 设为默认值 (30%)
    *   选择 **Impute missing values**

#### MLP 4

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **MLP 4**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Multi-layer perceptron (MLP)**
    *   隐藏层：选择 **Custom number of units**
    *   将 **Hidden layer 1** 设为 30，**Hidden layer 2** 设为 30
3.  **停止规则**
    *   选择 **Use maximum training time** 并设置为 15 分钟
    *   选择 **Customize number of maximum training cycles** 并设置为 400
    *   选择 **Use minimum accuracy** 并设置为 90%
4.  **高级设置**
    *   将 **Overfit prevention set** 设为默认值 (30%)

#### RBF 1

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **RBF 1**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Radial Basis Function (RBF)**
    *   隐藏层：选择 **Automatically compute number of units**

#### RBF 2

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **RBF 2**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Radial Basis Function (RBF)**
    *   隐藏层：选择 **Custom number of units**
    *   将 **Hidden layer 1** 设为 20

#### RBF 3

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **RBF 3**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Radial Basis Function (RBF)**
    *   隐藏层：选择 **Custom number of units**
    *   将 **Hidden layer 1** 设为 50

#### RBF 4

1.  向流程添加一个 **Neural Net** 节点，将其连接到 **Partition** 节点，并将其命名为 **RBF 4**。打开节点设置。
2.  **基础设置**
    *   神经网络模型：**Radial Basis Function (RBF)**
    *   隐藏层：选择 **Custom number of units**
    *   将 **Hidden layer 1** 设为 100

### 冠军模型

运行所有模型后，**Neural Net** 节点提供以百分比表示的准确率，对于具有连续目标字段的关联模型，这等同于解释能力 (EP)。为与其他章节和方法保持一致，我们将此指标称为 EP。值得注意的是，在 SPSS Modeler 中，此指标仅针对训练样本提供。

