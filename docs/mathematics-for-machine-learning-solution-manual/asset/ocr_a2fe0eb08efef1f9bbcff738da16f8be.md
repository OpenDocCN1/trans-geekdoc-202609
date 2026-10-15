which yields the same result as the previous question, i.e.,

$F \cap G = \text{span}\begin{bmatrix}2\\1\\3\end{bmatrix}$

# 2.16 Are the following mappings linear?

Recall: To show that $\Phi$ is a linear mapping from $E$ to $F$, we need to show that for all $x$ and $y$ in $E$ and all $\lambda$ in $\mathbb{R}$:

+   - $\Phi(x + y) = \Phi(x) + \Phi(y)$
+   - $\Phi(\lambda x) = \lambda \Phi(x)$

a. Let $a, b \in \mathbb{R}$.

$\Phi : L^1([a,b]) \to \mathbb{R}$

$f \mapsto \Phi(f) = \int_a^b f(x)dx$,

where $L^1([a,b])$ denotes the set of integrable functions on $[a,b]$.

+   - Let $f, g \in L^1([a,b])$. It holds that
+   $\Phi(f)+\Phi(g)=\int_a^b f(x)dx+\int_a^b g(x)dx=\int_a^b f(x)+g(x)dx=\Phi(f+g)$.
+   - For $\lambda \in \mathbb{R}$ we have
+   $\Phi(\lambda f)=\int_a^b \lambda f(x)dx=\lambda \int_a^b f(x)dx=\lambda \Phi(f)$.

Therefore, $\Phi$ is a linear mapping. (In more advanced courses/books, you may learn that $\Phi$ is a linear functional, i.e., it takes functions as arguments. But for our purposes here this is not relevant.)

b.

$\Phi : C^1 \to C^0$

$f \mapsto \Phi(f) = f'$,

where for $k \ge 1$, $C^k$ denotes the set of $k$ times continuously differentiable functions, and $C^0$ denotes the set of continuous functions.

+   - For $f, g \in C^1$ we have
+   $\Phi(f + g) = (f + g)' = f' + g' = \Phi(f) + \Phi(g)$
+   - For $\lambda \in \mathbb{R}$ we have
+   $\Phi(\lambda f) = (\lambda f)' = \lambda f' = \lambda \Phi(f)$

Therefore, $\Phi$ is linear. (Again, $\Phi$ is a linear functional.)
From the first two exercises, we have seen that both integration and differentiation are linear operations.