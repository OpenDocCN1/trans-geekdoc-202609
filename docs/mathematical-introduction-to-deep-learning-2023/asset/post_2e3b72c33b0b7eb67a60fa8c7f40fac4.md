
```python
delta = 0.9
eps = 1e-10

moments = [p.clone().detach().zero_() for p in net.parameters()]
Delta = [p.clone().detach().zero_() for p in net.parameters()]

for n in range(N):
    indices = torch.randint(0, M, (j,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    with torch.no_grad():
        for m, D, p in zip(moments, Delta, net.parameters()):
            m.mul_(beta)
            m.add_((1 - beta) * p.grad * p.grad)
            inc = ((eps + D) / (eps + m)).sqrt() * p.grad
            p.sub_(inc)
            D.mul_(delta)
            D.add_((1 - delta) * inc * inc)

    if n % 1000 == 0:
        with torch.no_grad():
            x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            print(f"Iteration: {n+1}, Loss: {loss_val}")
```

Source code 7.10 (code/optimization_methods/adadelta.py): Python code implementing the Adadelta SGD optimization method in PyTorch

## 7.9 Adaptive moment estimation SGD optimization (Adam)

In this section we introduce the stochastic version of the Adam GD optimization method from Section 6.8 (cf. Kingma & Ba [247]).

Definition 7.9.1 (Adam SGD optimization method). Let $n \in \mathbb{N}$, $(\gamma_n)_{n\in\mathbb{N}} \subseteq [0, \infty)$, $(J_n)_{n\in\mathbb{N}} \subseteq \mathbb{N}$, $(\alpha_n)_{n\in\mathbb{N}} \subseteq [0, 1]$, $(\beta_n)_{n\in\mathbb{N}} \subseteq [0, 1]$, $\varepsilon \in (0, \infty)$ satisfy

$$ \max\{\alpha_1, \beta_1\} < 1, \tag{7.152} $$

let $(\Omega, \mathcal{F}, \mathbb{P})$ be a probability space, let $(S, \mathcal{S})$ be a measurable space, let $\xi: \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ be a random variable, for every $n \in \mathbb{N}, j \in \{1, 2, \ldots, J_n\}$ let $X_{n,j}: \Omega \rightarrow S$ be a random variable, and let $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^{\mathcal{D}} \times S}: \mathbb{R}^{\mathcal{D}} \times S \rightarrow \mathbb{R}$ and $\boldsymbol{\mathcal{Q}} = (\boldsymbol{q}_1, \ldots, \boldsymbol{q}_{\mathcal{D}}): \mathbb{R}^{\mathcal{D}} \times S \rightarrow \mathbb{R}^{\mathcal{D}}$ satisfy for all $U \in \{V \subseteq \mathbb{R}^{\mathcal{D}}: V \text{ is open}\}$, $x \in S$, $\theta \in U$ with $(U \ni \partial \ni \ell(\partial, x) \in \mathbb{R}) \in C^1(U, \mathbb{R})$ that

$$ \mathcal{Q}(\theta, x) = \left(\nabla_{q^\ell}\theta\right) \ell(\theta, x). \tag{7.153} $$

Then we say that $\Theta$ is the Adam SGD process on $(\Omega, \mathcal{F}, \mathbb{P}), (S, \mathcal{S})$ for the loss function $\ell$ with generalized gradient $\boldsymbol{q}$, learning rates $(\gamma_n)_{n \in \mathbb{N}}$, batch sizes $(J_n)_{n \in \mathbb{N}}$, momentum decay factors $(\alpha_n)_{n \in \mathbb{N}}$, second moment decay factors $(\beta_n)_{n \in \mathbb{N}}$, regularizing factor $\varepsilon \in (0, \infty)$, initial value $\boldsymbol{\xi}$, and data $(X_{n,j})_{(n,j) \in \{(k,i) \in \mathbb{N}^2: 1 \leq i < j\}}$ (we say that $\Theta$ is the Adam SGD process for the loss function $\ell$ with learning rates $(\gamma_n)_{n \in \mathbb{N}}$, batch sizes $(J_n)_{n \in \mathbb{N}}$, momentum decay factors $(\alpha_n)_{n \in \mathbb{N}}$, second moment decay factors $(\beta_n)_{n \in \mathbb{N}}$, regularizing factor $\varepsilon \in (0, \infty)$, initial value $\boldsymbol{\xi}$, and data $(X_{n,j})_{(n,j) \in \{(k,i) \in \mathbb{N}^2: 1 \leq i < j\}}$ if and only if it holds that $\Theta = (\Theta^{(1)}, \ldots, \Theta^{(\mathcal{D})}): \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ is the function from $\mathbb{N}_0 \times \Omega$ to $\mathbb{R}^{\mathcal{D}}$ that satisfies that there exist $\boldsymbol{m} = (\boldsymbol{m}^{(1)}, \ldots, \boldsymbol{m}^{(\mathcal{D})}): \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ and $\mathbb{M} = (\mathbb{M}^{(1)}, \ldots, \mathbb{M}^{(\mathcal{D})}): \mathbb{N}_0 \times \Omega \rightarrow \mathbb{R}^{\mathcal{D}}$ such that for all $n \in \mathbb{N}$, $i \in \{1, 2, \ldots, \mathcal{D}\}$ it holds that

$$ \Theta_0 = \boldsymbol{\xi}, \quad \quad \boldsymbol{m}_0 = 0, \quad \quad \mathbb{M}_0 = 0, \tag{7.154} $$

$$ \boldsymbol{m}_n = \alpha_n \boldsymbol{m}_{n-1} + (1 - \alpha_n) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} \boldsymbol{q}(\Theta_{n-1}, X_{n,j}) \right], \tag{7.155} $$

