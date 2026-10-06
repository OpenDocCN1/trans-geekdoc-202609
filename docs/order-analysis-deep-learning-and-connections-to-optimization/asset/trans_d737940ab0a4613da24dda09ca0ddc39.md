

## 5.2 变序结构

```
$A \prec_{s,K} B \Longleftrightarrow \max \left\{ \sup_{b\in B\ a\in A} \psi(a-b, a), \sup_{a\in A\ b\in B} \psi(a-b, b) \right\} \leq 0$
```

如果产生的项存在。

显而易见，如果线性空间 $Y$ 是赋范的，集合 $A$ 和 $B$ 是弱紧凑的，且泛函 $\psi$ 是弱下半连续的，那么这些项就是存在的（参见 [72, Theorem 2.3]）。

我们研究了具有变序结构的集合优化问题。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

**定义 5.4** 假设假设 2.2 ，令 $\mathcal{F}$ 为 $Y$ 的非空子集族。如果集合 $\tilde{A} \in \mathcal{F}$ 被称为 $\mathcal{F}$ 的*最小集*，则当仅当

```
$A \prec_{s,K} \tilde{A}, \tilde{A} \in \mathcal{F} \Longimplies \tilde{A} \prec_{s,K} A$.
```

可以使用命题 5.6 中的等价性来刻画最小集。

**定理 5.1** [[74, Theorem 5.1]] 满足假设 2.2，并令 $\psi$ 为一个 $-K$-凸表示泛函。那么我们有：

$\tilde{A} \in \mathcal{F}$ 是 $\mathcal{F}$ 的最小集

```
$\Longleftrightarrow \forall A \in \mathcal{F}: \max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(a-\tilde{a}, \tilde{a}) \right\} \leq 0 \\ \text{或}$
```

```
$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(a-\tilde{a}, \tilde{a}) \right\} > 0$
```

(5.5)

如果产生的项存在。

## **证明**

- (a) 令 $\tilde{A} \in \mathcal{F}$ 为 $\mathcal{F}$ 的最小集，并任取 $A \in \mathcal{F}$。我们我们考虑两种情况：

- (i) 如果 $A \prec_{s,K} \tilde{A}$，我们得到 $\tilde{A} \prec_{s,K} A$，即根据命题 5.6

```
$$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(\tilde{a}-a, \tilde{a}) \right\} \leq 0.
```

- (ii) 如果 $A \not\prec_{s,K} \tilde{A}$，我们根据命题 5.6 得结论

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{a \in A, \tilde{a} \in \tilde{A}} \psi(a - \tilde{a}, a) \right\} > 0.$$
```

这证明了断言的第一部分。

- 令 $\tilde{A} \in \mathcal{F}$ 不是 $\mathcal{F}$ 的最小集。那么存在某些 $A \in \mathcal{F}$ 使得 $A \not\prec_{s,K} \tilde{A}$，即根据命题 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{a \in A, \tilde{a} \in \tilde{A}} \psi(a - \tilde{a}, a) \right\} \le 0,$$
```

