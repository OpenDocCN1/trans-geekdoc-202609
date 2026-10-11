

## 多层循环神经网络的实现与测试

### 代码实现

```python
        elif dhs.shape[0] != seq_len:            
            raise RuntimeError(
                "dhs has inconsistent seq_len: got {}, expected {}".format(
                    dhs.shape[0], seq_len))
        else:           
            pass     
        
        #----dhidden--------    
        dhidden = [None for i in range(self.n_layers)]        
        for layer in reversed(range(self.n_layers)):
            layer_hs = hs[layer]
            layer_zs = zs[layer]
            cell = self.cells[layer]
            if layer == 0:
                layer_input = input
            else:
                if self.mode == 'LSTM':
                    layer_input = self.hs[layer-1]
                    layer_input = [h for h, c in layer_input]
                else:
                    layer_input = self.hs[layer-1]
            h_0 = self.h[layer]                 
            dh = np.zeros_like(dhs[0]) # 来自下一时刻的梯度
            if self.mode == 'LSTM':
                h_0 = (self.h[0][layer], self.h[1][layer])
                dc = np.zeros_like(dhs[0])
            for t in reversed(range(seq_len)):
                dh += dhs[t] # 下一时刻的梯度 + 当前时刻的梯度
                h_pre = h_0 if t == 0 else layer_hs[t-1]
                if self.mode == 'LSTM':
                    dhc = (dh, dc)
                    dx, dhc, _ = cell.backward(dhc, layer_zs[t], layer_input[t], h_pre)  
                    dh, dc = dhc
                else:
                    dx, dh, _ = cell.backward(dh, layer_zs[t], layer_input[t], h_pre)  
                if layer > 0:
                    dhs[t] = dx
                else:
                    dinput[t] = dx
                #----dhidden--------    
                if t == 0:
                    if self.mode == 'LSTM':
                        dhidden[layer] = dhc
                    else:
                        dhidden[layer] = dh                    
        return np.array(dinput), np.array(dhidden)

    def parameters(self):
        if self._params is None:
            self._params = []           
            for i, _ in enumerate(self.params):  
                self._params.append([self.params[i], self.grads[i]])  
        return self._params
```

基于此基类，可以实现多层循环神经网络。例如，以下代码分别表示 `RNN`、`LSTM` 和 `GRU` 实现了多层简单循环网络、LSTM 和 GRU 循环神经网络：

```python
class RNN(RNNBase):
    def __init__(self, *args, **kwargs):
        if 'nonlinearity' in kwargs:
            if kwargs['nonlinearity'] == 'tanh':
                mode = 'RNN_TANH'
            elif kwargs['nonlinearity'] == 'relu':
                mode = 'RNN_RELU'
            else:
                raise ValueError("Unknown nonlinearity '{}'".format(
                    kwargs['nonlinearity']))
            del kwargs['nonlinearity']
        else:
            mode = 'RNN_TANH'
        super(RNN, self).__init__(mode, *args, **kwargs)

class LSTM(RNNBase):
    def __init__(self, *args, **kwargs):        
        super(LSTM, self).__init__('LSTM', *args, **kwargs)

class GRU(RNNBase):
    def __init__(self, *args, **kwargs):        
        super(GRU, self).__init__('GRU', *args, **kwargs)
```

这些多层循环神经网络可以通过以下代码进行测试：

