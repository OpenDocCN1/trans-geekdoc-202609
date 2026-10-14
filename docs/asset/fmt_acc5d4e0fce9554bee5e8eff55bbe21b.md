
### 3.5 练习

- 1. **3.1** 计算两个单变量高斯分布之间的 KL 散度：`q(x) ~ N(μ₁, σ₁²)` 和 `q(x) ~ N(μ₂, σ₂²)`。

- 2. **3.2** 计算伯努利分布的 `E[X]`、`Var(X)` 和 `H(X)`。

- 3. **3.3** 推导 `Beta(a, b)` 分布的均值、众数和方差。

### 总结

- 变分推断的主要思想是从可处理分布族中选择近似分布 `q(x)`，然后使该近似尽可能接近真实后验分布 `p(x)`。

- 证据下界是我们寻求最大化的目标函数，以学习模型的变分参数。

- 在 mean-field 近似中，我们假设近似分布 `q(x)` 完全分解。

- 互信息最大化可以通过推导并最大化 MI 下界来实现。

## 软件实现

![](img/325742126d3ff007c6c385f4ffb5c3be_78_0.png)

**This chapter covers**

- 数据结构：线性、非线性和概率

- 问题求解范式：完全搜索、贪心、分治和动态规划

- ML 研究：采样方法和变分推断

在前几章中，我们研究了贝叶斯推断的两个主要阵营：马尔可夫链蒙特卡洛和变分推断。在本章中，我们回顾了从头实现算法所需的计算机科学概念。要编写高质量的代码，掌握数据结构和算法基础非常重要。本章旨在介绍常见计算结构和问题求解范式。本节中回顾的许多概念在 VisuAlgo 网站 (`https://visualgo.net/en`) 上进行了交互式可视化。

### 4.1 数据结构

数据结构是存储和组织数据的一种方式。数据结构支持多种操作，例如插入、搜索、删除和更新，正确选择数据结构可以简化算法的运行时间。每种数据结构都提供不同的性能权衡。因此，了解数据结构的工作原理很重要。

#### 4.1.1 线性

如果数据结构的元素以线性方式排列，则认为它是 *线性* 的。*线性* 数据结构的最简单示例是 *固定大小数组*（其中数组的大小可能作为问题的约束指定）。访问数组中元素的耗时是常数：`O(1)`。如果数组的大小事先未知，最好使用 *动态可调整大小数组*（例如 Python 中的 `List` 或 C++ 中的 `Vector`），因为这些数据结构旨在原生处理调整大小。

应用于数组的两种常见操作是搜索和排序。最简单的搜索是在 `O(n)` 时间内对所有元素进行线性扫描。如果数组已排序，我们可以在 `O(log n)` 时间内使用二分搜索，这是一个分治算法的示例，我们很快会讨论。诸如选择排序和插入排序等朴素数组排序算法的复杂度为 `O(n^2)`，因此仅适用于小输入。一般来说，元素两两比较的基于比较的排序，如归并、堆或快速排序，运行时间为 `O(n log n)`，因为时间复杂度可以被视为遍历一棵完全二叉树，其中每个叶节点代表一种排序顺序。在此表示中，树的高度 `h` 等于算法运行时间。由于存在 `n!` 种可能的排序（叶节点），我们可以按如下方式限制运行时间。

$$\begin{aligned}
h &= \log n! = \log n(n - 1)(n - 2) \times \cdots \times 1 \\
&= \log n + \log(n - 1) + \cdots + \log 1 \\
&< \log n + \log n + \cdots + \log n = n \log n = O(n \log n)
\end{aligned} \tag{4.1}$$

如果我们在输入上添加额外约束，我们可以构建线性时间 `O(n)` 排序算法，例如计数排序、基数排序和桶排序。例如，计数排序可以应用于小范围内的整数，而基数排序通过逐位应用计数排序工作，如 Steven Halim（2010）所著的 *Competitive Programming* 中所述。使算法分布式可以进一步减少运行时间，如 Maurice Herlihy 和 Nir Shavit（2012）所著的 *The Art of Multiprocessor Programming* 中所述。

*链表* 由从头节点开始存储值和下一个指针的节点组成。它通常由于其线性 `O(n)` 搜索时间而被避免。*栈* 允许以后进先出（LIFO）顺序进行 `O(1)` 插入（`push`）和 `O(1)` 删除（`pop`）。这在递归实现的算法中特别有用（例如括号匹配或拓扑排序）。*队列* 允许从后方进行 `O(1)` 插入（`enqueue`）和从前方进行 `O(1)` 删除（`dequeue`）；因此，它遵循先进先出（FIFO）模型。它是诸如广度优先搜索（BFS）及其基于 BFS 的算法中常用的数据结构。在下一节中，我们将定义并检查几种非线性数据结构的示例。

#### 4.1.2 非线性

