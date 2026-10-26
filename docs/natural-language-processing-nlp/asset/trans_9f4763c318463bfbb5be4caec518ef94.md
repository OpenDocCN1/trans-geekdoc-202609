

![](img/ba66a8f6f22adeb28512d560b999a231_155_0.png)

图 6.2：长短期记忆（LSTM）架构。门以带虚线的方框显示。在 LSTM 语言模型中，每个 $\boldsymbol{h}_m$ 会被用来预测下一个单词 $w_{m+1}$。

门是输入和前一隐藏状态的函数。它们由逐元素的 sigmoid 激活 $\sigma(x) = (1 + \exp(-x))^{-1}$ 计算得到，确保其值处于 $[0, 1]$ 范围内。因此，它们可以被视为软性、可微分的逻辑门。LSTM 架构如图 6.2 所示，完整的更新方程如下：

$\boldsymbol{f}_{m+1} = \sigma(\boldsymbol{\Theta}^{(h \to f)} \boldsymbol{h}_m + \boldsymbol{\Theta}^{(x \to f)} \boldsymbol{x}_{m+1} + \boldsymbol{b}_f)$    遗忘门    [6.35]
$\boldsymbol{i}_{m+1} = \sigma(\boldsymbol{\Theta}^{(h \to i)} \boldsymbol{h}_m + \boldsymbol{\Theta}^{(x \to i)} \boldsymbol{x}_{m+1} + \boldsymbol{b}_i)$    输入门    [6.36]
$\tilde{\boldsymbol{c}}_{m+1} = \tanh(\boldsymbol{\Theta}^{(h \to c)} \boldsymbol{h}_m + \boldsymbol{\Theta}^{(w \to c)} \boldsymbol{x}_{m+1})$    更新候选    [6.37]
$\boldsymbol{c}_{m+1} = \boldsymbol{f}_{m+1} \odot \boldsymbol{c}_m + \boldsymbol{i}_{m+1} \odot \tilde{\boldsymbol{c}}_{m+1}$    记忆单元更新    [6.38]
$\boldsymbol{o}_{m+1} = \sigma(\boldsymbol{\Theta}^{(h \to o)} \boldsymbol{h}_m + \boldsymbol{\Theta}^{(x \to o)} \boldsymbol{x}_{m+1} + \boldsymbol{b}_o)$    输出门    [6.39]
$\boldsymbol{h}_{m+1} = \boldsymbol{o}_{m+1} \odot \tanh(\boldsymbol{c}_{m+1})$    输出。    [6.40]

运算符 $\odot$ 是逐元素（Hadamard）乘积。每个门由一个权重向量控制，这些权重对前一隐藏状态（例如 $\boldsymbol{\Theta}^{(h \to f)}$）和当前输入（例如 $\boldsymbol{\Theta}^{(x \to f)}$）进行参数化，再加上一个向量偏置（例如 $\boldsymbol{b}_f$）。整体操作可以非正式地概括为 $(\boldsymbol{h}_m, \boldsymbol{c}_m) = \text{LSTM}(\boldsymbol{x}_m, (\boldsymbol{h}_{m-1}, \boldsymbol{c}_{m-1}))$，其中 $(\boldsymbol{h}_m, \boldsymbol{c}_m)$ 表示读取第 $m$ 个词元后的 LSTM 状态。

LSTM 在广泛的问题上优于标准循环神经网络。它最初由 Sundermeyer 等人（2012）用于语言建模，但可以更普遍地应用：向量 $\boldsymbol{h}_m$ 可以被视为一个完整表示
（2014）为语素引入向量表示，并将这些表示构建到对数双线性语言模型中；Bhatia 等人（2016）将语素向量融入 LSTM。

## 补充资源

多种神经网络架构已被应用于语言建模。较早值得注意的非循环架构包括神经概率语言模型（Bengio 等人，2003）和对数双线性语言模型（Mnih 和 Hinton，2007）。关于这些模型的更多细节可参见 Goodfellow 等人（2016）的教材。

## 练习

- 1. 证明：如果 n-gram 概率是有效的，则 n-gram 语言模型给出有效概率。具体来说，假设：

  $$\sum_{w_m}^{V} p(w_m \mid w_{m-1}, w_{m-2}, \dots, w_{m-n+1}) = 1 \tag{6.43}$$

  对所有上下文 $(w_{m-1}, w_{m-2}, \dots, w_{m-n+1})$ 成立。证明对所有 $w \in \mathcal{V}^*$，$\sum_w p_n(w) = 1$，其中 $p_n$ 是 n-gram 语言模型下的概率。你的证明应采用归纳法。你应该处理字符串起始情形 $p(w_1 \mid \underbrace{\square,\dots,\square}_{n-1})$，但无需处理字符串结束标记。

- 2. 首先，使用与上一题类似的证明技术，证明 RNN 语言模型是有效的。

  接下来，令 $p_r(w)$ 表示在 RNN $r$ 下 $w$ 的概率。一个 RNN 语言模型集成计算如下概率：

  $$p(w) = \frac{1}{R} \sum_{r=1}^{R} p_r(w). \tag{6.44}$$

  RNN 语言模型集成计算出的概率是否有效？

- 3. 考虑一个词表大小为 $V$ 的一元语言模型。假设一个单词在一个总共有 $M$ 个词元的语料库中出现了 $m$ 次。使用参数为 $\alpha$ 的 Lidstone 平滑时，对于哪些 $m$ 值，平滑概率大于未平滑概率？

- 4. 考虑一种简单语言，其中每个词元以概率 $\frac{1}{V}$ 从词表 $\mathcal{V}$ 中抽取，并且独立于所有其他词元。

## 7.3 Viterbi 算法

通过将评分函数分解为局部部分的求和，可以将标注问题重写如下：

