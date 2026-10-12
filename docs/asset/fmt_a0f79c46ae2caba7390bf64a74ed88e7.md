
## 不同的循环神经网络模型

不同的循环神经网络模型可以通过神经网络单元来实现。

### LSTM 单元实现

```python
def sigmoid(x):
    return (1 / (1 + np.exp(-x)))

def lstm_cell(x, hc, w_ih, w_hh, b_ih, b_hh): 
    h, c = hc[0], hc[1]
    hidden_size = w_ih.shape[1] // 4
    ifgo_Z = np.dot(x, w_ih) + b_ih + np.dot(h, w_hh) + b_hh
    i = sigmoid(ifgo_Z[:, :hidden_size])
    f = sigmoid(ifgo_Z[:, hidden_size:2*hidden_size])
    g = np.tanh(ifgo_Z[:, 2*hidden_size:3*hidden_size])
    o = sigmoid(ifgo_Z[:, 3*hidden_size:])   
    c_ = f * c + i * g
    h_ = o * np.tanh(c_)
    return (h_, c_), np.column_stack((i, f, g, o))

def lstm_cell_back(dhc, ifgo, x, hc_pre, w_ih, w_hh, b_ih, b_hh):
    hidden_size = w_ih.shape[1] // 4
    if isinstance(dhc, tuple):
        dh_, dc_next = dhc
    else:
        dh_ = dhc
        dc_next = np.zeros_like(dh_)
    h_pre, c = hc_pre
    i, f, g, o = ifgo[:, :hidden_size], ifgo[:, hidden_size:2*hidden_size], \
                 ifgo[:, 2*hidden_size:3*hidden_size], ifgo[:, 3*hidden_size:]
    c_ = f * c + i * g
    dc_ = dc_next + dh_ * o * (1 - np.square(np.tanh(c_)))
    do = dh_ * np.tanh(c_)
    di = dc_ * g
    dg = dc_ * i
    df = dc_ * c
    diz = i * (1 - i) * di
    dfz = f * (1 - f) * df
    dgz = (1 - np.square(g)) * dg
    doz = o * (1 - o) * do
    dZ = np.column_stack((diz, dfz, dgz, doz))
    dW_ih = np.dot(x.T, dZ)
    dW_hh = np.dot(h_pre.T, dZ)
    db_hh = np.sum(dZ, axis=0, keepdims=True) 
    db_ih = np.sum(dZ, axis=0, keepdims=True) 
    dx = np.dot(dZ, w_ih.T)
    dh_pre = np.dot(dZ, w_hh.T)
    # return dx, dh_pre, (dW_ih, dW_hh, db_ih, db_hh)
    dc = dc_ * f
    return dx, (dh_pre, dc), (dW_ih, dW_hh, db_ih, db_hh)

class LSTMCell(RNNCellBase):
    """   \begin{array}{ll}
        i = \sigma(W_{ii} x + b_{ii} + W_{hi} h + b_{hi}) \\
        f = \sigma(W_{if} x + b_{if} + W_{hf} h + b_{hf}) \\
        g = \tanh(W_{ig} x + b_{ig} + W_{hg} h + b_{hg}) \\
        o = \sigma(W_{io} x + b_{io} + W_{ho} h + b_{ho}) \\
        c' = f * c + i * g \\
        h' = o * \tanh(c') \\
        \end{array}      
        """
    def __init__(self, input_size, hidden_size, bias=True):
        super(LSTMCell, self).__init__(input_size, hidden_size, bias, num_chunks=4)

    def init_hidden(batch_size):
        zeros = np.zeros(input.shape[0], self.hidden_size, dtype=input.dtype)  
        return (zeros, zeros) # np.array([zeros, zeros])

    def forward(self, input, h=None): 
        self.check_forward_input(input)
        if h is None:
            h = init_hidden(input.shape[0])            
        self.check_forward_hidden(input, h[0], '[0]')
        self.check_forward_hidden(input, h[1], '[1]')
        return lstm_cell(
                input, h,
                self.W_ih, self.W_hh,
                self.b_ih, self.b_hh,
            )

    def __call__(self, input, h=None): 
        return self.forward(input, h)

    def backward(self, dhc, ifgo, input, hc_pre):
        if hc_pre is None:
            hc_pre = init_hidden(input.shape[0])
        dx, dh_pre, grads = lstm_cell_back(
                            dhc, ifgo,
                            input, hc_pre,
                            self.W_ih, self.W_hh,
                            self.b_ih, self.b_hh)
        # grads = (dW_ih, dW_hh, db_ih, db_hh)
        for a, b in zip(self.grads, grads):
            a += b 
        return dx, dh_pre, grads           
```

