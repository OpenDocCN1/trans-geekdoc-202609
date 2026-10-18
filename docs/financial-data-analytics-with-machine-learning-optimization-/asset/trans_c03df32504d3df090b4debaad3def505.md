

状态 $s_j$ 被称为可从状态 $s_i$ *访问*，记作 $s_i \to s_j$，如果存在某个整数 $n \ge 0$ 使得 $p_{i,j}^{(n)} > 0$。两个状态 $s_i$ 和 $s_j$ 被称为 *通信*（记作 $s_i \leftrightarrow s_j$），如果它们可以相互访问。可以很容易地建立，*通信*是一个 *等价关系*：(i) $s_i \leftrightarrow s_i$（自反性）；(ii) 如果 $s_i \leftrightarrow s_j$，则 $s_j \leftrightarrow s_i$（对称性）；以及 (iii) 如果 $s_i \leftrightarrow s_j$ 且 $s_j \leftrightarrow s_k$，则 $s_i \leftrightarrow s_k$（传递性）。结果，马尔可夫链的状态可以被划分为不相交的通信状态类，使得两个状态 $s_i$ 和 $s_j$ 属于同一类当且仅当 $s_i \leftrightarrow s_j$。如果整个状态空间形成一个单一的通信类，即每个状态都与其他每个状态通信，则该马尔可夫链被称为 *不可约*。马尔可夫链正则的一个充分（但非必要）条件是它是不可约的。

接下来，我们定义马尔可夫链状态 $i$ 的 *周期* 如下：

$$d(i) = \begin{cases} \gcd\{n \ge 1 : p_{i,i}^{(n)} > 0\}, & \text{if } p_{i,i}^{(n)} > 0 \text{ for some } n \ge 1; \\ 0, & \text{if } p_{i,i}^{(n)} = 0, \text{ for all } n \ge 1. \end{cases}$$

其中 gcd 表示一组数的最大公约数。以下是周期的几个性质：

1. 如果 $s_i \leftrightarrow s_j$，则 $d(i) = d(j)$。即，周期在每个等价类中是常数。

