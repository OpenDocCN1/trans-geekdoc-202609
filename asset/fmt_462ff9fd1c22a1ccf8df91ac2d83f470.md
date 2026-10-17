
# 组平均链接

组平均链接，也称为**算术平均无权成对分组法**（Unweighted Pair Group Method with Arithmetic mean，UPGMA），是另一种非常直观的链接方法，在实践中常被认为是最好的选择之一。其思想是捕获不同簇中元素之间的平均距离，即：

$$d_{\text{avg}}(A,C) := \frac{1}{n_A n_C} \sum_{a \in A} \sum_{c \in C} d(a,c)$$

显然，对于单元素簇，有 $d_{\text{avg}}(\{a\}, \{c\}) = d(a, c)$。递推计算公式易于推导：

$$

\begin{array}{l}

d_{\text{avg}}(A \cup B, C) = \frac{1}{n_{AB} n_C} \left( \sum_{a \in A} \sum_{c \in C} d(a,c) + \sum_{b \in B} \sum_{c \in C} d(b,c) \right) \\

\quad = \frac{1}{n_{AB} n_C} \left( n_A n_C d_{\text{avg}}(A,C) + n_B n_C d_{\text{avg}}(B,C) \right) \\

\quad = \frac{n_A}{n_{AB}} d_{\text{avg}}(A,C) + \frac{n_B}{n_{AB}} d_{\text{avg}}(B,C) \qquad (5.12)

\end{array}

$$

术语“weighted”（可追溯至 Sokal and Sneath [634, 638]）容易引起混淆：它指的是每个点所拥有的影响力。在“unweighted”组平均法中，每个*对象*具有相同的权重（因此每个簇的权重与其包含的对象数量成正比）；而在“weighted”版本（即 McQuitty 和 Median 链接）中，每个*簇*具有相同的权重（因此较大簇中的每个对象权重会降低）。正如表 5.5 所示，如果我们将簇大小固定为常数 $n_A = n_B := 1$（即合并时忽略簇大小），两种“weighted”版本均对应其“unweighted”对应版本。

