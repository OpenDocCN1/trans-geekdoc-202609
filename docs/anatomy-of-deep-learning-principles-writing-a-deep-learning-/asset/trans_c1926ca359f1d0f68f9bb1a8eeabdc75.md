

## 代码实现

### EncoderRNN_Embed 类

```python
embed_out = []

for x in input:              
    embedded = self.embedding(x).reshape(1,1,-1)
    self.embedded_x.append(self.embedding.x)
    self.embedded_out.append(embedded)

self.embedded_out = np.concatenate(self.embedded_out, axis=0) 
output, hidden = self.gru(self.embedded_out, hidden)
return output, hidden

def __call__(self, input, hidden):
    return self.forward(input, hidden)

def initHidden(self):
    return np.zeros((1, 1, self.hidden_size))

def parameters(self):
    return self.gru.parameters()

def backward(self, dhs): 
    dinput, dhidden = self.gru.backward(dhs, self.embedded_out)
    T = dinput.shape[0]
    for t in range(T):
        dinput_t = dinput[t]
        self.embedding.x = self.embedded_x[t]  # recover the original x 
        self.embedding.backward(dinput_t)
```

因为 `Embedding` 层的权重参数也是需要学习的模型参数，所以在反向推导时，也需要计算损失函数关于 `Embedding` 层权重参数的梯度，即 `self.embedding.backward(dinput_t)`。反向推导归结为每个时刻 `t` 的求导。需要知道此时刻 `t` 的输入 `self.embedding.x`。因此，在正向计算过程中，有必要保存每个时刻 `Embedding` 层的输出 `self.embedded_x.append(self.embedding.x)`。

如图 7-54 所示，解码器也使用词嵌入层的输出向量作为 RNN 单元的输入：

**图 7-54** 输入词（对应索引的独热向量）通过嵌入层 `embedding` 转换为低维数值向量，然后将 `relu` 激活函数的输出和隐藏状态一起作为循环神经网络单元的输入。计算输出和潜在向量。

同样需要对嵌入层进行正向计算和反向推导，代码如下：

### DecoderRNN_Embed 类

```python
class DecoderRNN_Embed(object):
    def __init__(self, hidden_size, output_size, num_layers=1, teacher_forcing_ratio=0.5):
        super().__init__()       
        self.hidden_size = hidden_size       
        self.num_layers = 1
        self.teacher_forcing_ratio = teacher_forcing_ratio
        self.embedding = Embedding(output_size, hidden_size)
        self.relu = Relu()
        self.gru = GRU(hidden_size, hidden_size, 1)
        self.linear = Dense(hidden_size, output_size)
        self.layers = [self.embedding, self.gru, self.linear]
        self._params = None

    def initHidden(self, batch_size):        
        self.h_0 = np.zeros((self.num_layers, batch_size, self.hidden_size))    

    def forward_step(self, input_t, hidden, train=True): 
        embedded = self.embedding(input_t)  # .reshape(1,1,-1)
        self.embedded_x.append(self.embedding.x)        
        output = self.relu(embedded)   
        self.relu_x = self.relu.x
        relu_output = output.reshape(1, output.shape[0], -1)
        self.input.append(relu_output)  # output)  # input of gru         
        output_hs, hidden = self.gru(relu_output, hidden)  
        output = self.linear(output_hs[0])  # seq_len = 1 
        return output, hidden, output_hs[0]

    def forward(self, input_tensor, hidden): 
        self.input = []
        target_length = input_tensor.shape[0]  # input_tensor.size(0)  
        teacher_forcing_ratio = self.teacher_forcing_ratio
        use_teacher_forcing = True if random.random() < teacher_forcing_ratio else False
        output_hs = []
        output = []
        hidden_t = hidden
        h_0 = hidden.copy()
        input_t = np.array([SOS_token])
        hs = []
        zs = []
        self.embedded_x = []
        self.relu_x = []
        for t in range(target_length):
            output_t, hidden_t, output_hs_t = self.forward_step(
                input_t, hidden_t)
            hs.append(self.gru.hs)  # Keep the hidden state of the middle layer
            zs.append(self.gru.zs)  # Keep the calculation result of the middle layer           
            output_hs.append(output_hs_t)
            output.append(output_t)
            if use_teacher_forcing:
                input_t = input_tensor[t]  # Teacher forcing               
            else:             
                input_t = np.argmax(output_t)  # maximum probability
                if input_t == EOS_token:
                    break  
                input_t = np.array([input_t])
        output = np.array(output)
        self.output_hs = np.array(output_hs)
        self.h_0 = h_0         
        self.hs = np.concatenate(hs, axis=1)
        self.zs = np.concatenate(zs, axis=1)
        # self.gru.hs = self.hs
        # self.gru.zs = self.zs 
        return output

    def __call__(self, input, hidden):
        return self.forward(input, hidden)

    def evaluate(self, hidden, max_length):
        # input: (1, batch_size=1, input_size)  
        input = np.array([SOS_token])
        decoded_words = []
        for t in range(max_length):
            output, hidden, _ = self.forward_step(input, hidden, False)
            output = np.argmax(output)         
            if output == EOS_token:
                break
            else:           
                decoded_words.append(output)               
                input = np.array([output])
        return decoded_words    

    def backward(self, dZs):
        dhs = []
        output_hs = self.output_hs
        input = np.concatenate(self.input, axis=0)
        for i in range(len(input)):
            self.linear.x = output_hs[i]
            dh = self.linear.backward(dZs[i])
            dhs.append(dh)
        dhs = np.array(dhs)
        self.gru.hs = self.hs
        self.gru.zs = self.zs
        self.gru.h = self.h_0
        dinput, dhidden = self.gru.backward(dhs, input)  
        for i in range(len(input)):
            dinput_t = dinput[i]
            d_embeded = self.relu.backward(dinput_t)            
            self.embedding.x = self.embedded_x[i]  # recover the original x
            self.embedding.backward(d_embeded)
        return dinput, dhidden 

    def backward_dh(self, dZ):
        dh = self.linear.backward(dZ)
        return dh    

    def parameters(self):
        if self._params is None:
            self._params = []
            for layer in self.layers:
                for i, _ in enumerate(layer.params):  
                    self._params.append([layer.params[i], layer.grads[i]])  
        return self._params    
```

### Vocab 类

重新定义词表类 `Vocab`，使其能够包含特殊的开始和结束词 "SOS"、"EOS"，并将出现次数少于 `min_count` 的词视为未知词：

```python
import numpy as np
from collections import defaultdict

SOS_token = 0
EOS_token = 1
UNK_token = 2

class Vocab:
    def __init__(self, min_count=1, corpus=None): 
        self.min_count = 1
        self.word2count = {}
        self.word2index = {"SOS": 0, "EOS": 1, "UNK": 2}        
        self.index2word = {0: "SOS", 1: "EOS", 2: "UNK"}
        self.n_words = 3  # Count SOS and EOS
        if corpus is not None:
            for sentence in corpus:
                self.addSentence(sentence)
            self.build()               

    def addSentence(self, sentence):
        if isinstance(sentence, str):
            for word in sentence.split(' '):
                self.addWord(word)                
        else:
            for word in sentence:
                self.addWord(word)              

    def addWord(self, word):
```
