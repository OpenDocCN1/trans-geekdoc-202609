
## 6.6 Gradient Methods

![](img/e4a2e491dbba0d9f71abf293f149cd5b_119_0.png)

**Fig. 6.9** Level lines of the Rosenbrock function $f: \mathbb{R}^2 \to \mathbb{R}$ with $f(x_1, x_2) := 100(x_2 - x_1^2)^2 + (1 - x_1)^2$ for all $(x_1, x_2) \in \mathbb{R}^2$

(b) The gradient descent method basically determines a zero of the gradient of the objective function. The condition $\nabla f(x)=0$ is a necessary optimality condition for a global as well as for a local minimal or maximal point. Since the method belongs to the class of descent methods, i.e., the function values of the iteration points are decreased from step to step (see Lemma 6.1), the gradient descent method runs to a local minimal point in the “valley" where it starts. To find a (global) minimal point, it is recommended to start the procedure repeatedly with different starting points and to select the one with the smallest objective value among all approximate solutions. An example of this is the Himmelblau function [60] $f: \mathbb{R}^2 \to \mathbb{R}$

$f(x_1, x_2) := (x_1^2 + x_2 - 11)^2 + (x_1 + x_2^2 - 7)^2$ for all $(x_1, x_2) \in \mathbb{R}^2$.

The Himmelblau function is illustrated by level lines in Fig. 6.10. It has four (global) minimal points (located approximately at $(3.58, -1.85)$, $(-3.78, -3.28)$, $(-2.81, 3.13)$, and $(3, 2))$ with $0$ as the value of the objective function, one local maximal point (located approximately at $(-0.27, -0.92)$), and four saddle points (located approximately at $(3.39, 0.07)$, $(-3.07, -0.08)$, $(-0.09, 2.88)$, and $(-0.13, -1.95))$ where $\nabla f$ also vanishes.

![](img/e4a2e491dbba0d9f71abf293f149cd5b_120_0.png)

**Fig. 6.10** Level lines of the Himmelblau function $f: \mathbb{R}^2 \to \mathbb{R}$ with $f(x_1, x_2) := (x_1^2+x_2-11)^2 + (x_1^2+x_2-7)^2$ for all $(x_1, x_2) \in \mathbb{R}^2$. The four black dots indicate the location of the (global) minimal points

The determination of an optimal step size in Algorithm 6.1 is generally associated with a high numerical effort, which is why simpler approaches are used. We now consider the possibility that the step size $\lambda_i$ can be chosen arbitrarily in a certain interval. Under suitable assumptions, we can then prove the linear convergence of Algorithm 6.1 modified in this way. For this proof, we first need the two lemmas:

**Lemma 6.2** (Variational Inequality [42, Lemma 2.14]) *For some $\mu > 0$, let the function $f : \mathbb{R}^n \to \mathbb{R}$ be $\mu$-strongly convex and differentiable. Then we have*

$\nabla f(x)^T(y-x) \geq f(x) - f(y) + \frac{\mu}{2} \|x-y\|_2^2$ for all $x, y \in \mathbb{R}^n$

**Proof** By Proposition 1.12, we get

$f(y) \geq f(x) + \nabla f(x)^T(y-x) + \frac{\mu}{2} \|y-x\|_2^2$ for all $x, y \in \mathbb{R}^n$

which implies

$\nabla f(x)^T(x-y) \geq f(x) - f(y) + \frac{\mu}{2}\|x-y\|_2^2$ for all $x, y \in \mathbb{R}^n$.

**Lemma 6.3 (Lipschitz Continuity [42, Lemma 2.28])** Let the function $f:\mathbb{R}^n \to \mathbb{R}$ be differentiable, let the gradient $\nabla f$ be Lipschitz continuous with some Lipschitz constant $L > 0$, and $\tilde{x} \in \mathbb{R}^n$ be a minimal point of $f$. Then we have

$\|\nabla f(x)\|^2 \leq 2L(f(x)-f(\tilde{x}))$ for all $x \in \mathbb{R}^n$.

**Proof** By Garrigos and [42, Lemma 2.25], the inequality

$f(y) \leq f(x) + \nabla f(x)^T(y-x) + \frac{L}{2}\|y-x\|_2^2$ for all $x, y \in \mathbb{R}^n$

is valid. Therefore, for $y := x-\frac{1}{L}\nabla f(x)$

$f(x-\frac{1}{L}\nabla f(x)) \leq f(x)-\frac{1}{L}\nabla f(x)^T\nabla f(x) + \frac{L}{2}\|-\frac{1}{L}\nabla f(x)\|_2^2 = f(x)-\frac{1}{L}\|\nabla f(x)\|_2^2+\frac{1}{2L}\|\nabla f(x)\|_2^2 = f(x)-\frac{1}{2L}\|\nabla f(x)\|_2^2$ for all $x \in \mathbb{R}^n$.

Consequently, we obtain

$\|\nabla f(x)\|^2 \leq 2L(f(x)-f(x-\frac{1}{L}\nabla f(x))) \geq 2L(f(x)-f(\tilde{x}))$ for all $x \in \mathbb{R}^n$, which has to be shown.