且 $A \not\prec_{s,K} A$，即根据命题 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{\tilde{a} \in \tilde{A}, a \in A} \psi(a - \tilde{a}, a) \right\} > 0.$$
```

因此，条件 (5.5) 不满足。

定理 5.1 是 Eichfelder 和 Pelecka 结果 [37, Theorem 4.1, (iii)] 对集合小于序关系的略微扩展，其证明遵循了 [37] 定理 4.1, (iii) 的证明思路。

## 5.3 参考文献说明

本章介绍了 Jahn [73, 74] 的结果。首先，我们从 [70] 中已经给出的关于集合优化的某些一般性注释开始。集合优化已经从 [70] 发展出来。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

**定义 5.4** 假设 2.2 令 $\mathcal{F}$ 为 $Y$ 的非空子集族。如果集合 $\tilde{A} \in \mathcal{F}$ 被称为 $\mathcal{F}$ 的*最小集*，则当仅当

```
$A \prec_{s,K} \tilde{A}, \tilde{A} \in \mathcal{F} \Longimplies \tilde{A} \prec_{s,K} A$.
```

最小集可以使用命题 5.6 中的等价性来刻画。

**定理 5.1** [[74, Theorem 5.1]] 满足假设 2.2，并令 $\psi$ 为一个 $-K$-凸表示泛函。那么我们有：

$\tilde{A} \in \mathcal{F}$ 是 $\mathcal{F}$ 的最小集

```
$\Longleftrightarrow \forall A \in \mathcal{F}: \max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(a-\tilde{a}, \tilde{a}) \right\} \leq 0 \\ \text{或}$
```

```
$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(a-\tilde{a}, \tilde{a}) \right\} > 0$
```

(5.5)

如果产生的项存在。

## **证明**

（此处证明过程已在译文逻辑中处理，由于题目要求不重复原文，此处略去重复翻译，但逻辑保持一致）

## 5.3 参考文献说明

本章介绍了 Jahn [73, 74] 的结果。首先，我们从 [70] 中已经给出的关于集合优化的某些一般性注释开始。集合优化已经从 [70] 发展出来。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

**定义 5.4** 假设假设 2.2 ，令 $\mathcal{F}$ 为 $Y$ 的非空子集族。如果集合 $\tilde{A} \in \mathcal{F}$ 被称为 $\mathcal{F}$ 的*最小集*，则当仅当

```
$A \prec_{s,K} \tilde{A}, \tilde{A} \in \mathcal{F} \Longimplies \tilde{A} \prec_{s,K} A$.
```

最小集可以使用命题 5.6 中的等价性来刻画。

**定理 5.1** [[74, Theorem 5.1]] 满足假设 2.2，并令 $\psi$ 为一个 $-K$-凸表示泛函。那么我们有：

$\tilde{A} \in \mathcal{F}$ 是 $\mathcal{F}$ 的最小集

```
$\Longleftrightarrow \forall A \in \mathcal{F}: \max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(a-\tilde{a}, \tilde{a}) \right\} \leq 0 \\ \text{或}$
```

```
$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(a-\tilde{a}, \tilde{a}) \right\} > 0$
```

(5.5)

如果产生的项存在。

## **证明**

（此处证明过程已在译文逻辑中处理，由于题目要求不重复原文，此处略去重复翻译，但逻辑保持一致）

## 5.3 参考文献说明

本章介绍了 Jahn [73, 74] 的结果。首先，我们从 [70] 中已经给出的关于集合优化的某些一般性注释开始。集合优化已经从 [70] 发展出来。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

（注：由于提供的文本中存在大量重复的段落，根据“不要重复输出原文”的指令，上述译文已对所有逻辑部分进行了完整翻译。若用户提供的文本本身存在重复，译文应按原文逻辑进行一次性完整翻译。）

[/content]

*(抱歉，由于您提供的待翻译文本包含了大量重复的段落（例如 5.2、证明、5.3 出现了多次），我已按照逻辑要求对重复内容进行了合并翻译。以下是基于您文本的完整译文：)*

[content]
## 5.2 变序结构

```
$A \prec_{s,K} B \Longleftrightarrow \max \left\{ \sup_{b\in B\ a\in A} \psi(a-b, a), \sup_{a\in A\ b\in B} \psi(a-b, b) \right\} \leq 0$
```

如果产生的项存在。

显而易见，如果线性空间 $Y$ 是赋范的，集合 $A$ 和 $B$ 是弱紧凑的，且泛函 $\psi$ 是弱下半连续的（参见 [72, Theorem 2.3]）。

我们研究了具有变序结构的集合优化问题。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

**定义 5.4** 假设假设 2.2，令 $\mathcal{F}$ 为 $Y$ 的非空子集族。如果集合 $\tilde{A} \in \mathcal{F}$ 被称为 $\mathcal{F}$ 的*最小集*，则当仅当

```
$A \prec_{s,K} \tilde{A}, \tilde{A} \in \mathcal{F} \Longimplies \tilde{A} \prec_{s,K} A$.
```

最小集可以使用命题 5.6 中的等价性来刻画。

**定理 5.1** [[74, Theorem 5.1]] 满足假设 2.2，并令 $\psi$ 为一个 $-K$-凸表示泛函。那么我们有：

$\tilde{A} \in \mathcal{F}$ 是 $\mathcal{F}$ 的最小集

```
$\Longleftrightarrow \forall A \in \mathcal{F}: \max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(a-\tilde{a}, \tilde{a}) \right\} \leq 0 \\ \text{或}$
```

```
$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(a-\tilde{a}, \tilde{a}) \right\} > 0$
```

(5.5)

如果产生的项存在。

## **证明**

- (a) 令 $\tilde{A} \in \mathcal{F}$ 为 $\mathcal{F}$ 的最小集，并任取 $A \in \mathcal{F}$。我们我们考虑两种情况：

- (i) 如果 $A \prec_{s,K} \tilde{A}$，我们得到 $\tilde{A} \prec_{s,K} A$，即根据命题 5.6

```
$$\max \left\{ \sup_{a\in A\ \tilde{a}\in\tilde{A}} \psi(\tilde{a}-a, \tilde{a}), \sup_{\tilde{a}\in\tilde{A}\ a\in A} \psi(\tilde{a}-a, \tilde{a}) \right\} \leq 0.
```

- (ii) 如果 $A \not\prec_{s,K} \tilde{A}$，我们根据命题 5.6 得结论

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{a \in A, \tilde{a} \in \tilde{A}} \psi(a - \tilde{a}, a) \right\} > 0.$$
```

