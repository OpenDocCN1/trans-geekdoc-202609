
where `f`[`i`] ∈ `R`^(`d`) is also referred to as the feature representation of the image `x`[`i`]. 通常，标准 CNN 被用作特征提取器 `ϕ`，它生成这些特征表示。特征提取器 `ϕ` 的整体目标是将每个图像 `x`[`i`] 投影到高度可分离的嵌入空间，其中属于同一类别的特征嵌入相互靠近，并与其他类别的特征嵌入很好地分开，即：

$\\begin{array}{r} {D(f\_{i},f\_{j}) < D(f\_{i},f\_{k});\\forall i,j \\in y\_{l};\\forall k \\notin y\_{l}} \\\\ \\end{array}$

![si3_e](images/S0169716123000032/si3_e.png)  (2)

其中 `D` 是嵌入空间中定义良好的距离度量。`y`[`l`] 表示与图像关联的类标签。例如，如果考虑的距离度量是欧氏距离，则公式 ([2](#Ch004_59-79_S0169716123000032.xhtml#fo0015)) 可以改写为：

$\\begin{array}{r} {{\\parallel \\mathbf{f}\_{i} - \\mathbf{f}\_{j} \\parallel}^{2} < {\\parallel \\mathbf{f}\_{i} - \\mathbf{f}\_{k} \\parallel}^{2};\\forall i,j \\in y\_{l};\\forall k \\notin y\_{l}} \\\\ \\end{array}$

![si4_e](images/S0169716123000032/si4_e.png)  (3)

最近，许多特征提取器将最终特征表示的范数限制为单位范数。将特征表示的范数限制为单位范数会使嵌入流形成为 n 维单位高球面（如下图所示）。当特征表示位于单位高球面上时，角度分离被用作衡量特征表示相似性和不同性的指标。给定两个特征表示 `f`[`i`] 和 `f`[`j`]，可以计算两个表示之间的余弦相似度，即：

$\\begin{array}{r} {S = \\frac{f\_{i}^{T}f\_{j}}{||f\_{i}||.||f\_{j}||},i,j \\in n} \\\\ \\end{array}$

![si5_e](images/S0169716123000032/si5_e.png)  (4)

由于特征表示的幅度为 1，点积的相似值提供了两个特征向量之间的角度分离。`S` 的取值范围在 -1 到 1 之间，其中 1 表示特征表示之间的 0 度角度分离，-1 表示 180 度的分离。对于大数据集 `X`，目标 [2](#Ch004_59-79_S0169716123000032.xhtml#fo0015) 通常在每个小批批 `B` 中强制执行。整个章节我们将假设使用小批批方式优化深度神经网络。

##  3: Pair-based formulation

本节我们将探讨基于信息对的采样方法以实现更好的优化。我们将讨论几种在计算机视觉相关应用中广泛使用的方法，如人脸识别 ([Sankaran et al., 2019](#Ch004_59-79_S0169716123000032.xhtml#bb0070))、指纹识别 [(Jawade et al., 2021](#Ch004_59-79_S0169716123000032.xhtml#bb0020), [2022)](#Ch004_59-79_S0169716123000032.xhtml#bb0025)、图像检索 ([Mohan et al., 2020](#Ch004_59-79_S0169716123000032.xhtml#bb0050))、人再识别 ([Lee et al., 2022](#Ch004_59-79_S0169716123000032.xhtml#bb0040)) 和跨模态检索 ([Jawade et al., 2023](#Ch004_59-79_S0169716123000032.xhtml#bb0030))。

###  3.1: Contrastive loss

如前面所述，标准度量学习损失公式的主要目标由公式 ([2](#Ch004_59-79_S0169716123000032.xhtml#fo0015)) 给出。实现这一点的一种方法是在训练深度神经网络时，在目标函数中强制执行相同的约束。给定两个特征表示，`f`[`i`] 和 `f`[`j`]，如果它们属于同一类，目标是减小两个表示之间的距离。如果样本属于不同类，则目标是增加特征表示之间的距离，这可以数学表达为：

$\\begin{matrix} {L\_{con} = \\begin{cases} {{\\parallel \\mathbf{f}\_{i} - \\mathbf{f}\_{j} \\parallel}^{2},\\quad} & {\\text{if}\\; y\_{i} = y\_{j}} \\\\ {{\\lbrack\\alpha - ({\\parallel \\mathbf{f}\_{i} - \\mathbf{f}\_{j} \\parallel}^{2})\\rbrack}\_{+},\\quad} & {\\text{else\\ if}\\; y\_{i} \\neq y\_{j}} \\\\ \\end{cases}} \\\\ \\end{matrix}$

![si6_e](images/S0169716123000032/si6_e.png)

其中 `y`[`i`] 和 `y`[`j`] 是 `f`[`i`] 和 `f`[`j`] 所对应的类别。`α` 这里是边界值。我们将在下一节详细讨论 `α`。

###  3.2: Triplet loss

Triplet Loss 是 [Schroff et al. (2015)](#Ch004_59-79_S0169716123000032.xhtml#bb0075) 提出的对比损失公式的改进，是创建可分离嵌入空间的广泛使用的度量学习目标函数。考虑三个特征表示 `f`[`a`]、 `f`[`p`] 和 `f`[`n`]，对应于数据集中的三张图像。让 `f`[`a`] 和 `f`[`p`] 是属于同一类别的两张图像的特征表示，我们称它们为 *Anchor* 和 *Positive* 样本。让 `f`[`n`] 属于不同类别的样本称为 *Negative* 样本（[Fig. 2](#Ch004_59-79_S0169716123000032.xhtml#f0015)）。Triplet loss 最小化 Anchor 和 Positive 之间的特征嵌入距离，同时最大化 Anchor 和 Negative 之间的距离。当使用欧氏距离时，三元组损失定义如下：

$\\begin{array}{r} {\\mathcal{L} = \\sum\\limits\_{a,p,n \\subset N}\\left\\lbrack {\\;{\\parallel \\mathbf{f}\_{a} - \\mathbf{f}\_{p} \\parallel}^{2} - {\\parallel \\mathbf{f}\_{a} - \\mathbf{f}\_{n} \\parallel}^{2} + \\alpha\\;} \\right\\rbrack\_{+}} \\\\ \\end{array}$

![si7_e](images/S0169716123000032/si7_e.png)  (5)

![Fig. 2 Illustration of Triplet Loss. The Positive sample is attracted toward the Anchor, whereas the Negative sample is repelled from the anchor. Here and in all diagrams in this chapter, we represent an anchor with-in a *brown circle*. *Red arrow* is used to represent repulsion and *green arrow* is used to represent attraction.](images/S0169716123000032/f04-02-9780443184307.jpg)

[Fig. 2](#Ch004_59-79_S0169716123000032.xhtml#B-f0015) Illustration of Triplet Loss. The Positive sample is attracted toward the Anchor, whereas the Negative sample is repelled from the anchor. Here and in all diagrams in this chapter, we represent an anchor with-in a *brown circle*. *Red arrow* is used to represent repulsion and *green arrow* is used to represent attraction.

术语 ***f***[`a`]、***f***[`p`]、***f***[`n`] 分别对应锚点、正样本和负样本的特征嵌入，其中 *a*、*p*、*n* 从训练数据集 *N* 中采样。`α` 定义了锚点-负样本距离与锚点-正样本距离之间的边界值。[.][+] 表示 *max*(., 0) 函数。

这种数学表达可以被视为对比损失公式的扩展，因为它明确强制 Anchor-Positive 相似性，同时驱逐 Negative。此外，还可以通过对损失 ([Eq. 5](#Ch004_59-79_S0169716123000032.xhtml#fo0035)) 关于这些特征表示的导数进行分析，从而获得吸引和排斥力作用方向的几何图像。为此，我们计算损失的导数如下：

$\\begin{matrix} \\frac{\\partial\\mathcal{L}}{\\partial\\mathbf{f}\_{a}} & {= 2(\\mathbf{f}\_{n} - \\mathbf{f}\_{p})} \\\\ \\frac{\\partial\\mathcal{L}}{\\partial\\mathbf{f}\_{p}} & {= 2(\\mathbf{f}\_{p} - \\mathbf{f}\_{a})} \\\\ \\frac{\\partial\\mathcal{L}}{\\partial\\mathbf{f}\_{n}} & {= 2(\\mathbf{f}\_{a} - \\mathbf{f}\_{n})} \\\\ \\end{matrix}$

![si8_e](images/S0169716123000032/si8_e.png)  (6)
