
inner product). 如果查询词是“dog”，并且我们使用 $h = 2$ 或 $h = 30$，最近邻如下：

```
h=2: cat, horse, fox, pet, rabbit, pig, animal, mongrel, sheep, pigeon
h=30: kennel, puppy, pet, bitch, terrier, rottweiler, canine, cat, to bark
```

2词上下文窗口对句法更敏感，而30词窗口对语义更敏感。上下文大小 $h$ 的“最优”值取决于应用。

### 19.5.1.3 PMI

实际上，如果用 **点互信息 (PMI)** [CH90] 替换原始计数 $C_{ij}$，LSA（及其他类似方法）的结果会好得多，定义为

$$\mathbb{PMI}(i,j)=\log\frac{p(i,j)}{p(i)p(j)}\tag{19.16}$$

如果词 $i$ 与上下文 $j$ 强烈相关，则 $\mathbb{PMI}(i,j)>0$。如果 PMI 为负，意味着 $i$ 和 $j$ 的共同出现频率低于独立时的情况；然而，这种负相关可能不可靠，因此通常使用 **正点互信息**：$\mathbb{PPMI}(i,j)=\max(\mathbb{PMI}(i,j),0)$。在 [BL07] 中，他们表明对 PPMI 矩阵应用 SVD 得到的结果在与词义相关的许多任务上表现良好。参见第 19.5.3 节，了解解释这一经验性能的理论模型。

### 19.5.2 Word2vec

本节中，我们讨论来自 [Mik+13a; Mik+13b] 的流行 **word2vec** 模型，它是用于根据上下文预测词的“浅层”神经网络。在第 19.5.3 节中，我们将讨论与 PMI 矩阵 SVD 的联系。

word2vec 模型有两个版本。第一个称为 CBOW，全称为“continuous bag of words”。第二个称为 skipgram。下面我们讨论这两种。

### 19.5.2.1 Word2vec CBOW model

在连续词袋 (**CBOW**) 模型中（见图 19.10(a)），词序列的对数似然使用以下模型计算：

$$\log p(\mathbf{w}) = \sum_{t=1}^{T}\log p(w_t|\mathbf{w}_{t-H:t+H}) = \sum_{t=1}^{T}\log\frac{\exp(\mathbf{v}_{w_t}^{\top}\bar{\mathbf{v}}_t)}{\sum_{w'} \exp(\mathbf{v}_{w'}^{\top}\bar{\mathbf{v}}_t)}\tag{19.17}$$
$$= \sum_{t=1}^{T}\mathbf{v}_{w_t}^{\top}\bar{\mathbf{v}}_t - \log\sum_{w'}\exp(\mathbf{v}_{w'}^{\top}\bar{\mathbf{v}}_t)\tag{19.18}$$

其中 $\mathbf{v}_{w_t}$ 是位置 $w_t$ 处词的向量，并且

$$\bar{\mathbf{v}}_t = \frac{1}{2H}\sum_{h=1}^{H}(\mathbf{v}_{w_{t+h}}+\mathbf{v}_{w_{t-h}})\tag{19.19}$$

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_631_0.png)

是词 $w_t$ 周围大小为 $H$ 的窗口中词向量的平均值。因此我们尝试根据上下文预测每个词。该模型称为 CBOW，因为它对上下文使用词袋假设，并用连续嵌入表示每个词。

### 19.5.2.2 Word2vec Skip-gram model

在 CBOW 中，每个词由其上下文预测。其变体是根据每个词预测上下文（周围词）。这产生以下目标：

$$\log p(\mathbf{w}) \approx \sum_{t=1}^{T}\left[\sum_{h=1}^{H_t}\log p(w_{t-h}\mid w_t)+\log p(w_{t+h}\mid w_t)\right] \tag{19.20}$$

$$=\sum_{t=1}^{T}\left[\sum_{h=1}^{H_t}\mathbf{u}_{w_{t-h}}^{\mathsf{T}}\mathbf{v}_{w_t}+\mathbf{u}_{w_{t+h}}^{\mathsf{T}}\mathbf{v}_{w_t}-2\log\sum_{w'}\exp\left(\mathbf{v}_{w_t}^{\mathsf{T}}\mathbf{u}_{w'}\right)\right] \tag{19.21}$$

其中 $H_t$ 是位置 $t$ 的随机采样窗口长度，$\mathbf{u}_w$ 是词 $w$ 作为上下文词而非预测词时的嵌入向量。参见图 19.10(b) 的插图。

我们可以通过为每个 $w_t$ 采样单个上下文词 $c_t$ 来近似此目标，而不是对窗口中所有词 $w_{t-h},\ldots,w_{t+h}$ 求和：

$$\log p(\mathbf{w}) \approx \sum_t \log p(c_t\mid w_t)=\sum_t\left[\mathbf{u}_{c_t}^{\mathsf{T}}\mathbf{v}_{w_t}-\log\sum_{w'}\exp\left(\mathbf{v}_{w_t}^{\mathsf{T}}\mathbf{u}_{w'}\right)\right] \tag{19.22}$$

该模型被称为 **skipgram 模型**，因为我们使用的是 $H$-gram 模型，但跳过了大部分项。

### 第 19 章. 使用更少标记示例的学习

