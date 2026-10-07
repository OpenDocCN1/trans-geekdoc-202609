
但最常用的损失衡量方法是 RMSE，即均方根误差，我们将在下一章用它来构建自动编码器（Auto-Encoders）。

此外，我们在第二个for循环中增加了计数器 `s` 和 `train_loss`。在第二个for循环之外，我们计算归一化的 `train_loss`，并打印这个值和轮数（epoch）。

```python
# Error rate
train_loss += torch.mean(torch.abs(vk[v0 >= 0]) - v0[v0 >= 0])
s += 1.0

loSS = train_loss/s
print(f"Epoch no. {epoch}.t loss = {loSS}")
```

在最后步骤中，值正接近最优解。最优样本可见节点的 Gibbs 采样（Gibbs sampling）步骤包含了我们最好的预测排名。
我们比较了通过网络的一批用户后，最后一个可见节点的非负值：对比散度的最后一步和目标向量，它们的绝对值，并计算了绝对值的简单距离。即预测评分与真实评分之间的绝对值简单距离。

记住，在训练过程中我们忽略了实际上不存在的评分，即 -1 的评分被忽略了。因此，我们在这里考虑了非负值。

当我们比较这些真实评分与预测之间的差异时，我们必须考虑那些实际上存在的。

```python
# Training the RBM
nb_epoch = 10
for epoch in range(1, nb_epoch + 1):
    train_loss = 0
    for u_id, nb_users in range(0, batch_size, batch_size):
        vk = train_set[u_id:u_id + batch_size] # 输入向量
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

```python
return p_v_given_h, torch.bernoulli(p_v_given_h)
def train(self, v0, vk, phk):
    return torch.mean(v0.t(), phk) - torch.mean(vk.t(), phk)
    self.b += torch.sum(v0 - phk, 0)
    self.a += torch.sum(ph0 - phk, 0)
```

现在，`print(rbm.W.size())` 将显示 `torch.Size([108, 1682])`
`print(torch.mean(v0.t(), ph0)-torch.mean(vk.t(), phk).size())` 将显示 `torch.Size([1682, 100])`

所以看起来我们应该对 `(torch.mm(v0.t(), ph0)-torch.mm(vk.t(), phk))` 进行转置，因此它应该类似于 **torch.mm(v0.t(), ph0)** - **torch.mm(vk.t(), phk)**：我们只需使用 **t()** 进行转置。

因此，在我们的 RBM 类中更新这段代码：

```python
class RBM:
    def __init__(self, nv, nh):
        pass

    def train(self, v0, vk, ph0, phk):
        self.w += torch.mm(v0.t(), ph0) - torch.mm(vk.t(), phk)
```

```python
# 创建神经网络的架构
class RBM:
    def __init__(self, nv, nh):
        self.w = torch.randn(nh, nv)
        self.a = torch.randn(1, nh)
        self.b = torch.randn(1, nv)

    def sample_h(self, x):
        wx = torch.mm(x, self.w)
        activation = wx + self.a.expand(wx)
        p_h = torch.sigmoid(activation)
        return torch.bernoulli(p_h)

    def sample_v(self, y):
        wy = torch.mm(y, self.w.t())
        activation = wy + self.b.expand(wy)
        p_v = torch.sigmoid(activation)
        return torch.bernoulli(p_v)

    def train(self, v0, vk, ph0, phk):
        self.w += torch.mm(v0.t(), ph0) - torch.mm(vk.t(), phk)
        self.b += torch.sum(v0 - vk, 0)
        self.a += torch.sum(ph0 - phk, 0)
```

```python
# 创建神经网络架构
nv = len(train_set)
nh = 100
batch_size = 100

rbm = RBM(nv, nh)

# Training RBM
nb_epoch = 10
for epoch in range(1, nb_epoch + 1):
    train_loss = 0
    for u_id, nb_users in range(0, batch_size, batch_size):
        vk = train_set[u_id:u_id + batch_size] # 输入向量
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
