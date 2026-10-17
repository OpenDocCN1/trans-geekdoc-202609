
```python
v0 = train_set[u_id:u_id + batch_size] # 目标向量

ph0 = rbm.sample_h(v0) # 概率

# applying-k contrastive divergence

for k in range(10):

    _hk = rbm.sample_h(vk) # 采样隐藏节点

    _vk = rbm.sample_v(_hk) # 采样可见节点

    vk[v0 < 0] = 0 # 防止更新未评分的节点

phk = rbm.sample_h(vk) # k步后的概率

rbm.train(v0, vk, phk) # 训练RBM模型

# Error rate

train_loss += torch.mean(torch.abs(vk[v0 >= 0]) - v0[v0 >= 0])

s += 1

loSS = train_loss/s

print(f"Epoch no. {epoch}.t loss = {loSS}")
```

> 在执行模型前的一个修复：张量扩展后的大小（1682），我们在单例维度 1 上找到了匹配的尺寸（100）

这里也是一样，我们的 RBM 推荐模型经过了**10 步（k 步）的训练**，而对于测试集，它必须只执行 `only-one` 一步。

- 结合 MCMC（马尔可夫链蒙特卡洛）的盲走技术原理。这是指在随机游走中，要记住概率是不相等的，它是带有不同概率的盲走。

所以我们的预测将*直接*是**一次往返的结果吗？** 瑞布斯采样（Gibbs sampling）。盲走的一**步**我们就能一次性获得**测试**集的所有预测结果。

在这一步中，我们将根据条件开始/过滤掉**测试集**中的**未见过的电影**（那些从未被预测过的 -1 评分）。现在是时候处理训练-测试的 0 集合了。

- 我们使用 `len()` 来获取从目标 `vt` 中存在的真实评分（测试集的原始评分）。
- 我们使用条件 `vt=0` 获取所有存在的评分。
- `len(vt[vt==0]) > 0`：指定包含非负评分的节点数必须大于零，在这种情况下我们可以进行一些预测。

为了进行预测，我们使用 `sample_h()` 和 `sample_v()` 函数。在这一步中我们使用 `hk` 和 `vk` 的 `h` 和 `v`。

```python
if len(vt[vt==0]) > 0:
    h = rbm.sample_h(v)
    v = rbm.sample_v(h)
```

对于输入节点，我们只会得到隐藏节点，因为有一个隐藏节点向量来获取我们的最终预测，这就是盲走的一步的全部。我们不需要 `vk[0] < v[0]`，我们没有使用 `train()`，所以删除了那些行。注意，我们必须在这个 `if` 块内部更新 **test_loss** 和 **counter**（计数器）。因为这些在 `if` 块中，我们只对存在的目标计算 **test_loss**，我们使用了 `torch.mean()` 和 `torch.abs()`。

```python
test_loss += torch.mean(torch.abs(vt[vt==0] - v[vt==0]))
```

```python
if len(vt[vt==0]) > 0:
    h = rbm.sample_h(v)
    v = rbm.sample_v(h)
```

```python
# Error率
test_loss += torch.mean(torch.abs(vt[vt==0] - v[vt==0]))
cnt += 1
```

```python
eval_loss = test_loss/cnt
print(f"Evaluation or Test loss = {eval_loss}")
```

```python
# 在测试集上评估 RBM
test_loss = 0
cnt = 0
for u_id in range(nb_users):
    v = train_set_tensor[u_id:u_id + 1]
    vt = test_set_tensor[u_id:u_id + 1]
```

```python
if len(vt[vt==0]) > 0:
    h = rbm.sample_h(v)
    v = rbm.sample_v(h)
```

```python
# Error率
test_loss += torch.mean(torch.abs(vt[vt==0] - v[vt==0]))
cnt += 1
```

```python
eval_loss = test_loss/cnt
print(f"Evaluation or Test loss = {eval_loss}")
```

# 总结：

1. 我们从计数器为零开始，测试损失为零。
2. 我们循环遍历所有用户。
3. 然后，对于测试集中所有存在的评分，我们首先采样隐藏节点。
4. 我们使用隐藏节点作为输入来采样可见节点。
5. 我们在 `if` 块内部更新 `test_loss` 和计数器。

```python
test_loss = 0
cnt = 0
for u_id in range(nb_users):
    v = train_set_tensor[u_id:u_id + 1] # 来自训练集的输入向量
    vt = test_set_tensor[u_id:u_id + 1] # 来自测试集的目标向量
    if len(vt[vt==0]) > 0:
        h = rbm.sample_h(v) # 采样隐藏节点
        v = rbm.sample_v(h) # 采样可见节点
    # Error率
    test_loss += torch.mean(torch.abs(vt[vt==0] - v[vt==0]))
    cnt += 1
eval_loss = test_loss/cnt
print(f"Evaluation and Test loss is {eval_loss}")
```

# 在 [2]:

执行代码后，我们得到了 0.24 的测试损失。这绝对是优秀的，因为对于新电影的新观测值，我们成功地在四个评分中预测了一些正确的评分，甚至更好。因为我们略低于 25%。

- 在这里我们确实成功建立了一个稳健的推荐系统，但这是一个预测 0 和 1 二进制评分的简单情况。
- 在下一章中，我们将提升一个水平，因为我们将使用自动编码器（AutoEncoders）预测 1 到 5 的评分。
- 处理连续值将增加问题的复杂性。但它有助于我们通过应用不同的深度学习模型来构建不同的推荐系统。
- 但好消息是，自动编码器（AE）实际上比玻尔兹曼机（Boltzmann machine）简单得多。
- 我们为 1 到 5 的评分获得了一些惊人的预测。

# 一次性完成所有代码：RBM 推荐模型

```python
# --- RBM 推荐 ---

# 导入库
import pandas as pd
import numpy as np
import torch
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim
import torch.utils.data as data

## 导入数据
movies = pd.read_csv('./movie_len/movies.csv', sep='\t', header=None, encoding='python', encoding='latin-1')
users = pd.read_csv('./movie_len/users.csv', sep='\t', header=None, encoding='python', encoding='latin-1')
ratings = pd.read_csv('./movie_len/ratings.csv', sep='\t', header=None, encoding='python', encoding='latin-1')
```
（注：OCR 文本有很多重复和碎片化，我将根据提供的逻辑提供清理后的版本。）

## 结果

```
In [1] runfile('/O/1/Development_2.0/ML_phase_3_ML_Intro/ml_p3_ch14_dp_BLTZ/prct_RBM.py', wdir='Dr/1/Development_2.0/ML_phase_3_ML_Intro/ml_p3_ch14_dp_BLTZ')
Epoch. 1.
loss = 0.3745898604393054
Epoch. 2.
loss = 0.2449556178510856
Epoch. 3.
loss = 0.2507295629617837
Epoch. 4.
loss = 0.2438576570433044
Epoch. 5.
loss = 0.2508241567224175
Epoch. 6.
loss = 0.2465479856472015
Epoch. 7.
loss = 0.2476613223557039
Epoch. 8.
loss = 0.25108692049980164
Epoch. 9.
loss = 0.2465537935493766
Epoch. 10.
loss = 0.248631545727281
Evaluation of Test loss = 0.2431282029337383
```
