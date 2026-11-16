

## GENETIC ALGORITHMS FOR THE TRAVELING SALESMAN PROBLEM

### Traveling Salesman Problem

The TSP is a classic combinatorial optimization problem, simple in its formulation but very difficult to solve. This problem is known to be NP-hard, in other words it cannot be solved exactly in a polynomial time. Many exact and heuristic algorithms have been developed in the field of Operations Research (OR) to solve it. The problem is to find the shortest possible tour through a set of n vertices in such a way that each vertex is visited once and only once.

TSP是一种经典的组合优化问题，其表述简单但求解非常困难。该问题已知是NP-hard的，也就是说，它不能在多项式时间内被精确求解。许多精确算法和启发式算法已在运筹学（OR）领域开发出来以求解该问题。该问题的目标是找到经过n个顶点集合的最短可能巡回路径，使得每个顶点被且仅被访问一次。

This problem can be divided into two categories depending on the form of the costs matrix: symmetric and asymmetric. If the equality C(i, j) = C(j, i) is satisfied, the TSP is symmetric, otherwise it is called an asymmetric TSP, i and j being any vertices. In a symmetric tsp of n cities, there are (n-1)!/2 possible solutions and their inverses cyclic permutations with the same total cost. The purpose is then to find a Hamiltonian cycle of minimum total cost (Cicerello & Smith, 2000).

根据成本矩阵的形式，该问题可分为两类：对称和非对称。如果满足等式C(i, j) = C(j, i)，则TSP为对称的，否则称为非对称TSP，其中i和j为任意顶点。在n个城市的对称TSP中，存在(n-1)!/2个可能的解及其具有相同总成本的逆向循环排列。目标是寻找总成本最小的哈密顿回路（Cicerello & Smith, 2000）。

### Mathematical Formulation

The tsp is formulated as a cost matrix in n dimensions of d_ij values Figure 1, where the purpose is to obtain a permutation of these values, as the sum of costs d_ij is minimal, for all i and j, where i is a node and j is next in a sequence.

TSP被表述为一个n维的d_ij值成本矩阵（见图1），其目标是获得这些值的一个排列，使得对所有i和j的成本d_ij之和最小，其中i是一个节点，j是序列中下一个节点。

More formally, we have:

```
MINIMIZE \sum_{i=1}^{n} \sum_{j=1}^{n} d_{ij} x_{ij}
```

更正式地，我们有：

```
MINIMIZE \sum_{i=1}^{n} \sum_{j=1}^{n} d_{ij} x_{ij}
```

With:

```
\sum_{j=1}^{n} x_{ij} = 1, \forall i, \quad \sum_{i=1}^{n} x_{ij} = 1, \forall j, \quad x_{ij} \in \{0,1\}, \forall i, j
```

其中：

```
\sum_{j=1}^{n} x_{ij} = 1, \forall i, \quad \sum_{i=1}^{n} x_{ij} = 1, \forall j, \quad x_{ij} \in \{0,1\}, \forall i, j
```

```
\sum_{i,j \in S} x_{ij} \le |S|, \forall S \subset V, S \neq \emptyset
```

```
\sum_{i,j \in S} x_{ij} \le |S|, \forall S \subset V, S \neq \emptyset
```

### Figure 1. distance matrix of symmetric tsp of 8 cities

### 图1. 8个城市对称TSP的距离矩阵

| | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 12 | 3 | 23 | 1 | 5 | 32 | 56 |
| 2 | 12 | 0 | 9 | 18 | 3 | 41 | 45 | 5 |
| 3 | 3 | 9 | 0 | 89 | 56 | 21 | 12 | 49 |
| 4 | 23 | 18 | 89 | 0 | 87 | 46 | 75 | 17 |
| 5 | 1 | 3 | 56 | 87 | 0 | 55 | 22 | 86 |
| 6 | 5 | 41 | 21 | 46 | 55 | 0 | 21 | 76 |
| 7 | 32 | 45 | 12 | 75 | 22 | 21 | 0 | 11 |
| 8 | 56 | 5 | 49 | 17 | 86 | 76 | 11 | 0 |

$X_{ij}$ is the decision matrix (connection).

$X_{ij}$是决策矩阵（连接）。

