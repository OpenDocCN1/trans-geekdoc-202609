
## 32 2 -C Representing Functionals

with $k \in N$ and nonzero vectors $a^1,...,a^k \in \mathbb{R}^m$, the functional $\psi : \mathbb{R}^m \to \mathbb{R}$

$$\psi(y) := \max_{i\in\{1,\dots,k\}} \{-a_i^T y\} \text{ for all } y \in \mathbb{R}^m$$

is $-C$ representing. Compare Example 2.2 for a differentiable $-C$ representing functional.

In the special case $C := R_m^+$, we get the simple $-C$ representing functional $\psi$ given by

$$\psi(y) := \max\{y_1,...,y_m\} \text{ for all } y = (y_1,...,y_m) \in \mathbb{R}^m$$

The functional $\psi : \mathbb{R}^m \to \mathbb{R}$

$$\psi(y) := ||(y_1,...,y_{m-1})||_2^2 + y_m \text{ for all } y \in \mathbb{R}^m$$

(where $m \ge 2$ and $||\cdot||_2$ denotes the Euclidean norm in $\mathbb{R}^{m-1}$) is $-C_L$ for the Lorentz cone

$C_L = \{(y_1,...,y_m) \in \mathbb{R}^m \mid ||(y_1,...,y_{m-1})||_2 \le y_m\}$

(compare also Example 2.1).

## 2.3 Basic Properties

We summarize some properties of $-C$ representing functionals.

Proposition 2.3 ([74, Proposition 3.1]) Let Assumption 2.1 be satisfied, and let $\psi$ be a $-C$ representing functional.

- (a) $C \neq \{0\} \iff y \in Y\setminus\{0\}: \psi(y) \le 0$.
- (b) $C$ is pointed $\iff (y \in Y, \max\{-y\}, \psi(y)) \le 0 \Rightarrow y = 0)$.

Proof

- (a) Since $C \neq \{0\} \Leftrightarrow -C \neq \{0\}$, the assertion follows with Eq. (2.1).
- (b) Since the convex cone $C$ is pointed $\iff C \cap (-C) = \{0\}$, the assertion follows with Eq. (2.1).

Proposition 2.4 ([74, Proposition 3.2]) Let Assumption 2.1 be satisfied, and let $\psi$ be a $-C$ representing functional.

- (a) $\forall y \in Y: \psi(y) \le 0 \Rightarrow \psi(\lambda y) \le 0$ for all $\lambda \ge 0$.
- (b) $\forall y^1, y^2 \in Y: \max\{\psi(y^1), \psi(y^2)\} \le 0 \Rightarrow \psi(y^1 + y^2) \le 0$.
- (c) $\psi(0) \le 0$.

## 2.4 Sublinearity

- (d) *If, in addition, Y is a real topological linear space, $\psi$ is continuous at $0$, and $C \neq Y$, we have $\psi(0) = 0$.*

**Proof** The assertions (a) and (b) follow from the conditions of the convex cone $-C$, i.e.,

$y \in -C \Rightarrow \lambda y \in -C \text{ for all } \lambda \geq 0$

and

$y^1, y^2 \in -C \Rightarrow y^1 + y^2 \in -C$.

Part (c) is a simple consequence of $0 \notin -C$. In part (d), notice that there is some $y \notin -C$ implying

$\psi(\lambda y) > 0 \text{ for all } \lambda > 0$.

Consequently, we obtain $\psi(0) \geq 0$ and the assertion follows from part (c).

**Proposition 2.5** ([74, 3.3]) *Let Assumption 2.1* be satisfied, and let $\psi$ be a $-C$ representing functional. Then*