$$ \mathbb{M}_n^{(i)} = \beta_n \mathbb{M}_{n-1}^{(i)} + (1 - \beta_n) \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} q_i(\Theta_{n-1}, X_{n,j}) \right]^2, \tag{7.156} $$

$$ \text{and} \qquad \Theta_n^{(i)} = \Theta_{n-1}^{(i)} - \gamma_n \left[ \varepsilon + \left[ \frac{\mathbb{M}_n^{(i)}}{(1 - \prod_{\ell=1}^n \beta_\ell)} \right]^{1/2} \right]^{-1} \left[ \frac{\boldsymbol{m}_n^{(i)}}{(1 - \prod_{\ell=1}^n \alpha_\ell)} \right]. \tag{7.157} $$

Remark 7.9.2. In Kingma & Ba [247] it is proposed to choose

$$ 0.001 = \gamma_1 = \gamma_2 = \ldots, \quad \quad 0.9 = \alpha_1 = \alpha_2 = \ldots, \quad \quad 0.999 = \beta_1 = \beta_2 = \ldots, \tag{7.158} $$

and $10^{-8} = \varepsilon$ as default values for $(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$, $(\alpha_n)_{n \in \mathbb{N}} \subseteq [0, 1]$, $(\beta_n)_{n \in \mathbb{N}} \subseteq [0, 1]$, $\varepsilon \in (0, \infty)$ in Definition 7.9.1.

An implementation in PyTorch of the Adam SGD optimization method as described in Definition 7.9.1 above is given in Source code 7.11. The Adam SGD optimization method as described in Definition 7.9.1 above is also available in PyTorch in the form of the built-in torch.optim.Adam optimizer (which, for applications, is generally much preferable to implementing it from scratch).

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
lr = 0.0001
alpha = 0.9
beta = 0.999
eps = 1e-8
adj = 1.
adj2 = 1.

m = [p.clone().detach().zero_() for p in net.parameters()]
MM = [p.clone().detach().zero_() for p in net.parameters()]

for n in range(N):
    indices = torch.randint(0, M, (J,))

    x = X[indices]
    y = Y[indices]

    net.zero_grad()

    loss_val = loss(net(x), y)
    loss_val.backward()

    with torch.no_grad():
        adj *= alpha
        adj2 *= beta
        for m_p, M_p, p in zip(m, MM, net.parameters()):
            m_p.mul_(alpha)
            m_p.add_((1 - alpha) * p.grad)
            M_p.mul_(beta)
            M_p.add_((1 - beta) * p.grad * p.grad)
            p.sub_(lr * m_p / ((1 - adj) * (eps + (M_p / (1 - adj2)).sqrt() )))

    if n % 1000 == 0:
        with torch.no_grad():
            x = torch.rand((1000, 1)) * 4 * np.pi - 2 * np.pi
            y = torch.sin(x)
            loss_val = loss(net(x), y)
            print(f"Iteration: {n+1}, Loss: {loss_val}")
```

Source code 7.11 (code/optimization_methods/adam.py): Python code implementing the Adam SGD optimization method in PyTorch.

Whereas Source code 7.11 and the other source codes presented in this chapter so far served mostly to elucidate the definitions of the various optimization methods introduced in this chapter by giving example implementations, in Source code 7.12 we demonstrate how an actual machine learning problem might be solved using the built-in functionality of PyTorch. This code trains a neural network with 3 convolutional layers and 2 fully connected layers (with each hidden layer followed by a ReLU activation function) on the MNIST dataset (introduced in Bottou et al. [47]), which consists of 28 × 28 pixel grayscale images of handwritten digits from 0 to 9 and the corresponding labels and is one of the most commonly used benchmarks for training machine learning systems in the literature. Source code 7.12 uses the cross-entropy loss function and the Adam SGD optimization method and outputs a graph showing the progression of the average loss on the training set and on a test set that is not used for training as well as the accuracy of the model’s predictions over the course of the training, see Figure 7.4.

```python
import torch
import torchvision.datasets as datasets
import torchvision.transforms as transforms
import torch.nn as nn
import torch.utils.data as data
import torch.optim as optim
import matplotlib.pyplot as plt
from matplotlib.ticker import ScalarFormatter, NullFormatter

# We use the GPU if available. Otherwise, we use the CPU.
device = torch.device(
    "cuda" if torch.cuda.is_available() else "cpu"
)

# We fix a random seed. This is not necessary for training a
# neural network, but we use it here to ensure that the same
# plot is created on every run.
torch.manual_seed(0)

# The torch.utils.data.Dataset class is an abstraction for a
# collection of instances that has a length and can be indexed
```
