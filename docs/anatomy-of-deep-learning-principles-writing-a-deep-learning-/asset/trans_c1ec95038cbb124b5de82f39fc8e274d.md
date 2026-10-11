

#### 训练与损失记录

```python
epoch_losses, H = rnn_train_epoch(params, data_it, optimizer, iterations, loss_function, print_n=50)

# losses.extend(epoch_losses)

epoch_losses = np.array(epoch_losses).mean()

losses.append(epoch_losses)
```

#### 输出形状与训练日志

```
(5000,)

X: (50, 3, 1) Y: (50, 3, 1) H: (3, 100)

Z: (3, 1) H: (3, 100)

(3, 1)

iter 0, loss: 52.575362

iter 0, loss: 41.488531

iter 0, loss: 2.666009

iter 0, loss: 1.424797

iter 0, loss: 0.849381

iter 0, loss: 0.723504

iter 0, loss: 0.581355

iter 0, loss: 0.938593

iter 0, loss: 1.019344

iter 0, loss: 0.297335
```

#### 绘制训练损失曲线

```python
import matplotlib.pyplot as plt

plt.plot(losses)
plt.show()
```

![](EPUB/media/file152.png)

**图 7-25** RNN 自回归模型训练损失曲线

#### predict

以下代码使用训练好的 RNN 模型，从某一时刻的数据预测未来 500 个时刻的输出：

```python
H = rnn_hidden_state_init(1, hidden_size)

start = 3

x = data[start:start+1].copy()
x = x.reshape(x.shape[0], 1, -1)
print(x.shape)

x = x.reshape(1, -1)

ys = []
print(x.flatten())

for i in range(500):
    F, H = rnn_forward_step(params, x, H)
    x = F
    ys.append(F[0, 0])

print(len(ys))
ys = ys[:]

plt.plot(ys[:500])
plt.plot(data[start+1:start+1+500])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y', 'y_real'])
plt.show()
```

```
(1, 1, 1)

[1.12085582]

500
```

![](EPUB/media/file153.png)

**图 7-26** RNN 自回归模型长期预测数据与真实数据对比

该预测准确度一般。若仅从当前时刻预测下一时刻数据，即从 `data[t]` 预测 `data[t+1]`，则效果会好得多。以下代码采用这种短期预测方法，利用 `data[start, start+500]` 中每一时刻的数据预测下一时刻，即预测 `data[start+1, start+1+500]`：

```python
H = rnn_hidden_state_init(1, hidden_size)

start = 3
ys = []

for i in range(500):
    x = data[start+i:start+i+1].copy()
    x = x.reshape(1, -1)
    F, H = rnn_forward_step(params, x, H)
    ys.append(F[0, 0])

ys = ys[:]

plt.plot(ys[:500])
plt.plot(data[start+1:start+501])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y', 'y_real'])
plt.show()
```

![](EPUB/media/file154.png)

**图 7-27** RNN 自回归模型短期预测数据与真实数据对比

下一时刻的短期预测结果与真实数据完全重合，表明短期预测效果极佳。上述 RNN 相关代码位于本书代码中的 `rnn.py` 文件中。

#### 股票数据的训练与预测

对于股票数据，可仅使用收盘价作为序列数据来预测收盘价。以下代码将股票收盘价数据作为自回归数据：

```python
data = read_stock('sp500.csv')
data = np.array(data.iloc[:, -2]).reshape(-1, 1)
```

对于此类自回归序列数据，可直接使用上述代码进行训练和预测。学习率为 `1e-4`，批量梯度下降法的迭代轮数 `epoches` 为 40。模型训练的损失曲线如下：

![](EPUB/media/file155.png)

**图 7-28** 股票收盘价自回归模型训练损失曲线

长期预测与短期预测分别如下图所示：

![](EPUB/media/file156.png)

**图 7-29** 股票收盘价自回归模型长期预测

![](EPUB/media/file157.png)

