

## 7.4 单层循环神经网络的实现

### 7.4.1 初始化模型参数

循环神经网络沿时间维度计算序列数据。如果在任意时刻 `t`，输入 `x^(⟨t⟩)` 是一个长度为 `input_dim` 的向量，单层神经网络的神经元数量为 `hidden_dim`，输出 `f^(⟨t⟩)` 是一个长度为 `output_dim` 的向量，则可以使用以下函数 `rnn_params_init()` 来初始化网络的模型参数。

```python
import numpy as np

np.random.seed(1)

def rnn_params_init(input_dim, hidden_dim, output_dim, scale=0.01):
    Wx = np.random.randn(input_dim, hidden_dim) * scale  # 输入到隐藏层
    Wh = np.random.randn(hidden_dim, hidden_dim) * scale  # 隐藏层到隐藏层
    bh = np.zeros((1, hidden_dim))  # 隐藏层偏置
    Wf = np.random.randn(hidden_dim, output_dim) * scale  # 隐藏层到输出
    bf = np.zeros((1, output_dim))  # 输出偏置
    return [Wx, Wh, bh, Wf, bf]
```

除了模型参数外，还需要初始化 RNN 网络的隐藏状态向量 `h`。一个输入样本 `x` 对应一个隐藏状态向量 `h`。训练模型时，如果输入一批样本 `X = (x^(1), x^(2), ..., x^(m))^T`，它将对应一批隐藏状态向量 `H = (h^(1), h^(2), ..., h^(m))^T`。以下函数用于初始化一批样本的隐藏状态向量 `H`：

```python
def rnn_hidden_state_init(batch_dim, hidden_dim):
    return np.zeros((batch_dim, hidden_dim))
```

### 7.4.2 前向计算

循环神经网络是一个在时间维度上顺序处理序列数据的过程。训练循环神经网络时，通常使用一序列数据进行训练。如果使用批量梯度下降法，训练模型的序列数据长度为 `T`，则在 `t = 0, 1, ..., T-1` 每个时刻都会有一批样本。如果用 `Xs` 表示序列数据，每个时刻 `t` 的数据用 `Xs[t]` 表示，则以下函数从时刻 `t=0` 顺序计算到最后一个时刻 `t = len(Xs)-1` 每个时刻的隐藏状态 `Hs[t]` 和输出值 `Fs[t]`。

```python
def rnn_forward(params, Xs, H_):
    Wx, Wh, bh, Wf, bf = params
    H = H_  # np.copy(H_)
    Fs = []
    Hs = {}
    Hs[-1] = np.copy(H)
    for t in range(len(Xs)):
        X = Xs[t]
        H = np.tanh(np.dot(X, Wx) + np.dot(H, Wh) + bh)
        F = np.dot(H, Wf) + bf
        Fs.append(F)
        Hs[t] = H
    return Fs, Hs
```

其中 `params` 是模型参数，`H_` 是 `t=0` 时的隐藏状态输入（通常初始值为 0）。

假设每个序列元素是一个一维向量，则 `Xs` 是一个三维张量，即有 3 个轴分别代表序列长度、批量大小和输入数据长度。如图 7-22 所示，

**图 7-22** `Xs` 是一个三维张量，其三个轴分别代表序列长度 `T`、批量大小 `batch_dim` 和输入数据长度 `input_dim`。

`Hs` 用字典表示。`Hs[-1]` 代表 `t=0` 时的输入状态，`Hs[t]` 代表时刻 `t` 的输出状态。因为此时 `len(Hs) = len(Xs) + 1`，所以 `Hs[len(Hs)-2]` 是最后一个时刻 `len(Xs)-1` 的状态。每个 `Hs[t]` 是一个二维张量，第一个轴代表批量大小，第二个轴代表状态向量长度，即 `hidden_dim`。同理，`Fs` 代表所有时刻的输出值，可以表示为三维张量或列表。每个时刻的 `Fs[t]` 是一个二维张量，第一个轴代表批量大小，第二个轴代表输出向量的大小，即 `output_dim`。

每个时刻的前向计算过程可以写成一个单独的函数 `rnn_forward_step()`：

```python
def rnn_forward_step(params, X, preH):
    Wx, Wh, bh, Wf, bf = params
    H = np.tanh(np.dot(X, Wx) + np.dot(preH, Wh) + bh)
    F = np.dot(H, Wf) + bf
    return F, H
```

其中，`X` 是某一时刻的输入，`preH` 是上一时刻的隐藏状态，它们都是二维张量。所有时刻的前向计算过程可以写成函数 `rnn_forward_()`：

```python
def rnn_forward_(params, Xs, H_):
    Wx, Wh, bh, Wf, bf = params
    H = H_
    Fs = []
    Hs = {}
    Hs[-1] = np.copy(H)
    for t in range(len(Xs)):
        X = Xs[t]
        F, H = rnn_forward_step(params, X, H)
        Fs.append(F)
        Hs[t] = H
    return Fs, Hs
```

### 7.4.3 损失函数

根据输出值 `Fs` 和目标值 `Ys`，可以计算模型的损失。如果这是一个同步多对多循环神经网络，则需要计算每个时刻 `t` 的损失 `L[t]`，所有时刻的累积损失即为总损失 $\mathcal{L} = \sum_{t=1}^{T} \mathcal{L}_t$。

根据问题不同，损失 `L[t]` 可以是回归问题的均方误差损失，也可以是分类问题的交叉熵损失。以下函数 `rnn_loss_grad()` 使用传入的函数对象参数 `loss_fn()` 来计算每个时刻的损失 `loss_t` 以及损失相对于输出 `Fs[i]` 的梯度 `dF_t`。并将所有时刻的梯度放在字典变量 `dFs` 中。

```python
import util

def rnn_loss_grad(Fs, Ys, loss_fn=util.loss_gradient_softmax_crossentropy, flatten=True):
    loss = 0
    dFs = {}
    for t in range(len(Fs)):
        F = Fs[t]
        Y = Ys[t]
        if flatten and Y.ndim >= 2:
            Y = Y.flatten()
        loss_t, dF_t = loss_fn(F, Y)
        loss += loss_t
        dFs[t] = dF_t
    return loss, dFs
```

