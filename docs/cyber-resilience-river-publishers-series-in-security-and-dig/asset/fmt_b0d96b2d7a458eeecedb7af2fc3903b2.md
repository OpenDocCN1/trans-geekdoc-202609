
# Forming the Passport Program

To form the passport program, the following actions are required:

1.  **Solving the observative problem** (the computational process simulation by an oriented program control graph).
2.  **Solving the problem of presenting calculations by similarity equations on linear graph parts**, i.e., transforming the arithmetic operations of the form:

    $$
    {\mathit{z}_{i}\,}_{}(\mathit{x}_{1}\,,\mathit{x}_{2}\,,\ldots{\,,\,,\text{  }\mathit{x}}_{\mathit{m}}) = \underset{j = 1}{\overset{p}{\Sigma}}z_{ij}\,(\mathit{x}_{1},\mathit{x}_{2},\ldots\,\,\,,\mathit{x}_{\mathit{m}})
    \tag{1.23}
    $$

    To dimensionless form:

    $$
    \left\lbrack \mathit{z}_{ij}\,(\mathit{x}_{1},\mathit{x}_{2},{\ldots\,\,\,,\mathit{x}}_{\mathit{m}}) \right\rbrack = \left\lbrack \mathit{z}_{il\,}\,(\mathit{x}_{1},\mathit{x}_{2},\ldots{\,,\,,\text{  }\,\mathit{x}}_{\mathit{m}}) \right\rbrack,\mathit{j},\mathit{l} = \overline{1⁢\,,\mathit{p}}
    \tag{1.24}
    $$

To ensure calculation correctness, the following actions are required:

1.  **Solving the problem of managing the computational process** by comparing the semantic invariants with the program passport. This means it is necessary to find the maps:

    $$
    \psi: Z' \to \Pi' \quad \mu: \Pi' \to \Pi' \quad \xi: \Pi \to Z
    \tag{1.25}
    $$

## Limitations and Assumptions

1.  Considered set of arithmetic operations `{+, -, *, /, =}`.
2.  `t[i] < t[max]`[,] where `t[i]` - computation time recovery, `t[max]` - maximum allowable time to recover the calculations correctness.