**图 7-30** 股票收盘价自回归模型短期预测

以上仅利用股票收盘价历史数据预测未来收盘价。下面的代码使用股票的所有指标（开盘价、最高价、最低价、收盘价、成交量）来预测收盘价。首先训练 RNN 模型：

```python
import pandas as pd
import numpy as np

data = read_stock('sp500.csv')

stock_data = np.array(data)
print("stock_data.shape", stock_data.shape)
print("stock_data[:3]\n", stock_data[:3])

def stock_data_iter(data, seq_length):
    feature_n = data.shape[1]
    num = (len(data) - 1) // seq_length

    while True:
        for i in range(num):
            # 选择一个训练样本
            p = i * seq_length
            inputs = data[p:p+seq_length]
            targets = data[p+1:p+seq_length+1][:, -2]
            inputs = np.expand_dims(inputs, axis=1)
            targets = targets.reshape(-1, 1)

            if i == 0:
                yield inputs, targets, True
            else:
                yield inputs, targets, False

batch_size = 1
input_dim = stock_data.shape[1]
hidden_dim = 100
output_dim = 1

params = rnn_params_init(input_dim, hidden_dim, output_dim)
H = rnn_hidden_state_init(batch_size, hidden_dim)

seq_length = 100  # RNN 展开步数
data_it = stock_data_iter(stock_data, seq_length)

X, Y, _ = next(data_it)
print(X.shape, Y.shape)

loss_function = lambda F, Y: rnn_loss_grad(F, Y, util.mse_loss_grad, False)

# 超参数
epoches = 2
learning_rate = 1e-4
iterations = 2000

losses = []

# optimizer = AdaGrad(params, learning_rate)
momentum = 0.9
optimizer = SGD(params, learning_rate, momentum)

for epoch in range(epoches):
    data_it = stock_data_iter(stock_data, seq_length)
    # epoch_losses, param, H = rnn_train(params, data_it, learning_rate, iterations, loss_function, print_n=100)
    epoch_losses, H = rnn_train_epoch(params, data_it, optimizer, iterations, loss_function, print_n=200)
    losses.extend(epoch_losses)
    # epoch_losses = np.array(epoch_losses).mean()
    # losses.append(epoch_losses)

plt.plot(losses)
```

```
stock_data.shape (4697, 5)

stock_data[:3]
 [[-0.00597324 -0.00591629 -0.01567558 -0.01231037 -0.19118446]
  [-0.01226569 -0.01617188 -0.03401657 -0.03724877 -0.1842296 ]
  [-0.0372919  -0.03505779 -0.04286668 -0.03604657 -0.17733781]]

(100, 1, 5) (100, 1)

iter 0, loss: 0.105906
iter 200, loss: 0.092861
iter 400, loss: 0.561419
iter 600, loss: 0.061234
iter 800, loss: 0.447817
iter 1000, loss: 2.762900
iter 1200, loss: 0.713906
iter 1400, loss: 0.022479
iter 1600, loss: 0.004160
iter 1800, loss: 0.011423
iter 2000, loss: 0.033837
```

![](EPUB/media/file158.png)

**图 7-31** 股票数据模型训练损失曲线

上述序列数据并非自回归数据。每一时刻的股票数据是由多个特征组成的向量，而预测的下一时刻股价是一个单一数值，即输入为多值向量、输出为单值数据，因此该模型无法进行长期预测。以下代码基于训练好的 RNN 进行短期预测：

```python
H = rnn_hidden_state_init(1, hidden_dim)

start = 3
data = stock_data[start:, :]
ys = []

for i in range(len(data)):
    x = data[i, :].copy()
    x = x.reshape(1, -1)
    f, H = rnn_forward_step(params, x, H)
    ys.append(f[0, 0])

ys = ys[:]

plt.plot(ys[:500])
plt.plot(data[:500, -2])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y', 'y_real'])
```

