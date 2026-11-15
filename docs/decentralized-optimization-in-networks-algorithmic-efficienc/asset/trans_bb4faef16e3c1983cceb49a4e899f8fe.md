

\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle g_t^i(x_t^j), x_t^j - \bar{x}_t + \bar{x}_t - x_t^i \rangle]\\
\le nK \sum_{t=1}^T \mathbb{E}[||x_t^j - \bar{x}_t||] + K \sum_{t=1}^T \sum_{i=1}^n \mathbb{E}[||x_t^i - \bar{x}_t||].

回顾关于投影算子 \(\Pi_\Omega^\phi(\cdot)\) 的结果，该结果指出对于任何向量 \(u, v \in \mathbb{R}^m\)，不等式 \(||\Pi_\Omega^\phi(u, \alpha) - \Pi_\Omega^\phi(v, \alpha)|| \le \alpha ||u - v||\) 成立，如文献 [21] 所述。因此，对于属于集合 \(\mathcal{V}\) 的任何 \(i\)，

```
\(\mathbb{E}[||x_t^i - \bar{x}_t||] \le \alpha_t \max_{i \in \mathcal{V}} \mathbb{E}[||q_t^i - \bar{q}_t||].\)
```

鉴于 \(\alpha_t = \frac{\alpha_0}{\sqrt{t+1}}\)，可得 \((1/\alpha_T) < \frac{2\sqrt{T}}{\alpha_0}\)，且直到时间 \(T\) 的步长累积和满足 \(\sum_{t=1}^T \alpha_{t-1} \le \sum_{t=1}^T (\frac{\alpha_0}{\sqrt{t}}) \le 2\alpha_0 \sqrt{T}\)。调用引理 6.4，我们可以得出公式 (6.20) 的初始项受到某个界限的限制：

```
\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^j) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i)] \le 4\alpha_0 n K O_1 \sqrt{T}.\quad (6.21)\)
```

值得注意的是，\(\check{x}\) 与 \(x^*\) 之间的距离被 \(\xi D\) 所上界限。因此，公式 (6.20) 的第二个分量限制在一定范围内：

```
\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n f_t^i(\check{x}) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(x^*)] \le \xi T n K D.\quad (6.22)\)
```

注意 \(\nabla \hat{f}_t^i(x) = \mathbb{E}_{\beta_t^i \in \mathbb{S}^m}[\hat{g}_t^i(x)]\)，对所有 \(x \in (1-\xi)\Omega\) 成立。随后，从引理 6.1(a) 和 6.1(b) 的综合断言可以推断：

```
\(\mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n (f_t^i(x_t^i) - f_t^i(\check{x}))]\\
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n (\hat{f}_t^i(x_t^i) - \hat{f}_t^i(\check{x}) + \delta K)]\\
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle \nabla \hat{f}_t^i(x_t^i), \bar{x}_t - \check{x} + x_t^i - \bar{x}_t \rangle] + T n \delta K\\
\le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle \hat{g}_t^i, \bar{x}_t - \check{x} \rangle] + \alpha_0 n m K O_1 \sqrt{T} + T n \delta K\\
= \Theta_1 + \Theta_2 + \alpha_0 n m K O_1 \sqrt{T} + T n \delta K,\quad (6.23)\)
```

其中

```
\(\Theta_1 = \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n \langle \frac{n \hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} (\frac{\nu_{t+1}^i}{n} - \theta_{t+1}^i), \bar{x}_t - \tilde{x} \rangle],\)

\(\Theta_2 = \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n (\langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i - \vartheta_t^i \theta_t^i, \bar{x}_t - \tilde{x} \rangle].\)
```

在假设 6.2 下，可以推断出 \(\|\bar{x}_t - x^*\| \le D\)。随后，从引理 6.1(c) 和引理 6.2 可以推出：

