

$$q_{n}(\mathbf{x}_{1:n}) = q_{1}(\mathbf{x}_{1})\prod\limits_{k = 2}^{n}q_{k}(\mathbf{x}_{k}|\mathbf{x}_{1:k - 1}).$$

![Equation](images/B9780443292385000238/si61.png)(17.8)

这意味着只需选择 $q_{k}(\mathbf{x}_{k}|\mathbf{x}_{1:k - 1})$，$k = 2, 3, \dots, n$，以及初始（先验）$q_{1}(\mathbf{x}_{1})$。请注意，给定过去的情况下，$q_{k}(\cdot | \cdot)$ 中涉及的随机向量的维度在所有时间瞬间保持*固定*。从另一个角度来看，公式 [(17.8)](#Chp017_855-884_B9780443292385000238.xhtml#deq12) 揭示了：为了抽取一个跨越至时间 $n$ 的单个（多元）样本，即 $\mathbf{x}_{1:n}^{(i)} = \{\mathbf{x}_{1}^{(i)}, \mathbf{x}_{2}^{(i)}, \dots, \mathbf{x}_{n}^{(i)}\}$，我们是*递归地*构建它的；我们首先抽取 $\mathbf{x}_{1}^{(i)} \sim q_{1}(\mathbf{x})$，然后抽取 $\mathbf{x}_{k}^{(i)} \sim q_{k}(\mathbf{x}|\mathbf{x}_{1:k - 1}^{(i)})$，$k = 2, 3, \dots, n$。相应的未归一化权重也是递归计算的 [16]。确实，