如果数据结构中的元素不遵循线性顺序，则该数据结构被视为非线性。非线性数据结构的示例包括映射（字典）和集合。这是因为有序字典和有序集合构建于自平衡二叉搜索树（BST）之上，该树保证插入、搜索和删除操作的时间复杂度为 `O(log n)`。BST 具有这样的性质：对于每个子树，根节点的值大于其左子节点，且小于其右子节点。自平衡 BST 通常实现为 Adelson-Velskii-Landis（AVL）树或红黑（RB）树（详见 Thomas H. Cormen、Charles E. Leiserson、Ronald L. Rivest 和 Clifford Stein 所著的《算法导论》[1990]）。有序映射（字典）与有序集合数据结构之间的区别在于：映射存储（键-值）对，而集合仅存储键。堆是另一种以树形表示组织数据的方式。例如，数组 `A = [2,7,26,25,19,17,1,90,3,36]` 可以表示为一棵树，如图 4.1 所示。

![](img/325742126d3ff007c6c385f4ffb5c3be_80_0.png)

图 4.1 一个二叉堆

我们可以轻松遍历二叉堆 `A = [90,36,17,25,26,7,1,2,3,19]`，从顶点 `i` 开始，使用简单的索引算术 `2i` 访问左子节点，`2i+1` 访问右子节点，`i/2` 访问父节点。与强制满足二叉搜索树（BST）性质不同，（最大）堆强制满足堆性质：在每一棵以 `x` 为根的子树中，`x` 的左子树和右子树上的项都小于（或等于）`x`。该性质保证（最大）堆的堆顶始终是最大元素。因此，（最大）堆支持快速提取最大元素。实际上，提取最大元素和插入操作均通过 `O(log n)` 的树遍历完成，并在必要时执行交换操作以维持堆性质。堆构成了优先队列的基础，而优先队列在 Prim 和 Kruskal 最小生成树（MST）、Dijkstra 单源最短路径（SSSP）以及 A* 搜索等算法中是一种重要的数据结构。最后，哈希表或无序映射是一种非常高效的数据结构，在无冲突假设下，访问时间为 `O(1)`。一类常用的哈希表是直接寻址（DA），其中键本身即为索引。哈希函数的目标是将表中的元素均匀分布，以尽量减少冲突。另一方面，如果你希望将相似项目分到同一个桶中，局部敏感哈希（LSH）能够帮助你找到最近邻，如 Alexandr Andoni、Piotr Indyk、Huy Le Nguyen 和 Ilya Razenshteyn 所著的《超越局部敏感哈希》（SODA，2014）中所述。

#### 4.1.3 概率型

概率型数据结构旨在处理大数据。它们提供概率性保证，并显著节省内存。概率型数据结构应对以下常见的大数据挑战：

- 成员查询：布隆过滤器、计数布隆过滤器、商过滤器和布谷鸟过滤器

- 基数估计：线性计数、概率计数、LogLog、HyperLogLog 和 HyperLogLog++

- 频率估计：多数算法、frequent、count sketch 和 count-min sketch

- 秩估计：随机抽样、q-digest 和 t-digest

- 相似性：LSH、MinHash 和 SimHash

关于概率型数据结构的全面讨论，请参阅 Andrii Gakhov（2022）所著的《大数据应用的概率型数据结构与算法》。在下一节中，我们将讨论四种主要的算法范式。

### 4.2 问题求解范式

有四种主要的算法范式：完全搜索、贪心、分治和动态规划。根据手头的问题，通常可以通过回顾这些算法范式来找到解决方案。在本节中，我们将讨论每种策略并提供一个示例。

#### 4.2.1 完全搜索

完全搜索（又称暴力搜索）是一种通过遍历整个搜索空间来求解问题的方法。在搜索过程中，我们可以剪掉那些确定不会通向所需解决方案的搜索空间部分。例如，考虑生成子集的问题。我们可以使用递归解法或迭代解法。两种方式中，当我们达到所需的子集大小时即终止。在下面的代码清单中，我们将基于生成子集的示例来实现一种完全搜索策略。

### 代码清单 4.1 子集生成

```
def search(k, n):
    if (k == n):
        print(subset)  # <-- process subset
    else:
        search(k+1, n)
        subset.append(k)
        search(k+1, n)
        subset.pop()
#end if

def bitseq(n):
    for b in range(1 << n):
        subset = []
        for i in range(n):
            if (b & 1 << i):
                subset.append(i)
        #end for
        print(subset)
    #end for

if __name__ == "__main__":
    n = 4
    subset = []
    search(0, n)  <-- recursive

    subset = []
    bitseq(n)  <-- iterative
```

一个涉及完全搜索的机器学习示例是通过完全枚举进行精确推理——详见 David J. C. MacKay 所著的《信息论、推理与学习算法》第 21 章。给定一个图模型，我们希望根据条件独立关系对联合分布进行分解，并使用贝叶斯规则计算某些事件的后验概率。在这种情况下，我们需要完整地填出所需的概率表以进行计算。

#### 4.2.2 贪心