```
\(\Theta_1 \le \mathbb{E}[\sum_{t=1}^T \sum_{i=1}^n || \frac{n \hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} || \frac{\nu_{t+1}^i}{n} || \theta_{t+1}^i - \theta_{t+1}^i || || \bar{x}_t - \tilde{x} ||]\)

\(\le n^2 \omega m K D Q \sum_{t=1}^T \lambda^{T-t-1} \le \frac{n^2 \omega m K D Q}{1 - \lambda}.\) (6.24)
```

接下来，我们继续分析项 \(\Theta_2\)。鉴于 \(\vartheta_t^i\) 服从分布 \(\mathcal{L}(0, b_t)\)，可知对于集合 \(\mathcal{V}\) 中的所有 \(i\) 以及所有 \(t \ge 1\)，\(\vartheta_t^i\) 的期望值均为零。因此，

```
\(\Theta_2 = \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \bar{x}_t \rangle]\)

\(- \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \tilde{x} \rangle].\) (6.25)
```

接下来，我们深入考察公式 (6.25) 右侧部分的第二个分量。该特定项可追溯至公式 (6.13)，

```
\(\sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \tilde{x} \rangle = \langle \bar{q}_{T+1} - \bar{q}_1, \tilde{x} \rangle.\) (6.26)
```

观察到不等式 \(\alpha_t \le \alpha_{t-1}\)，我们可以得出 \(\mathcal{H}_\Omega^\phi(-\bar{q}_{t+1}, \alpha_t)\) 小于或等于 \(\mathcal{H}_\Omega^\phi(-\bar{q}_{t+1}, \alpha_{t-1})\)。随后，应用引理 6.3，我们得到

```
\(\mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{t+1}, \alpha_t)\)

\(\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_t - \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i), \alpha_{t-1})\)

\(\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_t, \alpha_{t-1}) - \langle \bar{x}_t, \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i) \rangle\)

+ \frac{1}{2}\alpha_{t-1}|| \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2.\quad (6.27)
```

通过重组各项，我们得到

```
\langle \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i), \bar{x}_t \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_t, \alpha_{t-1}) - \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{t+1}, \alpha_t)
+ \frac{1}{2}\alpha_{t-1}|| \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2,\quad (6.28)
```

通过对所有 \(t\) 的值汇总公式 (6.28)，我们还得出以下结果：

```
\sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i, \bar{x}_t \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) - \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{T+1}, \alpha_T)
+ \frac{1}{2} \sum_{t=1}^T \alpha_{t-1}|| \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2.\quad (6.29)
```

此外，利用 \(\bar{x}_t\) 和 \(\mathcal{H}_\Omega^\phi(\cdot)\) 的概念，可以推断出 \(\mathcal{H}_\Omega^\phi(-\bar{q}_{T+1}, \alpha_T) = -\langle \bar{q}_{T+1}, \bar{x}_{T+1} \rangle - (1/\alpha_T)\phi(\bar{x}_{T+1})\)。因此，结合 (6.26) 和 (6.29) 得到

```
\sum_{t=1}^T \sum_{i=1}^n \langle \frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i, \bar{x}_t - \tilde{x} \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) - \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_{T+1}, \alpha_T)
+ \frac{1}{2} \sum_{t=1}^T \alpha_{t-1} || \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2
- \langle \bar{q}_{T+1}, \tilde{x} \rangle + \langle \bar{q}_1, \tilde{x} \rangle
\le \mathcal{H}_{(1-\xi)\Omega}^\phi(-\bar{q}_1, \alpha_0) + \langle \bar{q}_1, \tilde{x} \rangle + \langle \bar{q}_{T+1}, \bar{x}_{T+1} - \tilde{x} \rangle
+ \frac{\phi(\bar{x}_{T+1})}{\alpha_T} + \frac{1}{2} \sum_{t=1}^T \alpha_{t-1} || \sum_{i=1}^n (\frac{\hat{\mathcal{G}}_t^i}{\nu_{t+1}^i}\theta_{t+1}^i + \vartheta_t^i\theta_t^i) ||^2.\quad (6.30)
```

