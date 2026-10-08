

## 5.3 受限玻尔兹曼机器

此处为空：

```
$P(s_i=1|s_{\sim i}) = \frac{\exp(\mathbf{d}_i + \mathbf{d}'_{s_{\sim i}} + 2\alpha'_{s_{\sim i}} + s'_{A\cdot s_{\sim i}})}{\exp(\mathbf{d}_i + \mathbf{d}'_{s_{\sim i}} + 2\alpha'_{s_{\sim i}} + s'_{A\cdot s_{\sim i}}) + \exp(\mathbf{d}'_{s_{\sim i}} + s'_{A\cdot s_{\sim i}}))}$
= \frac{\exp(\mathbf{d}_i + 2\alpha'_{s_{\sim i}})}{\exp(\mathbf{d}_i + 2\alpha'_{s_{\sim i}}) + 1} + \exp(-\mathbf{d}_i - 2\alpha'_{s_{\sim i}})}$
= \text{sign}(\mathbf{d}_i + 2\alpha'_{s_{\sim i}})$ (5.19)
```

这本质上是人工神经网络中根据其他 $s_{\sim i}$ 计算神经元输出的标准方程。

由于每个样本 $x$ 都需要两个 MCMC 链（一个用于正相，一个用于负相），梯度的计算可能非常昂贵，训练时间也很长。这本质上就是为什么玻尔兹曼机器在 20 世纪 80 年代后期被多层神经网络的反向传播算法取代成为主流学习方法的原因。然而，最近的工作表明，短链有时可以成功使用，这就是对比散度（Contrastive Divergence）的原理，该原理将在 5.4 节中讨论，用于训练 RBM。另外注意，负相不需要为每个新样本 $x$ 重新启动（因为它不依赖于训练数据），这一观察已在 5.4.2 节讨论的持久 MCMC 估计器 [161, 187] 中利用。

## 5.3 受限玻尔兹曼机器

*受限玻尔兹曼机器（Restricted Boltzmann Machine, RBM）* 是深度信念网络（DBN）的构建模块，因为它与 DBN 的各个层共享参数化，并且已经发现了训练它的高效学习算法。RBM 的无向图模型如图 4.5 所示，显示了在给定 $x$ 的情况下 $\mathbf{h}$ 之间相互独立，在给定 $\mathbf{h}$ 的情况下 $\mathbf{x}_j$ 之间相互独立。在 RBM 中，方程 (5.15) 中的 $U=0$ 且 $V=0$，这意味着唯一的交互项存在于隐藏单元和可见单元之间，而不是同一层的单元之间。这种形式的模型最早以*调和器（Harmonium）* [178] 的名称引入并在 [51] 中讨论了除玻尔兹曼机器以外的学习算法。最近提出了经过经验证明的高效学习算法及其变体 [31, 70, 200]。由于缺乏输入-输入和隐藏-隐藏的相互作用，能量函数是双线的：

```
$Energy(\mathbf{x}, \mathbf{h}) = -\mathbf{b}'\mathbf{x} - \mathbf{c}'\mathbf{h} - \mathbf{h}'\mathbf{Wx} \quad (5.20)$
```

以及通过方程 (5.11) 和 (5.13) 引入的输入自由能量分解，可以应用于 $\beta(\mathbf{x})=\mathbf{b}'\mathbf{x}$ 和 $\gamma_i(\mathbf{x},\mathbf{h})=-h_i(c_i + W_ix)$，其中 $W_i$ 是对应于 $\mathbf{W}$ 第 $i$ 行的行向量。因此，输入的自由能量（即其未归一化的对数概率）可以高效地计算：

```
$FreeEnergy(\mathbf{x}) = -\sum_{i} \log \sum_{h_i} e^{h_i(c_i + W_ix)} 
```

由于 $Energy(\mathbf{x},\mathbf{h})$ 关于 $\mathbf{h}$ 是仿射形式，使用相同的分解技术（方程 (5.12)），很容易得到条件概率 $P(\mathbf{h}|\mathbf{x})$ 的易处理表达式：

```
$P(\mathbf{h}|\mathbf{x}) = \frac{\exp(\mathbf{b}'\mathbf{x} + \mathbf{c}'\mathbf{h} + \mathbf{h}'\mathbf{Wx})}{\sum_{\mathbf{h}} \exp(\mathbf{b}'\mathbf{x} + \mathbf{c}'\mathbf{h} + \mathbf{h}'\mathbf{Wx})} = \frac{\prod_i \sum_{h_i} \exp(c_ih_i + W_ix)}{\prod_i \sum_{h_i} \exp(h_i(c_i + W_ix))} = \prod_i P(h_i|\mathbf{x}).
```

在 $h_i \in \{0,1\}$ 的常见情况下，我们得到了神经元输出的标准方程：

```
$P(h_i|\mathbf{x}) = \frac{e^{c_i+W_ix}}{1 + e^{c_i+W_ix}} = sign(c_i + W_ix). \quad (5.22)$
```

由于 $\mathbf{x}$ 和 $\mathbf{h}$ 在能量函数中起着对称的角色，类似的推导让我们能够计算：

```
$P(\mathbf{h}|\mathbf{x}) = \prod_i P(h_i|\mathbf{x}) \quad (5.23)$
```

在 $h_i \in \{0,1\}$ 的常见情况下，我们得到了神经元输出的标准方程：

```
$P(x_j=1|\mathbf{h}) = \sigma(\mathbf{b} + \mathbf{W}^T\mathbf{h}) \quad (5.24)$
```

其中 $W_j$ 是 $W$ 的第 $j$ 列。

（注：由于原文 OCR 存在大量重复和碎片，此处已根据书籍内容进行了清理重构。）

