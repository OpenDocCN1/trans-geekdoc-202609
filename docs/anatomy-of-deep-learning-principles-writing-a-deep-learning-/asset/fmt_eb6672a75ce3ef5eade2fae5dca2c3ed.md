
### 7.9.2 Class implementation of recurrent neural network unit

The most basic calculation of the cyclic neural network is the forward and reverse calculation of the neural network unit at a certain moment. At a certain moment, the neural network unit accepts the data input `x` and the state input `h` of the previous time step. For simple RNN and GRU, the output is the state `h'` of the current time step, and the current memory storage `c'` output by LSTM and the `h'` passed to the next time step. For example, for a simple RNN, its forward calculation formula is:

`h' = tanh(W[ih]x + b[ih] + W[hh]h + b[hh])`

Here, the original offset `b[h]` is split into 2 items: `b[ih]`, `b[hh]`. Denote the bias of the weighted sum of the data input and the bias of the weighted sum of the hidden state, respectively. Similarly, for LSTM, one offset of each original weighted sum can also be split into two offsets, that is, the calculation formula of LSTM:

$$
\begin{matrix}
i = \sigma(W_{ii}x + b_{ii} + W_{hi}h + b_{hi}) \\
f = \sigma(W_{if}x + b_{if} + W_{hf}h + b_{hf}) \\
g = \tanh(W_{ig}x + b_{ig} + W_{hg}h + b_{hg}) \\
o = \sigma(W_{io}x + b_{io} + W_{ho}h + b_{ho}) \\
c' = f * c + i * g \\
h' = o * \tanh(c')
\end{matrix}
$$

Similarly, the calculation formula of the GRU neural network unit is:

$$
\begin{matrix}
r = \sigma(W_{ir}x + b_{ir} + W_{hr}h + b_{hr}) \\
z = \sigma(W_{iz}x + b_{iz} + W_{hz}h + b_{hz}) \\
n = \tanh(W_{in}x + b_{in} + r * (W_{hn}h + b_{hn})) \\
h' = (1 - z) * n + z * h
\end{matrix}
$$

A common base class can be used to represent the common properties of these 3 different neural network units:

```python
import numpy as np
import math

class RNNCellBase(object):
    __constants__ = ['input_size', 'hidden_size']

    def __init__(self, input_size, hidden_size, bias, num_chunks):
        super(RNNCellBase, self).__init__()

        self.input_size, self.hidden_size = input_size, hidden_size
        self.bias = bias

        self.W_ih = np.empty((input_size, num_chunks * hidden_size))   # input to hidden
        self.W_hh = np.empty((hidden_size, num_chunks * hidden_size))  # hidden to hidden

        if bias:
            self.b_ih = np.zeros((1, num_chunks * hidden_size))
            self.b_hh = np.zeros((1, num_chunks * hidden_size))
            self.params = [self.W_ih, self.W_hh, self.b_ih, self.b_hh]
        else:
            self.b_ih = None
            self.b_hh = None
            self.params = [self.W_ih, self.W_hh]

        self.grads = [np.zeros_like(param) for param in self.params]
        self.param_grads = self.params.copy()
        self.param_grads.extend(self.grads)

        self.reset_parameters()

    def parameters(self, no_grad=True):
        if no_grad:
            return self.params
        return self.param_grads

    def reset_parameters(self):
        stdv = 1.0 / math.sqrt(self.hidden_size)
        for param in self.params:
            w = param
            w[:] = np.random.uniform(-stdv, stdv, (w.shape))

    def check_forward_input(self, input):
        if input.shape[1] != self.input_size:
            raise RuntimeError(
                "input has inconsistent input_size: got {}, expected {}".format(
                    input.shape[1], self.input_size))

    def check_forward_hidden(self, input, h, hidden_label=''):
        if input.shape[0] != h.shape[0]:
            raise RuntimeError(
                "Input batch size {} doesn't match hidden{} batch size {}".format(
                    input.shape[0], hidden_label, h.shape[0]))
        if h.shape[1] != self.hidden_size:
            raise RuntimeError(
                "hidden{} has inconsistent hidden_size: got {}, expected {}".format(
                    hidden_label, h.shape[1], self.hidden_size))
```

