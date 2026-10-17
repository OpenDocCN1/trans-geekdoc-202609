
我们讨论了两种基于代理的方法，即 Proxy-NCA 和 Proxy Anchor。尽管它们存在差异，但这两种方法的一个关键共同点是每个类使用一个全局代理作为表示原型。在度量学习（DML）中，我们希望将属于同一类但可能在视觉上差异很大的样本特征匹配，同时区分属于不同类但视觉上非常相似的样本特征。基于此，单一全局代理作为该类所有样本的表示可能并不是最优的代理优化方法。基于此，基于代理的深度图度量学习（ProxyGML）(Zhu et al., 2020)通过引入每个类的多个可训练子代理来克服这一问题，这些子代理能更好地表示局部类内部变异（Fig. 8）。

![Fig. 8 Illustration of ProxyGML loss (Zhu et al., 2020): Small stars represent the subproxies. Unlike Proxy-NCA (Movshovitz-Attias et al., 2017) and Proxy Anchor (Kim et al., 2020), ProxyGML (Zhu et al., 2020) uses multiple proxies per class. Proxies interact with samples and also among themselves in the final loss formulation. Proxies belonging to the same class come closer to one another and the samples belonging to that class, and move away from proxies and samples of other classes.](img/f04-08-9780443184307.jpg)

Fig. 8 Illustration of ProxyGML loss (Zhu et al., 2020): Small stars represent the subproxies. Unlike Proxy-NCA (Movshovitz-Attias et al., 2017) and Proxy Anchor (Kim et al., 2020), ProxyGML (Zhu et al., 2020) uses multiple proxies per class. Proxies interact with samples and also among themselves in the final loss formulation. Proxies belonging to the same class come closer to one another and the samples belonging to that class, and move away from proxies and samples of other classes.

设数据集 `D` 包含 `C` 个类别。ProxyGML 为每个类别分配 `M > 1` 个可训练子代理。因此，嵌入空间中的子代理总数为 `M × C`。ProxyGML 以图形方式建模样本与代理之间的全局和局部关系。这里，有向相似性图表示批量中所有代理与样本之间的全局相似性。

对于样本 `f[i]` 和代理 `P[j]`，全局相似性矩阵中的余弦相似性可定义为：

$$
\begin{array}{r} {S_{ij}^{p} = f_{i} \cdot P_{j}} \\ \end{array}
$$

(21)

因此，全局相似性矩阵 `S^p` 的维度为 `(M × C) × B`，其中 `M × C` 是代理的总数，`B` 是小批量中的样本总数。

对于属于样本 `f[i]` 的第 `i` 行 `S^p`，ProxyGML 选择 `K` 个最相似的代理，其中 `K` 是一个超参数。选择 `K` 个最相似的代理时，明确选择属于正类 `P^+` 的代理。其余 `K − M` 个代理则根据其与 `f[i]` 的相似性选择。这导致一个新的子相似性矩阵（记为 `S'`），维度为 `B × K`。

对 `S'` 进行子代理聚合，通过求和属于同一类别 `C` 的所有代理的余弦相似性，并对每个样本进行操作。注意，如果对于样本 `f[i]`，在 `S'` 中不存在属于某类别 `c` 的代理，则该类别的相似性被设置为零。这种子代理聚合策略产生最终相似性矩阵 `S`，维度为 `B × C`。

对于较小的 `K` 值，相似性矩阵 `S` 可能非常稀疏，包含许多零条目，导致传统 softmax 操作的分母膨胀。基于此，使用屏蔽 softmax 操作：

$$
\begin{array}{r} {P_{ij} = \frac{M_{ij}e^{S_{ij}}}{\sum M_{ij}e^{S_{ij}}}} \\ \end{array}
$$

(22)

其中 `M` 表示由 `M[ij] = 0 if S[ij] = 0 and M[ij] = 1 if S[ij] ≠ 0` 计算的零面具。`P[ij]` 表示样本 `i` 对类别 `j` 的 softmax 概率。

最后，交叉熵损失通过 `P[ij]` 计算为：

