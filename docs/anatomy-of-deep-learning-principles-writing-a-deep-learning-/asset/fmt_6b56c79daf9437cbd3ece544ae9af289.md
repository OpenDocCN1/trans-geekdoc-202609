
## 注意力机制的前向计算与反向传播

### `attn_forward` 函数

```python
def attn_forward(hidden, encoder_outputs):
    # hidden (B,D)   encoder_outputs (T,B,D)
    energies = np.sum(hidden * encoder_outputs, axis=2)  # (T,B)
    energies = energies.T  # (B,T)
    alphas = util.softmax(energies)
    return alphas, energies
```

### `attn_backward` 函数

```python
def attn_backward(d_alpha, energies, hidden, encoder_outputs):
    # hidden (B,D)   encoder_outputs (T,B,D)
    # d_alpha  energies: (B,T)
    d_energies = softmax_backward_2(energies, d_alpha, False)  # d_alpha, energies)
    d_energies = d_energies.T  # (T,B)
    d_energies = np.expand_dims(d_energies, axis=2)
    d_encoder_outputs = d_energies * hidden  # (T,B) (B,D)
    d_hidden = np.sum(d_energies * encoder_outputs, axis=0)  # (T,B) (T,B,D)
    return d_encoder_outputs, d_hidden
```

## 加权求和操作 (`bmm`) 的实现

以下是 `attn_weights` 加权求和 `encoder_outputs` 的前向计算和反向推导代码：

### `bmm` 前向函数

```python
def bmm(alphas, encoder_outputs):
    # (B,T), [T,B,D]
    encoder_outputs = np.transpose(encoder_outputs, (1, 0, 2))  # [T,B,D] -> [B,T,D]
    # weights = np.expand_dims(weights, axis=1)  # (B,T) -> (B,1,T)
    context = np.einsum("bj, bjk -> bk", alphas, encoder_outputs)  # [B,T]*[B,T,D] -> [B,D]
    return context
```

### `bmm_backward` 反向函数

```python
def bmm_backward(d_context, alphas, encoder_outputs):
    encoder_outputs = np.transpose(encoder_outputs, (1, 0, 2))  # [T,B,D] -> [B,T,D]
    d_alphas = np.einsum("bjk, bk -> bj", encoder_outputs, d_context)  # dx = Wdz^T (B,T,D) (B,D) -> (B,T)
    d_encoder_outputs = np.einsum("bi, bj -> bij", alphas, d_context)  # dW = x^T dz  # (B,T) (B,D) -> (B,T,D)
    d_encoder_outputs = np.transpose(d_encoder_outputs, (1, 0, 2))  # [B,T,D] -> [T,B,D]
    return d_alphas, d_encoder_outputs
```

## `np.einsum` 机制详解

首先，实现图中多序列样本的加权求和 `bmm` 操作。设 `T`、`B`、`D` 分别为序列长度、样本数量、每个时刻的数据长度。

`bmm()` 接受形状为 `(B, T)` 的权重矩阵（每一行代表一个样本的权重向量），以及形状为 `(T, B, D)` 的编码器输出内容向量 `encoder_outputs`。`encoder_outputs` 需要先转换为形状为 `(B, T, D)` 的张量，然后使用 `np.einsum()` 计算每个样本与其权重向量的加权求和，得到长度为 `D` 的向量。

`einsum()` 使用字符串指令控制灵活的点积（矩阵乘法）操作。例如，将 `"bj, bjk -> bk"` 中左侧的两个张量 `"bj"` 和 `"bjk"` 相乘，生成右侧的二维张量 `"bk"`，其中张量的轴用字母表示（代替 0, 1, 2）。该乘法过程可用以下代码模拟：

```python
# 遍历结果张量的每个元素（下标 bk）
for b in range(...):
    for k in range(...):
        C[b, k] = 0
        for j in range(...):
            C[b, k] += A[b, j] * B[b, j, k]
```

## 注意力层 `Atten` 封装

编码器输出内容的权重向量计算与加权求和过程可综合为一个注意力层 `Atten`：

```python
# 时间步 t 的注意力层
class Atten(Layer):
    def __init__(self, hidden_size):
        super().__init__()
        self.hidden_size = hidden_size

    def forward(self, hidden, encoder_outputs):
        self.hidden = hidden
        self.encoder_outputs = encoder_outputs
        alphas, energies = attn_forward(hidden, encoder_outputs)
        context = bmm(alphas, encoder_outputs)
        self.alphas, self.energies = alphas, energies
        return context, alphas, energies

    def __call__(self, hidden, encoder_outputs):
        return self.forward(hidden, encoder_outputs)

    def backward(self, d_context):  # (B,D)
        alphas, energies, hidden, encoder_outputs = (
            self.alphas,
            self.energies,
            self.hidden,
            self.encoder_outputs,
        )
        d_alphas, d_encoder_outputs_2 = bmm_backward(d_context, alphas, encoder_outputs)
        d_encoder_outputs, d_hidden = attn_backward(d_alphas, energies, hidden, encoder_outputs)
        d_encoder_outputs += d_encoder_outputs_2
        return d_hidden, d_encoder_outputs
```

