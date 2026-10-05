
The balance equation of this class arise in the ML problems with the RPM-QuaRand models. The probabilities of belonging that characterize the parameters of these models can be normalized or interval-type. In the former case, the ML-based estimation algorithm is formulated as a constrained maximization problem for the generalized Boltzmann information entropy. In the latter case, it seems more convenient to choose the generalized Fermi information entropy.

Write the empirical balance equations for the normalized probabilities of belonging (6.52) in the form

$$\begin{array}{r} {m_{j}(\mathbf{v}) = {\sum\limits_{h = 1}^{R}\frac{\beta^{(h)}(v_{1},\ldots,v_{s};\, j)}{\alpha^{(h)}(v_{1},\ldots,v_{s})}} + \gamma_{j}(v_{1},\ldots,v_{s}) = 0,\quad j = \overline{1,s},} \\ \end{array}$$

(7.17)

where

$$\begin{aligned} {\alpha^{(h)}(v_{1},\ldots,v_{s})} & {= {\sum\limits_{k = 1}^{V_{h}}p_{k}^{(h,0)}}{\prod\limits_{l = 1}^{V_{h}}v_{l}^{z_{k}^{(h)}\lbrack l\rbrack}},} \\ {\beta_{k}^{(h)}(v_{1},\ldots,v_{s};\, j)} & {= {\sum\limits_{k = 1}^{V_{h}}z_{k}^{(h)}}\lbrack j\rbrack p_{k}^{(h,0)}{\prod\limits_{l = 1}^{V_{h}}v_{l}^{z_{k}^{(h)}\lbrack l\rbrack}},} \\ {\gamma_{j}(v_{1},\ldots,v_{s})} & {= S\lbrack j\rbrack + \frac{q_{j}^{0}Z_{j}v_{j}^{Z_{j}}}{{\sum\limits_{l = 1}^{s}q_{j}^{0}}v_{j}^{Z_{l}}} - y\lbrack j\rbrack,} \\ v_{l} & {= \exp( - \theta_{l}),\text{\quad\quad}l = \overline{1,s}.} \\ \end{aligned}$$

(7.18)

The variables in these equations are defined on the nonnegative orthant *R*[+]^(*s*). Sometimes, they are called the exponential Lagrange multipliers.

Consider the empirical balance equations for the interval probabilities of belonging (6.58) and represent them in terms of the variables (*v*[1],…, *v*[*s*]) ≥ 0 (7.18). Introduce the following notations:

$$\begin{aligned} {\varrho_{j}^{(h)}(v_{1},\ldots,v_{s})} & {= {\sum\limits_{i = 1}^{V_{h}}\frac{p_{i}^{(h,0)}}{p_{i}^{(h,0)} + {\prod\limits_{l = 1}^{s}v_{l}^{z_{i}^{(h)}\lbrack l\rbrack}}}},} \\ {\vartheta_{j}(v_{j})} & {= Z_{j}\frac{q_{j}^{0}}{q_{j}^{0} + v_{j}^{Z_{j}}},} \\ {\omega\lbrack j\rbrack} & {= \vartheta_{j}(v_{j}) + \hat{s}\lbrack j\rbrack + \zeta_{j}^{-} - y\lbrack j\rbrack.} \\ \end{aligned}$$

(7.19)

Write equations (6.58) as

$$\begin{array}{r} {n_{j}(\mathbf{v}) = {\sum\limits_{h = 1}^{R}\varrho_{j}^{(h)}}(v_{1},\ldots,v_{s}) + \omega\lbrack j\rbrack = 0,\text{\quad\quad}j = \overline{1,s}.} \\ \end{array}$$

(7.20)

The final forms of the empirical balance equations allow us to identify some general properties of these equations, which can be fruitful for choosing appropriate computational methods.

## 7.2 Monte Carlo Packet Iterations for Global Optimization

The RML algorithms for the RPM-Orig and RPM-Rel models are intended for solving the empirical balance equations, in which the role of variables is played by the Lagrange multipliers or by the auxiliary variables taking their values within the unit nonnegative cube. An approach to design numerical methods proceeds from minimization of a residual function (generally, a quadratic norm). In an RML problem, there exists an algorithmically defined relation between the residual function and variables, and this feature of the problem finally reduces it to a global minimization problem. Under such conditions, the Monte Carlo method seems to be an suitable design tool for RML algorithms.

