# 6.6 Gradient Methods

by low numerical effort. For this purpose, an approximation by Barzilai and Borwein [12] has proven to be useful. This variant is considered in the following procedure:

```
**Algorithm 6.2** (Gradient descent method—practical form)
1 Input: $f: \mathbb{R}^n 	o \mathbb{R}$, starting vector $x^0 \in \mathbb{R}^n$, stopping criterion $\epsilon > 0$.
2
3 $i := 0$ % initialization
4 while $\|\nabla f(x^i)\|_2 > \epsilon$ do % iteration direction
5 $d^i := -\nabla f(x^i)$
6 if $i = 0$ then
7 $\lambda_0 := 1$
8 else
9 $\lambda_i := \frac{(x^i - x^{i-1})^T(x^i - x^{i-1})}{(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))}$ % Barzilai-Borwein step size rule
10 end if
11 $x^{i+1} := x^i + \lambda_i d^i$
12 $i := i + 1$
13 end while
14 Output: $x^1, x^2, \dots$
```

In deep learning, optimization problems with many variables can occur. The Barzilai-Borwein formula is advantageous in this case because basically two scalar products need to be calculated. In the calculation, make sure that the denominator in line 9 of Algorithm 6.2 does not become 0.

First, let us see if the line 9 of this algorithm is a bad choice of step size.

> **Remark 6.3** (Barzilai-Borwein Step Size Rule) If $f$ is twice continuously differentiable and $x^{i-1}, x^i \in \mathbb{R}^n$ (with $i \in \mathbb{N}$) are two arbitrary iteration points, then according to Taylor's formula, there is some $\vartheta \in (0, 1)$ so that

$\nabla f(x^i) = \nabla f(x^{i-1}) + H(x^{i-1}) + \vartheta(x^i - x^{i-1}))(x^i - x^{i-1}), (6.10)

where $H$ denotes the Hessian of $f$. The point $x^{i-1} + \vartheta(x^i - x^{i-1})$ is located on the connecting line between points $x^{i-1}$ and $x^i$. The equality (6.10) can be simply rewritten as

$H(x^{i-1} + \vartheta(x^i - x^{i-1}))(x^i - x^{i-1}) = \nabla f(x^i) - \nabla f(x^{i-1}).

In general, the matrix $H(x^{i-1} + \vartheta(x^i - x^{i-1}))$ is unknown and is therefore replaced by a matrix $B^i \in \mathbb{R}(n,n)$, which is an easy-to-handle approximation. The corresponding equality

$B^i(x^i - x^{i-1}) = \nabla f(x^i) - \nabla f(x^{i-1}) (6.11)