## 基于注意力机制的解码器 `DecoderRNN_Atten`

以下代码实现了上述简单注意力机制的解码器：

```python
from Layers import *
from rnn import *
import util

class DecoderRNN_Atten(object):
    def __init__(
        self,
        hidden_size,
        output_size,
        num_layers=1,
        teacher_forcing_ratio=0.5,
        dropout_p=0.1,
        max_length=MAX_LENGTH,
    ):
        super(DecoderRNN_Atten, self).__init__()
        self.hidden_size = hidden_size
        self.num_layers = 1
        self.teacher_forcing_ratio = teacher_forcing_ratio
        self.dropout_p = dropout_p
        self.max_length = max_length
        self.embedding = Embedding(output_size, hidden_size)
        self.dropout = Dropout(self.dropout_p)
        # self.attn = Dense(self.hidden_size * 2, self.max_length)
        self.attn = Atten(hidden_size)
        self.attn_combine = Dense(self.hidden_size * 2, self.hidden_size)
        self.relu = Relu()
        self.gru = GRU(hidden_size, hidden_size, 1)
        self.out = Dense(hidden_size, output_size)
        # self.layers = [self.embedding, self.attn, self.attn_combine, self.gru, self.out]
        self.layers = [self.embedding, self.attn_combine, self.gru, self.out]
        self._params = None
        self.use_dropout = False

    def initHidden(self, batch_size):
        self.h_0 = np.zeros((self.num_layers, batch_size, self.hidden_size))

    def forward_step_(self, input, prev_hidden, encoder_outputs, training=True):
        embedded = self.embedding(input)  # (B,D)
        if self.use_dropout and training:
            embedded = self.dropout(embedded, training)
        context, alphas, energies = self.attn(prev_hidden[0], encoder_outputs)
        attn_combine_out = self.attn_combine(np.concatenate((embedded, context), axis=1))
        relu_out = self.relu(attn_combine_out)
        self.relu_x.append(self.relu.x)
        relu_out = np.expand_dims(relu_out, axis=0)
        output_hs, hidden = self.gru(relu_out, prev_hidden)
        output_hs_t = output_hs[0]  # seq_len = 1
        output = self.out(output_hs_t)
        if training:
            self.embedded_x.append(self.embedding.x)
            if self.use_dropout:
                self.dropout_mask.append(self.dropout._mask)
            self.attn_x.append(
                (self.attn.alphas, self.attn.energies, self.attn.hidden, self.attn.encoder_outputs)
            )
            self.attn_combine_x.append(self.attn_combine.x)
            self.relu_x.append(self.relu.x)
            self.gru_x.append((relu_out, self.gru.h))
            self.gru_hs.append(self.gru.hs)  # 保留中间层的隐藏状态
            self.gru_zs.append(self.gru.zs)  # 保留中间层的计算结果
            self.out_x.append(self.out.x)
        return output, hidden, output_hs_t

    def forward(self, input_tensor, encoder_outputs):  # hidden, encoder_outputs):
        self.encoder_outputs = encoder_outputs  # (T,B,D)
        self.attn_weights_seq = []
        target_length = input_tensor.shape[0]  # input_tensor.size(0)
        teacher_forcing_ratio = self.teacher_forcing_ratio
        use_teacher_forcing = True if random.random() < teacher_forcing_ratio else False
        hidden_t = encoder_outputs[-1].reshape(
            1, encoder_outputs[-1].shape[0], encoder_outputs[-1].shape[1]
        )
        h_0 = hidden_t.copy()
        input_t = np.array([SOS_token])
        output = []
        output_hs = []
        self.gru_x = []  # gru input
        self.gru_hs = []
        self.gru_zs = []
        self.dropout_mask = []
        self.embedded_x = []
        self.relu_x = []
        self.attn_x = []
        self.attn_combine_x = []
        self.attn_weights_seq = []
        self.out_x = []
        # encoder_outputs = np.pad(self.encoder_outputs, ((0, self.max_length - self.encoder_outputs.shape[0]), (0, 0), (0, 0)), 'constant')
        for t in range(target_length):
```