S is a vertex Set from the global set V.

S是全局集合V中的一个顶点集合。

We consider $d_{ij} = d_{ji}$, ∀i, j to work on the symmetric TSP (STSP);

我们考虑$d_{ij} = d_{ji}$，∀i, j，以处理对称TSP（STSP）；

### Genetic Algorithm

### 遗传算法

### Representation Methods

### 表示方法

In this section we present the method of data representation which is best adapted to the handled problem. In recent decades there have been three vector representations considered within the tsp (Michalewicz, 1996): the adjacency representation, the ordinal representation and path representation.

在本节中，我们介绍最适合所处理问题的数据表示方法。在最近几十年中，TSP中考虑了三种向量表示（Michalewicz, 1996）：邻接表示、序数表示和路径表示。

Path Representation is the most natural representation of a tour; this is the one we adopt in this article. A path simply lists visited nodes using labels representing the successor and predecessor of each city. So a tour like [1 → 2 → 3 → 4 → 5 → 6] can be represented as shown in Figure 2.

路径表示是巡回路径最自然的表示方法；这是本文所采用的方法。路径简单地列出已访问节点，使用表示每个城市的后继和前驱的标签。因此，像[1 → 2 → 3 → 4 → 5 → 6]这样的巡回路径可以如图2所示表示。

### Figure 2. path representation

### 图2. 路径表示

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_233_0.png)

### Crossover Operators

### 交叉算子

Several ways to do the crossing in tsp optimization context are described in the literature: Partially Mapped Crossover (**PMX**) (David Edward Goldberg, 1989), Order Crossover (**OX**) proposed by (L. Davis, 1985) which produces offspring that preserves the cities relative order of parents, Edge Crossover (**EX**) (L. D. Whitley, Starkweather, & Fuquay, 1989), Subtour Exchange Crossover (**SXX**) (Yamamura, Ono, & Kobayashi, 1992), Edge Exchange Crossover (**EXX**) (Murata & Itai, 2008), Edge Assembly Crossover (**EAX**) (J. Watson et al., 1998).

文献中描述了在TSP优化上下文中进行交叉的几种方法：部分映射交叉（**PMX**）（David Edward Goldberg, 1989），顺序交叉（**OX**）由（L. Davis, 1985）提出，它产生保留父母城市相对顺序的后代，边交叉（**EX**）（L. D. Whitley, Starkweather, & Fuquay, 1989），子巡回路径交换交叉（**SXX**）（Yamamura, Ono, & Kobayashi, 1992），边交换交叉（**EXX**）（Murata & Itai, 2008），边组装交叉（**EAX**）（J. Watson et al., 1998）。

### Various Others Crossover Operators and Their Variations

### 各种其他交叉算子及其变体

The Modified crossover (L. Davis, 1985), this crossover operator is an extension of the one-point crossover for permutation problems. The Order-based crossover (**OBX**) which focuses on the relative order of the cities on the parent chromosomes, used by G. Syswerda in (L. D. Davis, 1991); Alternate Edges Crossover (**AEC**) is reported in (Grefenstette, Gopal, Rosmaita, & Van Gucht, 1985), the results with this operator have been uniformly discouraging. However, it was a good introduction to the other edge-preserving operators. (Deep & Mehrahtu, 2011) proposed three new additional variations of order crossover and their performance were far better than the existing variations. The variations are designed using cut point analysis on the standard ordered crossover operator. Freisleben and Merz (Freisleben & Merz, 1996) and (Merz & Freisleben, 1997) suggested the distance-preserving crossover (DPX) for TSP.

修改交叉（L. Davis, 1985），该交叉算子是针对排列问题的单点交叉的扩展。基于顺序的交叉（**OBX**）关注亲代染色体上城市的相对顺序，由G. Syswerda在（L. D. Davis, 1991）中使用；替代边交叉（**AEC**）报告于（Grefenstette, Gopal, Rosmaita, & Van Gucht, 1985），使用该算子的结果一直令人沮丧。然而，它是其他边保存算子的良好介绍。（Deep & Mehrahtu, 2011）提出了三种新的顺序交叉变体，其性能远优于现有变体。这些变体是使用标准有序交叉算子上的断点分析设计的。Freisleben和Merz（Freisleben & Merz, 1996）和（Merz & Freisleben, 1997）为TSP提出了距离保存交叉（DPX）。

