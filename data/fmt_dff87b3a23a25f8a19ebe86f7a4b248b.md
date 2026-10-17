
(\mathfrak{M}_{a_{l_L,l_{L-1}}} \circ \boldsymbol{\mathcal{A}}^{\mathcal{T}(\Phi),\sum_{i=1}^{L-2}l_i(l_{i-1}+1)}_{L-1,l_{L-2}} \circ \mathfrak{M}_{a_{l,L-2}} \circ \boldsymbol{\mathcal{A}}^{\mathcal{T}(\Phi),\sum_{i=1}^{L-3}l_i(l_{i-1}+1)}_{L-2,l_{L-3}}) \circ \dots \circ (\mathfrak{M}_{\mathfrak{a}_{1,l_1}} \circ \boldsymbol{\mathcal{A}}^{\mathcal{T}(\Phi),0}_{1,l_0})(x_0) & : L > 1 

\end{cases} \tag{1.104}

\end{equation}

\((参见定义 1.2.1)。\) 结合此结果、(1.103)、(1.5) 和 (1.91)，表明对于所有 \(x_0 \in \mathbb{R}^{l_0}\)，\(x_1 \in \mathbb{R}^{l_1}\)，\(\dots\)，\(x_L \in \mathbb{R}^{l_L}\)，且对于 \(\forall k \in \{1,2,\dots,L\} \) 有 \(x_k = \mathfrak{M}_{\mathfrak{a}_{k}}(\mathcal{W}_{k,\Phi}x_{k-1} + \boldsymbol{\mathcal{B}}_{k,\Phi})\)，则

\begin{equation}

(\mathcal{R}_{a}^{\mathbb{N}}(\Phi))(x_0) = x_L = \mathcal{W}_{L,\Phi}x_{L-1} + \boldsymbol{\mathcal{B}}_{L,\Phi} = (\boldsymbol{\mathcal{A}}^{\mathcal{T}(\Phi),\sum_{i=1}^{L-1}l_i(l_{i-1}+1)}_{l_L,l_{L-1}})(x_{L-1}) 

\end{equation}

\begin{equation}

= \begin{cases} 

(\mathcal{N}_{\text{id}_{a}^{\mathcal{T}(\Phi),0},l_0}^{\mathcal{T}(\Phi),l_0})(x_0) & : L=1 \\

(\mathcal{N}_{\mathfrak{M}_{\mathfrak{a}_{1,l_1}},\mathfrak{M}_{\mathfrak{a}_{l,L-1}},\dots,\mathfrak{M}_{\mathfrak{a}_{l,L-1}}, \text{id}_{L}^{\mathcal{T}(\Phi),0}}^{\mathcal{T}(\Phi),l_0})(x_0) & : L > 1 

\end{cases} \tag{1.105}

\end{equation}

\((参见定义 1.1.3 和 1.3.4)。\) 因此命题 1.3.9 的证明完毕。 $\square$

# 1.4 卷积神经网络 (CNNs)

在本节中，我们回顾 CNN，即旨在处理具有空间结构数据的 ANNs。从广义上讲，CNN 可以被认为是任何涉及卷积运算的 ANNs（例如，参见下文定义 1.4.1）。粗略地说，卷积运算允许 CNN 通过在执行跨输入数据点不同区域的相同操作来利用数据的空间不变性。原则上，此类卷积运算可以与其他 ANN 架构元素组合使用，例如全连接层（例如，参见上述第 1.1 节和第 1.3 节）、残差层（例如，参见下文第 1.5 节）和循环结构（例如，参见下文第 1.6 节）。然而，为了简单起见，我们在本节中仅介绍基于离散卷积运算（无填充，有时称为 valid padding）的卷积层的前馈 CNN 的所有数学细节，参见定义 1.4.1（见下文定义 1.4.2 和 1.4.5）。对于 CNN 的其他介绍，例如参见 [4, Section 12.5], [60, Chapter 16], [63, Section 4.2], [164, Chapter 9], 和 [36, Section 1.6.1]。

CNN 最初由 LeCun 等人 [262] 为计算机视觉 (CV) 应用引入。被认为第一个成功的现代 CNN 架构是 Krizhevsky 等人 [257] 提出的 AlexNet 架构。其他一些非常成功的早期 CV CNN 架构包括 [152, 190, 206, 282, 291, 371, 378, 390]。尽管 CV 是 CNN 最流行的应用领域，但 CNN 在其他几个领域也取得了成功的发展。特别是，例如，参见 [110, 143, 245, 430, 434, 437] 中关于 CNN 在自然语言处理 (NLP) 中的应用，参见 [1, 59, 78, 359, 396] 中关于 CNN 在音频处理中的应用，以及参见 [46, 105, 236, 348, 408, 440] 中关于 CNN 在时间序列分析中的应用。最后，对于前馈 CNN 的近似结果，例如参见 Petersen & Voigtländer [34] 及其参考文献。

