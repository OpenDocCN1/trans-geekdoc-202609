
## 1.5 残差人工神经网络（续）

**定义 1.5.5（单位矩阵）。** 设 $d \in \mathbb{N}$。我们用 $I_d \in \mathbb{R}^{d \times d}$ 表示 $\mathbb{R}^{d \times d}$ 中的单位矩阵。

**源代码 1.20（`code/res-ann.py`）：** 使用 **PYTHON** 实现的**残差网络（ResNet）**的**全连接**代码。此处实现的模型对应于全连接**残差网络** $(\Phi, V)$，其中 $l_0 = 3$，$l_1 = 10$，$l_2 = 20$，$l_3 = 10$，$l_4 = 1$，$\Phi = ((W_1, B_1), (W_2, B_2), (W_3, B_3), (W_4, B_4)) \in \big(\bigotimes_{k=1}^{4} (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k})\big)$，$S = \{(1,3)\}$，$V = (V_{r,k})_{(r,k) \in S} \in \big(\bigotimes_{(r,k) \in S} \mathbb{R}^{l_k \times r}\big)$，且 $V_{1,3} = I_{10}$（参见**定义 1.5.5**）。

```python
import torch
import torch.nn as nn

class ResidualANN(nn.Module):
    def __init__(self):
        super().__init__()
        self.affine1 = nn.Linear(3, 10)
        self.activation1 = nn.ReLU()
        self.affine2 = nn.Linear(10, 20)
        self.activation2 = nn.ReLU()
        self.affine3 = nn.Linear(20, 10)
        self.activation3 = nn.ReLU()
        self.affine4 = nn.Linear(10, 1)

    def forward(self, x0):
        x1 = self.activation1(self.affine1(x0))
        x2 = self.activation2(self.affine2(x1))
        x3 = self.activation3(self.affine1(x1) + self.affine3(x2))
        x4 = self.affine4(x3)
        return x4
```

**例 1.5.6**（**定义 1.5.2** 的示例）。设 $l_0 = 1$，$l_1 = 1$，$l_2 = 2$，$l_3 = 2$，$l_4 = 1$，$S = \{(0,4)\}$，设

$$\Phi = ((W_1, B_1), (W_2, B_2), (W_3, B_3), (W_4, B_4)) \in \big(\bigotimes_{k=1}^{4} (\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k})\big) \quad (1.146)$$

满足

$$W_1 = (1), \quad B_1 = (0), \quad W_2 = \begin{pmatrix} 1 \\ 2 \end{pmatrix}, \quad B_2 = \begin{pmatrix} 0 \\ 1 \end{pmatrix}, \quad (1.147)$$

$$W_3 = \begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}, \quad B_3 = \begin{pmatrix} 0 \\ 0 \end{pmatrix}, \quad W_4 = \begin{pmatrix} 2 & 2 \end{pmatrix}, \quad \text{且} \quad B_4 = (1), \quad (1.148)$$

并设 $V = (V_{r,k})_{(r,k) \in S} \in \bigotimes_{(r,k) \in S} \mathbb{R}^{l_k \times r}$，满足

$$V_{0,4} = (-1). \quad (1.149)$$

则

$$(\mathcal{R}_{\dagger}^{\mathbf{R}}(\Phi, V))(5) = 28 \tag{1.150}$$

（参见定义 1.2.4 和 1.5.4）。

**例 1.5.6 的证明。** 在整个证明过程中，设 $x_0 \in \mathbb{R}^1$，$x_1 \in \mathbb{R}^1$，$x_2 \in \mathbb{R}^2$，$x_3 \in \mathbb{R}^2$，$x_4 \in \mathbb{R}^1$ 满足对于所有 $k \in \{1, 2, 3, 4\}$ 有 $x_0 = 5$ 且

$$x_k = \mathfrak{M}_{\mathbf{1}_{(0,k)}(k) + \operatorname{id}_{\mathbb{R}^1 \mathbf{1}_{\{4\}}(k),k}(W_k x_{k-1} + B_k + \sum_{r \in \mathbb{N}_0, (r,k) \in S} V_{r,k} x_r) \tag{1.151}$$

注意到 (1.151) 保证了

$$(\mathcal{R}_{\dagger}^{\mathbf{R}}(\Phi, V))(5) = x_4 \tag{1.152}$$

接着注意到 (1.151) 确保了

$$x_1 = \mathfrak{M}_{\mathbf{r},1}(W_1 x_0 + B_1) = \mathfrak{M}_{\mathbf{r},1}(5) \tag{1.153}$$

$$x_2 = \mathfrak{M}_{\mathbf{r},2}(W_2 x_1 + B_2) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 1 & 0 \\ 2 & 1 \end{pmatrix}\begin{pmatrix} 5 \\ 0 \end{pmatrix} + \begin{pmatrix} 0 \\ 1 \end{pmatrix}\right) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 5 \\ 11 \end{pmatrix}\right) = \begin{pmatrix} 5 \\ 11 \end{pmatrix} \tag{1.154}$$

$$x_3 = \mathfrak{M}_{\mathbf{r},2}(W_3 x_2 + B_3) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}\begin{pmatrix} 5 \\ 11 \end{pmatrix} + \begin{pmatrix} 0 \\ 0 \end{pmatrix}\right) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 5 \\ 11 \end{pmatrix}\right) = \begin{pmatrix} 5 \\ 11 \end{pmatrix} \tag{1.155}$$

且

