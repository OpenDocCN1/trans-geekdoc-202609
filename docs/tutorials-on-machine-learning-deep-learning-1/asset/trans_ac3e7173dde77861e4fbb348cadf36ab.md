

在这里我们将解释这个随机游走中发生了什么。

基本上，Gibbs 采样（Gibbs sampling）由 Gibbs 链组成。从可见节点到隐藏节点、从隐藏节点到可见节点，有若干次往返过程。

在我们输入的 Gibbs 采样的每次往返中，可见节点会被更新，并且我们一步步地接近我们理想的预测评分。

开始时，我们从输入的观测批次开始。也就是说，在我们包含 100 个用户的批次中，$v_0$ 中的输入评分。

采样隐藏节点：在 Gibbs 采样的第一步，使用 `sample_h()` 函数中我们的 $p\_h\_given$ 分布进行伯努利采样。

- $k$ 步对比散度（k-steps contrastive divergence）的第一步是在可见节点上进行 `sample_h(vk)`，以获得隐藏节点的第一次采样。

由于我们需要获取 `sample_h(vk)` 返回的第二个元素，因此我们像之前一样使用了 Python 技巧 `_`。

这一次，我们将使用下划线 `\_` 以及在对比散度第 $k$ 步中获取的隐藏节点。

```python
vk = rbm.sample_h(vk)
# sampling hidden nodes
```

由于我们正在根据第一个可见节点的值（即我们的原始评分）对第一个隐藏节点进行采样，因此在 Gibbs 采样的这一步中，`sample_h(vk)` 的输入保持不变。我们需要采取这一点，因为第一步 $v_0 = vk$，所以这是我们的观测输出，然后我们将对其进行更新。

- 在第一次采样后，获取可见节点的第一次更新。

采样可见节点：在我们使用以下函数 `sample_v(vk)` 更新 $vk$ 后。

所以现在 $vk = v_0$，但随后我们将 $vk$ 更新为 Gibbs 采样的第一步，即在获取它之后。

我们将通过在隐藏节点的第一次采样上使用 `sample_v(vk)` 及其我们的 $p\_v\_given$ 分布进行伯努利采样来获取它。

我们再次获取 `sample_v(vk)` 返回的第二个元素，我们使用了 Python 技巧下划线 `\_`。

```python
vk = rbm.sample_v(vk)
# sampling visible nodes
```

- 在第一次采样后，获取可见节点的第一次更新。

这是我们随机游走的第一步，也就是 Gibbs 采样的第一步。

```python
for k in range(10):
    _vk = rbm.sample_h(vk)
    # sampling hidden nodes
    _vk = rbm.sample_v(vk)
    # sampling visible nodes
```

随着循环继续，$hk$ 和 $vk$ 反复更新自身。

### 算法 1. RBM 对比散度
输入：RBM ($V_1, ..., V_m, H_1, ..., H_m$)，训练批次 $S$
输出：梯度近似 $\Delta w_{ij}, \Delta b_j$ 和 $\Delta v_i$，对于 $i=1, ..., n, j=1, ..., m$
初始化 $\Delta w_{ij} = \Delta b_j = \Delta v_i = 0$，对于 $i=1, ..., n, j=1, ..., m$
for $v$ in $S$
    $v^{(0)} \leftarrow v$
    for $t=0, ..., k-1$
        for $i=1, ..., n$ 执行采样 $h_i^{(t)} \sim p(h_i | v^{(t)})$
            for $j=1, ..., m$ 执行采样 $v_j^{(t+1)} \sim p(v_j | h^{(t)})$
        for $i=1, ..., n, j=1, ..., m$ 执行
            $\Delta w_{ij} \leftarrow \Delta w_{ij} + p(h_i | v^{(t)}) \cdot v_j^{(t)} - p(H_i=1 | v^{(k)}) \cdot v_j^{(k)}$
            $\Delta b_j \leftarrow \Delta b_j + v_j^{(t)} - v_j^{(k)}$
            $\Delta v_i \leftarrow \Delta v_i + p(H_i=1 | v^{(0)}) - p(H_i=1 | v^{(k)})$

循环结束后，我们将获得第 10 个隐藏节点采样和第 10 个可见节点采样。

在随机游走最后一步之后获取 $h_k$ 和 $v_k$，我们现在可以通过 $k$ 步对比散度算法的第 8、9 和 10 步来近似梯度。

我们观察到的是 $k$ 步对比散度算法的第 5 和 6 步。

我们想要在随机游走最后一步之后获取最后一个采样，即最后一个隐藏节点采样和最后一个可见节点采样。