## 1.4.1 离散卷积

**定义 1.4.1** (离散卷积). 设 \(T \in \mathbb{N}\)，\(a_1, a_2, \ldots, a_T\)，\(w_1, w_2, \ldots, w_T\)，\(\mathbf{d}_1, \mathbf{d}_2, \ldots, \mathbf{d}_T \in \mathbb{N}\)，且设 \(A = (A_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,a_t\})} \in \mathbb{R}^{a_1 \times a_2 \times \ldots \times a_T}\)，\(W = (W_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,w_t\})} \in \mathbb{R}^{w_1 \times w_2 \times \ldots \times w_T}\) 满足对于所有 \(t \in \{1, 2, \ldots, T\}\) 有

\[\mathbf{d}_t = a_t - w_t + 1. \quad (1.106)\]

则我们记为 \(A * W = ((A * W)_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,\mathbf{d}_t\})} \in \mathbb{R}^{\mathbf{d}_1 \times \mathbf{d}_2 \times \ldots \times \mathbf{d}_T}\) 的张量，该张量满足对于所有 \(i_1 \in \{1, 2, \ldots, \mathbf{d}_1\}\)，\(i_2 \in \{1, 2, \ldots, \mathbf{d}_2\}\)，\(\ldots\)，\(i_T \in \{1, 2, \ldots, \mathbf{d}_T\}\) 有

\[(A * W)_{i_1,i_2,\ldots,i_T} = \sum_{r_1=1}^{w_1} \sum_{r_2=1}^{w_2} \cdots \sum_{r_T=1}^{w_T} A_{i_1 - r_1 + 1, i_2 - r_2 + 1, \ldots, i_T - r_T + 1} W_{r_1,r_2,\ldots,r_T}. \quad (1.107)\]

## 1.4.2 前馈 CNN 的结构化描述

**定义 1.4.2** (前馈 CNN 的结构化描述). 我们将 \(\mathbf{C}\) 定义为由以下给出的集合

\[\mathbf{C} = \bigcup_{T,L \in \mathbb{N}} \bigcup_{l_0,l_1,\ldots,l_L \in \mathbb{N}} \bigcup_{(c_k, i)_{k=0}^{L} \in (\{1,2,\ldots,L\} \times \{1,2,\ldots,T\})^{L+1} \subseteq \mathbb{N}} \left( \bigtimes_{k=1}^{L} \left( (\mathbb{R}^{c_k} \times \mathbb{R}^{c_k} \times \ldots \times \mathbb{R}^{c_k})^{l_k} \times l_{k-1} \times \mathbb{R}^{l_k} \right) \right). \quad (1.108)\]

**定义 1.4.3** (前馈 CNN). 当且仅当满足

\[\Phi \in \mathbf{C}. \quad (1.109)\]

时，我们称 \(\Phi\) 为前馈 CNN。

(参见定义 1.4.2.)

## 1.4.3 前馈 CNN 的实现

**定义 1.4.4** (单一张量). 设 \(T \in \mathbb{N}\)，\(d_1, d_2, \ldots, d_T \in \mathbb{N}\)。则我们记 \(\mathbf{I}_{d_1,d_2,\ldots,d_T} = (\mathbf{I}_{i_1,i_2,\ldots,i_T})_{(i_1,i_2,\ldots,i_T) \in (\times_{t=1}^T \{1,2,\ldots,d_t\})} \in \mathbb{R}^{d_1 \times d_2 \times \ldots \times d_T}\) 为满足以下条件的张量：对于所有 \(i_1 \in \{1, 2, \ldots, d_1\}\)，\(i_2 \in \{1, 2, \ldots, d_2\}\)，\(\ldots\)，\(i_T \in \{1, 2, \ldots, d_T\}\) 有

\[\mathbf{I}_{i_1,i_2,\ldots,i_T}^{d_1,d_2,\ldots,d_T} = 1. \quad (1.110)\]

## 1.4. 卷积神经网络（CNNs）

### 定义 1.4.5（与前馈 CNN 相关联的实现）

