
代数范畴的研究。从范畴论的观点出发，给出指称语义的一般定义，以从本质上理解指称语义。

除语义学外，范畴论还可应用于形式本体论的研究。例如，在文献[11]和[12]中，阐述了基于范畴论的本体论研究，并分别研究了形式化和集成两个方面。本文主要从范畴论层面分析集合论的局限性，以及这种局限性对基于集合论方法的影响。此外，讨论了基于范畴论的本体论方法，并通过示例系统说明了范畴论本体论的构造方法。本体论能够完整描述某些问题域。而且，范畴论中本体论的概念和关系非常直观，但范畴论很少被使用。范畴论的重用结构是对集合论中结构的归纳和抽象。范畴论是集合论的发展，其优势体现在数学理论中。此外，本文还讨论了范畴论本体论的必要性、普遍性和直观性，并建立了本体论的表示方法。

在文献[13]中，范畴论被应用于搜索算法，主要用于分支定界法和回溯算法的统一实现。分支定界法和回溯算法已广泛应用于搜索和优化问题中，但它们在各类问题中的执行能力不同。范畴论可用于构建这两种算法推导和生成的统一过程。首先，为每种搜索策略定义一个通用规格说明。然后，利用PAR平台的增量细化技术详细推导算法，抽象程序，并使程序能够泛化。最后，我们使用极限计算来生成解决特定问题的有效过程。该方法在不损失性能的情况下实现了高水平的抽象和机械化。

2000年，Michael J. Healy等人提出了将范畴论应用于神经系统模型和图表示[15]。他们使用剩余极限、函子和自然变换来模拟概念层级的执行。提出了神经系统构成的范畴概念。在文献[14]中，介绍了一种模拟机器人控制范畴论设计方法的应用。神经网络架构的使用给工程师带来了挑战。主要问题在于“学习”，但在有限的情境下，只能提取所需的知识。Healy和CaudeI对范畴论的应用证明，架构设计和性能这两个方面都可以得到改善。我们提出了将范畴论设计应用于模拟机器人控制系统。基于所需概念的本体论进行神经网络控制，并进行三个实验，以探索预测方法的启发性和机器人性能的提升。

### 15.1.3 范畴论的基本概念

现代数学许多领域的研究可以推广为对特定数学对象及这些对象之间映射的研究。例如，集合之间的映射是集合论研究的主要对象。群（或环）和群同态（或环同态）构成了群论（或环论）的主要研究对象。拓扑空间之间的连续映射构成了拓扑学的主要研究对象，等等。范畴的概念是对这些特定数学对象和映射的概括和抽象。

**定义 15.1. 范畴** $\mathbb{C}$：
- (1) 对象 ob$\mathbb{C}$；
- (2) 任意对象对 $A, B$ 对应一个集合 $\mathbb{C}(A, B)$。其元素称为态射，且满足条件：如果 $A \neq A'$ 或 $B \neq B'$，则 $\mathbb{C}(A, B)$ 和 $\mathbb{C}(A', B')$ 没有交集。

态射具有以下性质：

- (a) 合成律：如果 $A, B, C \in \text{ob}\mathbb{C}$，$f \in \mathbb{C}(A, B)$，$g \in \mathbb{C}(B, C)$，则存在唯一的 $gf \in \mathbb{C}(A, C)$，称为 $f$ 和 $g$ 的合成；
- (b) 结合律：如果 $A, B, C, D \in \text{ob}\mathbb{C}$，$f \in \mathbb{C}(A, B)$，$g \in \mathbb{C}(B, C)$，$h \in \mathbb{C}(C, D)$，则 $h(gf) = (hg)f$；
- (c) 恒等态射：对于每个对象 $A$，存在一个态射 $1_{A} \in \mathbb{C}(A, A)$，满足以下条件：任意 $f \in \mathbb{C}(A, B)$ 和 $g \in \mathbb{C}(C, A)$ 都有 $f1_{A} = f$ 且 $1_{A}g = g$。

一些常见的范畴列于表 15.1。

表 15.1：范畴示例。

| 范畴 | 对象 | 态射 |
| :--- | :--- | :--- |
| Set | 集合 | 函数 |
| Top | 拓扑空间 | 连续函数 |
| Vect | 向量空间 | 线性变换 |
| Grp | 群 | 群同态 |