Solving these problems allowed developing a new method to control the computational program semantic correctness, which complemented the known method capabilities to ensure the required cyber resilience of the secured critical information infrastructure [34, [164](#Reference.xhtml#ref0167), [181](#Reference.xhtml#ref0184)].

## Program Control Graph

In order to control the software correctness, it was necessary to construct a program control graph.

Let us imagine some computational process in the form of a program control graph:

$$
G (B, D)
\tag{1.26}
$$

`B = {B[i]}` — set of vertices (linear program part).

where

$$
D = \{B \times B\}
$$

— set of arcs (control connections) between them.

Here, each linear graph part `B[i] 2∈ B` has its own arithmetic operator sequence, i.e.

$$
B[i] = (b[i][1], b[i][2], . . . ., b[il])
\tag{1.27}
$$

An ordered vertex sequence corresponds to each elementary (without cycles) route of the graph input vertex to output vertex:

$$
B^{(k)} = (B[1]^{(k)}, B[2]^{(k)}, \ldots, B[t]^{(k)})
\tag{1.28}
$$

where `B^(K) ⊆ B` and `B[i]^(k) = (b[i1]^(k), b[i2]^(k), …, b[il]^(k))`, `B[i]^(k) = (b[i1]^(k), b[i2]^(k), …, b[i1]^(k))` `∀i = \overline{1,p}` form a sequence of the executed arithmetic operators, called a program implementation or a computational process. The arithmetic expression sequence data is the potentially dangerous program fragments.

The computational process algorithm was reduced to the graph representation form to derive the arithmetic expression operators from the control operators (*conditional transitions, branching, cycles*). As a result, in the control graph, all arithmetic expression operators were grouped on a set of linear program parts – the graph vertices, into which *checkpoints (CP)* were entered. Here, checkpoints were needed to determine the route context within which the calculations take place. Moreover, the special systems of defining relations were constructed in the form of similarity equations at each checkpoint for arithmetic operators. The equation system solution allowed to form the matrices of similarity invariants to control the computational process semantics [34, 132, 133].

## A Similarity Equations System Development

The studies have shown that the most effective way to control the computation semantics is to test relations, based on theoretically based relations and computation features. Here the key relation in the approach for detecting the parameters of the incorrect computational process functioning is some invariant, which is understood as the auto modelling (constant) presentation of program execution in the actual operating secured infrastructure conditions. The invariant generation problem, from the different program representations, are non-trivial and poorly formalized. In the program execution dynamics, only semantic invariants remain fully computable (reproducible) (since they do not depend on the specific values of the program variables).

Let us imagine the implementation of `B^k` of the program control graph as an ordered primary relation sequence, corresponding to arithmetic operators:

$$
\left\{
\begin{matrix}
y_{1} = f_{1}^{k}{\left( x_{1},x_{2},\,\ldots,\,, x_{N} \right),} \\
y_{2} = f_{2}^{k}{\left( x_{1},x_{2},\,\ldots,\,, x_{N},y_{1} \right),} \\
\ldots \\
y_{M} = f_{M}^{k}\left( x_{1},x_{2},\,\ldots,\,, x_{N},y_{1},y_{2},\,\ldots,\,, y_{M - 1} \right)
\end{matrix}
\right.
\tag{1.29}
$$

Having performed the superposition `{y[i]}` *on X* on the right relation sides, we obtain a relation invariant system according to the displacement:

$$
\left\{
\begin{matrix}
y_{1} = z_{1}^{k}{\left( x_{1},x_{2},\,\ldots,\,, x_{N} \right),} \\
y_{2} = z_{2}^{k}{\left( x_{1},x_{2},\,\ldots,\,, x_{N} \right),} \\
\ldots \\
y_{m} = z_{m}^{k}{\left( x_{1},x_{2},\,\ldots,\,, x_{N} \right) \cdot}
\end{matrix}
\right.
\tag{1.30}
$$

The relation `y[i] = z[i]^(k) (x[1], x[2],..., x[N])` can be presented as:

$$
{\mathit{y}_{i}}_{\,} = \underset{i = 1}{\overset{pi}{\Sigma}}\mathit{z}_{ij}\,(\mathit{x}_{1}\,,\mathit{x}_{2}\,,\ldots\,\,\,,{\,\,\mathit{x}}_{\mathit{N}})\,
\tag{1.31}
$$

where `z[ij](x[1], x[2],..., x[N])` - a power monomial.

In accordance with the **Fourier rule**, the summands [(1.31)](#Ch02.xhtml#bck_cap_lbl0088) should be homogeneous in dimensions, i.e.

$$
\left\lbrack {\mathit{y}_{i}}_{} \right\rbrack = \left\lbrack \mathit{z}_{ij\,}(\mathit{x}_{1}\,,\mathit{x}_{2}\,,\ldots\,\,\,,\mathit{x}_{\mathit{N}}) \right\rbrack,\,\mathit{j} = \overline{1,p_{i⁢}}
$$

or

$$
\left\lbrack \mathit{Z}_{ij}(\mathit{x}_{1}\,,\mathit{x}_{2,,}\ldots\,\,\,,\mathit{x}_{\mathit{N}}) \right\rbrack = \left\lbrack \mathit{Z}_{il}\,(\mathit{x}_{1}\,,\mathit{x}_{2}\,,\ldots\,\,\,,\mathit{x}_{\mathit{N}}) \right\rbrack,\mathit{j},\mathit{l} = \overline{1,{\mathit{p}_{i}⁢}_{}}
\tag{1.32}
$$

System [(1.34)](#Ch02.xhtml#cap_lbl0091) is a defining relations system or a similarity equation system.

Using the function `ρ = X → [X]`, we associate each `x[j] ∈ X` with some abstract dimension `[x[j]] ∈ [X]`. Then the summand dimensions (1.31) will be expressed as

$$
\left\lbrack \mathit{Z}_{ij\,}\,(\mathit{x}_{1},\mathit{x}_{2}\,,\ldots\,\,\,,\mathit{x}_{\mathit{n}}) \right\rbrack = \,\underset{n = 1}{\overset{N}{\Pi}}\left\lbrack \mathit{x}_{\mathit{n}}\rbrack^{\lambda_{j\, n}} \right.,\mathit{j} = \overline{1,{\mathit{p}_{i}}_{}}
\tag{1.33}
$$

Using [(1.32)](#Ch02.xhtml#cap_lbl0089) and [(1.33)](#Ch02.xhtml#cap_lbl0090), we develop a system of defining relations