$$\hat{\boldsymbol{y}} = \underset{\boldsymbol{y}\in\mathcal{Y}(\boldsymbol{w})}{\operatorname{argmax}}\,\Psi(\boldsymbol{w},\boldsymbol{y})\tag{7.13}$$ $$= \underset{\boldsymbol{y}_{1:M}}{\operatorname{argmax}}\,\sum_{m=1}^{M+1}\psi(\boldsymbol{w},y_m,y_{m-1},m)\tag{7.14}$$ $$= \underset{\boldsymbol{y}_{1:M}}{\operatorname{argmax}}\,\sum_{m=1}^{M+1}s_m(y_m,y_{m-1}),\tag{7.15}$$

其中最后一行使用简写简化了记号：

$$s_m(y_m,y_{m-1}) \triangleq \psi(\boldsymbol{w}_{1:M},y_m,y_{m-1},m).\tag{7.16}$$

这个推理问题可以使用**动态规划**高效求解，这是一种在递推计算中复用工作的算法技术。我们首先求解一个辅助问题：不求最佳标注序列，而是计算最佳标注序列的得分：

$$\max_{\boldsymbol{y}_{1:M}}\Psi(\boldsymbol{w},\boldsymbol{y}_{1:M}) = \max_{\boldsymbol{y}_{1:M}}\sum_{m=1}^{M+1}s_m(y_m,y_{m-1}).\tag{7.17}$$

该得分涉及对所有长度为 $M$ 的标注序列进行最大化，记作 $\max_{\boldsymbol{y}_{1:M}}$。这个最大化可以分解为两部分：

$$\max_{\boldsymbol{y}_{1:M}}\Psi(\boldsymbol{w},\boldsymbol{y}_{1:M}) = \max_{y_M}\max_{\boldsymbol{y}_{1:M-1}}\sum_{m=1}^{M+1}s_m(y_m,y_{m-1}).\tag{7.18}$$

在求和中，只有最后一项 $s_{M+1}(\blacklozenge,y_M)$ 依赖于 $y_M$，因此我们可以将这一项从第二个最大化中提出来：

$$\max_{\boldsymbol{y}_{1:M}}\Psi(\boldsymbol{w},\boldsymbol{y}_{1:M}) = \left(\max_{y_M}s_{M+1}(\blacklozenge,y_M)\right) + \left(\max_{\boldsymbol{y}_{1:M-1}}\sum_{m=1}^{M}s_m(y_m,y_{m-1})\right).\tag{7.19}$$

等式 7.19 中的第二项与我们的原始问题形式相同，只需将 $M$ 替换为 $M-1$。这表明该问题可以重新表述为一个递推关系。我们通过定义一个称为 Viterbi 变量 $v_m(k)$ 的辅助变量来实现这一点，表示
如何估计这些特征上的权重。§ 2.3 介绍了三类主要的判别式分类器：感知机、支持向量机和逻辑回归。这些分类器中的每一个都有对应的结构化版本，使其能够从带标签的序列而非单个词元进行训练。

### 7.5.1 结构化感知机

感知机分类器通过增加与正确标签相关联特征的权重，并减少与错误预测标签相关联特征的权重来训练：

$$\hat{y} = \arg\max_{y\in\mathcal{Y}} \theta \cdot f(x,y)$$  
[7.60]

$$\theta^{(t+1)} \leftarrow \theta^{(t)} + f(x,y) - f(x,\hat{y}).$$  
[7.61]

在结构预测的情况下，我们可以应用完全相同的更新：

$$\hat{y} = \arg\max_{y\in\mathcal{Y}(w)} \theta \cdot f(w,y)$$  
[7.62]

$$\theta^{(t+1)} \leftarrow \theta^{(t)} + f(w,y) - f(w,\hat{y}).$$  
[7.63]

这种学习算法被称为**结构化感知机**，因为它学习预测结构化输出 $y$。唯一的区别在于，不是通过枚举整个集合 $\mathcal{Y}$ 来计算 $\hat{y}$，而是使用 Viterbi 算法高效搜索可能的标注集合 $\mathcal{Y}^M$。只要能够进行高效推理，结构化感知机就可以应用于其他结构化输出。与感知机分类一样，权重平均对于获得良好性能至关重要（参见 § 2.3.2）。

**示例** 对于示例 *they can fish*，假设参考标注序列为 $y^{(i)} = \mathrm{N\ V\ V}$，但标注器错误地返回了标注序列 $\hat{y} = \mathrm{N\ V\ N}$。假设模型具有发射特征 $(w_m,y_m)$ 和转移特征 $(y_{m-1},y_m)$，则相应的结构化感知机更新为：

$$\theta_{(\mathrm{fish},\mathrm{V})} \leftarrow \theta_{(\mathrm{fish},\mathrm{V})}+1, \qquad \theta_{(\mathrm{fish},\mathrm{N})} \leftarrow \theta_{(\mathrm{fish},\mathrm{N})}-1$$  
[7.64]

$$\theta_{(\mathrm{V},\mathrm{V})} \leftarrow \theta_{(\mathrm{V},\mathrm{V})}+1, \qquad \theta_{(\mathrm{V},\mathrm{N})} \leftarrow \theta_{(\mathrm{V},\mathrm{N})}-1$$  
[7.65]

$$\theta_{(\mathrm{V},\blacklozenge)} \leftarrow \theta_{(\mathrm{V},\blacklozenge)}+1, \qquad \theta_{(\mathrm{N},\blacklozenge)} \leftarrow \theta_{(\mathrm{N},\blacklozenge)}-1$$  
[7.66]

### 7.5.2 结构化支持向量机

支持向量机等大间隔分类器通过将分类边界推离训练实例来改进感知机。同样的思想可以