*设 $T, L \in \mathbb{N}$，$l_0, l_1, \dots, l_L \in \mathbb{N}$，令 $\{c_{k,t}\}_{(k,t) \in \{1, \dots, L\} \times \{1, 2, \dots, T\}} \subseteq \mathbb{N}$，令 $\Phi = (((W_{k,n,m})_{(n,m) \in \{1,2,\dots,l_k\} \times \{1,2,\dots,l_{k-1}\}}, (B_{k,n})_{n \in \{1,2,\dots,l_k\}})_{k \in \{1,2,\dots,L\}} \in \bigotimes_{k=1}^L ((\mathbb{R}^{c_{k,1} \times c_{k,2} \times \dots \times c_{k,T}})^{l_k \times l_{k-1}} \times \mathbb{R}^{l_k}) \subseteq \mathbb{C}$，且设 $a: \mathbb{R} \to \mathbb{R}$ 为一个函数。则我们将符号*

$$\mathcal{R}_a^\mathbf{C}(\Phi) : \left(\bigcup_{\substack{d_1,d_2,\dots,d_T \in \mathbb{N} \\ \forall t \in \{1,2,\dots,T\}: d_t - \sum_{k=1}^L c_{k,t-1} \geq 1}} (\mathbb{R}^{d_1 \times d_2 \times \dots \times d_T})^{l_0} \to \left(\bigcup_{d_1,d_2,\dots,d_T \in \mathbb{N}} (\mathbb{R}^{d_1 \times d_2 \times \dots \times d_T})^{l_L} \right) \tag{1.111}$$

*定义为满足以下条件的函数：对于所有 $\{\mathfrak{d}_{k,t}\}_{(k,t) \in \{0,1,\dots,L\} \times \{1,2,\dots,T\}} \subseteq \mathbb{N}$，$x_0 = (x_{0,1}, \dots, x_{0,l_0}) \in (\mathbb{R}^{\mathfrak{d}_{0,1} \times \mathfrak{d}_{0,2} \times \dots \times \mathfrak{d}_{0,T}})^{l_0}$，$x_1 = (x_{1,1}, \dots, x_{1,l_1}) \in (\mathbb{R}^{\mathfrak{d}_{1,1} \times \mathfrak{d}_{1,2} \times \dots \times \mathfrak{d}_{1,T}})^{l_1}$，$\dots$，$x_L = (x_{L,1}, \dots, x_{L,l_L}) \in (\mathbb{R}^{\mathfrak{d}_{L,1} \times \mathfrak{d}_{L,2} \times \dots \times \mathfrak{d}_{L,T}})^{l_L}$，其中*

$$\forall k \in \{1,2,\dots,L\}, \ t \in \{1,2,\dots,T\}: \mathfrak{d}_{k,t} = \mathfrak{d}_{k-1,t} - c_{k,t} + 1 \tag{1.112}$$

*且*

$$\forall k \in \{1,2,\dots,L\}, \ n \in \{1,2,\dots,l_k\} : \ x_{k,n} = \mathfrak{M}_{a|\{0,l_1(k)+\mathrm{id}_{\mathbb{R}}\,\mathbb{1}_{\{1\}(k)}\mathfrak{d}_{k,1},\mathfrak{d}_{k,2},\dots,\mathfrak{d}_{k,T}\}} (B_{k,n} \mathfrak{P}_{\mathfrak{d}_{k,1},\mathfrak{d}_{k,2},\dots,\mathfrak{d}_{k,T}} + \sum_{m=1}^{l_{k-1}} x_{k-1,m} * W_{k,n,m}) \tag{1.113}$$

*并且*

$$(\mathcal{R}_a^\mathbf{C}(\Phi))(x_0) = x_L \tag{1.114}$$

*我们将 $\mathcal{R}_a^\mathbf{C}(\Phi)$ 称为具有激活函数 $a$ 的前馈 CNN $\Phi$ 的实现函数（我们将 $\mathcal{R}_a^\mathbf{C}(\Phi)$ 称为具有激活函数 $a$ 的前馈 CNN $\Phi$ 的实现）（参见定义 1.2.1, 1.4.1, 1.4.2, 和 1.4.4）。*

```python
import torch
import torch.nn as nn


class ConvolutionalANN(nn.Module):
    def __init__(self):
        super().__init__()
        # The convolutional layer defined here takes any tensor of
        # shape (1, n, m) [a single input] or (N, 1, n, m) [a batch
        # of N inputs] where N, n, m are natural numbers satisfying
        # n >= 3 and m >= 3.
        self.conv1 = nn.Conv2d(
                in_channels=1, out_channels=5, kernel_size=(3, 3)
        )
        self.activation1 = nn.ReLU() 
        self.conv2 = nn.Conv2d(
            in_channels=5, out_channels=5, kernel_size=(5, 3)
        )
    
    def forward(self, x0):
        x1 = self.activation1(self.conv1(x0))
        print(x1.shape)
        x2 = self.conv2(x1)
        print(x2.shape)
        return x2
   

model = ConvolutionalANN()
x0 = torch.rand(1, 20, 20)
# This will print the shapes of the outputs of the two layers of
# the model, in this case:
# torch.Size([5, 18, 18])
# torch.Size([5, 14, 16])
model(x0)
```