The parameters `input_size` and `hidden_size` of the constructor represent the size of the input data and state, and `num_chunks` represent the number of calculation gates for each neural network unit. `check_forward_input` and `check_forward_hidden` are auxiliary methods to check whether the input data and hidden state size match the model parameters of the neural network unit. `num_chunks` represents the number of computing units in the cyclic neural network. For the basic RNN, its value is 1, and for LSTM and GRU, its values are 4 and 3, respectively.

A specific type of neural network unit can be defined on the basis of the base class `RNNCellBase` of the neural network unit. The following code defines the class `RNNCell` representing a simple RNN cell:

```python
def relu(x):
    return x * (x > 0)

def rnn_tanh_cell(x, h, W_ih, W_hh, b_ih, b_hh):
    # h' = \tanh(W_{ih} x + b_{ih}  +  W_{hh} h + b_{hh})
    if b_ih is None:
        return np.tanh(np.dot(x, W_ih) + np.dot(h, W_hh))
    else:
        return np.tanh(np.dot(x, W_ih) + b_ih + np.dot(h, W_hh) + b_hh)

def rnn_relu_cell(x, h, W_ih, W_hh, b_ih, b_hh):
    # h' = \relu(W_{ih} x + b_{ih}  +  W_{hh} h + b_{hh})
    if b_ih is None:
        return relu(np.dot(x, W_ih) + np.dot(h, W_hh))
    else:
        return relu(np.dot(x, W_ih) + b_ih + np.dot(h, W_hh) + b_hh)

class RNNCell(RNNCellBase):
    """        h' = \tanh(W_{ih} x + b_{ih}  +  W_{hh} h + b_{hh})"""

    __constants__ = ['input_size', 'hidden_size', 'nonlinearity']

    def __init__(self, input_size, hidden_size, bias=True, nonlinearity="tanh"):
        super(RNNCell, self).__init__(input_size, hidden_size, bias, num_chunks=1)
        self.nonlinearity = nonlinearity

    def forward(self, input, h=None):
        self.check_forward_input(input)

        if h is None:
            h = np.zeros(input.shape[0], self.hidden_size, dtype=input.dtype)

        self.check_forward_hidden(input, h, '')

        if self.nonlinearity == "tanh":
            ret = rnn_tanh_cell(input, h,
                                self.W_ih, self.W_hh,
                                self.b_ih, self.b_hh)
        elif self.nonlinearity == "relu":
            ret = rnn_relu_cell(input, h,
                                self.W_ih, self.W_hh,
                                self.b_ih, self.b_hh)
        else:
            ret = input
            raise RuntimeError(
                "Unknown nonlinearity: {}".format(self.nonlinearity))

        return ret

    def __call__(self, input, h=None):
        return self.forward(input, h)

    def backward(self, dh, H, X, H_pre):
        if self.nonlinearity == "tanh":
            dZh = (1 - H * H) * dh  # backprop through tanh nonlinearity
        else:
            dZh = H * (1 - H) * dh

        db_hh = np.sum(dZh, axis=0, keepdims=True)
        db_ih = np.sum(dZh, axis=0, keepdims=True)
        dW_ih = np.dot(X.T, dZh)
        dW_hh = np.dot(H_pre.T, dZh)
        dh_pre = np.dot(dZh, self.W_hh.T)
        dx = np.dot(dZh, self.W_ih.T)

        grads = (dW_ih, dW_hh, db_ih, db_hh)
        for a, b in zip(self.grads, grads):
            a += b

        return dx, dh_pre, grads
```

The following code demonstrates the forward and reverse calculation of a time step of `RNNCell`, where `x` is the input data with a batch size of 3, and `h` is the state corresponding to a batch size of 3:

```python
import numpy as np

np.random.seed(1)

x = np.random.randn(3, 10)  # (batch_size, input_dim)
h = np.random.randn(3, 20)  # (batch_size, hidden_dim)

rnn = RNNCell(10, 20)       # (input_dim, hidden_dim)

h_ = rnn(x, h)

print("h_:", h_)

dh_ = np.random.randn(*h.shape)

dx, dh, _ = rnn.backward(dh_, h_, x, h)

print("dh:", dh)
```

Test results slightly.

The following code uses sequence data `x` to demonstrate the calculation process of `RNNCell` with a step size of 6:

```python
import numpy as np

x = np.random.randn(6, 3, 10)
h = np.random.randn(3, 20)

rnn = RNNCell(10, 20)

h_0 = h.copy()
hs = []

for i in range(6):
    h = rnn(x[i], h)
    hs.append(h)
```
