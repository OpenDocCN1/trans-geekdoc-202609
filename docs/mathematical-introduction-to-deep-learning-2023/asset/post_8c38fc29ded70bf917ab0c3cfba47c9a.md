
## 7.5. SGD optimization with Nesterov momentum

```python
14 J = 64
15
16 N = 150000
17
18 loss = nn.MSELoss()
19 lr = 0.003
20 alpha = 0.999
21
22 m = [p.clone().detach().zero_() for p in net.parameters()]
23
24 for n in range(N):
25     indices = torch.randint(0, M, (J,))
26
27     x = X[indices]
28     y = Y[indices]
29
30     net.zero_grad()
31
32     # Remember the original parameters
33     params = [p.clone().detach() for p in net.parameters()]
34
35     for p, m_p in zip(params, m):
36         p.sub_(lr * alpha * m_p)
37
38     # Compute the loss
39     loss_val = loss(net(x), y)
40     # Compute the gradients with respect to the parameters
41     loss_val.backward()
42
43     with torch.no_grad():
44         for p, m_p, q in zip(net.parameters(), m, params):
45             m_p.mul_(alpha)
46             m_p.add_((1 - alpha) * p.grad)
47             q.sub_(lr * m_p)
48             p.copy_(q)
49
50     if n % 1000 == 0:
51         with torch.no_grad():
52             x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
53             y = torch.sin(x)
54             loss_val = loss(net(x), y)
55             print(f"Iteration: {n+1}, Loss: {loss_val}")
```

Source code 7.6 (code/optimization_methods/nesterov_sgd.py): PYTHON code implementing the Nesterov accelerated SGD optimization method in PyTorch

### 7.5.1 Simplified SGD optimization with Nesterov momentum

For reasons of algorithmic simplicity, in several deep learning libraries including PyTorch (see [338] and cf., for instance, [31, Section 3.5]) optimization with Nesterov momentum is not implemented such that it precisely corresponds to Definition 7.5.1. Rather, an alternative definition for Nesterov accelerated SGD optimization is used, which we present in Definition 7.5.3. The next result illustrates the connection between the original notion of Nesterov accelerated SGD optimization in Definition 7.5.1 and the alternative notion of Nesterov accelerated SGD optimization in Definition 7.5.3 employed by PyTorch (compare (7.121)–(7.123) with (7.134)–(7.136)).

**Lemma 7.5.2 (Relations between Definition 7.5.1 and Definition 7.5.3).** Let $d \in \mathbb{N}$, $(\gamma_n)_{n\in\mathbb{N}} \subseteq [0, \infty)$, $(J_n)_{n\in\mathbb{N}} \subseteq \mathbb{N}$, $(\alpha_n)_{n\in\mathbb{N}_0} \subseteq [0, 1)$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $(S, \mathcal{S})$ be a measurable space, let $X_{n, j}: \Omega \to \mathbb{R}^d$ be a random variable, for every $n \in \mathbb{N}$, $j \in \{1, 2, \dots, J_n\}$ let $X_{n, j}: \Omega \to S$ be a random variable, let $\ell = (\ell(\theta, x))_{(\theta,x)\in\mathbb{R}^d\times S}: \mathbb{R}^d\times S \to \mathbb{R}$ and $\mathbf{g} = (\mathbf{g}_1, \dots, \mathbf{g}_d): \mathbb{R}^d\times S \to \mathbb{R}^d$ satisfy for all $x \in S$, $\theta \in \{v \in \mathbb{R}^d: \ell(v, x) \text{ is differentiable at } v\}$ that $\mathbf{g}(\theta, x) = (\nabla_\theta \ell)(\theta, x)$, (7.120) $\psi: \mathbb{N}_0 \times \Omega \to \mathbb{R}^d$ and $\mathbf{m}: \mathbb{N}_0 \times \Omega \to \mathbb{R}^d$ satisfy for all $n \in \mathbb{N}$ that $\psi_0 = \xi$, $\mathbf{m}_0 = 0$, (7.121)
$$
\mathbf{m}_n = \alpha_n \mathbf{m}_{n-1} + \frac{1}{J_n} \sum_{j=1}^{J_n} \mathbf{g}\left(\psi_{n-1} - \gamma_n \alpha_n \mathbf{m}_{n-1}, X_{n, j}\right), \quad (7.122)
$$
and
$$
\psi_n = \psi_{n-1} - \gamma_n \mathbf{m}_n, \quad (7.123)
$$
let $(\beta_n)_{n\in\mathbb{N}} \subseteq [0, \infty)$, $(\delta_n)_{n\in\mathbb{N}} \subseteq [0, \infty)$ satisfy for all $n \in \mathbb{N}$ that $\beta_n = \frac{\alpha_n(1 - \alpha_{n-1})}{1 - \alpha_n} =: \alpha_n$, and $\delta_n = (1 - \alpha_n)\gamma_n$, (7.124) and let $\Psi: \mathbb{N}_0 \times \Omega \to \mathbb{R}^d$ and $\mathbf{m}: \mathbb{N}_0 \times \Omega \to \mathbb{R}^d$ satisfy for all $n \in \mathbb{N}_0$ that $\mathbf{m}_n = \mathbf{m}_n$ with $\alpha_n$ and $\Psi_n = \psi_n - \gamma_{n+1}\alpha_{n+1}\mathbf{m}_n$. (7.125)

Then (i) it holds that $\psi$ is the Nesterov accelerated SGD process on $((\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S}))$ for the loss function $\ell$ with generalized gradient $\mathbf{g}$, learning rates $(\gamma_n)_{n\in\mathbb{N}}$, batch sizes $(J_n)_{n\in\mathbb{N}}$, momentum decay factors $(\alpha_n)_{n\in\mathbb{N}}$, initial value $\xi$, and data $(X_{n, j})_{(n, j)\in\{ (k, l) \in \mathbb{N}^2 \times \{1 \leq j \leq k\} \}$, and

(ii) it holds for all $n \in \mathbb{N}$ that
$$
\Psi_0 = \xi, \qquad \mathbf{m}_0 = 0, \tag{7.126}
$$
$$
\mathbf{m}_n = \beta_n \mathbf{m}_{n-1} + \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right), \tag{7.127}
$$
and
$$
\Psi_n = \Psi_{n-1} - \delta_{n+1} \beta_{n+1} \mathbf{m}_n - \delta_n \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right) \right]. \tag{7.128}
$$

**Proof of Lemma 7.5.2.** Note that (7.121), (7.122), and (7.123) show item (i). Observe that (7.122) and (7.125) imply that for all $n \in \mathbb{N}$ it holds that
$$
\begin{aligned}
\mathbf{m}_n &= \frac{\alpha_n \mathbf{m}_{n-1}}{1 - \alpha_n} + \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right) \\
&= \frac{\alpha_n (1 - \alpha_{n-1}) \mathbf{m}_{n-1}}{1 - \alpha_n} + \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right). \tag{7.129}
\end{aligned}
$$
This and (7.124) demonstrate that for all $n \in \mathbb{N}$ it holds that
$$
\mathbf{m}_n = \beta_n \mathbf{m}_{n-1} + \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right). \tag{7.130}
$$
Furthermore, note that (7.122), (7.123), and (7.125) ensure that for all $n \in \mathbb{N}$ it holds that
$$
\begin{aligned}
\Psi_n &= \Theta_n - \gamma_{n+1} \alpha_{n+1} \mathbf{m}_n \\
&= \Theta_{n-1} - \gamma_n \mathbf{m}_n - \gamma_{n+1} \alpha_{n+1} \mathbf{m}_n \\
&= \Psi_{n-1} + \gamma_n \alpha_n \mathbf{m}_{n-1} - \gamma_n \mathbf{m}_n - \gamma_{n+1} \alpha_{n+1} \mathbf{m}_n \\
&= \Psi_{n-1} + \gamma_n \alpha_n \mathbf{m}_{n-1} - \gamma_n \alpha_n \mathbf{m}_{n-1} - \gamma_n (1 - \alpha_n) \left[\frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right)\right] \\
&\quad - \gamma_{n+1} \alpha_{n+1} \mathbf{m}_n \\
&= \Psi_{n-1} - \gamma_{n+1} \alpha_{n+1} \mathbf{m}_n - \gamma_n (1 - \alpha_n) \left[\frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right)\right] \\
&= \Psi_{n-1} - \gamma_{n+1} \alpha_{n+1} \left[(1 - \alpha_n) \mathbf{m}_n - \gamma_n (1 - \alpha_n) \left[\frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g}\left(\Psi_{n-1}, X_{n, j}\right)\right]\right]. \tag{7.131}
\end{aligned}
$$
This and $(7.124)$ establish that for all $n \in \mathbb{N}$ it holds that
$$
\begin{align*}
\Psi_n &= \Psi_{n-1} - \frac{\delta_{n+1}\alpha_{n+1}(1-\alpha_n)\boldsymbol{m}_n}{1-\alpha_{n+1}} - \delta_n \left[ \frac{1}{J_n}\sum_{j=1}^{J_n} \boldsymbol{\mathcal{G}}\left(\Psi_{n-1}, X_{n, j}\right) \right] \\
&= \Psi_{n-1} - \delta_{n+1} \beta_{n+1} \boldsymbol{m}_n - \delta_n \left[ \frac{1}{J_n}\sum_{j=1}^{J_n} \boldsymbol{\mathcal{G}}\left(\Psi_{n-1}, X_{n, j}\right) \right].
\end{align*}
$$
Combining this with $(7.121)$, $(7.125)$, and $(7.130)$ proves item $(ii)$. The proof of Lemma $7.5.2$ is thus complete.

**Definition 7.5.3 (Simplified Nesterov accelerated SGD optimization method).** Let $\boldsymbol{d} \in \mathbb{N}$, $(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$, $(J_n)_{n \in \mathbb{N}} \subseteq \mathbb{N}$, $(\alpha_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $(S, \mathcal{S})$ be a measurable space, let $\xi: \Omega \rightarrow \mathbb{R}^d$ be a random variable, for every $n \in \mathbb{N}$, $j \in \{1, 2, \dots, J_n\}$, let $X_{n,j}: \Omega \rightarrow S$ be a random variable, and let $\mathcal{L} = (\ell (\theta, x))_{(\theta, x) \in \mathbb{R}^d \times S}: \mathbb{R}^d \times S \rightarrow \mathbb{R}$ and $\boldsymbol{g} = (\boldsymbol{g}_1, \cdots, \boldsymbol{g}_d): \mathbb{R}^d \times S \rightarrow \mathbb{R}^d$ satisfy for all $x \in S$, $\theta \in \{v \in \mathbb{R}^d: \ell (\theta, x)\) is differentiable at \(v\}$ that
$$
\boldsymbol{g} (\theta, x) = (\nabla _ {\boldsymbol{\theta}} \ell) (\theta, x). \quad (7.133)
$$
Then we say that $\Theta$ is the simplified Nesterov accelerated SGD process on $((\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S}))$ for the loss function $\ell$ with generalized gradient $\boldsymbol{g}$, learning rates $(\gamma_{n})_{n \in \mathbb{N}}$, batch sizes $(J_{n})_{n \in \mathbb{N}}$, momentum decay factors $(\alpha_{n})_{n \in \mathbb{N}}$, initial value $\xi$, and data $(X_{n,j})_{(n,j) \in \{ (k,l) \in \mathbb{N}^{2}: l \leqslant J_{k} \}}$ (we say that $\Theta$ is the simplified Nesterov accelerated SGD process for the loss function $\ell$ with learning rates $(\gamma_{n})_{n \in \mathbb{N}}$, batch sizes $(J_{n})_{n \in \mathbb{N}}$, momentum decay rates $(\alpha_{n})_{n \in \mathbb{N}}$, initial value $\xi$, and data $(X_{n,j})_{(n,j) \in \{ (k,l) \in \mathbb{N}^{2}: l \leqslant J_{k} \}}$ if and only if $\Theta: \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{d}$ is the function from $\mathbb{N}_{0} \times \Omega$ to $\mathbb{R}^{d}$ which satisfies that there exists $\boldsymbol{m}: \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{d}$ such that for all $n \in \mathbb{N}$ it holds that
$$
\Theta_0 = \xi, \quad \boldsymbol{m}_0 = \mathbf{0}, \quad (7.134)
$$
$$
\boldsymbol{m}_n = \alpha_n \boldsymbol{m}_{n-1} + \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g} \left( \Theta_{n-1}, X_{n, j} \right), \quad (7.135)
$$
and
$$
\Theta_n = \Theta_{n-1} - \gamma_n \alpha_n \boldsymbol{m}_n - \gamma_n \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{g} \left( \Theta_{n-1}, X_{n, j} \right) \right]. \quad (7.136)
$$

The simplified Nesterov accelerated SGD optimization method as described in Definition $7.5.3$ is implemented in PyTorch in the form of the `torch.optim.SGD` optimizer with the `nesterov=True` option.

## 7.6 Adagrad SGD optimization (Adagrad)

In this section we introduce the stochastic version of the Adagrad GD optimization method from Section $6.5$ (cf. Duchi et al. [117]).
