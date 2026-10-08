```
19 lr = 0.02
20 eps = 1e-10
21
22 sum_sq_grad = [p.clone().detach().fill_(eps) for p in net.parameters()]
23
24 for n in range(N):
25     indices = torch.randint(0, M, (J,))
26
27     x = X[indices]
28     y = Y[indices]
29
30     net.zero_grad()
31
32     loss_val = loss(net(x), y)
33     loss_val.backward()
34
35     with torch.no_grad():
36         for a, p in zip(sum_sq_grad, net.parameters()):
37             a.add_(p.grad * p.grad)
38             p.sub_(lr * a.rsqrt() * p.grad)
39
40     if n % 1000 == 0:
41         with torch.no_grad():
42             x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
43             y = torch.sin(x)
44             loss_val = loss(net(x), y)
45             print(f"Iteration: {n+1}, Loss: {loss_val}")
```

Source code 7.7 (*code/optimization_methods/adagrad.py*): PYTHON code implementing the Adagrad SGD optimization method in PyTorch.

# **7.7 Root mean square propagation SGD optimization (RMSPROP)**

In this section we introduce the stochastic version of the RMSprop GD optimization method from Section 6.6 (cf. Hinton et al. \[199\]).

**Definition 7.7.1 (RMSprop SGD optimization method).** Let $\mathbf{d} \in \mathbb{N}$, $(\gamma_{n})_{n \in \mathbb{N}} \subseteq [0, \infty)$, $(J_{n})_{n \in \mathbb{N}} \subseteq \{ 0 \}$, $(\beta_{n})_{n \in \mathbb{N}} \subseteq [0, 1]$, $\varepsilon \in (0, \infty)$, let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $(S, \mathcal{S})$ be a measurable space, let $\xi: \Omega \rightarrow \mathbb{R}^{d}$ be a random variable, for every $n \in \mathbb{N}$, $j \in \{ 1, 2, \ldots, J_{n} \}$ let $X_{n,j}: \Omega \rightarrow S$ be a random variable, and let $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{d} \times S}: \mathbb{R}^{d} \times S \rightarrow \mathbb{R}$ and $\mathbf{g} = (\mathbf{g}_{1}, \ldots, \mathbf{g}_{d}): \mathbb{R}^{d} \times S \rightarrow \mathbb{R}^{d}$ satisfy for all $U \in \{ V \subseteq \mathbb{R}^{d}: V$ is open$\}$, $x \in S$, $\theta \in U$