**单态射**：设 $\mathbb{C}$ 为一个范畴，$f: A \rightarrow B$ 为 $\mathbb{C}$ 中的态射。如果 $\mathbb{C}$ 中任意一对平行态射 $g, h: C \rightarrow A$ 满足 $fg = fh$，则 $g = h$，此时称 $f$ 为单态射。

**满态射**：设 $\mathbb{C}$ 为一个范畴，$f: A \rightarrow B$ 为 $\mathbb{C}$ 中的态射。当且仅当 $\mathbb{C}$ 中任意一对平行态射 $g, h: B \rightarrow C$ 满足 $gf = hf$ 时，$g = h$，此时称 $f$ 为满态射。

**定义 15.2.** 设 $\mathcal{C}$ 和 $\mathcal{D}$ 为范畴。一个函子 $F: C \rightarrow D$ 由两个映射组成，
$$
\begin{aligned}
& \mathrm{ob}\mathcal{C} \rightarrow \mathrm{ob}\mathcal{D}: A \rightarrow F(A), \\
& \operatorname{Mor}\mathcal{C} \rightarrow \operatorname{Mor}\mathcal{D}: f \rightarrow F(f),
\end{aligned}
$$
满足 $\operatorname{dom}(F(f)) = F(\operatorname{dom}(f))$，$\operatorname{cod}(F(f)) = F(\operatorname{cod}(f))$，$F(1_A) = 1_{F(A)}$，且如果 $\operatorname{dom}(g) = \operatorname{cod}(f)$，则 $F(gf) = F(g)F(f)$。

任何范畴 $\mathcal{C}$ 都有一个到自身的单位函子 $1_C: C \rightarrow C$，满足对象和态射之间的对应关系是常数。

群范畴 Gp（拓扑空间范畴 Top，等等）有一个到集合范畴 Set 的遗忘函子 $G$，且 $G$ 满足每个群（拓扑、空间等）对应于其所在的集合，每个同态群（连续映射等）对应于自身。

通常，我们说函子 $\mathcal{C}^{\mathrm{op}} \rightarrow \mathcal{D}$ 是从 $\mathcal{C}$ 到 $\mathcal{D}$ 的反变函子。

**定义 15.3.** 设 $\mathcal{C}$ 和 $\mathcal{D}$ 为范畴，其中 $F: \mathcal{C} \rightarrow \mathcal{D}$ 和 $G: \mathcal{C} \rightarrow \mathcal{D}$ 为函子。自然变换 $\alpha: F \rightarrow G$ 是一个映射 $\mathrm{ob}\mathcal{C} \rightarrow \mathrm{Mor}\mathcal{D}$：

$$
A \mapsto (\alpha_A: F(A) \rightarrow G(A)), A \in \mathrm{ob}\mathcal{C}
$$

满足对 $\mathcal{C}$ 中的任意态射 $f: A \rightarrow B$，$G(f)\alpha_A = \alpha_B F(f)$，即发生以下图示交换：

![](img/456a7a56403cbb2b5f1a261793529a51_438_0.png)

自然变换 $\alpha: F \rightarrow G$ 满足对任意 $A \in \mathrm{ob}\mathcal{C}$，$\alpha_A: F(A) \rightarrow G(A)$ 是同构。此时，我们称 $\alpha$ 为自然同构。

在一些研究中，我们经常遇到这样的结构。在给定的特定范畴中（也可以看作是从该范畴到小范畴的函子），由对象到该范畴中每个对象的映射所形成的可交换映射家族具有“普适性”性质。例如，给定拓扑空间 $\{X_i | i \in I\}$，积空间 $\prod X_i$ 到每个因子空间之间的映射家族 $\{\pi_i: \prod X_i \rightarrow X_i | i \in I\}$ 具有“普适性”性质。对于任意拓扑空间 $X$ 和连续映射家族 $\{f_i: X \rightarrow X_i | i \in I\}$，存在唯一的连续映射 $f = \langle f_i \rangle: X \rightarrow \prod X_i$，其中每个 $f_i$ 可以分解为 $f_i = \pi_i f$ 且与 $f$ 相关。这样的性质可以抽象为纯粹的范畴性质，即范畴极限和余极限。

