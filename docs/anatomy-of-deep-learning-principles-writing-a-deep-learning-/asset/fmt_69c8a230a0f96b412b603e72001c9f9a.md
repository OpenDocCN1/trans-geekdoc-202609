
在反向推导过程中，不需要计算中间层关于 `a[l]` 的梯度，只需计算损失函数关于 `z[l]` 的梯度 `δ[l]`。

最后需要注意的是，如果输出层不直接输出加权和 `z[L]`，而是经过激活函数 `a[L] = f(z[L])` 输出，对于方差损失 $\frac{1}{2} \parallel a[L] - y \parallel^{2}$，损失函数关于 `a[L]` 的梯度 $\frac{\partial\mathcal{L}}{\partial a[L]} = a[L] - y$，然后根据 $\frac{\partial\mathcal{L}}{\partial z[L]} = \frac{\partial\mathcal{L}}{\partial a[L]}f'(z[L])$ 计算梯度 $\frac{\partial\mathcal{L}}{\partial z[L]}$。

$$
\delta^{(L)} = \frac{\partial L}{\partial z[L]} = \frac{\partial\mathcal{L}}{\partial a[L]}f'(z[L])
$$

对于二分类问题，激活函数 `f` 是 `σ` 函数，多分类问题则是 softmax 函数。交叉熵损失中 `a[L]` 和目标值 `y` 关于加权和 `z[L]` 的梯度 $\frac{\partial\mathcal{L}}{\partial z[L]} = a[L] - y$（多分类时 `y` 为 one-hot 向量形式）。多样本情况下，梯度为 $\frac{\partial\mathcal{L}}{\partial Z[L]} = \frac{1}{m}(A[L] - Y)$。

如果输出层直接输出加权和 `z[L]` 而不经过激活函数，则：

$$
\delta^{(L)} = \frac{\partial\mathcal{L}}{\partial z[L]} = f(z[L]) - y
$$

其中，回归问题 `f` 为恒等函数（假设方差损失 $\frac{1}{2} \parallel z[L] - y \parallel^{2}$），二分类或多分类 `f` 为 sigmoid 函数 `σ` 或 softmax 函数。多样本情况下，梯度为 $\frac{\partial\mathcal{L}}{\partial Z[L]} = \frac{1}{m}(f(Z[L]) - Y)$。

输出层损失函数的梯度公式，连同以下三个公式，称为反向推导的四大公式：

$$
\begin{matrix}
\frac{\partial\mathcal{L}}{\partial\mathbf{W}^{(l)}} = \mathbf{\delta}^{(l)}(\mathbf{a}^{(l - 1)})^{\text{T}} = \begin{bmatrix}
\delta_{1}^{(l)}a_{1}^{(l - 1)} & \delta_{1}^{(l)}a_{2}^{(l - 1)} & \cdots & \delta_{1}^{(l)}a_{k}^{(l - 1)} \\
\delta_{2}^{(l)}a_{1}^{(l - 1)} & \delta_{2}^{(l)}a_{2}^{(l - 1)} & \cdots & \delta_{2}^{(l)}a_{k}^{(l - 1)} \\
\vdots & \vdots & \ddots & \\
\delta_{j}^{(l)}a_{1}^{(l - 1)} & \delta_{j}^{(l)}a_{2}^{(l - 1)} & \cdots & \delta_{j}^{(l)}a_{k}^{(l - 1)} \\
\end{bmatrix} \\
\frac{\partial\mathcal{L}}{\partial\mathbf{b}^{(l)}} = \mathbf{\delta}^{(l)} \\
\delta^{[l - 1]} = ({W^{[l]}}^{T}\delta^{[l]}) \odot g'(z^{[l - 1]})
\end{matrix}
$$

其向量形式：