### GRU 单元实现

```python
def gru_cell(x, h, w_ih, w_hh, b_ih, b_hh):
    Z_ih, Z_hh = np.dot(x, w_ih) + b_ih, np.dot(h, w_hh) + b_hh
    hidden_size = w_ih.shape[1] // 3
    r = sigmoid(Z_ih[:, :hidden_size] + Z_hh[:, :hidden_size])
    u = sigmoid(Z_ih[:, hidden_size:2*hidden_size] + Z_hh[:, hidden_size:2*hidden_size]) 
    n = np.tanh(Z_ih[:, 2*hidden_size:] + r * Z_hh[:, 2*hidden_size:]) 
    h_next = u * h + (1 - u) * n 
    run = np.column_stack((r, u, n))
    # return h_next, (r, u, n)  
    return h_next, run 

def gru_cell_back(dh, run, x, h_pre, w_ih, w_hh, b_ih, b_hh):
    hidden_size = w_ih.shape[1] // 3
    # r, u, n = run
    r, u, n = run[:, :hidden_size], run[:, hidden_size:2*hidden_size], \
              run[:, 2*hidden_size:]
    # H = U H_pre + (1-U) H_tildas
    dn = dh * (1 - u)
    dh_pre = dh * u
    du = h_pre * dh - n * dh   
    # n = \tanh(W_{in} x + b_{in} + r * (W_{hn} h + b_{hn})) 
    dnz = (1 - np.square(n)) * dn 
    Z_hn = np.dot(h_pre, w_hh[:, 2*hidden_size:]) + b_hh[:, 2*hidden_size:]
    dr = dnz * Z_hn
    dZ_ih_n = dnz
    dZ_hh_n = dnz * r
    duz = u * (1 - u) * du
    dZ_ih_u = duz
    dZ_hh_u = duz
    drz = r * (1 - r) * dr
    dZ_ih_r = drz
    dZ_hh_r = drz    
    dZ_ih = np.column_stack((dZ_ih_r, dZ_ih_u, dZ_ih_n))
    dZ_hh = np.column_stack((dZ_hh_r, dZ_hh_u, dZ_hh_n))            
    dW_ih = np.dot(x.T, dZ_ih)
    dW_hh = np.dot(h_pre.T, dZ_hh)
    db_ih = np.sum(dZ_ih, axis=0, keepdims=True) 
    db_hh = np.sum(dZ_hh, axis=0, keepdims=True)             
    dh_pre += np.dot(dZ_hh, w_hh.T)
    dx = np.dot(dZ_ih, w_ih.T)
    return dx, dh_pre, (dW_ih, dW_hh, db_ih, db_hh)

class GRUCell(RNNCellBase):
    """  \begin{array}{ll}
        r = \sigma(W_{ir} x + b_{ir} + W_{hr} h + b_{hr}) \\
        z = \sigma(W_{iz} x + b_{iz} + W_{hz} h + b_{hz}) \\
        n = \tanh(W_{in} x + b_{in} + r * (W_{hn} h + b_{hn})) \\
        h' = (1 - z) * n + z * h
        \end{array}
        """
    def __init__(self, input_size, hidden_size, bias=True):
        super(GRUCell, self).__init__(input_size, hidden_size, bias, num_chunks=3)

    def forward(self, input, h=None): 
        self.check_forward_input(input)
        if h is None:
            h = np.zeros(input.shape[0], self.hidden_size, dtype=input.dtype) 
        self.check_forward_hidden(input, h, '')
        return gru_cell(
                input, h,
                self.W_ih, self.W_hh,
                self.b_ih, self.b_hh,
            )  

    def __call__(self, input, h=None): 
        return self.forward(input, h)

    def backward(self, dh, run, input, h_pre):       
        if h_pre is None:
            h_pre = np.zeros(input.shape[0], self.hidden_size, dtype=input.dtype)      
        dx, dh_pre, grads = gru_cell_back(
                            dh, run,
                            input, h_pre,
                            self.W_ih, self.W_hh,
                            self.b_ih, self.b_hh)
        # grads = (dW_ih, dW_hh, db_ih, db_hh)
        for a, b in zip(self.grads, grads):
            a += b 
        return dx, dh_pre, grads
```

