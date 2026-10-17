
$$
\begin{aligned}
\mathbf{x}'_l(t) &= \mathbf{x}_l(t) + r_0 \mathbf{v}_l(t), \\
\mathbf{x}'_w(t) &= \mathbf{x}_w(t) + r_0 \mathbf{v}_w(t),
\end{aligned}
\tag{3.10}
$$

随后落选粒子被更新为：

$$
\begin{aligned}
\Delta'(t) &= \mathbf{x}'_w(t) - \mathbf{x}'_l(t), \\
\mathbf{v}_l(t+1) &= r_0 \mathbf{v}_l(t) + r_1 \Delta'(t), \\
\mathbf{x}_l(t+1) &= \mathbf{x}_l(t) + \mathbf{v}_l(t+1).
\end{aligned}
\tag{3.11}
$$

然而，在执行公式 `(3.10)` 后，两个粒子的决策变量发生了变化，这意味着 $\mathbf{x}'_l$ 可能会比 $\mathbf{x}'_w$ 更好，因此它们应该被重新评估。为了避免额外的函数评估，上述公式可以写为

(3.12) ![`images/c03-math-0012.png`](images/c03-math-0012.png)
