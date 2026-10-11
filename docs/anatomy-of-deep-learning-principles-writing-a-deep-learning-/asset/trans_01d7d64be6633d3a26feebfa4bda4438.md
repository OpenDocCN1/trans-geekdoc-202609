

# 不同的循环神经网络模型

不同的循环神经网络模型可以通过神经网络单元来实现。

## 7.10 多层、双向循环神经网络

### 7.10.1 多层循环神经网络

前面的讨论是关于单层循环神经网络，即只有一个 RNN 网络层。与全连接神经网络或卷积神经网络类似，可以定义多层循环神经网络，如图 7-46 所示。一个隐藏层接受数据输入并生成隐藏状态 `H^((1))`，该隐藏状态被用作第二个隐藏层的输入，……，最后一个循环神经网络层可以用作整个网络的输出层，也可以后接一个或多个非循环神经网络层。

**图 7-46** 多层循环神经网络，第一个隐藏层接受数据输入并生成隐藏状态 `H^((1))`，该隐藏状态被用作第二个隐藏层的输入，最后一个循环神经网络层可以用作整个网络的输出层，也可以后接一个或多个非循环神经网络层。

在时刻 `t`，第 1 层神经元的输入包括数据输入 `X[t]` 和状态输入 `H[t-1]^((1))`，计算第一层的隐藏状态 `H[t]^((1))`：

`H[t]^((1)) = f[1](X[t], H[t-1]^((1)))`

第一层中 RNN 单元（神经元）的状态 `H[t]^((1))` 被用作第二层 RNN 单元（神经元）的数据输入，并结合第二层神经元在上一时刻自身的状态 `H[t-1]^((2))` 共同计算该神经元的状态 `H[t]^((2))`。该状态被用作第三层 RNN 单元（神经元）的数据输入，以计算第三层的隐藏状态 `H[t]^((3))`。一般来说，第 `l` 个隐藏层在时刻 `t` 接受隐藏状态 `H[t-1]^((l))` 及其前一层（即第 `l-1` 个隐藏层，通常为隐藏状态 `H[t]^((l-1))`）的输入，输出隐藏状态 `H[t]^((l))`，其计算过程可用以下公式表示：

`H[t]^((l)) = f[l](H[t]^((l-1)), H[t-1]^((l)))`

除了第一层的数据输入是初始数据输入 `X[t]` 之外，其他循环网络层的数据输入均为前一循环网络层的隐藏状态输出 `H[t]^((l-1))`。

多层循环网络最后一层的状态变量可以直接作为模型的输出 `F[t] = H[t]^((L))`，也可以通过激活函数输出。

`F[t] = g(H[t]^((L)))`

如果最后一个循环神经网络层是整个网络的输出层，则该 `F[t]` 即为整个网络的输出。如果该循环神经网络层后面还有非循环网络层，则该 `F[t]` 将继续作为后续网络层的输入。

与多层全连接或卷积神经网络类似，多层 RNN 可以捕获从低到高的分层特征。

在多层循环神经网络中，初始输入数据 `X` 的大小与隐藏状态 `H` 的大小通常不相等，且每个循环网络层中 `H` 的大小相同，因此第一层的数据输入与其他循环网络层的数据输入通常不同，所以除第一层外，循环网络层的权重参数形状相同。当然，也可以让不同的循环网络层具有不同大小的隐藏状态，但在实践中通常不这样做。

前面的循环神经网络单元可用于构建多层循环神经网络。以下代码基于神经网络单元构建了一个表示多层循环神经网络的基类 `RNNBase`：

```python
from Layers import * 

class RNNBase(Layer):

    def __init__(self, mode, input_size, hidden_size, n_layers, bias=True):

        super(RNNBase, self).__init__()        

        self.mode = mode

        if mode == 'RNN_TANH':
            self.cells = [RNNCell(input_size, hidden_size, bias, nonlinearity="tanh")]
            self.cells += [RNNCell(hidden_size, hidden_size, bias, nonlinearity="tanh") for i in range(n_layers-1)]
        elif mode == 'RNN_RELU':
            self.cells = [RNNCell(input_size, hidden_size, bias, nonlinearity="relu")]
            self.cells += [RNNCell(hidden_size, hidden_size, bias, nonlinearity="relu") for i in range(n_layers-1)]
        elif mode == 'LSTM':
            self.cells = [LSTMCell(input_size, hidden_size, bias)]
            self.cells += [LSTMCell(hidden_size, hidden_size, bias) for i in range(n_layers-1)]
        elif mode == 'GRU':
            self.cells = [GRUCell(input_size, hidden_size, bias)]
            self.cells += [GRUCell(hidden_size, hidden_size, bias) for i in range(n_layers-1)]

        self.input_size, self.hidden_size = input_size, hidden_size
        self.n_layers = n_layers
        self.flatten_parameters()
        self._params = None

    def flatten_parameters(self):
        self.params = []
        self.grads = []
        for i in range(self.n_layers):
            rnn = self.cells[i]
            for j, p in enumerate(rnn.params):
                self.params.append(p)
                self.grads.append(rnn.grads[j])

    def forward(self, x, h=None):
        seq_len, batch_size = x.shape[0], x.shape[1]
        n_layers = self.n_layers
        mode = self.mode
        hs = [[] for i in range(n_layers)]
        zs = [[] for i in range(n_layers)]        

        if h is None:
            h = self.init_hidden(batch_size)

        if False:
            if mode == 'LSTM':  # isinstance(h, tuple):
                self.h = (h[0].copy(), h[1].copy())       
            else:
                self.h = h.copy()     
        else:
            self.h = h

        for i in range(n_layers):
            cell = self.cells[i]
            if i != 0:
                x = hs[i-1]  # out h of pre layer
                if mode == 'LSTM':
                    x = np.array([h for h, c in x])

            hi = h[i]
            if mode == 'LSTM':
                hi = (h[0][i], h[1][i])

            for t in range(seq_len):
                hi = cell(x[t], hi) 
                if isinstance(hi, tuple):
                    hi, z = hi[0], hi[1]
                    zs[i].append(z) 
                hs[i].append(hi)                
                # if mode == 'LSTM' or mode == 'GRU':
                #     zs[i].append(z)                 

        self.hs = np.array(hs)  # (layer_size, seq_size, batch_size, hidden_size)
        if len(zs[0]) > 0:
            self.zs = np.array(zs)
        else:
            self.zs = None

        output = hs[-1]  # containing the output features (`h_t`) 
                         # from the last layer of the RNN,
        if mode == 'LSTM':
            output = [h for h, c in output]
        hn = self.hs[:, -1, :, :]  # containing the hidden state for `t = seq_len`
        return np.array(output), hn

    def __call__(self, x, h=None):
        return self.forward(x, h)

    def init_hidden(self, batch_size):
        zeros = np.zeros((self.n_layers, batch_size, self.hidden_size))
        if self.mode == 'LSTM':
            self.h = (zeros, zeros)
        else:
            self.h = zeros
        return self.h

    def backward(self, dhs, input):  # ,hs):      
        if self.hs is None:
            self.hs, _ = self.forward(input)
        hs = self.hs
        zs = self.zs if self.zs is not None else hs        
        seq_len, batch_size = input.shape[0], input.shape[1]       
        dinput = [None for t in range(seq_len)]
        if len(dhs.shape) == 2:  # dh at last time (batch, hidden)
            dhs_ = [np.zeros_like(dhs) for i in range(seq_len)]
            dhs_[-1] = dhs
            dhs = np.array(dhs_)
```

