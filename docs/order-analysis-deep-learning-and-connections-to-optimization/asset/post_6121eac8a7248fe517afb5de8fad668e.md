
## 74 Application in Vector Optimization

**Fig. 4.4** Illustration of a variable order structure with respect to the order relation $\le I$

![](img/e4a2e491dbba0d9f71abf293f149cd5b_85_0.png)

**Theorem 4.5** ([74, Theorem 4.3]) *Let Assumption 4.2 be satisfied, and $\psi$ be a $-K$-valued functional. Then we have*

- (a) $\tilde{y}$ is nondominated element of $T \iff \psi(y - \tilde{y}, y) > 0$ for all $y \in T\setminus\{\tilde{y}\}$
- (b) $\tilde{y}$ is minimal element of $T \iff \psi(y - \tilde{y}, \tilde{y}) > 0$ for all $y \in T\setminus\{\tilde{y}\}$

***Proof***

(a) By Definition 4.4 (a) and Remark 2.5, we have

$\tilde{y}$ is a nondominated element of the set $T$
$\iff y \in T : y \le_1 \tilde{y} \text{ and } y \neq \tilde{y}$
$\iff y \in T\setminus\{\tilde{y}\} : \psi(y - \tilde{y}, y) \le 0$
$\iff \psi(y - \tilde{y}, y) > 0$ for all $y \in T\setminus\{\tilde{y}\}$

and the assertion is shown.

- (b) Following the lines of the proof of part (a), we obtain

$\tilde{y}$ is a minimal element of the set $T$
$\iff y \in T : y \le_2 \tilde{y} \text{ and } y \neq \tilde{y}$
$\iff y \in T\setminus\{\tilde{y}\} : \psi(y - \tilde{y}, \tilde{y}) \le 0$
$\iff \psi(y - \tilde{y}, \tilde{y}) > 0$ for all $y \in T\setminus\{\tilde{y}\}$

which completes the proof.

Under an additional assumption, the following corollary presents a scalarization result extending Theorem 4.1 to the case of variable order structures.

## 4.3 Conditional Vector Optimization Problems

**Corollary 4.2 ([74, Corollary 4.1])** *Let the assumptions in Theorem 4.5 be satisfied. In addition, let $\psi(0, \tilde{y})=0$ be fulfilled for some $y \in T$. Then we have*

- (a) $\tilde{y}$ nondominated element of $T \Leftrightarrow \tilde{y}$ unique minimal solution of $\min \psi(y-\tilde{y}, y)$.
- (b) $\tilde{y}$ minimal element of $T \Leftrightarrow \tilde{y}$ unique minimal solution of $\min \psi(y-\tilde{y}, y).$

**Proof**

- (a) By Theorem 4.5 (a) and the assumption $\psi(0, \tilde{y})=0$, we have

$\tilde{y}$ is a nondominated element of the set $T$
$\iff \psi(y-\tilde{y}, \tilde{y})>0=\psi(0, \tilde{y})$ for all $y \in T\setminus\{\tilde{y}\}$
$\iff \tilde{y}$ unique minimal solution of $\min \psi(y-\tilde{y}, \tilde{y}),$

which has to be shown.

- (b) In a similar way as in the proof of part (a), we obtain

$\tilde{y}$ is a minimal element of the set $T$
$\iff \psi(y-\tilde{y}, \tilde{y})>0=\psi(y-\tilde{y}, \tilde{y})$ for all $y \in T\setminus\{\tilde{y}\}$
$\iff \tilde{y}$ unique minimal solution of $\min \psi(y-\tilde{y}, \tilde{y}),$

which completes the proof.

Adapting the result of Proposition 2.10 to $K$ representing functionals, the assumption in Corollary 4.2 that $\psi(0, \tilde{y})=0$ for some $y \in T$ is satisfied if the functional $\psi(\cdot, \tilde{y})$ is positively homogeneous or subadditive (see also the note on page 36).

Conditional vector optimization problems (see [76, Section 4]) are vector optimization problems with objectives and constraints, which are only valid under a condition. If this condition is not fulfilled, the corresponding constraint or objective vanishes. For these nonstandard problems, we have the following assumption:

