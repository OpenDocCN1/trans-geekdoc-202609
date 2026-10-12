
```python
import math

def grad_clipping(grads, alpha):
    norm = math.sqrt(sum((grad ** 2).sum() for grad in grads))
    if norm > alpha:
        ratio = alpha / norm
        for i in range(len(grads)):
            grads[i] *= ratio

def rnn_backward(params, Xs, Hs, dZs, clip_value=5.):  # Ys, loss_function):
    Wx, Wh, bh, Wf, bf = params
    dWx, dWh, dWf = np.zeros_like(Wx), np.zeros_like(Wh), np.zeros_like(Wf)
    dbh, dbf = np.zeros_like(bh), np.zeros_like(bf)
    dh_next = np.zeros_like(Hs[0])
    h = Hs
    x = Xs
    T = len(Xs)  # 序列长度（时间长度）
    for t in reversed(range(T)):
        dZ = dZs[t]
        dWf += np.dot(h[t].T, dZ)
        dbf += np.sum(dZ, axis=0, keepdims=True)
        dh = np.dot(dZ, Wf.T) + dh_next
        dZh = (1 - h[t] * h[t]) * dh
        dbh += np.sum(dZh, axis=0, keepdims=True)
        dWx += np.dot(x[t].T, dZh)
        dWh += np.dot(h[t-1].T, dZh)
        dh_next = np.dot(dZh, Wh.T)
    grads = [dWx, dWh, dbh, dWf, dbf]
    if clip_value is not None:
        grad_clipping(grads, clip_value)
    return grads
```

由于循环网络随时间展开，类似于深度神经网络，会出现梯度爆炸和梯度消失问题。为了解决梯度爆炸问题，可以使用梯度裁剪方法防止梯度爆炸。如上述代码 `backward()` 函数所示，在最后对梯度进行裁剪 `grad_clipping(grads, 5.)`。

同样，每一时刻的反向推导可以写成单独的函数 `rnn_backward_step()`：

```python
def rnn_backward_step(params, dZ, X, H, H_, dh_next):
    Wx, Wh, bh, Wf, bf = params
    dWf = np.dot(H.T, dZ)
    dbf = np.sum(dZ, axis=0, keepdims=True)
    dh = np.dot(dZ, Wf.T) + dh_next
    dZh = (1 - H * H) * dh
    dbh = np.sum(dZh, axis=0, keepdims=True)
    dWx = np.dot(X.T, dZh)
    dWh = np.dot(H_.T, dZh)
    dh_next = np.dot(dZh, Wh.T)
    return dWx, dWh, dbh, dWf, dbf, dh_next
```

对序列数据进行反向微分的函数可以调用这个单时刻反向微分函数：

```python
def rnn_backward_(params, Xs, Hs, dZs, clip_value=5.):
    Wx, Wh, bh, Wf, bf = params
    dWx, dWh, dWf = np.zeros_like(Wx), np.zeros_like(Wh), np.zeros_like(Wf)
    dbh, dbf = np.zeros_like(bh), np.zeros_like(bf)
    dh_next = np.zeros_like(Hs[0])
    T = len(Xs)  # 序列长度（时间长度）
    for t in reversed(range(T)):
        dZ = dZs[t]
        H = Hs[t]
        H_ = Hs[t-1]
        X = Xs[t]
        dWx_, dWh_, dbh_, dWf_, dbf_, dh_next = rnn_backward_step(params, dZ, X, H, H_, dh_next)
        for grad, grad_t in zip([dWx, dWh, dbh, dWf, dbf], [dWx_, dWh_, dbh_, dWf_, dbf_]):
            grad += grad_t
    grads = [dWx, dWh, dbh, dWf, dbf]
    if clip_value is not None:
        grad_clipping(grads, clip_value)
    return grads
```

### 7.4.5 梯度验证

为了验证反向推导是否正确，可以定义一个简单的 RNN 模型，并使用一组测试样本比较解析梯度和数值梯度。以下代码针对输入层、隐藏层和输出层大小分别为 4、10 和 4 的 RNN。模型生成一组测试样本：

```python
import numpy as np

np.random.seed(1)

# 生成一批样本 Xs，每批 2 个样本，共 4 个时刻的目标
# 定义一个输入层、隐含层、输出层大小分别为 4、10、4 的 RNN 模型
if True:
    T = 5
    input_dim, hidden_dim, output_dim = 4, 10, 4
    batch_size = 1
    seq_len = 5
    Xs = np.random.rand(seq_len, batch_size, input_dim)
    # Ys = np.random.randint(input_dim, size=(seq_len, batch_size, output_dim))
    Ys = np.random.randint(input_dim, size=(seq_len, batch_size))
    # Ys = Ys.reshape(Ys.shape[0], Ys.shape[1])
else:
    input_size, hidden_size, output_size = 4, 3, 4
    batch_size = 1
    vocab_size = 4
    inputs = [0, 1, 2, 2]   # hello
    targets = [1, 2, 2, 3]
    Xs = []
    Ys = []
    for t in range(len(inputs)):
        X = np.zeros((1, vocab_size))  # 采用 1-of-k 编码表示
        X[0, inputs[t]] = 1
        Xs.append(X)
        Ys.append(targets[t])

print(Xs)
print(Ys)
```