- More Specific Crossover for Ordered Problems
  - Position-Based Crossover Operator (POS) (Goel & Wadhwa, 2013)
  - Voting Recombination Crossover Operator (VR) (Muhlenbein, 1989)
- Alternating-Position Crossover Operator (AP) (Larranaga, Kuijpers, Poza, & Murga, 1997)
- Sequential Constructive Crossover Operator (SCX) (Zakir, 2010)
- Brief Description of Used Crossovers
- Partially Matched Crossover (PMX): PMX is one of the most popular Crossovers for the tsp, (Kumar, Karambir, & Kumar, 2012) says it gives better results compared to other cross operators as Cyclic Crossover CX which has been proposed by (I. M. Oliver, D. J. Smith, & J. R. C. Holland, 1987) and the Order Crossover OX already introduced in the previous paragraph. PMX and many variants of it have proved their worth on the ordered problems such as TSP (Deep & Mehrahtu, 2012). In this method, two crossing points are randomly selected. Children completely inherit segments inside the cut points, while the borders of children are filled by a mapped matching with vertices in the two parents as shown in Figure 3. The complexity of this crossover is O(n).
- Edge Recombination Crossover (ERX): Since its introduction by (D. Whitley, Starkweather, & Shaner, 1990), this method is among the most used in the literature to solve various problems of planning and scheduling using GA. It tends to preserve inherited edges from parents. In this method, we select an initial city in one parent (it can be a random or guided choice by a defined criteria) and all occurrences of this city are eliminated from other cities neighborhoods. If this selected city still has neighbors (unvisited) then we choose the city with the least neighborhood (for exceptional cases random is carried out) and then redo the same process for the chosen city until filling the current child Figure 4.

- 针对有序问题的更具体的交叉
  - 基于位置的交叉算子（POS）（Goel & Wadhwa, 2013）
  - 投票重组交叉算子（VR）（Muhlenbein, 1989）
- 交替位置交叉算子（AP）（Larranaga, Kuijpers, Poza, & Murga, 1997）
- 顺序构造性交叉算子（SCX）（Zakir, 2010）
- 所用交叉的简要描述
- 部分匹配交叉（PMX）：PMX是TSP最流行的交叉之一，（Kumar, Karambir, & Kumar, 2012）表示与其他交叉算子（如由（I. M. Oliver, D. J. Smith, & J. R. C. Holland, 1987）提出的循环交叉CX，以及前一段已介绍的顺序交叉OX）相比，它能取得更好的结果。PMX及其许多变体已在TSP等有序问题上证明了其价值（Deep & Mehrahtu, 2012）。在此方法中，随机选择两个交叉点。子代完全继承断点内的片段，而子代的边界则通过与两个亲代顶点的映射匹配来填充，如图3所示。该交叉的复杂度为O(n)。
- 边重组交叉（ERX）：自（D. Whitley, Starkweather, & Shaner, 1990）引入该方法以来，它是文献中用于使用GA解决各种规划和调度问题的最常用方法之一。它倾向于保留从亲代继承的边。在此方法中，我们选择一个亲代中的初始城市（可以是随机选择，也可以根据定义标准进行引导选择），并从此城市从其他城市的邻域中删除所有出现项。如果该选定的城市仍有邻居（未访问），则我们选择邻域最少的城市（对于特殊情况则随机选择），然后对所选城市重复相同的过程，直到填充当前子代（见图4）。

*Figure 3. PMX*

*图3. PMX*

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_234_0.png)

### Figure 4. ERX

### 图4. ERX

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_235_0.png)

- R-opt Heuristic: First introduced by (Lin & Kernighan, 1973) is one of the most powerful heuristic algorithms for the TSP. It was proposed almost fifty years ago but even nowadays it is the state-of-the-art TSP local search (Johnson & McGeoch, 2002), (Rocki & Suda, 2012) and (Manthey & Veenstra, 2013). An R-opt operator consists of replacing r edges from a tour by r edges not in the tour if this decreases the length of the tour (Jog, Suh, & Gucht, 1989). For giving an example, a 2-opt strategy randomly selects two edges (1,2) and (3,4) from a tour and checks if ED(1,2) + ED(3,4) > ED(1,4) + ED(2,3) (ED stands for Euclidean distance). If this is the case, the new tour is obtained by removing the edges (1,2) and (3,4) and replacing them with the edges (1,4) and (3,2) as shown in Figure 5.