Vast amounts of literature have been published dealing with applications of the Monte Carlo method in different global optimization problems. Some insight into these problems and methods to solve them can be gained from \[135, 158, 171–[173](#refbib.xhtml#r173), [196](#refbib.xhtml#r196), [199](#refbib.xhtml#r199)\].

In contrast to the existing methods, the idea put forward here is to use *simple Monte Carlo simulations*, i.e., the generation of independent random vectors with the uniform distribution on the nonnegative unit cube.

### 7.2.1 Canonical form of global optimization problem

Consider the global minimization problem

$$\begin{aligned} & \left. f(\mathbf{x})\Rightarrow\text{globmin} \right. \\ & \text{subject~to~the~following~constraints:} \\ & {\mathbf{x} \in \mathcal{G}_{\mathbf{x}} = \left\{ \mathbf{x}:\mathbf{g}(\mathbf{x}) \leq \mathbf{0},\, \mathbf{x} \in R^{d} \right\},\quad\mathbf{g} \in R^{r},\, r < d.} \\ \end{aligned}$$

(7.21)

The objective function *f*(**x**) satisfies the Hölder condition with constants *H* > 0 and *w* > 0, i.e., its modulus of continuity has the form

$$\begin{array}{r} \left. \omega(t) = \max_{(\widetilde{\mathbf{v}},\widetilde{\mathbf{y}}) \in R^{d}\mspace{2mu}:\|\widetilde{\mathbf{v}} - \widetilde{\mathbf{y}}\| \leq t} \middle| f(\widetilde{\mathbf{v}}) - f(\widetilde{\mathbf{y}}) \middle| \leq Ht^{w}. \right. \\ \end{array}$$

(7.22)

The functions **g**(**x**) in (7.22) are assumed to be continuous.

Write *the canonical form* of the problem (7.21) as

$$\begin{aligned} & \left. F(\mathbf{z})\Rightarrow\text{globmin} \right. \\ \end{aligned}$$

(7.23)

$$\begin{aligned} & \text{subject~to~the~following~constraints:} \\ & {\mathbf{z} \in \mathcal{K}_{\mathbf{z}} = \mathcal{G}_{\mathbf{z}}{\cap Z_{+}^{d}},} \\ & {Z_{+}^{d} = \left\{ \mathbf{z}:\mathbf{0} \leq \mathbf{z} \leq \mathbf{1} \right\} \subset R^{d},} \\ & {\mathcal{G}_{\mathbf{z}} = \left\{ \mathbf{z}:\mathbf{w}(\mathbf{z}) \leq \mathbf{0},\, \mathbf{z} \in Z_{+}^{d} \right\},\quad\mathbf{w} \in R^{r},\, r < d.} \\ \end{aligned}$$

(7.24)

A relation between the original problem and its canonical form is defined by a continuously differentiable bijective transformation of the variables, i.e.,

$$\begin{array}{r} {\mathbf{z} = \mathcal{T}(\mathbf{x}),\text{\quad\quad}\mathbf{x} = \mathcal{T}^{( - 1)}(\mathbf{z}).} \\ \end{array}$$

(7.25)

In fact, quite a few transformations answer these conditions, e.g.,

$$\begin{aligned} & {\mathbf{z} = \left\{ \frac{1}{1 + exp( - a_{i}x_{i})},\, \middle| \, i = \overline{1,d} \right\},} \\ & {\mathbf{x} = \left\{ \frac{1}{a_{i}}\ln\frac{z_{i}}{1 - z_{i}},\, \middle| \, i = \overline{1,d} \right\}.} \\ \end{aligned}$$

(7.26)

Due to the continuity of the transformation (7.26), the function *F*(**z**) is bounded below on 𝒦[**z**], i.e., there exists a constant *c* such that

$$\begin{array}{r} {F^{\*} \geq c.} \\ \end{array}$$

(7.30)

The constant *c* is generally unknown but equals 0 in some special global minimization problems. For example, this takes place for the problems in which the function *F*(**z**) is defined as the residual between the left- and right-hand sides of a certain system of equations.

The function *F*(**z**) also satisfies the Hölder condition with other constants *L* and *p*, i.e.,

$$\begin{array}{r} \left. \omega(h) = \max_{(\mathbf{v},\mathbf{y}) \in \mathcal{K}_{\mathbf{x}}\mspace{2mu}:\|\mathbf{v} - \mathbf{y}\| \leq h} \middle| F(\mathbf{v}) - F(\mathbf{y}) \middle| \leq Lh^{s}. \right. \\ \end{array}$$

(7.31)

Denote by *ℤ*^(*) the set of all global minimum points **z**^(*) and by *F*(**z**^(*)) = *F*^(*) the global minimum value in the problem (7.23). In other words, assume that a global minimum is achieved not at a unique point but on a finite set ℤ^(*).