```
[[[4.17022005e-01 7.20324493e-01 1.14374817e-04 3.02332573e-01]]
 [[1.46755891e-01 9.23385948e-02 1.86260211e-01 3.45560727e-01]]
 [[3.96767474e-01 5.38816734e-01 4.19194514e-01 6.85219500e-01]]
 [[2.04452250e-01 8.78117436e-01 2.73875932e-02 6.70467510e-01]]
 [[4.17304802e-01 5.58689828e-01 1.40386939e-01 1.98101489e-01]]]
[[1]
 [1]
 [1]
 [3]
 [3]]
```

以下代码计算上述样本的解析梯度：

```python
# --------check gradient-------------
params = rnn_params_init(input_dim, hidden_dim, output_dim)
H_0 = rnn_hidden_state_init(batch_size, hidden_dim)
Fs, Hs = rnn_forward(params, Xs, H_0)
loss_function = rnn_loss_grad
print(Fs[0].shape, Ys[0].shape)
loss, dFs = loss_function(Fs, Ys)
grads = rnn_backward(params, Xs, Hs, dFs)
```

```
(1, 4) (1,)
```

以下代码定义了用于计算 RNN 损失的辅助函数 `rnn_loss()`，然后调用 `util` 中的通用数值梯度函数 `numerical_gradient()` 计算 RNN 模型参数的数值梯度，并与上述解析梯度比较误差，同时输出模型参数的第一组梯度：

```python
def rnn_loss():
    H_0 = np.zeros((1, hidden_dim))
    H = np.copy(H_0)
    Fs, Hs = rnn_forward(params, Xs, H)
    loss_function = rnn_loss_grad
    loss, dFs = loss_function(Fs, Ys)
    return loss

numerical_grads = util.numerical_gradient(rnn_loss, params, 1e-6)  # rnn_numerical_gradient(rnn_loss, params, 1e-10)
# diff_error = lambda x, y: np.max(np.abs(x - y))
diff_error = lambda x, y: np.max(np.abs(x - y) / (np.maximum(1e-8, np.abs(x) + np.abs(y))))

print("loss", loss)
print("[dWx, dWh, dbh, dWf, dbf]")
for i in range(len(grads)):
    print(diff_error(grads[i], numerical_grads[i]))

print("grads", grads[1][:2])
print("numerical_grads", numerical_grads[1][:2])
```

```
loss 6.931604253116049
[dWx, dWh, dbh, dWf, dbf]
4.30868739852771e-06
0.00014321848390554473
8.225164888798296e-08
2.030282934604882e-07
1.155121982079175e-10
grads [[-2.39049602e-04 8.14220495e-05 1.57776751e-04 5.67414815e-05
  -2.52527076e-04 7.67751376e-05 8.81253550e-05 2.07270381e-04
  -6.92579913e-05 5.33532921e-05]
 [-1.59775181e-04 8.33693576e-05 7.68434971e-05 4.16925859e-05
  -1.31768112e-04 1.87065893e-05 3.02967764e-05 1.17071893e-04
  -3.32692578e-05 2.22690120e-05]]
numerical_grads [[-2.39049225e-04 8.14224244e-05 1.57776459e-04 5.67408343e-05
  -2.52526444e-04 7.67759190e-05 8.81255069e-05 2.07270645e-04
  -6.92583768e-05 5.33533218e-05]
 [-1.59774860e-04 8.33693115e-05 7.68434205e-05 4.16924273e-05
```

### 7.4.6 梯度下降训练

在前向计算、损失函数和反向推导的基础上，可以使用训练样本对 RNN 模型进行训练。首先，定义最基础的更新参数的梯度优化器 `SGD`：

```python
class SGD():

    def __init__(self, model_params, learning_rate=0.01, momentum=0.9):

        self.params, self.lr, self.momentum = model_params, learning_rate, momentum

        self.vs = []

        for p in self.params:

            v = np.zeros_like(p)

            self.vs.append(v)

    def step(self, grads):

        for i in range(len(self.params)):

            grad = grads[i]

            self.vs[i] = self.momentum * self.vs[i] + self.lr * grad

            self.params[i] -= self.vs[i]

    def scale_learning_rate(self, scale):

        self.lr *= scale
```

当然，也可以使用其他参数优化器，例如 `AdaGrad` 优化器：

```python
class AdaGrad():

    def __init__(self, model_params, learning_rate=0.01):

        self.params, self.lr = model_params, learning_rate

        self.vs = []

        self.delta = 1e-7

        for p in self.params:

            v = np.zeros_like(p)

            self.vs.append(v)

    def step(self, grads):

        for i in range(len(self.params)):

            grad = grads[i]

            self.vs[i] += grad**2

            self.params[i] -= self.lr * grad / (self.delta + np.sqrt(self.vs[i]))

    def scale_learning_rate(self, scale):

        self.lr *= scale
```

下面的训练函数 `rnn_train_epoch()` 使用数据迭代器 `data_iter` 遍历采样训练数据集以完成一个训练过程。该函数每次从数据迭代器 `data_iter` 获取一批序列训练样本。每个样本序列 (`Xs`, `Ys`) 由多个时刻的样本组成。`start` 指示该样本序列是否与前一个样本序列首尾相连。对于每个样本序列 (`Xs`, `Ys`)，首先使用 `rnn_forward(params, Xs, H)` 计算每个时刻的输出 `Zs` 和状态 `Hs`，然后使用损失函数 `loss_function(Zs, Ys)` 计算模型的损失以及损失对输出的梯度 `dzs`，再通过反向推导 `rnn_backward(params, Xs, Hs, dzs)` 计算损失对模型参数的梯度，最后更新模型参数。`iterations` 是最大迭代次数，用于防止无限循环，`print_n` 表示打印信息的间隔数。