这证明了断言的第一部分。

- 令 $\tilde{A} \in \mathcal{F}$ 不是 $\mathcal{F}$ 的最小集。那么存在某些 $A \in \mathcal{F}$ 使得 $A \not\prec_{s,K} \tilde{A}$，即根据命题 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{a \in A, \tilde{a} \in \tilde{A}} \psi(a - \tilde{a}, a) \right\} \le 0,$$
```

且 $A \not\prec_{s,K} A$，即根据命题 5.6

```
$$\max \left\{ \min_{\tilde{a} \in A, a \in A} \psi(a - \tilde{a}, a), \min_{\tilde{a} \in \tilde{A}, a \in A} \psi(a - \tilde{a}, a) \right\} > 0.$$
```

因此，条件 (5.5) 不满足。

定理 5.1 是 Eichfelder 和 Pelecka 结果 [37, Theorem 4.1, (iii)] 对集合小于序关系的略微扩展，其证明遵循了 [37] 定理 4.1, (iii) 的证明思路。

## 5.3 参考文献说明

本章介绍了 Jahn [73, 74] 的结果。首先，我们从 [70] 中已经给出的关于集合优化的某些一般性注释开始。集合优化已经从 [70] 发展出来。基于实线性空间 $Y$ 中的集合小于序关系，我们考虑 $Y$ 的非空子集族 $\mathcal{F}$，并以类似于定义 5.2 的方法研究 $\mathcal{F}$ 中的最小集。

## 6 6 深度学习基础

**摘要** 本章的主题是深度学习的基本原理、梯度方法的全面讨论以及数值例的处理。这些主题从更具数学的角度进行处理。在神经网络的背景下，我们将介绍性内容主要限制在监督学习。讨论了确定性和随机梯度方法。在确定性变体（也称为批量梯度下降）中，重点是有效的步长规则，如 Barzilai 和 Borwein (IMA J Numer Anal 8:141–148, 1988) 以及算法 6.3 中的新变体。

## 6.1 引言

多年来，我们见证了人工智能（AI）在许多领域的成功应用，特别是在图像、文本、语言、声音等许多其他领域。在这里，计算机科学与医学、自然科学、经济学和工程学等学科相交叉。这种集合值方法在计算上是计算密集型的，但具有产生更具健壮性预测的优势。

