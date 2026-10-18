

$$\\begin{array}{l} \\begin{array}{ll} \\text{smooth} & {w\_{k + 1}^{s} = w\_{k}^{s} - \\eta\_{k}^{s}\\left\\lbrack {{\\sum\\limits\_{i = 1}^{n}\\tau\_{i}^{s,k}} + \\nabla g(w\_{k}^{s})} \\right\\rbrack,} \\\\ \\text{非光滑~} & {w\_{k + 1}^{s} = Prox\_{\\eta\_{k}^{s}}^{g}\\left( {w\_{k}^{s} - \\eta\_{k}^{s}{\\sum\\limits\_{i = 1}^{n}\\tau\_{i}^{s,k}}} \\right),} \\\\ \\end{array} \\\\ \\end{array}$$

(4.5)

where $\\tau\_{i}^{s,k} = \\left\\{ \\begin{array}{l} {\\frac{1}{b}\\nabla f\_{i}(w\_{k}^{s})\\quad\\text{如果}\\, i \\in B\_{k}} \\\\ {\\frac{1}{l}{\\widetilde{\\tau}}\_{i}^{s,k}\\quad\\text{否则}} \\\\ \\end{array}~ \\right.$ and ${\\widetilde{\\tau}}\_{i}^{s,k} = \\left\\{ \\begin{array}{l} {\\nabla f\_{i}(w\_{k}^{s})\\quad\\text{如果}\\, i \\in B\_{k}} \\\\ {{\\widetilde{\\tau}}\_{i}^{s - 1,k}\\quad\\text{否则}.} \\\\ \\end{array}~ \\right.$

SAAG-II:

$$\\begin{array}{l} \\begin{array}{ll} \\text{smooth} & {w\_{k + 1}^{s} = w\_{k}^{s} - \\eta\_{k}^{s}\\left\\lbrack {\\widetilde{\\nabla}f\_{B\_{k}}(w\_{k}^{s}) + \\nabla g(w\_{k}^{s})} \\right\\rbrack,} \\\\ \\text{非光滑~} & {w\_{k + 1}^{s} = Prox\_{\\eta\_{k}^{s}}^{g}\\left( {w\_{k}^{s} - \\eta\_{k}^{s}\\widetilde{\\nabla}f\_{B\_{k}}(w\_{k}^{s})} \\right),} \\\\ \\end{array} \\\\ \\end{array}$$

(4.6)

where $\\widetilde{\\nabla}f\_{B\_{k}}(w\_{k}^{s}) = 1/b{\\sum\\limits\_{i \\in B\_{k}}\\nabla}f\_{i}(w\_{k}^{s}) - 1/n{\\sum\\limits\_{i \\in B\_{k}}\\nabla}f\_{i}({\\widetilde{w}}^{s}) + {\\widetilde{\\mu}}^{s}$ and ${\\widetilde{\\mu}}^{s} = 1/n{\\sum\\limits\_{i = 1}^{n}\\nabla}f\_{i}({\\widetilde{w}}^{s})$. 与 SVRG 和 VRSGD 不同，与 SAG 和 SAGA 类似，SAAGs 是有偏梯度估计器，因为梯度估计器的期望不等于全梯度，即，$\\mathbb{E}\\lbrack\\widetilde{\\nabla}f\_{B\_{k}}(w\_{k}^{s})\\rbrack = \\nabla f(w\_{k}^{s}) + (m - 1)/m\\nabla f({\\widetilde{w}}^{s - 1})$，如 [Lemma 6](#06chap_04.xhtml#lemma_6) 中详细说明。

SAAG-I 算法，由 [Algorithm 10](#06chap_04.xhtml#algorithm_10) 表示，将数据集划分为 *m* 个大小相等（例如）的小批量 *b*，并以 *S*（时代数）作为输入。在每次内部迭代期间，它从 *\[n\]* 中随机选择一个小批量数据点，计算小批量上的梯度，更新总梯度值，并在 *B*[*k*] 上执行随机回溯-Armijo 线搜索（SBAS）。然后，对于光滑正则化器使用选项 I，对于非光滑正则化器使用选项 II 来更新参数。内部迭代运行 *m* 次，其中 *n* = *m**b*，然后最后一次迭代作为下一个时代的起始点。

![](Images/algo10.jpg)

SAAG-II 算法，由 [Algorithm 11](#06chap_04.xhtml#algorithm_11) 表示，以时代数（*S*）和大小相等（例如）的小批量数（*m*）作为输入。它初始化 *w*[0]¹ = *w̃*⁰。在每次内部迭代期间，它随机选择一个小批量 *B*[*k*]，计算最后一次迭代和快照点上 *B*[*k*] 的两个梯度，更新 $\\widetilde{\\nabla}f\_{B\_{k}}(w\_{k}^{s})$，并在 *B*[*k*] 上执行随机回溯-Armijo 线搜索（SBAS）。然后，对于光滑正则化器使用选项 I，对于非光滑正则化器使用选项 II 来更新参数。内部迭代之后，它使用最后一次迭代来设置快照点和下一个时代的起始点。

![](Images/algo11.jpg)

## 4.4  SAAG-III 和 IV 算法

SAAG-III 算法，由 [Algorithm 12](#06chap_04.xhtml#algorithm_12) 表示，将数据集划分为 *m* 个大小相等（例如）的小批量 *b*，并以 *S*（时代数）作为输入。在每次内部迭代期间，它从 *\[n\]* 中随机选择一个小批量数据点 *B*[*k*]，计算小批量上的梯度，更新总梯度值，并在 *B*[*k*] 上执行随机回溯-Armijo 线搜索（SBAS）。然后，对于光滑正则化器使用选项 I，对于非光滑正则化器使用选项 II 来更新参数。内部迭代运行 *m* 次，其中 *n* = *m**b*，然后计算迭代平均值并用作下一个时代的起始点，$w\_{0}^{s + 1} = 1/m{\\sum\\limits\_{i = 1}^{m}w\_{i}^{s}}$。

![](Images/algo12.jpg)

SAAG-IV 算法，由 [Algorithm 13](#06chap_04.xhtml#algorithm_13) 表示，以时代数（*S*）和大小相等（例如）的小批量数（*m*）作为输入。它初始化 *w*[0]¹ = *w̃*⁰。在每次内部迭代期间，它随机选择一个小批量 *B*[*k*]，计算最后一次迭代和快照点上 *B*[*k*] 的两个梯度，更新 $\\widetilde{\\nabla}f\_{B\_{k}}(w\_{k}^{s})$，并在 *B*[*k*] 上执行随机回溯-Armijo 线搜索（SBAS）。然后，对于光滑正则化器使用选项 I，对于非光滑正则化器使用选项 II 来更新参数。内部迭代之后，它计算平均值来设置快照点，并使用最后一次迭代作为新时代的起始点，分别为 ${\\widetilde{w}}^{s} = 1/m{\\sum\\limits\_{i = 1}^{m}w\_{i}^{s}}$ 和 *w*[0]^(*s* + 1) = *w*[*m*]^(*s*)。

![](Images/algo13.jpg)

## 4.5  分析

一般来说，SAAG-IV 对于大规模学习问题的效果优于 SAAG-III。因此，在本节中，我们提供了考虑所有光滑性和强凸性情况的 SAAG-IV 收敛率。此外，由于梯度估计器的有偏性质以及全梯度是增量维护而不是像 SAAG-IV 那样在固定点计算，SAAG-III 的分析代表了一个典型案例。因此，SAAG-III 的分析留待未来研究。所有不同光滑性和强凸性组合的收敛率如下所示。

本章中考虑了以下假设：

我们的证明灵感来源于 \[39\] 和 \[138\]。在提供证明之前，我们首先给出以下引理：

遵循非光滑问题的 [Lemma 2](#06chap_04.xhtml#lemma_2)，可以轻松证明光滑问题的以下结果，

此处给出的所有证明都证明了 SAAG-IV 在光滑性和强凸性的四种组合下的线性收敛（根据收敛定义），结果中包含一些由于常数项引起的初始误差。SAAGs 基于实践中的直觉 \[23\]，它们试图比旧梯度值更重视最新的梯度值，这使得它们成为有偏技术，并导致了这个额外的常数项。这个常数项表明 SAAGs 收敛到靠近解的区域，这非常实际，因为所有机器学习算法都用于近似求解问题，我们永远无法找到问题的精确解 \[[15](#bib.xhtml#refbib_15)]，因为计算上的困难。此外，这个常数项是由于最优点处的小批量梯度值引起的，即，$\\frac{1}{\\left| B\_{k} \\right|}{\\sum\\limits\_{i \\in B\_{k}}\\nabla}f\_{i}(w^{\*})$。如果小批量的大小增加并最终等于数据集大小，那么这个常数就等于全梯度并消失，即，$\\frac{1}{n}{\\sum\\limits\_{i = 1}^{n}\\nabla}f\_{i}(w^{\*}) = 0.$

正则化器的强凸性和光滑性的所有组合的线性收敛，是一阶方法在没有曲率信息的情况下表现出的最大收敛率。SAG、SVRG、SAGA 和 VR-SGD 也对强凸性和光滑问题表现出线性收敛，但除了 VR-SGD 之外，它们不涵盖所有情况，例如，SVRG 不涵盖非强凸情况。然而，VR-SGD 提供的理论结果证明了强凸情况下的线性收敛，类似于我们的结果，但 VR-SGD 对于非强凸情况仅提供 *O*(1/*T*) 收敛，而不像我们的线性收敛结果。

## 4.6  实验结果

在本节中，我们展示了实验结果[⁵](#fn5)

