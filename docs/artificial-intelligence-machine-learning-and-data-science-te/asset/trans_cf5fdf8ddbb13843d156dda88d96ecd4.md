

## 深度注意力融合

深度融合在执行状态更新时，会在计算状态更新时合并互注意力和自注意力（由解码器发起）。

按如下方式计算时间步 `t` 的输入与整个源序列中各 token 之间的互注意力：

```
b_{j}^{t} = u^{t} tanh( W_{\gamma}\gamma_{j} + W_{x}x_{t} + W_{\overline{\gamma}}{\widetilde{\gamma}}_{t - 1} ) (12.13)
```

```
p[j]^{(t)} = softmax(b[j]^{(t)}) (12.14)
```

我们按如下方式测量源记忆带 `\tilde{\alpha}[t]` 和隐藏带 `\tilde{\gamma}[t]` 的自适应表示：

```
\begin{bmatrix} {\widetilde{\gamma}}_{t} \\ {\widetilde{\alpha}}_{t} \\ \end{bmatrix} = \sum\limits_{j = 1}^{m}p_{j}^{t} \cdot \begin{bmatrix} \gamma_{j} \\ \alpha_{j} \\ \end{bmatrix} (12.15)
```

然后，我们可以通过另一个门控操作 `r[t]` 将自适应源表示 `\tilde{\alpha}[t]` 移至目标记忆，这类似于公式中的门控机制。

新的目标记忆由互对齐 `r[t] ⊙ \tilde{\alpha}[t]`、内部关系 `f[t] ⊙ \tilde{C}[t]` 以及新颖输入信息 `i[t] ⊙ \hat{C}[t]` 组成：

```
C[t] = r[t] ⊙ \tilde{\alpha}[t] + f[t] ⊙ \tilde{C}[t] + i[t] ⊙ \hat{C}[t] (12.16)
```

```
h[t] = o[t] ⊙ tanh(C[t]) (12.17)
```

深度融合的主要修改在于目标记忆网络中互对齐向量的循环存储，这是一种帮助目标网络分析源信息的方式。

## 12.2.4 NLP-机器翻译