$$
\begin{array}{r} {\mathcal{L}_{\text{CE}} = \frac{1}{B}\sum\limits_{i = 0}^{B}\sum\limits_{j = 0}^{C}y_{i} \cdot log(P_{ij})} \\ \end{array}
$$

(23)

其中 `y[i]` 表示第 `i` 个样本的真实标签。由于每个类别包含多个子代理，这些子代理充当类中心，因此对同类子代理之间的相似性施加了第三个硬约束。设 `SP` 为给定的 `M × C` 个子代理之间的相似性：

$$
\begin{array}{r} {SP_{ij} = P_{i} \cdot P_{j}} \\ \end{array}
$$

(24)

通过 Eq. (24) 采用 proxy-to-proxy 正则化约束，计算 `SP` 的软最大概率，并将其转换为交叉熵损失：

$$
\begin{aligned} {PP_{ij}} & {= \frac{e^{SP_{ij}}}{\sum e^{SP_{ij}}}} \\ \end{aligned}
$$

(25)

$$
\begin{aligned} \mathcal{L}_{\text{reg}} & {= \frac{1}{M \times C}\sum\limits_{i = 0}^{M \times C}\sum\limits_{j = 0}^{C}y_{i}^{p} \cdot log(PP_{ij})} \\ \end{aligned}
$$

(26)

其中 `PP` 表示 proxy-to-proxy 相似性的软最大概率，`y^p` 表示 proxy 到类标签的真实映射。

最终损失计算如下：

$$
\begin{array}{r} {\mathcal{L} = \mathcal{L}_{\text{CE}} + \lambda \cdot \mathcal{L}_{\text{reg}}} \\ \end{array}
$$

(27)

在此，`λ` 表示正则化项的权重。该方法表明，通过最小化最终目标 `ℒ` 的端到端训练，可获得更具辨识度的嵌入空间。

## 5: 正则化

在前面的章节中，我们探讨了基于样本-样本和样本-代理相似性的损失形式，用于创建增强的特征表示。大多数方法主要关注样本-样本或样本-代理之间的交互。是否可以利用其他信息来构建更稳健的嵌入空间？本节将研究两种信息来源——语言和方向——并说明它们如何集成到现有的 DML 公式中。

### 5.1: 语言引导

大语言模型（LLMs）如 BERT (Devlin et al., 2018)、RoBERTa (Liu et al., 2019) 等在自然语言建模和内容表示方面取得了显著成功。它们通常在海量数据上预训练，能够编码语义上下文并正确建模语义关系。相反，仅使用前一节所述的 DML 目标在数据集 `X = {(x[1], y[1]), (x[2], y[2])…(x[m], y[m])}`（图片-标签对）上训练可能无法捕获所有数据点的语义上下文。那么，如何利用 LLMs 的语义上下文来改进 DML 目标？

Roth et al. (2022) 提出一种方法，将 LLMs 的表示知识纳入 DML 目标。已知 `X = {(x[1], y[1]), (x[2], y[2])…(x[m], y[m])}` 表示图片-标签集合。遵循 Multi-Similarity 损失的讨论，使用数据样本的特征表示计算相似性矩阵 `S[I]`，公式如 Eq. (10) 所示。为了加入语言正则化因子，从类标签生成提示。每个批次中的类标签 `y[i]` 用于创建提示 `T[i]`，即 “A photo of 〈`y[i]`〉”。设批次对应的提示集合为 `T`，即 `T = {T[1], T[2]…T[C]}`，其中 `C` 为批次大小。这些提示通过大语言模型 `Ω` 进行处理，得到低维表示：

$$
\begin{array}{r} {f_{i}^{lang} = \Omega(T_{i};\theta_{\omega});\forall i \in m} \\ \end{array}
$$

(28)

`Ω` 为预训练语言模型（如 BERT、RoBERTa 等）。获取语言表示 `f_i^lang` 后，可像构建 `S[I]` 一样，使用 Eq. (10) 构建相似性矩阵 `S[L]`。

给定两个相似性矩阵 `S[I]` 和 `S[L]`，提出了一种蒸馏损失，用于将语言模态的知识转移到视觉模态：