$$
\begin{matrix}
\frac{\partial\mathcal{L}}{\partial\mathbf{W}^{(l)}} = \mathbf{\delta}^{(l)}(\mathbf{a}^{(l - 1)})^{\text{T}} = \frac{\partial\mathcal{L}}{\partial z[l]}(\mathbf{a}^{(l - 1)})^{\text{T}} \\
\frac{\partial\mathcal{L}}{\partial\mathbf{b}^{(l)}} = \mathbf{\delta}^{(l)} = \frac{\partial\mathcal{L}}{\partial z[l]} \\
\delta^{[l - 1]} = ({W^{[l]}}^{T}\delta^{[l]}) \odot g'(z[l - 1]) = ({W^{[l]}}^{T}\frac{\partial\mathcal{L}}{\partial z[l]}) \odot g'(z[l - 1])
\end{matrix}
$$

多样本的向量形式：

$$
\begin{matrix}
\frac{\partial\mathcal{L}}{\partial\mathbf{W}^{(l)}} = \frac{\partial\mathcal{L}}{\partial Z[l]}(\mathbf{A}^{(l - 1)})^{\text{T}} \\
\frac{\partial\mathcal{L}}{\partial\mathbf{b}^{(l)}} = np.sum(\frac{\partial\mathcal{L}}{\partial Z[l]}, axis=1, keepdims=True) \\
\frac{\partial\mathcal{L}}{\partial Z[l - 1]} = ({W^{[l]}}^{T}\frac{\partial\mathcal{L}}{\partial Z[l]}) \odot g'(Z[l - 1])
\end{matrix}
$$

## 4.3 实现简单的深度学习框架

### 4.3.1 神经网络的训练过程

与其他机器学习算法一样，神经网络的训练过程包括：

*   **准备数据**：准备用于训练模型的样本数据集，除训练集外可能包含验证集和测试集；
*   **确定神经网络结构**：针对具体问题设计合适的神经网络模型。模型规模过大，训练时间长且难以训练；模型规模过小，表达能力可能不足。需根据实际问题选择合适的网络结构。网络结构还包括选择何种激活函数、定义何种误差（损失）评价方法即何种损失函数；
*   **训练模型**：包括模型参数的随机初始化，以及使用梯度下降法寻找最优解。可能需要验证集协助选择合适的模型和超参数，以避免过拟合和欠拟合。

与回归模型类似，神经网络也使用梯度下降算法训练模型以找到最合适的模型参数。梯度下降算法可分为三步：

1.  **前向传播计算模型输出和损失函数值**：
    *   1.1 从第一层开始，依次计算各后续层的中间变量和激活输出值，直到输出层。
        $$Z[l] = X W[l] + b[l] = A[l-1] W[l] + b[l]$$
        $$A[l] = g[l](Z[l])$$
    *   1.2 根据不同的损失评价标准计算损失函数值
        $$\mathcal{L} = \mathcal{L}(A[L], y)$$

2.  **反向推导**：
    *   计算损失函数关于输出层输出的梯度，即 $\delta^{[L]} = \frac{\partial\mathcal{L}}{\partial Z^{[L]}}$
    *   从输出层 L 一直到第 1 层，计算损失函数关于 W、b、x 的梯度 $\frac{\partial\mathcal{L}}{\partial W^{[l]}}, \frac{\partial\mathcal{L}}{\partial b^{[l]}}, \frac{\partial\mathcal{L}}{\partial A^{[l-1]}}, \frac{\partial\mathcal{L}}{\partial Z^{[l-1]}}$。

    $$
    \frac{\partial\mathcal{L}}{\partial W^{[l]}} = {A^{[l-1]}}^{T}\frac{\partial\mathcal{L}}{\partial Z^{[l]}}
    $$
    $$
    \frac{\partial\mathcal{L}}{\partial b^{[1]}} = np.sum(\frac{\partial\mathcal{L}}{\partial Z^{[1]}}, axis=0, keepdims=True)
    $$
    $$
    \frac{\partial\mathcal{L}}{\partial A^{[l-1]}} = \frac{\partial\mathcal{L}}{\partial Z^{[l]}}{W^{[l]}}^{T}
    $$
    $$
    \frac{\partial\mathcal{L}}{\partial Z^{[l]}} = \frac{\partial\mathcal{L}}{\partial A^{[l]}} \cdot g'(Z^{[l]})
    $$

3.  **更新模型参数**
