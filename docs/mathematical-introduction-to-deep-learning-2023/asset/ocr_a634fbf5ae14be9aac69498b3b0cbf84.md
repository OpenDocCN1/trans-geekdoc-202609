$U \in\{V \subseteq \mathbb{R}^{\mathfrak{d}}$: $V$ is open$\}$, $x \in S$, $\vartheta \in U$ with $(U \cup \varnothing \to \ell(\vartheta, x) \in \mathbb{R}) \in C^{1}(U, \mathbb{R})$ that

$$\vartheta^{\prime} \vartheta(\vartheta, x)=(\nabla \ell^{\vartheta^{\prime}})(\vartheta, x) \text{.} \qquad(7.143)$$

Then we say that $\Theta$ is the bias-adjusted RMSprop **SGD** process on $((\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S}))$ for the loss function $\ell$ with generalized gradient $\vartheta^{\prime}$, learning rates $(\gamma_{n})_{n \in \mathbb{N}}$, batch sizes $(J_{n})_{n \in \mathbb{N}}$, second moment decay factors $(\beta_{n})_{n \in \mathbb{N}}$, regularizing factor $\varepsilon$, initial value $\xi$, and data $(X_{n, j})_{(n, j) \in\{k, \ell\} \times \{j: 1 \leq J_{k}\}}$ (we say that $\Theta$ is the bias-adjusted RMSprop **SGD** process for the loss function $\ell$ with learning rates $(\gamma_{n})_{n \in \mathbb{N}}$, batch sizes $(J_{n})_{n \in \mathbb{N}}$, second moment decay factors $(\beta_{n})_{n \in \mathbb{N}}$, regularizing factor $\varepsilon$, initial value $\xi$, and data $(X_{n, j})_{(n, j) \in\{k, \ell\} \times \{j: 1 \leq J_{k}\}}$ if and only if it holds that $\Theta=(\Theta^{(1)}, \ldots, \Theta^{(\mathfrak{d})}): \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathfrak{d}}$ is the function from $\mathbb{N}_{0} \times \Omega$ to $\mathbb{R}^{\mathfrak{d}}$ which satisfies that there exists $\mathbb{M}=(\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathfrak{d})}): \mathbb{N}_{0} \times \Omega \rightarrow \mathbb{R}^{\mathfrak{d}}$ such that for all $n \in \mathbb{N}$, $i \in\{1,2, \ldots, \mathfrak{d}\}$ it holds that

$$\Theta_{0} \equiv \xi \text{, } \mathbb{M}_{0} \equiv 0 \text{,} \qquad \qquad \qquad(7.144)$$

$$\mathbb{M}_{n}^{(i)} = \beta_{n} \mathbb{M}_{n-1}^{(i)} + \left(1 - \beta_{n}\right)\left[\frac{1}{J_{n}} \sum_{j = 1}^{J_{n}} \vartheta_{i}(\Theta_{n-1}, X_{n, j})\right]^{2} \text{,} \qquad \qquad(7.145)$$

and $\Theta_{n}^{(i)} = \Theta_{n-1}^{(i)} - \gamma_{n}\left[\varepsilon + \left[\left(\frac{\mathbb{M}_{n}^{(i)}}{(1 - \prod_{l = 1}^{n} \beta_{l})}\right)\right]^{1/2}\right]^{-1}\left[\frac{1}{J_{n}} \sum_{j = 1}^{J_{n}} \vartheta_{i}(\Theta_{n-1}, X_{n, j})\right]$ . $\qquad(7.146)$

An implementation in **PYTORCH** of the bias-adjusted RMSprop **SGD** optimization method as described in Definition **7.7.3** above is given in Source code **7.9**.

```
```python
import torch
import torch.nn as nn
import numpy as np

net = nn.Sequential(
    nn.Linear(1, 200), nn.ReLU(), nn.Linear(200, 1)
)

M = 1000

X = torch.rand((M, 1)) * 4 * np.pi - 2 * np.pi
Y = torch.sin(X)

J = 64

N = 150000

loss = nn.MSELoss()
lr = 0.001
beta = 0.9
eps = 1e-10
adj = 1
```
```