我们需要这些最后的采样来更新权重和偏置，以近似梯度。

实际上，这里是可见节点的最后一个采样：

- 但我们不仅使用最后一个隐藏节点采样，那只是为了获取最后一个可见节点。
- 我们得到了 $v_k$：我们现在可以近似权重和偏置的梯度。
- 我们使用 RBM 类中的 `train()` 来更新权重和偏置。

忽略权重更新期间不需要的内容：在使用此函数更新权重之前，我们需要做一些重要的工作：

- 我们不想更新没有评分的单元格，即值为 -1 的单元格。
- 我们将在训练过程中忽略包含 -1 的单元格。
- 我们冻结这些可见节点，以便在 Gibbs 采样期间无法更新它们。

如何冻结这些包含 -1 的可见节点？我们需要获取 $v_k$ 可见节点，并在 for 循环内部：

```python
for k in range(10):
    _hk = rbm.sample_h(vk) # sampling hidden nodes
    vk = rbm.sample_v(vk) # sampling visible nodes
    vk[<0] = v_0[<0]
```

也就是说，我们使用 $v_0$ 来保持 $vk$ 不被更新。$vk[<0]$ 获取了评分 -1 的节点，即原始未评分的节点。我们使用 $v_0$ 是因为它不被更新。评分不是 -1 要就是 1。

通过这种方式，我们确保训练不是针对实际上未评分的评分进行的。

现在我们退出了这个循环，很快就会开始训练。

### 14.5.4 训练 RBM 模型 - 部分 3：train()

$ph_k$：我们想要应用 `train()` 函数来更新权重和偏置。但注意，在这个 `train()` 函数中，我们需要：

```python
def train(self, v0, ph0, phk):
```

i. 目标，$v_0$
ii. 我们在随机游走最后一步采样的可见节点，$vk$。
iii. 初始概率，$ph_0$。
iv. $k$ 步概率，$ph_k$。

注意，我们有 $ph_k$：它在开始时并没有计算。所以在应用 `train()` 函数之前，我们计算了 $ph_k$。

我们获取 `sample_h()` 返回的第一个元素。我们在 $vk$ 上应用 `sample_h()`，即最后一个可见节点采样（我们从 for 循环结束得到的），随机游走第 10 步的最后一个可见节点，Gibbs 采样。

```python
ph_k = rbm.sample_h(vk) # probabilities after k-step
```

现在我们准备好应用 `train()` 函数了。

- train()现在让我们应用 `train()` 函数。将会有很多操作。
- 注意，`train()` 函数不返回任何内容。它根据第 8、9、10 步的 $k$ 步对比散度更新权重。
- 所以我们不需要新变量。
- 我们使用 RBM 对象并应用 `train()`，使用 $v_0, vk$ 和 $ph_k$ 值。

```python
# 创建 RBM 模型
v = len(train_tensor[0])
h = 100
batch_size = 100

m = RBM(nv, nh)

# 训练 RBM
for epoch in range(1, nb_epoch + 1):
    s = 0
    for u_id in range(0, nb_users - batch_size, batch_size): # 输入向量
        vk = train_tensor[u_id:u_id + batch_size] # 目标向量
        v0 = train_tensor[u_id:u_id + batch_size]

        ph_0 = rbm.sample_h(v0) # 初始概率
        # 应用 k 步对比散度
        for k in range(10):
            _hk = rbm.sample_h(vk) # 采样隐藏节点
            _vk = rbm.sample_v(vk) # 采样可见节点
            vk[<0] = v0[<0] # 防止更新未评分节点

        ph_k = rbm.sample_h(vk) # k 步后的概率
        rbm.train(v0, vk, ph_0, ph_k) # 训练 RBM 模型
```

现在训练正在进行。权重和偏置将朝着极大似然的方向进行更新。

因此，我们所有的概率 $(v|h)$，可见节点看到隐藏节点将变得越来越相关。

它将为最重要的概率获得最大的权重，最终引导我们获得接近真实评分的预测评分。

### 14.5.5 训练 RBM 模型 - 部分 4：衡量误差-train_loss

我们现在计算 `train_loss` 来衡量预测评分与真实评分之间的关系。

现在我们更新 `train_loss`，它之前被设置为 0，因为现在我们有了所有的预测，使用我们的权重 `training()`。

- 这里 `torch.abs(vk[>=0] - v0[>=0])` 计算的是 $vk - v0$ 的绝对值张量。
- 我们只取 $vk$ 和 $v0$ 的非负值，使用条件 $v0 \ge 0$。
- 最后我们使用 `torch.mean()` 找到绝对值的简单差异。