让我们定义 \(\psi(x)\) 为 \(\bar{q}_{T+1}\) 与 \(x\) 的内积加上缩放函数 \(\phi(x)/\alpha_T\)，并认识到 \(\bar{x}_{T+1}\) 是相对于函数 \(\phi\) 和参数 \(\alpha_T\)，\(\bar{q}_{T+1}\) 在集合 \(\Omega\) 上的投影，记为 \(\Pi_{\Omega}^{\phi}(\bar{q}_{T+1}, \alpha_T)\)。鉴于 \(\phi(x)\) 具有 1-强凸性，这意味着 \(\psi(x)\) 表现出模数为 \(1/\alpha_T\) 的强凸性。根据文献 [43] 中的引理 4，我们可以推断出

\((\bar{q}_{T+1}, \bar{x}_{T+1} - \tilde{x}) + \frac{\phi(\bar{x}_{T+1})}{\alpha_T} \le \frac{\phi(\tilde{x})}{\alpha_T}.\) (6.31)

此外，利用 Cauchy–Schwarz 不等式，我们可以推断出

```
\(\mathbb{E}[|| \sum_{i=1}^n ( \frac{\hat{g}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i ) ||^2]\)
\(\le \mathbb{E}[|| \sum_{i=1}^n || \frac{\hat{g}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i ||^2]\)
\(\le 2 \mathbb{E}[ \sum_{i=1}^n || \frac{\hat{g}_t^i}{\nu_{t+1}^i} ||^2 || \theta_{t+1}^i ||^2 + \sum_{i=1}^n || \vartheta_t^i ||^2 || \theta_t^i ||^2 ]\)
\(\le 2nm^2 K^2 \omega^2 + 4nm b_{\max}^2 = O_2.\) (6.32)
```

因此，从公式 (6.25) 和 (6.29)-(6.31) 可以推出：

```
\(\Theta_2 = \mathbb{E}[n \sum_{t=1}^T \sum_{i=1}^n ( \frac{\hat{g}_t^i}{\nu_{t+1}^i} \theta_{t+1}^i + \vartheta_t^i \theta_t^i, \bar{x}_t - \tilde{x} ) ]\)
\(\le n \mathcal{H}_{(1-\xi)\Omega}^{\phi}(-\bar{q}_1, \alpha_0) + n \langle \bar{q}_1, \tilde{x} \rangle + n( \frac{2\phi(\tilde{x})}{\alpha_0} + \alpha_0 O_2 )\sqrt{T}.\) (6.33)
```

引用 (6.24) 和 (6.33)，(6.20) 的第三个分量受到以下界限的限制：

```
\(\mathbb{E}[ \sum_{t=1}^T \sum_{i=1}^n f_t^i(x_t^i) - \sum_{t=1}^T \sum_{i=1}^n f_t^i(\tilde{x}) ]\)
\(\le O_3 + ( \frac{2n\phi(\tilde{x})}{\alpha_0} + \alpha_0 n O_2 + 2\alpha_0 nm K O_1 )\sqrt{T} + Tn\delta K,\) (6.34)
```

其中

\(O_3 = \frac{n^2 \omega m K D Q}{1 - \lambda} + n \mathcal{H}_{(1-\xi)\Omega}^{\phi}(-\bar{q}_1, \alpha_0) + n \langle \bar{q}_1, \tilde{x} \rangle.\)

因此，从 (6.21)、(6.22) 和 (6.34) 可得：

```
\(\bar{R}_T^j \le (2(2+m)\alpha_0 n K O_1 + \frac{2n\phi(\tilde{x})}{\alpha_0} + \alpha_0 n O_2 )\sqrt{T}\)
\(+ O_3 + Tn\delta K + \xi Tn K D,\)
```

这便是预期的结果。