为了避免对所有词 $w'$ 的昂贵求和，我们可以对 $w_t$ 的较小的负词集合求和：

$$\log p(\mathbf{w}) \approx \sum_t \left[ \mathbf{u}_{c_t}^{\mathsf{T}} \mathbf{v}_{w_t} - \sum_{w' \in \text{neg}_t} \log(1 - \sigma(\mathbf{v}_{w_t}^{\mathsf{T}} \mathbf{u}_{w'})) \right] \tag{19.23}$$

其中 $\text{neg}_t$ 是在 $w_t$ 的上下文窗口中未出现的随机选择的词集合。这种方法称为带负采样的 skip-gram（SGNS），比标准 skip-gram 训练快得多。SGNS 训练比 CBOW 训练慢，但倾向于学习比 CBOW 更好的词嵌入。

在 [LG14a] 中，他们表明 SGNS 等价于对 PMI 矩阵的平移版本应用 SVD，定义为

$$\text{shiftedPMI}(i, j) \triangleq \text{PMI}(i, j) - \log(N^-) \tag{19.24}$$

其中 $N^-$ 是为每个词 $i$ 采样的负上下文数量。

与使用词的独热编码相比，词嵌入显著提高了各种 NLP 模型的性能。自然会想知道为什么上述词嵌入效果如此好。本节中，我们给出了一个基于 [Aro+16] 的简单文本文档生成模型来解释这一现象。

考虑一个词序列 $w_1, \ldots, w_T$。我们假设每个词由潜在上下文或话语向量 $\mathbf{z}_t \in \mathbb{R}^D$ 生成，使用以下对数双线性语言模型，类似于 [MH07]：

$$p(w_t \mid \mathbf{z}_t) = \frac{\exp(\mathbf{z}_t^{\mathsf{T}} \mathbf{v}_w)}{Z(\mathbf{z}_t)} \tag{19.25}$$

其中 $\mathbf{v}_w \in \mathbb{R}^D$ 是词 $w$ 的嵌入，$Z(\mathbf{z}_t)$ 是配分函数。我们假设 $D < M$，$M$ 为词汇表中词的数量。

进一步假设词嵌入 $\mathbf{v}_w$ 的先验为各向同性高斯分布，且潜在主题 $\mathbf{z}_t$ 经历缓慢的高斯随机游走。（因此称为 RAND-WALK 模型。）在该模型下，可以证明 $Z(\mathbf{z}_t)$ 近似等于与上下文无关的固定常数 $Z$。这被称为对数线性模型的自归一化性质 [AK15]。此外，可以证明模型预测的点互信息为

$$\text{PMI}(w, w') \approx \frac{\mathbf{v}_w^{\mathsf{T}} \mathbf{v}_{w'}}{D} \tag{19.26}$$

因此，我们可以通过使模型的 PMI 预测值与经验值匹配来拟合 RAND-WALK 模型，即最小化

$$L(V) = \sum_{w,w'} X_{w,w'} \left(\text{PMI}(w, w') - \mathbf{v}_w^{\mathsf{T}} \mathbf{v}_{w'}\right)^2 \tag{19.27}$$

其中 $X_{w,w'}$ 是 $w$ 和 $w'$ 相邻出现的次数。该目标可视为公式 (19.12) 中 SVD 损失的频率加权版本。

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_633_0.png)

图 19.11：word2vec 嵌入空间中算术运算的可视化。From https://www.tensorflow.org/tutorials/representation/word2vec.

此外，还可以使用一些额外的近似来证明 RAND-WALK 模型的 NLL 等价于 CBOW 和 SGNS word2vec 目标。我们还可以推导出 [PSM14a] 中流行的 GloVe 模型的目标。（GloVe 代表“global Vectors for word representation”。）

### 19.5.4 词类比

由 word2vec、GloVe 及其他类似方法产生的词嵌入最显著的特性之一是，学习到的向量空间似乎以简单的向量加法形式捕捉关系语义。特别是，我们可以通过计算来解决形式为“a 与 b 如同 c 与 ?”的词类比问题，记为 a : b :: c : ?，

$$\mathbf{d}^* = \arg\min_{\mathbf{d}} \|\left(\mathbf{v}_a - \mathbf{v}_b\right) - \left(\mathbf{v}_c - \mathbf{v}_d\right)\| \tag{19.28}$$

例如，我们有 man:woman::king:queen，事实上我们发现

$$\mathbf{v}_{\text{man}} - \mathbf{v}_{\text{woman}} \approx \mathbf{v}_{\text{king}} - \mathbf{v}_{\text{queen}} \tag{19.29}$$

我们可以使用脚本 word_embedding_spacy.py 在经验上验证这一点，该脚本使用预训练的词嵌入模型。参见图 19.11。

在 [PSM14a] 中，他们猜想 a : b :: c : d 成立当且仅当对于词汇表中的每个词 $w$，我们有

$$\frac{p(w|a)}{p(w|b)} \approx \frac{p(w|c)}{p(w|d)} \tag{19.30}$$

在 [Aro+16] 中，他们表明这源于第 19.5.3 节中 RAND-WALK 建模假设。另见 [AH19; EDH19]，其中基于不同的建模假设对词类比为何有效给出了其他解释。
