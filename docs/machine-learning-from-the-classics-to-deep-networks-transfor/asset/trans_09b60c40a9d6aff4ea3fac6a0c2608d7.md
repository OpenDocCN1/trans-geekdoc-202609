

现在让我们考虑以下恒等式：

$$p(x) \equiv \int_0^{p(x)} 1 \, dx = \int_{-\infty}^{+\infty} \chi_{[0, p(x)]}(u) \, du$$

其中 $\chi_{[0, p(x)]}(\cdot)$ 是我们熟悉的区间 $[0, p(x)]$ 上的特征函数，即

$$
\chi_{[0, p(x)]}(u) = \begin{cases}
1, & \quad 0 \leqslant u \leqslant p(x), \\
0, & \quad \text{其他情况}。
\end{cases}
$$

对比公式 [(14.21)](#Chp014_717-754_B9780443292385000202.xhtml#deq35) 和 [(14.22)](#Chp014_717-754_B9780443292385000202.xhtml#deq36)，结果表明 $\chi_{[0, p(x)]}(u)$ 可以解释为定义在集合

$$\mathcal{A} = \{(x, u) : x \in \mathbb{R}, 0 \le u \le p(x)\}$$

上的二元组 $(x, u)$ 的联合 PDF。