$$
\begin{array}{r} {L_{Lang} = \frac{1}{C}\sum\limits_{i = 1}^{C}\left\{ {\sigma(S_{I}^{i})\;\text{log}\left\lbrack \frac{\sigma(S_{I}^{i})}{\sigma(S_{L}^{i} + \gamma_{L})} \right\rbrack} \right\}} \\ \end{array}
$$

(29)

其中 `σ(S[I]^i)` 和 `σ(S[L]^i)` 分别表示对 `S[I]` 和 `S[L]` 每行的 softmax。`γ[L]` 为语言常数，设为 1。该蒸馏损失本质上是对每行 softmax 后的 KL 差异的求和。

最终损失公式为先前的对样本 DML 损失 `L[DML]` 与语言正则化损失 `L[Lang]` 的组合：

$$
\begin{array}{r} {L = L_{DML} + \omega L_{Lang}} \\ \end{array}
$$

(30)

其中 `ω` 是超参数，控制语言正则化项对最终目标的影响。

### 5.2: 方向正则化

迄今为止，DML 方法主要依赖精心设计的采样策略和损失函数，以优化可分辨的嵌入空间。虽然在采样和损失设计方面已有大量工作，但对样本对之间的相对交互以及在嵌入空间中这些对所受力的方向性关注相对较少。为了理解最优位移的需求，我们回顾三元组损失及其方向。可以注意到，负样本在每次更新时在径向方向被推离锚样本。虽然从直观上看，将负样本径向推离锚样本是合理的，但由于存在其他正样本，这种方向可能不是最优的。还需注意，三元组中的正样本并不对负样本的力方向产生影响。是否存在更优的力方向？

在 Fig. 3 中，我们可以看到每个样本上梯度力的方向。此情况下，我们希望负样本的移动方向与 `a` 和 `p` 的类中心之间的正交方向，即近似为 `f_c = \frac{f_a + f_p}{2}`（如 Fig. 9 所示）。数学上，需要强制满足以下约束：

$$
\begin{array}{r} \left. NC\;\bot\; PA\mspace{500mu}\Longrightarrow\mspace{500mu}\frac{NC}{\parallel NC \parallel} \cdot \frac{PA}{\parallel PA \parallel} = 0 \right. \\ \end{array}
$$

(31)

![Fig. 9 Geometric illustration of the layout of the anchor, positive, and negative samples. The lines OA, OP, and ON represent the unit-normalized embedding vectors for the anchor (`f_a`), positive (`f_p`), and negative (`f_n`), respectively. C is the midpoint of PA and OC represents the average embedding vector `f_c` (not unit-normalized).](img/f04-09-9780443184307.jpg)

Fig. 9 Geometric illustration of the layout of the anchor, positive, and negative samples. The lines OA, OP, and ON represent the unit-normalized embedding vectors for the anchor (`f_a`), positive (`f_p`), and negative (`f_n`), respectively. C is the midpoint of PA and OC represents the average embedding vector `f_c` (not unit-normalized).

Analyzing this in more detail, it turns out that incorporating the cosine similarity between the vectors Anchor-Positive and Anchor-Negative helps achieve this objective. (We are skipping the proof for brevity, please refer to Mohan et al. (2020) for more details.) This can be written as

$$
\begin{array}{r} {Cos(AN,AP) = \frac{1 - \mathbf{f}_{p} \cdot \mathbf{f}_{a}}{\parallel \mathbf{f}_{n} - \mathbf{f}_{a} \parallel \parallel \mathbf{f}_{p} - \mathbf{f}_{a} \parallel}} \\ \end{array}
$$

(32)

We find that minimizing this cosine similarity term helps to satisfy the condition in Eq. (31). Since the current metric learning losses lack explicit enforcement of the orthogonality of the negative sample with respect to the anchor-positive pair, when incorporated as a regularization term, it helps create a much more robust embedding space. The following equations provide definitions and the intuition on how easily this regularization term can be adapted into any standard metric learning loss function. The modified triplet loss can be written as:
