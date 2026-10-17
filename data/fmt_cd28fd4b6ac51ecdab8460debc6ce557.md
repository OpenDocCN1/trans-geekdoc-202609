
```python
def predict_lstm(params, prefix, n):
    Wi, bi, Wf, bf, Wo, bo, Wc, bc, Wy, by = params
    vocab_size, hidden_dim = Wi.shape[0] - Wy.shape[0], Wy.shape[0]
    h, c = lstm_state_init(1, hidden_dim)
    output = [char_to_idx[prefix[0]]]

    for t in range(len(prefix) + n - 1):
        # Use the output of the previous time step as the input of the current time step.
        x = one_hot_idx(output[-1], vocab_size)
        z, h, c, _ = lstm_forward_step(params, x, h, c)

        if t < len(prefix) - 1:
            output.append(char_to_idx[prefix[t + 1]])
        else:
            p = np.exp(z) / np.sum(np.exp(z))
            # idx = int(p.argmax(axis=1))
            idx = np.random.choice(range(vocab_size), p=p.ravel())
            output.append(idx)

    return ''.join([idx_to_char[i] for i in output])
```

```python
str = predict_lstm(params, "he", 200)
print(str)
```

###### 输出示例

```
he done!

GLOUCESTER:
Why was I being your houghcessing in lord?

CARILLO:
How, or your his dessent;
Come his false, what comon:

HASTINGS:
Put she with your howiring act a both,
But long and you have

T
```

### 7.7.4 LSTM 的变体

以上是最经典的 LSTM，实际使用的 LSTM 模型往往略有不同。Gers & Schmidhuber (2000) 引入了“peephole connection”（窥孔连接），如图 7-42 所示，使得各个门可以观察细胞的状态。

![](img/file161.png "fig:")

图 7-42 引入“peephole connection”的 LSTM

在该图中，所有门都添加了“peepholes”（窥孔），即 `f[t]`、`i[t]`、`o[t]` 可以看到相应的细胞状态 `C[t-1]`、`C[t]`。不过，也有一些论文只添加一部分。

考虑到 LSTM 细胞过于复杂，2014 年 Kyunghyun Cho 等人提出了一种更多样化的 LSTM 变体——**门控循环单元**（**Gated Recurrent Unit, GRU**）。GRU 将遗忘门和输入门合并为单个“更新门”，将细胞状态和隐藏状态合并，并引入了一些其他变化。该模型比标准 LSTM 模型更简化，效果却优于经典 LSTM，因此现在越来越流行。

还有一些其他模型，例如 Yao 等人 (2015) 提出的 Depth Gated RNNs。同时，也有许多完全不同的方法来解决长期依赖问题，例如 Koutnik 等人 (2014) 提出的 Clockwork RNNs。

不同模型哪个最好？差异真的重要吗？Greff 等人 (2015) 对流行变体进行了比较，发现它们基本相同。Jozefowicz 等人 (2015) 测试了超过 10,000 种 RNN 结构，发现其中一些在特定任务上的表现优于 LSTM。

## 7.8 门控循环单元 (GRU)

### 7.8.1 GRU 的工作原理

与 LSTM 使用 `C[t]` 和 `H[t]` 分别表示总历史信息和参与下一时刻计算的历史信息不同，GRU 像简单的 RNN 一样，仅使用一个隐藏状态 `H[t]` 来表示所有历史信息。与 LSTM 一样，GRU 也有遗忘门，也称为重置门，用于表示记忆信息对当前时刻计算的影响，以及用于当前激活值 `H_tilde_t` 和历史信息 `H[t-1]` 更新当前时刻历史信息 `H[t]` 的更新门。如图 7-43 所示，GRU 单元中有两个门：重置门 R 和更新门 U。

![](img/file162.png "fig:")

图 7-43 GRU 的重置门和更新门

与 LSTM 的门一样，这两个门输出 `[0,1]` 之间的值，计算公式如下：

**R[t]** = `σ(X[t]W[xr] + H[t-1]W[hr] + W[hr] + mathbfb[r])`

**U[t]** = `σ(X[t]W[xu] + H[t-1]W[hu] + W[hu] + mathbfb[u])`

普通 RNN 神经元使用历史信息 `H[t-1]` 和当前输入数据 `X[t]` 计算当前时刻的信息，即隐藏状态 `H[t]`。

**H[t]** = `tanh(X[t]W[xh] + H[t-1]W[hh] + W[hh] + mathbfb[h])`

重置门表示本次计算遗忘了多少历史记忆，或者说保留了多少历史记忆参与本次计算，即重置门的输出值 `R[t]` 乘以历史记忆 `H[t-1]` 参与当前信息的计算。

`H_tilde_t = tanh(X_t W_xh + (R_t ⊙ H_{t-1}) W_hh + b_h)`

这个 `H_tilde_t` 表示当前时刻的激活值，也称为**当前候选记忆**。如图 7-44 所示：

![](img/file163.png "fig:")

图 7-44 GRU 当前工作单元输出当前时刻的激活值

通过更新门对当前候选记忆 `H_tilde_t` 和历史记忆 `H[t-1]` 进行加权平均，作为当前时刻的隐藏状态：

`H_t = U_t ⊙ H_{t-1} + (1 - U_t) ⊙ H_tilde_t`

如图 7-45 所示，更新门的输出值 **U[t]** 用于对历史记忆和当前候选记忆进行加权平均，

![](img/file164.png "fig:")

图 7-45 GRU 神经网络单元的完整结构，更新门输出当前隐藏状态 `H[t]`

GRU 的反向推导与 LSTM 类似。在已知损失函数对 GRU 输出的梯度 dZ 后，反向推导计算损失函数对模型参数和中间变换的梯度。读者可以模仿 LSTM 的反向推导来推导 GRU 的反向推导公式。

与 LSTM 一样，GRU 可以维持长期记忆并防止梯度爆炸和消失。其性能也与 LSTM 相当，甚至在某些问题上优于 LSTM。其实现比 LSTM 更简单，计算效率更高。因此，在实际使用中，通常用 GRU 代替传统的 LSTM。

### 7.8.2 GRU 代码实现

GRU 的代码实现与 LSTM 类似。以下是实现代码：

```python
import numpy as np

def sigmoid(x):
    return 1 / (1 + np.exp(-x))

def gru_init_params(input_dim, hidden_dim, output_dim, scale=0.01):
    normal = lambda m, n: np.random.randn(m, n) * scale
    three = lambda: (normal(input_dim, hidden_dim), normal(hidden_dim, hidden_dim), np.zeros((1, hidden_dim)))

    Wxu, Whu, bu = three()  # 更新门参数
    Wxr, Whr, br = three()  # 重置门参数
    Wxh, Whh, bh = three()  # 候选隐藏状态参数

    Wy = normal(hidden_dim, output_dim)
    by = np.zeros((1, output_dim))

    params = [Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by]
    return params

def gru_state_init(batch_size, hidden_size):
    return np.zeros((batch_size, hidden_size))

def gru_forward(params, Xs, H_0):
    Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by = params

    H = H_0
    Hs = {}
    Ys = []
    Hs[-1] = np.copy(H)
    Rs = []
    Us = []
    H_tildas = []

    for t in range(len(Xs)):
        X = Xs[t]

        U = sigmoid(np.dot(X, Wxu) + np.dot(H, Whu) + bu)
        R = sigmoid(np.dot(X, Wxr) + np.dot(H, Whr) + br)
        H_tilda = np.tanh(np.dot(X, Wxh) + np.dot(R * H, Whh) + bh)

        H = U * H + (1 - U) * H_tilda

        Y = np.dot(H, Wy) + by

        Hs[t] = H
        Ys.append(Y)
        Rs.append(R)
        Us.append(U)
        H_tildas.append(H_tilda)

    return Ys, Hs, (Rs, Us, H_tildas)

def gru_backward(params, Xs, Hs, dZs, cache):  # Ys, loss_function):
    Wxu, Whu, bu, Wxr, Whr, br, Wxh, Whh, bh, Wy, by = params

    Rs, Us, H_tildas = cache

    dWxu, dWhu, dWxr, dWhr, dWxh, dWhh, dWy = np.zeros_like(Wxu), np.zeros_like(Whu), np.zeros_like(Wxr), np.zeros_like(Whr), np.zeros_like(Wxh), np.zeros_like(Whh), np.zeros_like(Wy)
    dbu, dbr, dbh, dby = np.zeros_like(bu), np.zeros_like(br), np.zeros_like(bh), np.zeros_like(by)

    dH_next = np.zeros_like(Hs[0])

    input_dim = Xs[0].shape[1]
    T = len(Xs)

    for t in reversed(range(T)):
        R = Rs[t]
        U = Us[t]
        H = Hs[t]
        X = Xs[t]
        H_tilda = H_tildas[t]
        H_pre = Hs[t-1]
        dZ = dZs[t]

        # 输出层模型参数的梯度
        dWy += np.dot(H.T, dZ)
        dby += np.sum(dZ, axis=0, keepdims=True)

        # 隐藏状态 h 的梯度
        dH = np.dot(dZ, Wy.T) + dH_next

        # H = U H_pre + (1-U) H_tildas
        dH_tilda = dH * (1 - U)
        dH_pre = dH * U
        dU = H_pre * dH - H_tilda * dH
```