$$x_4 = \mathfrak{M}_{\mathbf{r},1}(W_4 x_3 + B_4 + V_{0,4} x_0) = \mathfrak{M}_{\mathbf{r},1}\left(\begin{pmatrix} 2 & 2 \end{pmatrix}\begin{pmatrix} 5 \\ 11 \end{pmatrix} + \begin{pmatrix} 1 \end{pmatrix} + (-1)\begin{pmatrix} 5 \end{pmatrix}\right) = \mathfrak{M}_{\mathbf{r},1}(28) = 28 \tag{1.156}$$

结合 (1.152)，这就证明了 (1.150)。因此，例 1.5.6 的证明结束。

**练习 1.5.1。** 设 $l_0 = 1$，$l_1 = 2$，$l_2 = 3$，$l_3 = 1$，$S = \{(0, 3), (1, 3)\}$，设

$$\Phi = ((W_1, B_1), (W_2, B_2), (W_3, B_3)) \in \left(\bigotimes_{k=1}^{3}(\mathbb{R}^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k})\right) \tag{1.157}$$

满足

$$W_1 = \begin{pmatrix} 1 \\ 2 \end{pmatrix}, \quad B_1 = \begin{pmatrix} 3 \\ 4 \end{pmatrix}, \quad W_2 = \begin{pmatrix} -1 & 2 \\ 3 & -4 \\ -5 & 6 \end{pmatrix}, \quad B_2 = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \tag{1.158}$$

$$W_3 = \begin{pmatrix} -1 & 1 & -1 \end{pmatrix}, \quad \text{且} \quad B_3 = \begin{pmatrix} -4 \end{pmatrix} \tag{1.159}$$

并设 $V = (V_{r,k})_{(r,k) \in S} \in \bigotimes_{(r,k) \in S} \mathbb{R}^{l_k \times l_r}$ 满足

$$V_{0,3} = \begin{pmatrix} 1 \end{pmatrix} \quad \text{且} \quad V_{1,3} = \begin{pmatrix} 3 & -2 \end{pmatrix} \tag{1.160}$$

证明或反驳以下陈述：成立

$$(\mathcal{R}_{\dagger}^{\mathbf{R}}(\Phi, V))(-1) = 0 \tag{1.161}$$

（参见定义 1.2.4 和 1.5.4）。

## 1.6 循环人工神经网络（RNNs）

在本节中，我们将回顾循环人工神经网络（RNNs），这是一种旨在接收数据序列作为输入的ANN类型。大致而言，与在前馈ANN中通过依次应用一系列*不同*的参数化函数来处理输入不同（参见上述定义 1.1.3、1.3.4、1.4.5 和 1.5.4），在RNN中，输入序列是通过重复应用*相同*的参数化函数来处理的；在首次应用后，该参数化函数的每次后续应用都以输入序列中的一个新元素以及上一次应用中产生的部分输出作为输入。RNN的输出则由参数化函数重复应用所产生的部分输出序列给出（参见下文定义 1.6.2 对RNN的精确描述，例如参见 [4, 第12.7节]、[60, 第17章]、[63, 第5章] 以及 [164, 第10章] 中对RNN的其他介绍）。

RNN中重复应用的参数化函数通常被称为*RNN节点*，而任何*RNN架构*都是通过指定相应的RNN节点架构来确定的。我们将在第 1.6.2 节中详细回顾此类RNN节点及其对应RNN的一个简单变体，并在第 1.6.3 节中简要介绍最常用的一种RNN节点，即所谓的*长短期记忆（LSTM）*节点。

在认为序列数据相关的广泛应用领域中，基于RNN的深度学习正被采用和开发。此类应用领域的例子包括自然语言处理（NLP），涵盖语言翻译（例如参见 [11, 76, 77, 388] 及其参考文献）、语言生成（例如参见 [51, 169, 238, 340] 及其参考文献）和语音识别（例如参见 [6, 81, 170, 172, 360] 及其参考文献），时间序列预测分析，包括股市预测（例如参见 [130, 133, 372, 376] 及其参考文献）和天气预报（例如参见 [352, 375, 407] 及其参考文献）以及视频分析（例如参见 [108, 235, 307, 401] 及其参考文献）。

### 1.6.1 RNN 的描述

**定义 1.6.1**（函数展开）。*设 $X, Y, I$ 为集合，设 $f: X \times I \to Y \times I$ 为函数，且设 $T \in \mathbb{N}$，$\mathbb{I} \in I$。则我们用 $\mathfrak{R}_{f,T,I}: X^T \to Y^T$ 表示满足以下条件的函数：对于所有 $x_1, x_2, \ldots, x_T \in X$，$y_1, y_2, \ldots, y_T \in Y$，$i_0, i_1, \ldots, i_T \in I$，其中 $i_0 = \mathbb{I}$ 且 $\forall t \in \{1, 2, \ldots, T\}: (y_t, i_t) = f(x_t, i_{t-1})$，有*

$$\mathfrak{R}_{f,T,I}(x_1, x_2, \ldots, x_T) = (y_1, y_2, \ldots, y_T) \tag{1.62}$$

*我们称 $\mathfrak{R}_{f,T,I}$ 为具有初始信息 $\mathbb{I}$ 的展开 $T$ 次的函数 $f$。*

**定义 1.6.2**（RNN 的描述）。*设 $X, Y, I$ 为集合，设 $\mathfrak{D}, T \in \mathbb{N}$，$\theta \in \mathbb{R}^\mathfrak{D}$，$\mathbb{I} \in I$，且设 $\mathfrak{N} = (\mathfrak{N}_\vartheta)_{\vartheta \in \mathbb{R}^\mathfrak{D}}: \mathbb{R}^\mathfrak{D} \times X \times I \to Y \times I$ 为函数。则我们称 $R$ 为具有RNN节点 $\mathfrak{N}$、参数向量 $\theta$ 和初始的展开 $T$ 步的RNN的实现函数*