McQuitty 的**算术平均加权成对分组法**（Weighted Pair-Group Method with Arithmetic mean，WPGMA [[482]](#backmatter-001.xhtml#b_9783110785944-010_ref_482)）可递归定义为：

$$d_{\text{McQ}}(A \cup B, C) = \frac{1}{2} \left( d_{\text{McQ}}(A,C) + d_{\text{McQ}}(B,C) \right)$$

这引入了一个不幸的依赖，即依赖于子簇 $A$ 和 $B$ 的“合并历史”。给定三个对象 $a, b, c$，先合并 $a$ 和 $b$ 再与 $c$ 合并，可能产生与先合并其他对不同的结果。类似的论证也适用于下文讨论的 median linkage (WPGMC)。

**基于质心的无权成对分组法**（Unweighted Pair-Group Method using Centroids，UPGMC），也称为 centroid linkage，通过簇均值的距离来合并簇：

$$\mu_A = \frac{1}{|A|} \sum_{x \in A} x$$

![Fig. 5.10 An example showing why median and centroid linkages are non-monotone: the midpoint m of the merged cluster {a, b} is closer to c than any of its clusters members a and b were.](img/b_9783110785944-005_fig_010.png)

**图 5.10** 示例说明为何 median 和 centroid 链接是非单调的：合并簇 $\{a, b\}$ 的中点 $m$ 比其簇成员 $a$ 和 $b$ 中的任意一个都更接近 $c$。

即它总是合并最小的 $d_{\text{cent}}(A, C) = \|\mu_A - \mu_C\|$。显式计算均值间的距离需要大量额外的距离计算，因此比递推方法更慢且资源效率更低。但均值、方差和平方欧氏距离之间存在一种特殊关系，我们可以利用它通过递推优雅地计算这一特殊情况。我们不失一般性地仅针对单变量数据讨论这一关系，因为平方欧氏距离仅仅是平方变量的和。我们有：

$$\|\mu_A - \mu_C\|² = \mu_A² + \mu_C² - 2\mu_A\mu_C$$

并得到：

$$

\begin{array}{l}

d_{\text{cent}}(A \cup B, C) = \frac{n_A}{n_{AB}} d_{\text{cent}}(A,C) + \frac{n_B}{n_{AB}} d_{\text{cent}}(B,C) - \frac{n_A n_B}{n_{AB}²} d_{\text{cent}}(A,B) \\

\quad = \mu_{AB}² + \mu_C² - 2\mu_{AB}\mu_C = \|\mu_{AB} - \mu_C\|² \qquad (5.13)

\end{array}

$$

这意味着对于平方欧氏距离，我们可以在不计算均值本身的情况下计算均值间的距离。因此，我们需要用平方欧氏距离初始化距离矩阵，并将最终的链接距离解释为这些平方值。

Median linkage（或**基于质心的加权成对分组法**，Weighted Pair-Group Method using Centroids，WPGMC）的思想是最小化中位数的距离 $\|m_{A \cup B} - m_C\|$，其中中位数递归定义为：

$$m_{A \cup B} = \frac{1}{2} (m_A + m_B)$$

即前两个中位数的中点。对于平方欧氏距离，我们同样有递推公式：推导过程与 centroid linkage 完全相同，但固定 $n_A = n_B = 1$。Median linkage 和 centroid linkage 有一个怪癖：距离 $d(A \cup B, C)$ 可能小于 $d(A, C)$，这会产生非单调的树状图。如果我们绘制一棵表示簇合并的树，并用链接距离作为分支的高度，生成的树不会单调增长。树中的此类异常也称为 inversions（逆序），仅当链接不具备 Bruynooghe 的可约性质 [[89]](#backmatter-001.xhtml#b_9783110785944-010_ref_089) 时才会存在。直观上，当新中心位于两个间隔良好的簇之间，且比这两个簇中的任意一个都更接近第三个簇时，就会发生这种情况，如图 5.10 所示。这可能导致不良结果，因此应谨慎使用这些链接方法。

流行的 Ward linkage 优化以下准则 [[16, 364, 707]](#backmatter-001.xhtml#b_9783110785944-010_ref_016)：

$$d_{\text{Ward}}(A,B) = \frac{2 n_A \cdot n_B}{n_{AB}} \|\mu_A - \mu_B\|² \qquad (5.14)$$

![Fig. 5.11 Basic structure of a CF-Tree](img/b_9783110785944-005_fig_011.png)

**图 5.11** CF-Tree 的基本结构

该方程中的因子 2 确保了 `dWard = a, b[2]`，这正是单元素簇所期望的。该准则可描述为“平方和的最小增加” [\[582\]](#backmatter-001.xhtml#b_9783110785944-010_ref_582)，考虑到该方程仅使用均值，且似乎不包含平方和，这可能会让人感到惊讶。读者可能已经注意到，`k`-means 聚类也最小化平方和。此处的主要区别在于，Ward 连接在结果上施加了层次结构，而 `k`-means 则施加了扁平的划分，分成 `k` 个分区。通常，在 `k` 个分区处切割 Ward 连接的结果会比 `k`-means 差（通常差距很大）（关于类似 medoid 连接情况的一致性原因，参见 Schubert [\[613\]](#backmatter-001.xhtml#b_9783110785944-010_ref_613)），但不同 `k` 值的 `k`-means 结果通常不会嵌套成簇的层次结构。方程 5.14 可通过 König-Huygens 定理重写平方和的增加而获得：

```
\begin{array}{l} {d_{\text{Ward~}}\left( {A,B} \right) = {\sum\limits_{x \in A \cup B}\left\| {x - \mu_{AB}} \right\|^{2}} - {\sum\limits_{a \in A}\left\| {a - \mu_{A}} \right\|^{2}} - {\sum\limits_{b \in B}\left\| {b - \mu_{B}} \right\|^{2}}} \\ {\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\, = \frac{2n_{A}n_{B}}{n_{AB}}\left\| {\mu_{A} - \mu_{B}} \right\|^{2}} \\ \end{array}
```

Tab. 5.5 中给出的 Lance-Williams 递推公式如下（完整推导省略）：

```
\begin{array}{l} {d_{\text{Ward~}}\left( {A \cup B,C} \right) = \frac{2n_{AB}n_{C}}{n_{ABC}}\left\| {\mu_{AB} - \mu_{C}} \right\|^{2} = \frac{2n_{AB}n_{C}}{n_{ABC}}\left\| {\frac{n_{A}}{n_{AB}}\mu_{A} + \frac{n_{B}}{n_{AB}}\mu_{B} - \mu_{C}} \right\|^{2}} \\ {\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\,\, = \frac{n_{AC}}{n_{ABC}}d_{\text{Ward~}}\left( {A,C} \right) + \frac{n_{BC}}{n_{ABC}}d_{\text{Ward~}}\left( {B,C} \right) - \frac{n_{C}}{n_{ABC}}d_{\text{Ward~}}\left( {A,B} \right)} \\ \end{array}
```

## 5.3.3 簇特征树（CF-Tree）

我们现在简要介绍改进版 BETULA 的 CF-Tree \[413, 414\]，它提高了原始 BIRCH CF-Tree \[737, 738\] 的数值精度。

CF-Tree（簇特征树）是一种存储簇特征（CF）的基本高度平衡树。每个 BETULA 簇特征 [\[414\]](#backmatter-001.xhtml#b_9783110785944-010_ref_414) 是一个三元组

(5.15) CF : = (n, μ, SSE)

其中在该语境下 `n` 是数据点的数量或其聚合权重，`μ` 表示均值向量，SSE 是偏离均值的平方和。两个 BETULA 簇特征可以高效地合并为一个：

(5.16) n[AB] = n[A] + n[B]

(5.17) μ_AB = μ_A + (n_B / n_AB)(μ_B - μ_A) (5.17)

(5.18) SSE[AB] = SSE[A] + SSE[B] + nB(μ[B]−μ[AB])。

单个数据点 `x` 可以用簇特征 (1, x, 0) 简单表示。这些规则也源自 König-Huygens 定理，可在 Lang 和 Schubert [\[413\]](#backmatter-001.xhtml#b_9783110785944-010_ref_413) 中找到。原始 BIRCH 方法的数值不准确性此前已被 Schubert 和 Gertz [\[614\]](#backmatter-001.xhtml#b_9783110785944-010_ref_614) 观察到。

CF-Tree 是一棵高度平衡树：每个叶节点都是一个代表数据点的簇特征。内部节点存储其子节点的聚合信息。该树通过顺序插入所有数据点来构建。当向树中添加数据点或簇特征时，通过遍历树并在每一层选择距离最近的节点来插入。当到达叶条目时，如果不违反吸收阈值（参见 5.3.4 节），则将数据添加到该叶条目。如果数据无法添加到现有的叶条目，则生成一个新的叶条目。阈值可基于专家输入设定，从而生成大小可变但具有固定精度保证的树。但因为我们也可以以相同方式向 CF-Tree 添加簇特征，所以一旦达到选定的最大叶条目数，我们就可以用增加的阈值从其叶条目动态重建树，以减少树的内存使用量。在这种情况下，树在固定大小范围内构建，但精度可变，这对于存在内存资源限制的场景很有利。

## 5.3.4 簇特征的距离

Zhang 等人 \[737, 738\] 最初为 BIRCH 簇特征提出了几种距离函数和吸收准则。两者本质上都度量一种距离，但距离函数用于选择插入子树，而吸收准则用于决定何时添加到现有节点，或何时创建新节点。正如 Lang 和 Schubert [\[414\]](#backmatter-001.xhtml#b_9783110785944-010_ref_414) 所建议的，我们在下文中不区分距离和吸收准则，因为这样做没有好处。

欧氏距离：

(5.19) D0(A,B) = ∥μ[A]−μ[B]∥

曼哈顿距离：

(5.20) D1(A, B) = ∥μ[A]−μ[B]∥[1]

簇间距离：

(5.21) D2(A,B) = √(1/(n_A n_B) ∑_{x ∈ A} ∑_{y ∈ B} ∥x - y∥²) (5.21)

表 5.6 用于（平方）欧氏距离的连接策略及相应的 BIRCH 距离及其目标函数。

| 连接方式 | 闭式解 | BIRCH 距离 |
| --- | --- | --- |
| UPGMA | (1/(n_A n_B)) ∑_{x ∈ A} ∑_{y ∈ B} ∥x - y∥² | D2² |
| UPGMC | μA − ‖μB‖ | D0² |
| Ward | (2 n_A n_B / n_AB) ∥μ_A - μ_B∥² | 2 · D4² |

簇内距离（= 直径吸收准则）：

(5.22) D3(A,B) = √(1/(n_AB (n_AB - 1)) ∑_{x,y ∈ AB} ∥x - y∥²) (5.22)

方差增加距离：

(5.23) D4(A,B) = √(∑_{x ∈ AB} ∥x - μ_AB∥² - ∑_{x ∈ A} ∥x - μ_A∥² - ∑_{x ∈ B} ∥x - μ_B∥²) (5.23)

半径吸收准则：

(5.24) R(A,B) = √(1/n_AB ∑_{x ∈ AB} ∥x - μ_AB∥²) (5.24)

这些距离可以基于存储在 `BETULA` 簇特征中的摘要统计量高效计算。相应的方程及其推导见 Lang 和 Schubert [\[413\]](#backmatter-001.xhtml#b_9783110785944-010_ref_413) 的文献。

## 5.3.5 基于簇特征的层次聚类

虽然 `CF-Tree` 本身是一种层次聚类形式，但其层级和内部结构并非易于解释的形式。因此，它通常仅用于数据聚合，作为实际聚类的准备工作，此时仅使用叶节点条目。一种朴素的方法是直接使用叶节点条目的中心，并应用标准的层次聚类算法。这种方法丢弃了簇特征的方差信息。

现在的一个有趣观察是，链接策略和 `CF` 距离并没有太大区别。我们将展示，文献中已知的某些链接策略与 `BIRCH` 距离及其相应的目标函数之间存在对应关系，这种关系可以被用于聚类，即在仅使用中心之外，还结合了存储在簇特征中的额外信息。在 表 5.6 中，我们总结了已识别的链接策略与 `BIRCH` 距离及其各自目标函数之间的关系。最明显的相似性体现在质心欧氏距离（`D0`，公式 5.19）和质心链接（公式 5.13）上，二者几乎相同。Ward 链接（公式 5.14）与方差增大距离（`D4`，公式 5.23）的区别仅在于符号表示，以及 `D4` 的平方等于 Ward 距离，但由于 `BETULA` 出于计算原因内部使用平方距离，这一差异微不足道。最后一个可表示为 `BETULA` 距离的链接策略是 `UPGMA`，它实际上是平方簇间距离（`D2`，公式 5.21）。当用平方欧氏距离的 `UPGMA` 通用方程替换时，这种相显而易见：

(5.25) $d\_{\text{UPGMA}}\left( {A,B} \right) = \frac{1}{n\_{A} \cdot n\_{B}}{\sum\_{a \in A}{\sum\_{b \in B}d}}\left( {a,b} \right)\left( 5.25 \right)$

(5.26) $= \frac{1}{n\_{A} \cdot n\_{B}}{\sum\_{a \in A}{\sum\_{b \in B}\left\| a - b \right\|^{2}}}.\left( 5.26 \right)$

虽然 `WPGMA` 无法找到完全匹配，但由于它们之间的密切关系，我们仍可分别选择 `D2` 和 `D0` 作为其相应的“非加权”对应形式。利用这一知识，我们现在可以通过基于簇特征间对应距离计算距离矩阵，利用 Lance-Williams 公式，有意义地从簇特征过渡到层次聚类。
