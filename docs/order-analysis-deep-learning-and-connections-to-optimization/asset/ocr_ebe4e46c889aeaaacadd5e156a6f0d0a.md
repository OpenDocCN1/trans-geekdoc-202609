# 4 Application in Vector Optimization

$\le (\{\hat{y} + a\ - C\{0y\}) \cap T$
$= (\{\hat{y}\} - C\{0y\}) \cap T$
= \emptyset$

(notice that $-C\{0y\} = -C\{0y\}$ because the convex cone $C$ is assumed to be pointed). So, the minimal value of problem (4.4) equals 1, and $(\hat{y}, 1)$ is a unique minimal cone of the optimization problem (4.3).

The scalarized problem (4.3) is a simple optimization problem, which can be used for the determination of minimal elements of a nonconvex set $T$ with a certain lower bound $\hat{y}$.

**Example 4.1** ([74, Example 4.1]) In a real space $(Y, ||\cdot||)$, we consider Bishop-Phelps points when

$C(\ell) := \{y \in Y \mid |\ell(y)| \ge ||y||}$

for some given continuous linear functional $\ell \in Y^*$. Moreover, we choose $-C(\ell)$ representing functional $\varphi_{\ell}: Y \to \mathbb{R}$ with

$\varphi_{\ell}(y) := \ell(y) + ||y||$ for all $y \in Y$.

Then the scalar optimization problem (4.3) can be written as

with an inequality constraint guaranteed by a convex functional.

Next, we turn our attention to the so-called weakly minimal elements of a set, which are well-known in vector optimization (compare [69]. Definition 4.12, (a)).

**Definition 4.2** Let Assumption 4.1 be satisfied, and let $C$ have a nonempty algebraic interior core(C). An element $\hat{y} \in T$ is a *weakly minimal element* of the set $T$ iff

For this special optimality notion, we get the following scalarization result: