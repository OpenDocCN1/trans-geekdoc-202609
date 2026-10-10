

## 图 12.4 传统 C&W 模型和用于学习情感特定词嵌入的神经网络（SSWEh 和 SSWEu）（[Ghosh et al. 2017](#ch20.xhtml#r458)）

在 `SSWEh` 模型中，Softmax 层的交叉熵误差为：

```
$loss_{h}\left( t \right) = - \sum\limits_{k = \{{0,1}\}}f_{k}^{g}\left( t \right) \cdot log\left( {f_{k}^{h}\left( t \right)} \right)$ (12.5)
```

其中 `f^g(t)` 显示情感分布，而 `f^h(t)` 显示预测的情感分布。

损失函数 `SSWEu` 是 `SSWEu` 组合模型中两个铰链损失的顺序混合。

```
$loss_u(t,t^{(\tau)}) = \alpha \cdot loss_{c\omega}(t,t^{(\tau)}) + (1-\alpha) \cdot loss_{us}(t,t^{(\tau)})$ (12.6)
```

其中 `loss_{c\omega}(t,t^{(\tau)})` 是句法损失，`loss_{us}(t,t^{(\tau)})` 是公式 12.7 中描述的情感损失。超参数 `α` 权衡这两部分。

```
$loss_{us}(t,t^{(\tau)}) = max(0,1-\delta[s](t)f[1]^{(u)}(t)+\delta[s](t)f[1]^{(u)}(t^{(\tau)}))$ (12.7)
```

使用相同的神经网络和相似的参数设置，一元语法、二元语法和三元语法的嵌入分别执行。

一元语法（二元语法/三元语法）的上下文分别是周围的一元语法（二元语法/三元语法）。