**Assumption 4.3** Let $X$ be a linear space, and $k, m \in \mathbb{N}$, $F_1, \dots, F_k, G_1, \dots, G_m$ be nonempty subsets of $X$. Let $Y_1, \dots, Y_k, Z_1, \dots, Z_m$ be real linear spaces, and let $f_1 : \hat{S} \to Y_1, \dots, f_k : \hat{S} \to Y_k, g_1 : \hat{S} \to Z_1, \dots, g_m : \hat{S} \to Z_m$ be given functions. Let $C_{Y_1}, \dots, C_{Y_k}, C_{Z_1}, \dots, C_{Z_m}$ be convex cones in $Y_1, \dots, Y_k$ and $Z_1, \dots, Z_m$, respectively. Let the constraint set
$S := \{x \in \hat{S} \mid g_1(x) \in -C_{Z_1}, \text{if } x \in G_1, \dots, g_m(x) \in -C_{Z_m}, \text{if } x \in G_m\}$
be nonempty.

Under this assumption, we consider the conditional vector optimization problem in a simplified form
$\min \begin{cases} f_1(x), & \text{if } x \in F_1 \\ \dots f_k(x), & \text{if } x \in F_k \end{cases}$
subject to the constraints $g_1(x) \in -C_{Z_1}, \text{if } x \in G_1, \dots, g_m(x) \in -C_{Z_m}, \text{if } x \in G_m$
$x \in \hat{S}.$ (4.8)

This is not a standard vector optimization problem because objectives/constraints may vanish at some $x \in \hat{S}$. For this problem type, there are concrete applications in structural optimization and image registration of medical data, and are relations to problems with switching constraints. For more information, see the bibliographical notes in Sect. 4.4.

We begin with a very simple example. **Example 4.2** ([76, Example 4.5]) We investigate the conditional optimization problem
$\min \sin x$
subject to the constraints $1 \le x \le 2\pi, \cos x \ge 0, \text{if } x \in (\pi, 2\pi)$
$x \in Z.$

Here we set $F_1 := G_1 := G_2 := \mathbb{R}$ and $\hat{S} := \mathbb{R}$. It is obvious that the set $S$ of feasible points is given as $S := [1, 2\pi]$ and $\tilde{x} := \pi$ is the only minimal solution of this optimization problem (compare Fig. 4.5).

It is well-known that problem (4.8) can be written as a vector optimization problem with variable order structure formulated in the following way. In addition to Assumption 4.3, we assume that the vector functions $f_1, \dots, f_k, g_1, \dots, g_m$ are injective. For every $i \in \{1, \dots, k\}$ and every $j \in \{1, \dots, m\}$, we define the set-valued maps $\mathcal{K}_{f_i}: f_i(\hat{S}) \Rightarrow Y_i$ and $\mathcal{K}_{g_j}: g_j(\hat{S}) \Rightarrow Z_j$ by
$\mathcal{K}_{f_i}(f_i(x)) := \begin{cases} C_i, & \text{if } x \in F_i \\ Y_i, & \text{if } x \notin F_i \end{cases}$ for all $x \in \hat{S}$
and
$\mathcal{K}_{g_j}(g_j(x)) := \begin{cases} C_j, & \text{if } x \in G_j \\ Z_j, & \text{if } x \notin G_j \end{cases}$ for all $x \in \hat{S}.$
respectively. Note, because of the special problem formulation, the domain of these maps can be restricted to the image sets of $f_i$ and $g_j$, respectively. Since the set-valued maps are defined at an image vector of the vector functions $f_1, \dots, f_k, g_1, \dots, g_m$, the injectivity assumption ensures that each image vector has a unique preimage vector, so that the set-valued maps are well-defined on the image set of each vector function. Under the further additional assumption that objectives do not vanish all together, we can give a formulation of the conceptual conditional vector optimization problem (4.8) in a formal way:
$$\min_{\mathcal{K}_{f_1}(f_1(x))\dots\mathcal{K}_{f_k}(f_k(x))} \begin{cases} f_1(x) \vdots \ f_k(x) \end{cases} \\ \text{subject to the constraints} \ g_1(x) \in -\mathcal{K}_{g_1}(g_1(x)) \vdots \ g_m(x) \in -\mathcal{K}_{g_m}(g_m(x)) \ x \in \hat{S}.$$

The complexity of problem (4.8) is now hidden in the variable order structures.
