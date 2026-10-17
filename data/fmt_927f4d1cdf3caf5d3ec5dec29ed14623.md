
![Images](img/image00586.jpeg)

* * *

### FIGURE 4-2 Symmetrical graph

如果我们用图来表示学生与教授之间的关系，则该关系不对称，如 Figure 4-3 所示：

![Images](img/image00587.jpeg)

* * *

### FIGURE 4-3 Asymmetrical graph

Figure 4-3 所示的图是 *directed graph*，即顶点之间的关系存在方向。根据研究内容，方向可以是任意的。例如，如果你想描绘从教授到学生的知识传播，则箭头会指向学生，并且可能会包含多个学生。

你已经看到了 *vertex* 和 *edge* 的定义。在继续之前，我需要定义几个其他术语：

![image](img/image00484.jpeg) **Incidence** 边（有向或无向）与其端点之一相邻的顶点称为 *incident*。

![image](img/image00484.jpeg) **Degree of a vertex** 顶点的 *degree* 是与该顶点相邻的边的数量。有向图中的顶点也可以称为 *in degree* 和 *out degree*。入度是指向顶点的边的总数，出度是指向顶点的边（如 Figure 4-3 所示）。

![image](img/image00484.jpeg) **Adjacency** 两个顶点通过一条边相连时，它们是 *adjacent*。

![image](img/image00484.jpeg) **Directed graph** 有向图（也称为 *digraph*）是边有方向的图。

![image](img/image00484.jpeg) **Weighted digraph** 这是一类有“成本”或“权重”属性的有向图，即每条边（即每种关系）都有强弱之分。

![image](img/image00484.jpeg) **A complete graph** 这是一张每对顶点之间都有边的图。若有 N 个顶点，则会有 N × (N – 1) 条边。

一旦你理解了图的基本概念以及顶点与边的关系，接下来自然的问题是：如何遍历给定的图？这个问题可以通过多种方式回答。让我们考虑 Figure 4-4 所示的图，它包含五个顶点和七条边。

![Images](img/image00588.jpeg)

* * *

### FIGURE 4-4 Traversing a graph

你可以通过三种基本方式遍历图：

![image](img/image00484.jpeg) **Path** 在路径中，顶点不能重复——例如，a-b-c-d-e。你可以重复边，但不能重复顶点。

![image](img/image00484.jpeg) **Trail** 路径的相反概念：边不能重复——例如，a-b-c-d-e-b-d。

![image](img/image00484.jpeg) **Walk** 没有限制。例如，a-b-e-d-b-c。

无论使用哪种遍历方法，如果你在起点和终点相同，则该遍历被视为 *closed*。例如，如果你从顶点 b 开始并结束于 b，则无论使用路径、路径还是步行，这都是闭合的。遍历的长度仅为你需要跨越的边数。

有两种特殊的遍历类型：

![image](img/image00484.jpeg) **Circuit** 闭合路径（例如，a-b-c-d-b-e-d-a）

![image](img/image00484.jpeg) **Cycle** 闭合路径（例如，a-b-c-d-a）

由此引出几个其他术语：

![image](img/image00484.jpeg) **Acyclic** 图中不存在循环的图

![image](img/image00484.jpeg) **Tree** 连通且不含循环的图

![image](img/image00484.jpeg) **Rooted tree** 带有“根”或“ distinguished”顶点的树；树的叶子是根树中的终端节点

![image](img/image00484.jpeg) **Directed acyclic graph (DAG)** 无环的有向图

现在你对图的基本概念及其类型有了初步了解。与其继续深入抽象的图论概念，我更想回答你此时可能在思考的问题：图有什么用途？

图论有许多应用。例如，它们可以帮助你确定两个顶点/节点之间的最短（或最长）路径，或最小权重（而非最小长度）的路径。如果你只花一瞬间思考这两个问题，就会看到它们在计算机网络中有明确的应用。图论也用于研究网站结构和连接客户端。旅行问题显然也通过图论来解决。还有在粒子物理、生物学，甚至政治学中的应用。

**Tip**

学习离散数学的初学者的一个极佳资源是 Steven Krantz 所著的 *Discrete Mathematics Demystified*（McGraw-Hill Education，2008）。

#### Conclusions

本章介绍了你在后续章节理解密码算法所需的基本数学工具。本章主要介绍了数字系统，最重要的是对质数的深入介绍，包括如何生成质数。相对质数（co-prime）的概念也已涵盖。这些都是你应该深入理解并应用于 RSA 算法的重要主题。

