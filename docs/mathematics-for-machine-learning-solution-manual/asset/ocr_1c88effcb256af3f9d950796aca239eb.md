We get the latter result by defining $y = A x$, such that

$y_i = \sum_j A_{ij} x_j \implies \frac{\partial y_i}{\partial x_k} = A_{ik} \implies \frac{\partial y_i}{\partial x} = [A_{i1}, ..., A_{iN}] \in \mathbb{R}^{1 \times N}$

$\implies \frac{\partial y}{\partial x} = A$

The overall derivative is an $M \times N$ matrix.

# 5.9 We define

$g(z, \nu) := \log p(x, z) - \log q(z, \nu)$
$z := t(\epsilon, \nu)$

for differentiable functions $p, q, t$. By using the chain rule, compute the gradient

$\frac{\mathrm{d}}{\mathrm{d}\nu} g(z, \nu)$.

$\frac{\mathrm{d}}{\mathrm{d}\nu} g(z, \nu) = \frac{\mathrm{d}}{\mathrm{d}\nu} (\log p(x, z) - \log q(z, \nu)) = \frac{\mathrm{d}}{\mathrm{d}\nu} \log p(x, z) - \frac{\mathrm{d}}{\mathrm{d}\nu} \log q(z, \nu)$
$= \frac{\partial}{\partial z} \log p(x, z) \frac{\partial t(\epsilon, \nu)}{\partial \nu} - \frac{\partial}{\partial z} \log q(z, \nu) \frac{\partial t(\epsilon, \nu)}{\partial \nu} - \frac{\partial}{\partial \nu} \log q(z, \nu)$
$= \left( \frac{\partial}{\partial z} \log p(x, z) - \frac{\partial}{\partial z} \log q(z, \nu) \right) \frac{\partial t(\epsilon, \nu)}{\partial \nu} - \frac{\partial}{\partial \nu} \log q(z, \nu)$
$= \left( \frac{1}{p(x, z)} \frac{\partial}{\partial z} p(x, z) - \frac{1}{q(z, \nu)} \frac{\partial}{\partial z} q(z, \nu) \right) \frac{\partial t(\epsilon, \nu)}{\partial \nu} - \frac{\partial}{\partial \nu} \log q(z, \nu)$