

# 6.3 用于音频信号处理和分类的算法时间线

音频信号处理和分类的研究已开展很长时间，始于二十世纪初。语音识别（SR）是其他音频处理技术中主要关注的领域。环境声音分类和音乐处理是近年来才引起关注的。花费了多年研究才达到用于音频分类的神经网络方法，该方法优于当时所有其他已知技术。在此之前，HMM 和其他概率模型既用于分类也用于生成。本节将详细阐述这些模型及其局限性。

## 6.3.1 隐马尔可夫模型

HMM 是用于序列的随机模型。HMM 的主要功能包括词性（POS）标注、SR 和命名实体标注等。HMM 源自马尔可夫链模型（MCM），后者由一组状态 `Q` = {`q`[0,]`q`[1],`q`[2], …, `q[N]`}、一个转移矩阵 `A`（如 eq. (6.9) 所示）以及一个起始状态（`q[0]`）和一个最终状态（`q[N]`）组成。

(6.9)$A = \\ \\begin{bmatrix} a\_{11} & \\ldots & a\_{1N} \\\\ \\vdots & \\ddots & \\vdots \\\\ a\_{N1} & \\cdots & a\_{NN} \\\\ \\end{bmatrix}$

在上述方程中，`a[ij,]`, 即第 `i^(th)` 行和第 `j^(th)` 列的元素，表示从状态 `i` 到状态 `j` 的转移概率。从一个状态到所有其他状态的概率之和为 1，因此矩阵中每一行的和为 1。MCM 的主要特性是，处于某个特定状态的概率仅取决于前一个状态；如 eq. (6.10) 所示。

(6.10)*P*\[`X`[`t` + 1] = `x`[`t` + 1]|`X`[`t*] = `x`[`t*], `X`[`t` − 1] = `x`[`t` − 1], …, `X`[0] = `x`[0]\] = *P*\[`X`[`t` + 1] = `x`[`t` + 1]|`X`[`t*] = `x`[`t*]\]

当模型中的所有状态对我们完全可见，并且需要计算一系列事件的概率时，MCM 很有用。[Figure 6.5](#bodymatter-006.xhtml#b_9783110670905-006_fig_005) 显示了一个简单的马尔可夫模型。

![Figure 6.5: A five state Markov model with state transition probabilities.](graphic/converted/b_9783110670905-006_fig_005.png)

Figure 6.5: A five state Markov model with state transition probabilities.

但是有许多事件对我们来说并不完全可见，例如，如果我们要从门窗紧闭的房间里预测外面的天气，或者我们要预测从一个装有多种颜色球的球罐中抽出的球的颜色。为了能够预测这些事件，引入了 HMM。HMM 中有 `N` 个隐藏状态 – {`S`[1],`S`[2], …, `S[N]`}，在大多数情况下，每个状态都可以从其他状态到达。时刻 `t` 的状态由 `q[t]` 表示。每个状态包含 `M` 个观测值 – {`v`[1],`v`[2], …, `v[M]`}。状态转移矩阵由 eq. (6.9) 表示，对 MCM 和 HMM 都通用。除此之外，HMM 还有一个观测符号概率分布 `B` = {`b[y]`(x)}，它表示在状态 `q[y]` 中观测值 `v[x]` 的可能性，其中 1 ≤ x ≤ `M` 且 1 ≤ `y` ≤ `N`，如 eq. (6.11) 所示。

(6.11)*b*[`y`](`x`) = *P*\[`v`[`x*] *a**t* *t*|`q`[`t*]\=`S`[`y*]\]

最后，它由初始状态概率组成，表示在时刻 `t` = 1（即起点）处于某个特定状态的可能性。这由 `π` 表示，并通过 eq. (6.12) 解释。

(6.12) `π`[`i*] = *P*\[`q`[1]\=`S`[`i*]\] ; *w**h**e**r**e* 1 ≤ `i*` ≤ `N*`

包含 `N`、`M`、`A`、`B` 和 `π` 的整个模型由 `λ` 表示，并如 [Figure 6.6](#bodymatter-006.xhtml#b_9783110670905-006_fig_006) 所示。它用于解释或说明任何一组观测序列，例如，给定 `λ`，HMM 可用于计算从明天开始连续三天下雨的概率。HMM 解决三个主要问题：

### Problem 1:

计算在给定 `λ` 的情况下，持续时间 `T` 内观测序列 `O` = {`O`[1],`O`[2], …, O`[T]`} 的概率。解决此问题且计算量最少的最高效解决方案由 `forward–backward algorithm` \[[29](#bodymatter-006.xhtml#b_9783110670905-006_ref_029), [30](#bodymatter-006.xhtml#b_9783110670905-006_ref_030)\] 给出。

### Problem 2:

在给定模型 `λ` 的情况下，选择一个状态序列 `Q` = {`q`[1],`q`[2], …, `q[T]`}，以最好地解释观测序列 `O`。Viterbi 算法最好地解决了此问题 \[[31](#bodymatter-006.xhtml#b_9783110670905-006_ref_031), [32](#bodymatter-006.xhtml#b_9783110670905-006_ref_032)\]。

### Problem 3:

调整模型参数以最大化给定观测的概率，即 `P(O|λ)`。此问题由 Baum–Welch 方法 \[[33](#bodymatter-006.xhtml#b_9783110670905-006_ref_033)\] 或梯度技术 \[[34](#bodymatter-006.xhtml#b_9783110670905-006_ref_034)\] 解决。

![Figure 6.6: An hidden Markov model with hidden states depicted in `X` and visible states depicted in `Y`. The hidden state probabilities are given in `a` and probability of a visible state from a hidden state is given in `b`.](graphic/converted/b_9783110670905-006_fig_006.png)

Figure 6.6: An hidden Markov model with hidden states depicted in `X` and visible states depicted in `Y`. The hidden state probabilities are given in `a` and probability of a visible state from a hidden state is given in `b`.