**Theorem 6.3 (Convergence of the Gradient Method [42, Theorem 3])** For $\mu > 0$, let the function $f:\mathbb{R}^n \to \mathbb{R}$ be $\mu$-strongly convex and differentiable, let the gradient $\nabla f$ be Lipschitz continuous with some Lipschitz constant $L > 0$, and $\tilde{x} \in \mathbb{R}^n$ be the minimal point of $f$. If Algorithm 6.1 with arbitrarily chosen $\lambda_i \in (0, \lambda_{max}]$, for any $0 < \lambda_i \leq \min\{\frac{1}{L}, \frac{1}{\mu}\}$ (instead of optimal step size in line 7 of Algorithm 6.1) generates a sequence $(x^i)_{i\in\mathbb{N}}$, then

$\|x^{i+1}-\tilde{x}\|_2^2 \leq (1-\lambda_i\mu)\|x^i-\tilde{x}\|_2^2$ for all $i \in \mathbb{N}\cup\{0\}$ (6.7)

and $\|x^{t}-\tilde{x}\|_2^2 \leq (1-\lambda_i\mu)^t \|x^0-\tilde{x}\|_2^2$ for all $t \in \mathbb{N}$, where $1-\lambda_i\mu \in [1-\lambda_{max}\mu, 1) \subseteq (0, 1)$ for all $i \in \mathbb{N}$.

**Proof**, by Lemma 1.1 the function $f$ has a unique minimal point $\tilde{x}$, since $f$ is $\mu$-strongly convex and continuous. For an arbitrary $i \in \mathbb{N}\cup\{0\}$, we then obtain

$\|x^{t+1}-\tilde{x}\|_2^2 = \|x^t-\tilde{x}-\lambda_i\nabla f(x^t)\|_2^2$
$= (x^t-\tilde{x}-\lambda_i\nabla f(x^t))^T(x^t-\tilde{x}) + \lambda_i^2\|\nabla f(x^t)\|_2^2$
$= \|x^t-\tilde{x}\|_2^2 - 2\lambda_i\nabla f(x^t)^T(x^t-\tilde{x}) + \lambda_i^2\|\nabla f(x^t)\|_2^2$
$\geq \|x^t-\tilde{x}\|_2^2 - 2\lambda_i(f(x^t)-f(\tilde{x}) + \frac{\mu}{2}\|x^t-\tilde{x}\|_2^2) + \lambda_i^2\|\nabla f(x^t)\|_2^2$ (by Lemma 6.2)
$\leq (1-\lambda_i\mu)\|x^t-\tilde{x}\|_2^2 - 2\lambda_i(f(x^t)-f(\tilde{x})) + \lambda_i^2\|\nabla f(x^t)\|_2^2$
$\leq 2L(f(x^t)-f(\tilde{x}))$ (by Lemma 6.3)
$\leq (1-\lambda_i\mu)\|x^t-\tilde{x}\|_2^2 - 2\lambda_i \frac{(1-\lambda_i L)}{L} (f(x^t)-f(\tilde{x}))$
$\geq 0$ (because of $\lambda_i < \frac{1}{L}$)
$\leq (1-\lambda_i\mu)\|x^t-\tilde{x}\|_2^2$,

which proves the inequality (6.7). The inequality (6.8) is a direct consequence of the inequality (6.7). With the inequality $\lambda > 0$ and $\mu < \frac{1}{L}$, the assertion (6.9) follows immediately.

**Corollary 6.1 (Linear Convergence of the Gradient Method (Compare [42, Remark 3]))** Let the assumptions of Theorem 6.2 be satisfied. Then the sequence $(x^t)^{t \in \mathbb{N}}$ converges to the unique minimal point $\tilde{x}$ of $f$.

**Proof** It is obvious from the inequality (6.8) with condition (6.9) that the sequence $(x^t)^{t \in \mathbb{N}}$ converges to the unique minimal point $\tilde{x}$ of $f$. Inequality (6.7) together with condition (6.9) means that the sequence $(x^t)^{t \in \mathbb{N}}$ is linearly convergent.

Now, we turn our attention to a more practical variant of the conceptual Algorithm 6.1. In practice, it makes little sense to work with the optimal step size as lines 6 and 7 of Algorithm 6.1. Therefore, approximations are used, such as those given by Armijo, Goldstein, or Powell in nonlinear optimization (see [46, Chapter 2] among others). In deep learning, however, we need a variant that is characterized by low numerical effort. For this purpose, an approximation by Barzilai and Borwein [12] has proven to be useful. This variant is considered in the following procedure:

```
**Algorithm 6.2** (Gradient descent method—practical form)
1 Input: $f: \mathbb{R}^n \to \mathbb{R}$, starting vector $x^0 \in \mathbb{R}^n$, stopping criterion $\epsilon > 0$.
2 $i := 0$ % initialization
3 while $\|\nabla f(x^i)\|_2 > \epsilon$ do % iteration
4 $d^i := -\nabla f(x^i)$
5 if $i = 0$ then
6 $\lambda_0 := 1$
7 else
8 $\lambda_i := \frac{(x^i - x^{i-1})^T(x^i - x^{i-1})}{(x^i - x^{i-1})^T(\nabla f(x^i) - \nabla f(x^{i-1}))}$ % Barzilai-Borwein step size
9 end if
10 $x^{i+1} := x^i + \lambda_i d^i$
11 $i := i + 1$
12 end while
13 Output: $x^1, x^2, \dots$
```
