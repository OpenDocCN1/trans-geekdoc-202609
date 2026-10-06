# Application in Vector Optimization

![](bbox=[0.2587, 0.0835, 0.7033, 0.2935])

**Fig. 4.1** Minimal element $	ilde{y}$ of a set $T$ (see [69, Fig. 4.1])

**Theorem 4.1** ([74, Theorem 4.1]) Let Assumption 4.1 be satisfied, let $C$ be pointed, and let $\psi$ be a $-C$-representing functional with $\min \psi(0_Y) = 0$. Then we have

$\tilde{y}$ minimal element of $T \iff \tilde{y}$ unique minimal solution of $\min \psi(y-\tilde{y}) \{y\in T}$

**Proof** By definition, $	ilde{y}$ is a minimal element of the set $T$ iff the implication (4.1) holds. For any $y \in Y$ the inequality $y \leq c\tilde{y}$ means $y-\tilde{y} \in -C$ or $\psi(y-\tilde{y}) \leq 0$, the implication (4.1) is equivalent to

> ${y \in T \| \psi(y-\tilde{y}) \leq 0\} = {\tilde{y}\}$

also equivalent to

$\psi(y-\tilde{y}) > 0$ for all $y \in T \setminus{\tilde{y}\}$. (4.2)

With the assumption $\psi(0_Y) = 0$, the condition (4.2) is equivalent to

$\psi(y-\tilde{y}) > \psi(\tilde{y}-\tilde{y})$ for all $y \in T \setminus{\tilde{y}\}$

which means that $\tilde{y}$ is a unique minimal solution of the problem $\min \psi(y-\tilde{y})$, which has to be shown.

By Proposition 2.10, the assumption $\psi(0_Y) = 0$ in Theorem 4.1 is satisfied if the functional $\psi$ is additionally positively homogeneous or subadditive (see also the note on page 36).

Theorem 4.1 is a called-scalar scalarization result because minimal elements of a set are characterized as unique minimal solutions of an optimization problem with a scalar-valued objective functional. These scalar optimization problems have the drawback that the unique minimal solution is simultaneously a parameter in the objective functional. The next theorem avoids this disadvantage to some extent.