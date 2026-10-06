# 4.1 Fixed Structure

Theorem 4.2 ([74, Theorem 4.2]) Let Assumption 4.1 be satisfied, $C$ be pointed, let $\psi$ be a $-C$ representing functional, and let some $y \in Y$ with $T \subseteq \{\hat{y}\} + C\setminus\{0_y\}$. $	ilde{y}$ is a minimal element of the set $T$ if only if there is some $a \in C\setminus\{0_y\}$ so that $(	ilde{y}, 1)$ is a unique minimal solution of the optimization problem

```
$$\min \lambda \ntext{subject to the constraint} \n\psi(y-\tilde{y} -lambdalambda a) \leq 0 \n(y, \tilde{y}) \in T \times \mathbb{R}.$$
```

**Proof** Since $\psi$ is a $-C$ representing functional, the optimization problem (4.3) can also be rewritten as

```
$$\min \lambda, \ny \in ({\hat{y} + \lambda a\} - C) \cap T \n \in \mathbb{R}.$$
```

Next, we begin with the actual proof.

+   a) Let there exist some $a \in C\setminus\{0_y\}$ so that $(	ilde{y}, 1)$ is a unique minimal solution of the optimization problem (4.4). Assume that $	ilde{y}$ is not a minimal element of the set $T$. Then there exists some $y \neq \tilde{y}$ with $y \in ({\hat{y}\} - C) \cap T$. Because of the constraint $y \in ({\hat{y} + a\} - C$, we get with Proposition 1.1

```
${\tilde{y}} - C \subseteq {{\hat{y} + a} - C - C = {{\hat{y} + a} - C.$
```

Then we conclude

```
$y \in ({\hat{y} + a} - C) \cap T.$
```

Consequently, $(y, 1)$ is also a minimal solution of problem (4.4)—a contradiction to the assumption that $(\tilde{y}, 1)$ uniquely solves problem (4.3). Hence, $\tilde{y}$ is a minimal element of the set $T$.

+   b) Now, let $\tilde{y}$ be a minimal element of the set $T$, i.e., $(\{\tilde{y}\} - C) \cap T = {{\hat{y}}\}}$. With $a := \tilde{y} - \hat{y} \in C\setminus\{0_y\}$, we then have

```
${\hat{y} + 1 \cdot a} - C) \cap T = {{\tilde{y}}.$
```

Consequently, $(y, 1)$ is the only feasible point at objective level 1 of problem (4.4). If there would be a feasible $(y, \lambda)$ with $\lambda < 1$, we would obtain

```
$y \in ({\hat{y} + \lambda a} - C) \cap T \n = ({\hat{y} + a} - C - \{(1 - \lambda)} a_\}) \cap T \n_{>0} \in C\setminus\{0_y\}}$
```