```python
import numpy as np
from rnn import *

np.random.seed(1)

num_layers = 2
batch_size, input_size, hidden_size = 3, 5, 8
seg_len = 6
test_RNN = "LSTM"

if test_RNN == "rnnTANH":
    rnn = RNN(input_size, hidden_size, num_layers)
elif test_RNN == "rnnRELU":
    rnn = RNN(input_size, hidden_size, num_layers, nonlinearity='relu')
elif test_RNN == "GRU":
    rnn = GRU(input_size, hidden_size, num_layers)
elif test_RNN == "LSTM":
    rnn = LSTM(input_size, hidden_size, num_layers)
    c_0 = np.random.randn(num_layers, batch_size, hidden_size)

input = np.random.randn(seg_len, batch_size, input_size)
h_0 = np.random.randn(num_layers, batch_size, hidden_size)

print("input.shape", input.shape)
print("h_0.shape", h_0.shape)
print("c_0.shape", c_0.shape)

if test_RNN == "LSTM":   
    output, hn = rnn(input, (h_0, c_0))
else:
    output, hn = rnn(input, h_0)

print("output.shape", output.shape)
print("output", output)
print("hn", hn)

#------test backward---    
do = np.random.randn(*output.shape)
dinput, dhidden = rnn.backward(do, input)  # ,rnn.hs)#output)

print("dinput.shape:", dinput.shape)
print("dinput:", dinput)
print("dhidden:", dhidden)
```

测试结果略。

### 7.10.2 多层循环神经网络的训练与预测

上述多层 LSTM 循环神经网络的每个隐藏层的隐藏状态大小相同。为了使该多层神经网络适应不同输出值的问题，可以在多层 LSTM 循环神经单元的基础上再添加一个全连接输出层，以针对不同输出向量大小输出特定问题。以下 `LSTM_RNN` 即为这种多层循环神经网络，其中 `input_size`、`hidden_size` 和 `output_size` 分别为输入数据大小、隐藏状态大小和输出值大小，`num_layers` 为循环神经网络的层数。

```python
from Layers import *

class LSTM_RNN(object):
    def __init__(self, input_size, hidden_size, output_size, num_layers):
        super(LSTM_RNN, self).__init__()
        self.input_size = input_size
        self.hidden_size = hidden_size       
        self.num_layers = num_layers
        # 定义 LSTM 层
        self.lstm = LSTM(input_size, hidden_size, num_layers)
        # 定义输出层
        self.linear = Dense(hidden_size, output_size)
        self.layers = [self.lstm, self.linear]
        self._params = None

    def init_hidden(self, batch_size):
        # 这是我们将要初始化隐藏状态的方式
        self.h_0 = (np.zeros((self.num_layers, batch_size, self.hidden_size)),
                    np.zeros((self.num_layers, batch_size, self.hidden_size)))

    def forward(self, input):
        # input: (seq_len, batch, input_size)
        # hs_out 的形状: [input_size, batch_size, hidden_dim]
        # self.h_0 的形状: (a, b), 其中 a 和 b 的形状均为
        # (num_layers, batch_size, hidden_dim)。
        hs_out, self.h_0 = self.lstm(input, self.h_0)
        batch_size = input.shape[1]
        y_pred = self.linear(hs_out[-1].reshape(batch_size, -1))
        return y_pred  # .reshape(batch_size, -1)#.flatten() # view(-1)

    def __call__(self, input):
        return self.forward(input)

    def backward(self, dZs, input):
        dhs = self.linear.backward(dZs)
        dinput = self.lstm.backward(dhs, input)          

    def parameters(self):
        if self._params is None:
            self._params = []
            for layer in self.layers:
                for i, _ in enumerate(layer.params):  
                    self._params.append([layer.params[i], layer.grads[i]])  
        return self._params
```

下面的代码利用上述多层循环神经网络对自回归数据进行建模，其中 `ARData` 类源自 [https://github.com/jessicayung/blog-code-snippets/blob/master/lstm-pytorch/generate_data.py](https://github.com/jessicayung/blog-code-snippets/blob/master/lstm-pytorch/generate_data.py)，用于生成自回归训练数据。

```python
import util
from train import *
from generate_data import *
import matplotlib.pyplot as plt

%matplotlib inline

input_size = 20

# 数据参数
noise_var = 0
num_datapoints = 100
test_size = 0.2
num_train = int((1 - test_size) * num_datapoints)

data = ARData(num_datapoints, num_prev=input_size, test_size=test_size, noise_var=noise_var, \
              coeffs=fixed_ar_coefficients[input_size])

X_train = data.X_train
y_train = data.y_train

hidden_size = 32
```