- R-opt启发式：由（Lin & Kernighan, 1973）首次引入，是TSP最强大的启发式算法之一。它几乎五十年前就被提出，但即便在今天，它仍然是TSP局部搜索的最先进方法（Johnson & McGeoch, 2002），（Rocki & Suda, 2012）和（Manthey & Veenstra, 2013）。R-opt算子包括如果这能减少巡回路径长度，则用巡回路径中不存在的r条边替换巡回路径中的r条边（Jog, Suh, & Gucht, 1989）。例如，2-opt策略从巡回路径中随机选择两条边(1,2)和(3,4)，并检查ED(1,2) + ED(3,4) > ED(1,4) + ED(2,3)（ED代表欧几里得距离）。如果是这种情况，新巡回路径是通过移除边(1,2)和(3,4)并用边(1,4)和(3,2)替换它们得到的，如图5所示。

### Genetic Algorithm Functioning

### 遗传算法运行

We use a simple but effective strategy, to get an elitist genetic algorithm using overlapped populations. This principle has been presented as a Steady State Genetic Algorithm (David Edward Goldberg, 1989) and (Vavak & Fogarty, 1996).

我们采用一种简单而有效的策略，利用重叠种群获得精英遗传算法。该原则已作为稳态遗传算法（David Edward Goldberg, 1989）和（Vavak & Fogarty, 1996）提出。

### Figure 5. r-opt(2-opt)

### 图5. r-opt(2-opt)

![](img/ffe7d4fcc17dbb6c6c08d4db77d800ca_235_1.png)

During GA Evolving from one generation to another, the population is preserved and new individuals are inserted only if they improve the average quality of the population and this is performed by replacing those less useful as described in the pseudocode in Figure 6.

在GA从一代演进到下一代的过程中，种群被保留，新个体仅在它们提高种群平均质量时才被插入，这是通过替换那些不太有用的个体来实现的，如图6的伪代码所述。

### ADOPTED APPROACH: JUMP CROSSOVER

### 所采用的方法：跳跃交叉

A good crossover should mainly have two features: respect and edge transmission (Surry & Radcliffe, 1996). Respect means that the common traits between both parents must be inherited and transmission implies that each inherited trait must belong to at least one of the two parents. (R. A. Watson & Pollack, 2000) states that effective Crossover must also introduce new characteristic into generated children.

良好的交叉主要应具备两个特性：尊重和边传输（Surry & Radcliffe, 1996）。尊重意味着两个亲代之间的共同特征必须被继承，而传输意味着每个继承的特征必须属于两个亲代中的至少一个。（R. A. Watson & Pollack, 2000）指出，有效的交叉还必须向生成的子代引入新特征。

In summary, it is necessary that our operator tends to inherit the traits of the parents and also to introduce new traits for children diversity.

总之，我们的算子需要倾向于继承亲代的特征，同时也要为子代多样性引入新特征。

### Overview of the Jump Crossover

### 跳跃交叉概述

The Jump crossover operator is aimed at exchanging information between two parent chromosomes. The adjacency lists of the two parents are made then a starting item (city) and its link to a second item are chosen from one parent (it can be a random

跳跃交叉算子旨在交换两个亲代染色体之间的信息。首先构建两个亲代的邻接表，然后从其中一个亲代中选择一个起始项目（城市）及其到第二个项目的链接（可以是随机

### Figure 6. Pseudo-code of a standard GA

### 图6. 标准GA伪代码

```
BEGIN GA
gen=0 [ generation counter ]
Initialize population P(gen)
Evaluate population P(gen)
done:=false
WHILE not done DO
gen:=gen+1
Select P(gen) from P(gen -1)
Crossover P(gen)
Mutate P(gen)
Evaluate P(gen)
done:=Optimization criteria
END WHILE
Output of best solutions
END GA.
```