# H_tilda = tanh(X Wxh+(R*H_)Whh+bh)

```
dH_tildaZ = (1-np.square(H_tilda))*dH_tilda

dWxh+= np.dot(X.T,dH_tildaZ)

dWhh+= np.dot((R*H_pre).T,dH_tildaZ)

dbh += np.sum(dH_tildaZ, axis=0, keepdims=True)

dR = np.dot(dH_tildaZ, Whh.T)*H_pre

dH_pre += np.dot(dH_tildaZ, Whh.T)*R

# U = \sigma(UZ)   R = \sigma(RZ)                

dUZ = U*(1-U)*dU

dRZ = R*(1-R)*dR       

dH_pre += np.dot(dUZ, Whu.T)

dH_pre += np.dot(dRZ, Whr.T)

# R = \sigma(X Wxr+H_ Whr + br)        

dWxr+= np.dot(X.T,dRZ)

dWhr+= np.dot(H_pre.T,dRZ)

dbr += np.sum(dRZ, axis=0, keepdims=True)

dWxu+= np.dot(X.T,dUZ)

dWhu+= np.dot(H_pre.T,dUZ)

dbu += np.sum(dUZ, axis=0, keepdims=True)

if True:

    dX_RZ = np.dot(dRZ,Wxr.T)

    dX_UZ = np.dot(dUZ,Wxu.T)

    dX_H_tildaZ = np.dot(dH_tildaZ,Wxh.T)

    dX = dX_RZ+dX_UZ+dX_H_tildaZ

dH_next = dH_pre

return [dWxu, dWhu, dbu, dWxr, dWhr, dbr, dWxh, dWhh, dbh, dWy,dby]
```

使用以下代码检查解析梯度和数值梯度是否一致：

```
T  = 3

input_dim, hidden_dim,output_dim = 4,3,4

batch_size = 1        

Xs = np.random.randn(T,batch_size,input_dim)

Ys = np.random.randint(output_dim, size=(T,batch_size))

print("Xs",Xs)

print("Ys",Ys)        

# cheack gradient  

params = gru_init_params(input_dim, hidden_dim,output_dim)

HC = gru_state_init(batch_size,hidden_dim)

Zs,Hs,cache = gru_forward(params,Xs,HC) 

loss_function = rnn_loss_grad

loss,dZs = loss_function(Zs,Ys)  

grads = gru_backward(params,Xs,Hs,dZs,cache)

def rnn_loss():

    HC = gru_state_init(batch_size,hidden_dim)    

    Zs,Hs,cache= gru_forward(params,Xs,HC) 

    loss_function = rnn_loss_grad

    loss,dZs = loss_function(Zs,Ys)     

    return loss

numerical_grads = util.numerical_gradient(rnn_loss,params,1e-6) #rnn_numerical_gradient(rnn_loss,params,1e-10)

#diff_error = lambda x, y: np.max( np.abs(x - y)/(np.maximum(1e-8, np.abs(x) + np.abs(y))))

diff_error = lambda x, y: np.max( np.abs(x - y))

def rel_error(x, y):

  """ 返回相对误差 """

  return np.max(np.abs(x - y) / (np.maximum(1e-8, np.abs(x) + np.abs(y))))

print("loss",loss)

print("[Wi, bi,Wf, bf, Wo,bo,Wc, bc,Wy,by] ")

for i in range(len(grads)):

    print(diff_error(grads[i],numerical_grads[i]))

print("grads",grads[0])

print("numerical_grads",numerical_grads[0])
```

测试结果略有差异。

## 7.9 循环神经网络的类表示与实现

### 7.9.1 使用类实现循环神经网络

三种典型的循环神经网络——简单 RNN、LSTM 和 GRU——已使用函数实现。也可以使用类来实现这些不同类型的循环神经网络。

类 `LSTM` 可用于表示前面的 LSTM 相关函数：
