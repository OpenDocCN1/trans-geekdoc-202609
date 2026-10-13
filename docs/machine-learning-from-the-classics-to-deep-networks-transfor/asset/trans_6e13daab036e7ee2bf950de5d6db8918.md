
$P(x_{1}) = \frac{1}{Z}\sum\limits_{x_{i}:i \neq 1,l - 1,l}\ \prod\limits_{i = 1}^{l - 3}\psi_{i,i + 1}(x_{i},x_{i + 1})\sum\limits_{x_{l - 1}}\psi_{l - 2,l - 1}(x_{l - 2},x_{l - 1})\mu_{b}(x_{l - 1})$

![Equation](images/B9780443292385000214/si236.png)

*   其中该求和也涉及 $K^{2}$ 项。

![Equation](images/B9780443292385000214/si232.png)

我们现在准备好定义一般递归为

![](images/B9780443292385000214/fx006.jpg)

其反复应用导致

$\mu_{b}(x_{1}) = \sum\limits_{x_{2}}\psi_{1,2}(x_{1},x_{2})\mu_{b}(x_{2})$

![Equation](images/B9780443292385000214/si237.png)

最后

$P(x_{1}) = \frac{1}{Z}\mu_{b}(x_{1}).$

![Equation](images/B9780443292385000214/si238.png) (15.40)

该系列递归在 [图 15.22](#Chp015_755-803_B9780443292385000214.xhtml#f0120) 中进行了说明。

![Figure 15.21 An undirected chain graph with l nodes. There are l − 1 cliques consisting of pairs of nodes.](images/B9780443292385000214/gr021.jpg)

[图 15.21](#Chp015_755-803_B9780443292385000214.xhtml#cf0720) 一个包含 $l$ 个节点的无向链图。存在 $l - 1$ 个由节点对组成的团。

![Figure 15.22 To compute P(x1), starting from the last node, xl, each node (a) receives a message and (b) processes it locally via sum and product operations, which produces a new message; and (c) the latter is passed backward, to the node on its left. We have assumed that μb(xl)=1.](images/B9780443292385000214/gr022.jpg)

图 15.22 为计算 $P(x_{1})$，从最后一个节点 $x_{l}$ 开始，每个节点 (a) 接收一条消息并 (b) 通过求和与乘积运算在局部对其进行处理，从而产生一条新消息；(c) 后者被向后传递给其左侧的节点。我们假设 $\mu_{b}(x_{l})=1$。