- (a) $\tilde{y} - C = \{y \in Y \mid \psi(y-\tilde{y}) \leq 0 \text{ for all } \tilde{y} \in Y\}$.
- (b) $\tilde{y} + C = \{y \in Y \mid \psi(y-\tilde{y}) \leq 0 \text{ for all } \tilde{y} \in Y\}$.
- (c) $S - C = \{y \in Y \mid s \in S, \psi(y-s) \leq 0 \text{ for all nonempty sets } S \subseteq Y\}$.
- (d) $S + C = \{y \in Y \mid s \in S, \psi(y-s) \leq 0 \text{ for all nonempty sets } S \subseteq Y$.

**Proof** We show only the assertions (a) and (c) because the other two ones can be proven analytically:

- (a) $\tilde{y} - C = \{y \in Y \mid y-\tilde{y} \leq 0\} = \{y \in Y \mid \psi(y-\tilde{y}) \leq 0\} \text{ for all } \tilde{y} \in Y$.
- (c) $S - C = \{y \in Y \mid s \in S, \psi(y-s) \leq 0\} \text{ for all nonempty sets } S \subseteq Y$.

Here, we now study $-C$ representing functionals which are additionally sublinear. This additional assumption of sublinearity is not unrealistic, as the following example shows:

**Example 2.7** $(Y, \|\cdot\|)$ be a real normed space, and let some continuous functional $\ell \in Y^*$ be chosen. Then consider the Bishop-Phelps functional $\varphi_\ell : Y \to \mathbb{R}$

$$\varphi_\ell(y) := \ell(y) + \|y\|$$

By Remark 2.1, this functional is $-C$ representing. Furthermore, $\varphi_\ell$ is sublinear because

$\varphi_\ell(\lambda y) = \ell(\lambda y) + \|\lambda y\| = \lambda\ell(y) + \lambda\|y\|$ for all $y \in Y$ and $\lambda \geq 0$, and

$\varphi_\ell(y^1 + y^2) = \ell(y^1 + y^2) + \|y^1 + y^2\| \leq \ell(y^1) + \ell(y^2) + \|y^1\| + \|y^2\| = \varphi_\ell(y^1) + \varphi_\ell(y^2)$ for all $y^1, y^2 \in Y$ (compare Definition 1.7).

**Proposition 2.6** ([74, Proposition 3.4]) Let $Y$ be a real space. For every sublinear functional $\psi : Y \to \mathbb{R}$, the set $S := \{y \in Y \mid \psi(y) \leq 0\}$ is a convex cone.

**Proof** $\psi : Y \to \mathbb{R}$ be a sublinear functional. Arbitr chosen $y \in S$ and $\lambda \geq 0$, $\psi(\lambda y) = \lambda\psi(y) \leq 0$, i.e., $\lambda y \in S$. Moreover, for all $y^1, y^2 \in S$, we obtain

$\psi(y^1 + y^2) \leq \psi(y^1) + \psi(y^2) \leq 0$, which means $y^1 + y^2 \in S$. Consequently, the set $S$ is a convex cone.

But not every functional $\psi : Y \to \mathbb{R}$ (where $Y$ denotes a linear space) with the property that the sublevel set $\{y \in Y \mid \psi(y) \leq 0\}$ is a convex cone given by $(2.3)$.

**Proposition 2.7** ([74, Proposition 3.5]) Let Assumption 2.1 be satisfied, and let $\psi$ be a $-C$ representing sublinear functional. There exists some linear functional $\ell \in Y'$ so that $-C$ is contained in the halfspace $\{y \in Y \mid \ell(y) \leq 0\}$.

**Proof** $\psi$ is a sublinear functional, by the Hahn-Banach theorem, there is some linear functional $\ell \in Y'$ with $\psi(y) \geq \ell(y)$ for all $y \in Y$. For every $y \in -C$, we then have $0 \geq \psi(y) \geq \ell(y)$, which proves the assertion.

**Theorem 2.1** ([74, Proposition 3.6]) Let Assumption 2.1 be satisfied, and let $\psi$ be a $-C$ representing sublinear functional. Then

- (a) $\{y \in Y \mid \psi(y) \leq 0\} \subseteq \text{core}(-C)$.
- (b) $\text{core}(-C) \subseteq \{y \in Y \mid \psi(y) < 0\}$ if the latter is nonempty.

**Proof**

(a) $y \in Y$ with $\psi(y) < 0$ be arbitrarily chosen. For any $h \in Y$, there is some sufficiently small $\lambda > 0$ with

$$\psi(y + \lambda h) \leq \psi(y) + \lambda\psi(h) < 0 \text{ for all } \lambda \in [0, \tilde{\lambda}].$$

This implies $y \in \text{core}(-C)$. By assumption, there exists some $\bar{y} \in Y$ with $\psi(\bar{y}) < 0$. Then there is some $\lambda > 0$ with $-\lambda\bar{y} \in -C$. Consequently, we obtain

$$\psi(y) = \psi(y - \lambda\bar{y} + \lambda\tilde{y}) \leq \psi(\lambda\tilde{y}) \leq \lambda\psi(\tilde{y}) < 0.$$

which has to be shown.

Under the assumptions of Theorem 2.1, it then follows

$$y \in \text{core}(-C) \subseteq \{y \in Y \mid \psi(y) < 0\}$$

if the latter is nonempty.

**Proposition 2.8** ([74, Proposition 3.7]) Let Assumption 2.1 be satisfied, and let $\psi$ be a $-C$ representing functional. If $y \in Y$ with $\psi(y) < 0$ be arbitrarily chosen, then $y \in \text{core}(-C)$.

**Proof** Since $\psi(y) < 0$, we have $y \in \text{core}(-C)$.

**Proposition 2.9** ([74, Proposition 3.8]) Let $(Y, \|\cdot\|)$ be a real normed space, and let some continuous functional $\ell \in Y^*$ be chosen. Then $C = \{y \in Y \mid \ell(y) \leq 0\}$ is a convex cone.

**Proof** Since $\psi(y) < 0$, we have $y \in \text{core}(-C)$.

**Proposition 2.10** Let Assumption 2.1 be satisfied, and let $\psi$ be a $-C$ representing functional. If $\psi$ is positively homogeneous, i.e., $\psi(\lambda y) = \lambda\psi(y)$ for all $y \in Y$ and $\lambda \geq 0$, or subadditive, i.e., $\psi(y^1 + y^2) \leq \psi(y^1) + \psi(y^2)$ for all $y^1, y^2 \in Y$, then $\psi(0) = 0$.

## 2.5 Directional Derivative

Directional derivatives cannot be given in general $-C$ representing functionals, of course. However, in special linear spaces and for special functionals $\psi$, this is possible. Directional derivatives can be useful in the context of optimality.