贪心算法在每一步做出局部最优选择，希望最终能达到全局最优解。贪心算法通常依赖贪心启发式，而且我们常常能找到贪心算法未能达到全局最优的示例。例如，考虑分数背包问题。贪心背包问题的目标是选择物品放入容量有限的背包 `W` 中，以使背包内物品的总价值最大化，其中每个物品都有相应的重量和价值。我们可以将贪心启发式定义为物品价值与物品重量的比值（即我们希望贪心地选择同时具有高价值和低重量的物品，并根据这一标准对物品排序）。在分数背包问题中，我们允许取物品的一部分（与 0-1 背包不同）。在下面的代码清单中，我们将基于分数背包示例实现一种贪心策略。

### 代码清单 4.2 分数背包

```
class Item:
    def __init__(self, wt, val, ind):
        self.wt = wt
        self.val = val
        self.ind = ind
        self.cost = val // wt

    def __lt__(self, other):
        return self.cost < other.cost

class FractionalKnapSack:
    def get_max_value(self, wt, val, capacity):
        item_list = []
        for i in range(len(wt)):
            item_list.append(Item(wt[i], val[i], i))

        # sorting items by cost heuristic
        item_list.sort(reverse = True)  #O(nlogn)

        total_value = 0
        for i in item_list:
            cur_wt = int(i.wt)
            cur_val = int(i.val)
            if capacity - cur_wt >= 0:
                capacity -= cur_wt
                total_value += cur_val
            else:
                fraction = capacity / cur_wt
                total_value += cur_val * fraction
                capacity = int(capacity - (cur_wt * fraction))
                break
        return total_value

if __name__ == "__main__":
    wt = [10, 20, 30]
    val = [60, 100, 120]
    capacity = 50

    fk = FractionalKnapSack()
    max_value = fk.get_max_value(wt, val, capacity)
    print("greedy fractional knapsack")
    print("maximum value: ", max_value)
```

由于排序是最昂贵的操作，该算法的运行时间为 `O(n log n)`。我们可以看到，输入物品按价值/成本递减的比值排序；在贪心选择物品 1 和 2 后，我们取物品 3 的 2/3 份，总价值为 60 + 100 + (2/3)×120 = 240。

一个贪心算法的机器学习示例是传感器放置问题。给定一个房间和多个温度传感器，我们希望以最大化房间覆盖率的方式放置传感器。一种简单的贪心方法是：从空集 `S0` 开始，在第 `i` 次迭代中添加使增量函数最大化的传感器 `A`，例如互信息 `F_MI(A) = H(V\A) - H(V\A|A)`，其中 `V` 是所有传感器的集合。这里，我们使用了恒等式 `I(X; Y) = H(X) - H(X|Y)`。事实证明，如果观测变量在给定潜在状态时是独立的，则互信息是子模的，这导致了高效的贪心

```python
return 1
if (memo[n][k] != -1):
    return memo[n][k]
memo[n][k] = binomial_coeffs1(n-1, k-1) + binomial_coeffs1(n-1, k)
return memo[n][k]

def binomial_coeffs2(n, k):
    #bottom up DP
    for i in range(n+1):
        for j in range(min(i,k)+1):
            if (j == 0 or j == i):
                memo[i][j] = 1
            else:
                memo[i][j] = memo[i-1][j-1] + memo[i-1][j]
            #end if
        #end for
    #end for
    return memo[n][k]
def print_array(memo):
    for i in range(len(memo)):
        print('\t'.join([str(x) for x in memo[i]]))

if __name__ == "__main__":
    n = 5
    k = 2
    print("top down DP")
    memo = [[-1 for i in range(6)] for j in range(6)]
    nCk = binomial_coeffs1(n, k)
    print_array(memo)
    print("C(n={}, k={}) = {}".format(n,k,nCk))

    print("bottom up DP")
    memo = [[-1 for i in range(6)] for j in range(6)]
    nCk = binomial_coeffs2(n, k)
    print_array(memo)
    print("C(n={}, k={}) = {}".format(n,k,nCk))
```

时间复杂度为 `O(nk)`，空间复杂度为 `O(nk)`。在自顶向下 DP 的情况下，子问题的解会按需存储（记忆化），而在自底向上 DP 中，整个表从基例开始计算。

一个使用动态规划的机器学习示例可以在强化学习（RL）中找到，用于求解 Bellman 方程的解。我们可以根据时间 `t` 时的状态奖励以及未来折扣奖励之和来写出状态的值，如以下方程所示。

$$v_{\pi}(s)=\sum_a \pi(a|s)\sum_{r,s'}p(r,s'|s,a)[r+\gamma v_{\pi}(s')]$$

$$=E_{\pi}[R_t+\gamma v_{\pi}(S_{t+1})|S_t=s] \tag{4.3}$$

方程 4.3 被称为 `v(s)` 的 Bellman 最优性方程。我们可以通过求解使 `Q`-函数描述的状态奖励最大化的动作来恢复最优策略。

$$\pi(s)=\underset{a}{\arg\max}\ q(s,a) \tag{4.4}$$

对于少量状态和动作，我们可以使用动态规划以表格方式计算 Q 函数。在 RL 中，我们通常希望在探索和利用之间取得平衡——在这种情况下，我们以 1 − ε 的概率取前面的 argmax，并以 ε 的概率采取随机动作。

### 4.3 机器学习研究：采样方法和变分推断