## 7.10 多层、双向循环神经网络

### 7.10.1 多层循环神经网络

前面的讨论是关于单层循环神经网络，即只有一个 RNN 网络层。与全连接神经网络或卷积神经网络类似，可以定义多层循环神经网络，如图 7-46 所示。一个隐藏层接受数据输入并生成隐藏状态 `H^((1))`，该隐藏状态被用作第二个隐藏层的输入，……，最后一个循环神经网络层可以用作整个网络的输出层，也可以后接一个或多个非循环神经网络层。

**图 7-46** 多层循环神经网络，第一个隐藏层接受数据输入并生成隐藏状态 `H^((1))`，该隐藏状态被用作第二个隐藏层的输入，最后一个循环神经网络层可以用作整个网络的输出层，也可以后接一个或多个非循环神经网络层。

在时刻 `t`，第 1 层神经元的输入包括数据输入 `X[t]` 和状态输入 `H[t-1]^((1))`，计算第一层的隐藏状态 `H[t]^((1))`：

`H[t]^((1)) = f1))`

第一层中 RNN 单元（神经元）的状态 `H[t]^((1))` 被用作第二层 RNN 单元（神经元）的数据输入，并结合第二层神经元在上一时刻自身的状态 `H[t-1]^((2))` 共同计算该神经元的状态 `H[t]^((2))`。该状态被用作第三层 RNN 单元（神经元）的数据输入，以计算第三层的隐藏状态 `H[t]^((3))`。一般来说，第 `l` 个隐藏层在时刻 `t` 接受隐藏状态 `H[t-1]^((l))` 及其前一层（即第 `l-1` 个隐藏层，通常为隐藏状态 `H[t]^((l-1))`）的输入，输出隐藏状态 `H[t]^((l))`，其计算过程可用以下公式表示：

`H[t]^((l)) = fl), H[t-1]^((l)))`

除了第一层的数据输入是初始数据输入 `X[t]` 之外，其他循环网络层的数据输入均为前一循环网络层的隐藏状态输出 `H[t]^((l-1))`。

多层循环网络最后一层的状态变量可以直接作为模型的输出 `F[t] = H[t]^((L))`，也可以通过激活函数输出。

`F[t] = g(H[t]^((L)))`

如果最后一个循环神经网络层是整个网络的输出层，则该 `F[t]` 即为整个网络的输出。如果该循环神经网络层后面还有非循环网络层，则该 `F[t]` 将继续作为后续网络层的输入。

与多层全连接或卷积神经网络类似，多层 RNN 可以捕获从低到高的分层特征。

在多层循环神经网络中，初始输入数据 `X` 的大小与隐藏状态 `H` 的大小通常不相等，且每个循环网络层中 `H` 的大小相同，因此第一层的数据输入与其他循环网络层的数据输入通常不同，所以除第一层外，循环网络层的权重参数形状相同。当然，也可以让不同的循环网络层具有不同大小的隐藏状态，但在实践中通常不这样做。

前面的循环神经网络单元可用于构建多层循环神经网络。以下代码基于神经网络单元构建了一个表示多层循环神经网络的基类 `RNNBase`：
