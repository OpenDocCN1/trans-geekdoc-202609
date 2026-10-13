
## 概率消息传递公式

$$
\mu_{V_n \rightarrow S_n}(\mathbf{x}_n) = \sum_{\mathbf{x}_{n-1}} \mu_{V_{n-1} \rightarrow S_{n-1}}(\mathbf{x}_{n-1}) P(\mathbf{x}_n | \mathbf{x}_{n-1}) p(\mathbf{y}_n | \mathbf{x}_n)
$$

![Equation](images/B9780443292385000226/si236.png) (16.39)

初始条件为：

$$
\mu_{V_1 \rightarrow S_1}(\mathbf{x}_1) = P(\mathbf{x}_1) p(\mathbf{y}_1 | \mathbf{x}_1)
$$

![Equation](images/B9780443292385000226/si237.png) (16.40)

在 HMM 文献中，通常使用“alpha”符号表示交换的消息，即：

$$
\alpha(\mathbf{x}_n) := \mu_{V_n \rightarrow S_n}(\mathbf{x}_n)
$$

![Equation](images/B9780443292385000226/si238.png) (16.41)

如果考虑消息传递在节点 $V_n$ 处终止，则根据公式 [(16.7)](#Chp016_805-853_B9780443292385000226.xhtml#deq9)，并考虑到变量 $\mathbf{y}_1, \dots, \mathbf{y}_n$ 被聚类到观测值（回顾公式 [(15.44)](#Chp015_755-803_B9780443292385000214.xhtml) 后的相关注释），可以很容易地看出：

$$
\alpha(\mathbf{x}_n) = p(\mathbf{y}_1, \mathbf{y}_2, \dots, \mathbf{y}_n, \mathbf{x}_n)
$$

![Equation](images/B9780443292385000226/si241.png) (16.42)