通过注意力过程将神经网络连接到外部记忆资源的能力能够进行通信（[Li et al. 2016b](#ch20.xhtml#r466)）。这种池化安排类似于图灵机或冯·诺依曼架构，但具有端到端可微分的特性，能够通过梯度下降有效地训练数据。结果表明，神经图灵机通过在一种朴素方法上工作，性能优于其他算法。

固定长度向量的使用增强了编码器-解码器框架的有效性，并提出了一种自动模型来探索与预测目标词相关的源句子（[Lowe et al. 2015](#ch20.xhtml#r467)）。作者在英译法任务上测试了所提出的方法，并发现其有效。作者引入了一种先进的神经机器翻译架构（参见[图 12.6](#ch20.xhtml#f107)）。该先进架构包含一个双向 RNN 作为编码器，以及一个在解码翻译时可视化基础短语搜索的解码器。

![Figure 12.6 The graphical representation of the suggested framework trying to produce the t-th target word y_{t} given a source sentence ( x_{1},x_{2},...,x_{T}) .](html/images/9780367720919_C012_006.jpg)

图 12.6 给定源句子（ `x[1]`、`x[2]`、…、`x[T]`），建议框架试图生成第 t 个目标词 `y[t]` 的图形表示。

### 解码器：一般描述

我们在公式 12.18 中描述新模型框架中的每个条件概率：

```
p(y[i]|y[1],...,y[i-1],X) = g(y[i-1],s[i],c[i]) (12.18)
```

其中 `s[i]` 表示时间步 i 的 RNN 隐藏状态，由以下公式计算：

```
s[i] = f(s[i-1],y[i-1],c[i]) (12.19)
```

上下文向量 `c[i]` 依赖于一系列标注（`h[1]`、…..、`h[T[x]]`），编码器用这些标注来表示输入句子。每个标注 `h[i]` 包含关于整个输入序列的信息，并重点关注输入序列中第 i 个词周围的部分。

然后，上下文向量 `c[i]` 计算为这些标注 `h[i]` 加权总和：

```
c_{i} = \sum\limits_{j = 1}^{T_{x}}\alpha_{ij}h_{j} (12.20)
```

每个标注 `h[j]` 的权重 `\alpha[i j]` 由以下公式计算：

```
\alpha_{ij} = \frac{exp( e_{ij} )}{\sum_{k = 1}^{T_{x}}exp( e_{ik} )} (12.21)
```

其中

```
e[i j] = a(s[i-1],h[j])
```

表示评估位置 j 附近的输入与位置 i 的输出匹配程度的对齐模型。该分数基于 RNN 隐藏状态 `s[i-1]`（生成 i 之前，公式 12.18）和输入句子的第 j 个标注 `h[j]`。

### 编码器：用于标注序列的双向 RNN

双向 RNN 包含前向和后向 RNN。前向 RNN `\overset{\rightarrow}{f}` 按顺序读取输入结构（从 `x[1]` 到 `x[T[x]]`）并计算一系列前向隐藏状态（`{\overset{\rightarrow}{(h}}_{1},...,{\overset{\rightarrow}{h}}_{T_{x}}`）。后向 RNN 按相反顺序读取序列（从 `x[T[x]]` 到 `x[1]`），生成一系列后向隐藏状态（`{\overset{\leftarrow}{h}}_{1},...,{\overset{\leftarrow}{h}}_{T_{x}}`）。

有两个关键目标，即全局目标和局部目标，用于有效类别的注意力装置（[Lowe et al. 2016](#ch20.xhtml#r468)）。全局任务始终关联整个源词，而局部任务仅以特定方式处理词段。这两种任务在英德 WMT 翻译任务上进行了测试。在 WMT 15 英德翻译任务中，提出的集成技术获得了 25.9 BLEU 分。与其它先进方法相比，所提出的方法表现更优。

神经机器翻译（NMT）的覆盖建模与注意力模型相结合，该模型专注于未翻译的源词。广泛的研究表明，与翻译和对齐质量相比，所建议技术的有效性（[Luong et al. 2015](#ch20.xhtml#r469)）。

## 12.2.5 NLP-对话系统（开放域、生成式）

新回复生成系统通过非结构化的 Twitter 对话进行端到端训练（[Maas et al. 2011](#ch20.xhtml#r470)）。作者使用神经网络处理文本数据积累带来的稀疏性问题，并处理对话系统。与其他流行方法相比，所提出的方法表现更优，并在上下文敏感和非上下文敏感的机器释义及数据检索标准上实现了一致的准确性。

![Figure 12.7 In the above scheme, the DCGM-01 is shown on the left, while DCGM-02 is shown on the right. The decoder RLM obtains a discrimination from the context encoder. In DCGM-01, the encoding of the bag of words describe c and m in a single vector bcm. In DCGM-02, we combine the representations bc. and bm on the first layer to preserve order information.](html/images/9780367720919_C012_007.jpg)

图 12.7 在上图中，DCGM-01 显示在左侧，DCGM-02 显示在右侧。解码器 RLM 从上下文编码器获取判别信息。在 DCGM-01 中，词袋编码在单个向量 bcm 中描述 c 和 m。在 DCGM-02 中，我们在第一层组合表示 bc. 和 bm 以保留顺序信息。

作者建议了以下上下文敏感模型：

> **上下文敏感模型**，区分两个参与者 `A` 和 `B` 之间对话中的 3 个语言实体：上下文 `c`、消息 `m` 和回复 `r`。上下文 `c` 表示任意长度的一系列早期对话轮次；然后 `B` 产生一条消息 `m`，`A` 通过构思其回复 `r` 来进行响应。

我们使用 3 个基于上下文的生成模型来评估回复 `r`（`r = r[1], ..., r[T]`）的生成模型，条件是过去的信息 `c` 和 `m`：

```
p( r|c,m ) = \prod\limits_{t = 1}^{T}p( r_{t}|r_{1},...,r_{t - 1},c,m ) (12.22)
```