所引入的方法通过优化语义词典的向量空间表示，呈现出相似的向量演示（[Gonçalves et al. 2013](#ch20.xhtml#r459)）。大量实验验证了在多种语言上测试的有效性，并实现了词向量模型的改进。与流行方法相比，所提出的方法表现更优。

基于随机游走原型中的语篇向量，提出了一种简单高效的无监督句子嵌入方法，该原型旨在生成文本（[Graves et al. 2014](#ch20.xhtml#r460)）。与安排相同任务的基线任务相比，所提出的方法更优，且优于 RNN、LSTM 等监督方法。句子嵌入是通过下游监督方案实现的一种特性，其性能优于其他先进技术。

通过来自大量数据的情感词典，增强了词表示的学习（[Howard & Ruder 2018](#ch20.xhtml#r461)）。使用 `Word2Vec SkipGram` 提取了细粒度数据，即单词在训练期间的心理语言学和表达定位。对于累积学习，同时使用了 `Word2Vec CBOW` 和 `GloVe` 方法。由 Warriner 情感词典控制的未标注数据被用于正则化向量表示学习。大量研究显示了所建议方法的效率，且该方法在情感检测上表现更优。

作者为每个词开发了一种 Skipgram 技术，该词由字符 n-gram 包表示（[Kim 2014](#ch20.xhtml#r462)）。在此设计中生成的每个字母 n-gram 都与与其相关的向量和词相结合。所提出的方法速度快，训练期间提供快速数据访问，并允许词描绘。作者在九种不同语言上测试了所提出的方法，用于相似度和类比方案。与最近提出的形态词表示方法相比，所提出的方法表现更优。

作者给出了一种快速、简单且高效的方法，用于通过不同平台上的上下文学习词嵌入数据（[Kiperwasser & Goldberg 2016](#ch20.xhtml#r463)）。大量研究显示了所提出方法在众多下游 NLP 任务上的效率。

建议的方案工作如下：

首先，让我们描述 Skipgram 框架的意图。

```
$L_{\mathcal{D}} = \sum\limits_{({\omega,c}) \in \mathcal{D}}\#\left( {\omega,c} \right)\left( {\left( {log\,\sigma(\omega \cdot c} \right) + \sum\limits_{i = 1}^{k}E_{{c^{\prime}}_{i}^{}\sim P{(\omega)}}\left. \left\lbrack {\log\sigma\left( {- \omega \cdot {c^{\prime}}_{i}^{}} \right)} \right\rbrack \right)} \right)$ (12.8)
```

其中 `𝒟` 指的是我们通过其学习词嵌入的完整文本语料库。词 `w` 是当前词，`c` 是上下文词，`#(ω, c)` 是它们在 `𝒟` 中共现的次数。我们使用 `ω` 和 `c` 分别指代 `ω` 和 `c` 的向量表示。符号 `σ(⋅)` 表示 Sigmoid 函数。词 `c'[i]` 是从分布 `P(ω)` 中采样的“负样本”——通常选择为一元语法分布 `U(ω)` 的 3/4 次幂。

作者首先通过源域 `𝒟[s]` 为每个词 `ω` 学习一个嵌入 `ws`。接下来，我们按如下方式学习目标域嵌入：

```
${L'}_{\mathcal{D}_{t}}^{} = L_{\mathcal{D}_{t}} + \sum\limits_{\omega \in \mathcal{D}_{t} \cap \mathcal{D}_{s}}\alpha_{\omega} \cdot \left\| {\omega_{t} - \omega_{s}} \right\|^{2}$ (12.9)
```

其中 `𝒟[t]` 指的是目标域，`ω[t]` 是 `ω` 的目标域表示。这种正则化目标仍可使用标准随机梯度下降进行优化。

```
$\alpha[\omega] = \sigma(\lambda \cdot \varnothing(\omega))$ (12.10)
```

其中 `λ` 是一个超参数，用于决定重要性函数 `⌀(⋅)` 的缩放因子。定义词 `ω` 的归一化频率如下：

```
$\mathcal{F}_{\mathcal{D}}\left( \omega \right) = \frac{f_{\mathcal{D}}\left( \omega \right)}{\max\limits_{\omega'\epsilon\mathcal{D}_{k}}f_{\mathcal{D}}\left( \omega' \right)}$ (12.11)
```

函数 `⌀(⋅)` 基于以下度量，该度量由著名的 Sørensen-Dice 系数激发，计算公式为：

```
$\varnothing\left( \omega \right) = \frac{2 \cdot \mathcal{F}_{\mathcal{D}_{s}}\left( \omega \right) \cdot \mathcal{F}_{\mathcal{D}_{t}}\left( \omega \right)}{\mathcal{F}_{\mathcal{D}_{s}}\left( \omega \right) + \mathcal{F}_{\mathcal{D}_{t}}\left( \omega \right)}$ (12.12)
```

注意，只有当 `ℱ[𝒟[s]](ω)` 和 `ℱ[𝒟[t]](ω)` 都很高时，`φ(w)` 的值才会很高。

### 12.2.3 NLP-机器阅读

长短期记忆结构由记忆网络包含，而不是单一的记忆查找。所呈现的机器阅读基于一个模拟器，该模拟器用于测试从左到右（L-to-R）并通过记忆和注意力执行浅层推理（Li et al. 2016a）。所提出的方法允许通过神经网络在循环过程中自适应地使用单元。他们贡献了一条每周诱导令牌间关系的途径。它用于单一序列，但也通过编码-解码框架累积（见图 [12.5](#ch20.xhtml#f106)）。大量研究显示了所提出方法的效率。

**使用 LSTMN 对两个序列建模**，将专注于内部关系推理的 LSTMN 与编码器-解码器网络相结合，后者的注意力模块学习两个序列之间的交互对齐。

![图 12.5 编码器利用内部注意力，解码器利用内部以及交互注意力方案。上述结构演示了在解码器中融合内部和交互注意力的两种方法（Li et al. 2016a）。](html/images/9780367720919_C012_005.jpg)

图 12.5 编码器利用内部注意力，解码器利用内部以及交互注意力方案。上述结构演示了在解码器中融合内部和交互注意力的两种方法（[Li et al. 2016a](#ch20.xhtml#r465)）。

该图展示了两种组合方式。

> **浅层注意力融合**，浅层组合基本上将 LSTMN 作为一个独立部分处理，而不是标准的 RNN 或 LSTM，该部分可以简单地用于编码器和解码器设计中。