你也看到了一些基本的数学运算，例如求和和对数，并被介绍了离散对数。模运算的讨论对于理解非对称算法至关重要。本章以离散数学的介绍结束，包括集合论、逻辑、组合论和图论。本章简要涵盖了这些主题；如果你能够深入且全面地理解本章所讨论的内容，那么继续学习密码学就足够了。关键是要确保在继续深入之前，你已经彻底、完全地理解本章内容。如有需要，可以重新阅读本章，并参考文中提供的各种学习辅助材料。

### 测试你的知识

**1.** Two vertices connected by an edge are `adjacent`.

**2.** The statement “Any number *n* ≥ 2 is expressible as a unique product of 1 or more prime numbers” describes what?

**3.** `log[3]27 = 3`

**4.** A circuit is a closed `trail`.

**5.** Are the numbers 15 and 28 relatively prime?

**6.** A `congruence class` is a group of numbers that are all congruent for some given modulus.

**7.** `The Lucas-Lehmer test` is a deterministic test of primality that works on Mersenne numbers.

**8.** `Discrete logarithms` are logarithms in respect to a finite group.

**9.** Set B is the `complement` of set A if B has no elements that are also in A. This is symbolized as B = Ac.

**10.** `Permutations` are ordered arrangements of things.

### 答案

**1.** `adjacent`

**2.** `The fundamental theorem of arithmetic`

**3.** `3`

**4.** `trail`

**5.** `Yes`

**6.** `congruence class`

**7.** `The Lucas-Lehmer test`

**8.** `Discrete logarithms`

**9.** `complement`

**10.** `Permutations`

#### 尾注

**1.** Edna E. Kramer, *The Nature and Growth of Modern Mathematics*, (`Princeton University Press, 1983`).

### 5

**Essential Algebra**

**In this chapter we will cover the following:**

![image](img/image00483.jpeg) `Groups`, `rings`, and `fields`

![image](img/image00483.jpeg) `Diophantine equations`

![image](img/image00483.jpeg) `Basic matrix algebra`

![image](img/image00483.jpeg) `Algorithms`

![image](img/image00483.jpeg) `The history of algebra`

Certain aspects of algebra are very important to the cryptographic algorithms you will be exploring later in this book. Those of you with a solid background in mathematics might be wondering how I could cover such a broad topic in a single chapter. Those of you without a solid background in mathematics might be wondering if you can learn enough and grasp enough of the concepts to apply them to cryptography later on.

Let me address these questions before you continue reading. As I did with Chapter 4, in this chapter I’m going to focus only on the basic information you need to help you understand the cryptographic algorithms covered later. Certainly, each of these topics could be given much more coverage. Entire books have been written on abstract algebra, matrix mathematics, and algorithms—in fact, some rather large tomes have been written just on algorithms! But you don’t necessarily need all those details to understand what you will encounter in this book. I would, however, certainly recommend that you explore these topics in more depth at some point. In this chapter, as with the last, I won’t delve into mathematical proofs. This means that you must accept a few things simply on faith—or you can refer to numerous mathematical texts that do indeed provide proofs for these concepts.

Those of you with a less rigorous mathematical background should keep in mind that, although you’ll need to have a firm grasp of the concepts presented in this chapter, you don’t need to become a mathematician (though I would be absolutely delighted if this book motivated you to study mathematics more deeply). It might take a mathematician to create cryptographic algorithms, but anyone can understand the algorithms I’ll present here. The ultimate goal of this book is to help you understand existing cryptography. I will provide links to resources where you can get additional information and explanations if you need it.

#### Abstract Algebraic Structures

If you think of algebra only as solving linear and quadratic equations, as you probably did in secondary school, these first algebraic concepts might not seem like algebra at all. But solving such equations is only one application of algebra. A far more interesting topic, and one more pertinent to cryptography, is the study of *sets* and operations you can perform on those sets. This is the basis for *abstract algebra*. Mathematics students frequently struggle with these concepts, but I will endeavor to make them as simple as I can without leaving out any important details.

Special sets of numbers and the operations that can be accomplished on those numbers are important to abstract algebra, and `groups`, `rings`, and `fields` are simply sets of numbers with associated operations.

Let’s begin with some examples. Think about the set of real numbers, which is an infinite set, as you know. What operations can you do with numbers that are members of this set in which the result will still be within the set? You can add two real numbers, and the answer will always be a real number. You can multiply two real numbers, and the answer will always be a real number. What about the inverse of those two operations? You can subtract two real numbers and the answer will always be a real number. You can divide two real numbers and the answer will always be a real number (of course division by zero is undefined). At this point, you may think all of this is absurdly obvious, and you might even think it odd that I would spend a paragraph discussing it. However, let’s turn our attention to sets of numbers in which all of these facts are *not* true.
