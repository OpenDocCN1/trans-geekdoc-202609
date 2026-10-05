
$$
\begin{array}{r}
{{\int_{\mathcal{R}}F}(\mathbf{a},\overline{\mu})\, d\mathbf{a}\, d\,\overline{\mu} = 1,\quad\quad{\int_{\Xi_{j}}Q_{j}}({\overline{\xi}}^{(j)})\, d{\overline{\xi}}^{(j)} = 1,\quad j = \overline{1,s};} \\
\end{array}
$$

(5.36)

* —the balance constraints for the *k*-means of the observed output (5.33) and the real data, i.e.,

$$
\begin{array}{r}
{\mathbf{m}^{(k)}\lbrack F(\mathbf{a},\overline{\mu}),Q_{j}({\overline{\xi}}^{(j)}),j\rbrack = \mathbf{y}(t_{j}),\quad\quad j = \overline{1,s}.} \\
\end{array}
$$

(5.37)

Due to (5.15), the vector $\mathbf{m}^{(k)}\lbrack F(\mathbf{a},\overline{\mu}),Q_{j}({\overline{\xi}}^{(j)}),j\rbrack$ in these equality constraints has the components

$$
\begin{aligned}
{m_{i}^{(k)}\lbrack j\rbrack =} & {\left\lbrack {\int_{\mathcal{R}}F}(\mathbf{a},\overline{\mu})\mathbf{y}\lbrack t_{j}\, \middle| \, F(\mathbf{a},{\overline{\mu}}^{(t_{j})})\rbrack\, d\mathbf{a}d\overline{\mu} \right\rbrack^{1/k} +} \\
& {\left\lbrack {{\int_{\Xi_{j}}}\,}Q_{j}({\overline{\xi}}^{(j)})\,{\lbrack\xi_{i}^{(j)}\rbrack}^{k}\, d\xi_{i}^{(j)}} \right\rbrack^{1/k},} \\
& {\quad\quad\quad i = \overline{1,m},\, j = \overline{1,s}.} \\
\end{aligned}
$$

(5.38)

Consider the case in which the balance constraints involve the 1-mean of the RPM-F model output:

$$
\begin{aligned}
{m_{i}^{(1)}\lbrack j\rbrack =} & \left. {\int_{\mathcal{R}}F}(\mathbf{a},\overline{\mu})\mathbf{y}\lbrack t_{j}\, \middle| \, F(\mathbf{a},{\overline{\mu}}^{(t_{j})})\rbrack\, d\mathbf{a}d\overline{\mu} + \right. \\
& {{\int_{\Xi_{j}}}\,}Q_{j}({\overline{\xi}}^{(j)})\,\lbrack\xi_{i}^{(j)}\rbrack d\xi_{i}^{(j)},} \\
& {\quad i = \overline{1,m},\, j = \overline{1,s}.} \\
\end{aligned}
$$

(5.39)

Like in the optimization problem presented above, the functional constraints extract the subset $\Gamma\lbrack F(\mathbf{a},\overline{\mu}),Q(\overline{\xi})\rbrack$ of all admissible functions, where $Q(\overline{\xi}) = \left\{ Q_{1}({\overline{\xi}}^{(1)}),\ldots,Q_{s}({\overline{\xi}}^{(s)}) \right\},$ from the class ℂ¹. The problem (5.2.3—5.2.3) is also of the Lyapunov type.

*For the RPM-F model with input and output data errors, the entropy-robust RML algorithm* has the form

$$
\begin{array}{r}
{\left\lbrack {F(\mathbf{a},\overline{\mu}),\overline{Q}(\overline{\xi})} \right\rbrack^{\*} = \arg\max_{\lbrack F(\mathbf{a},\overline{\mu}),\overline{Q}(\overline{\xi})\rbrack}\left\{ \mathcal{H},\, \middle| \,\lbrack F(\mathbf{a},\overline{\mu}),\overline{Q}(\overline{\xi})\rbrack \in \Gamma \right\},} \\
\end{array}
$$

(5.40)

where the admissible set Γ is given by the normalization conditions (5.36) and the empirical balance constraints (5.2.3).

## 5.3 Optimality Conditions for Lyapunov-Type Problems

A comprehensive study of the Lyapunov-type functional programming problems, including a possible application of Lagrange's method of multipliers, can be found in the monographs \[77, 174\]. This section will briefly describe a mathematical framework based on the cited results and the Gateaux derivative \[[114](#refbib.xhtml#r114)\].

A minimization problem with integral nonlinear functionals (a Lyapunov-type problem) can be written as

$$
\begin{array}{r}
\left. \mathcal{J}\lbrack f(\mathbf{x})\rbrack = {\int_{\mathcal{X}}\Phi}\left\lbrack {f(\mathbf{x})} \right\rbrack d\mathbf{x}\Rightarrow\min_{f(\mathbf{x})} \right. \\
\end{array}
$$

(5.41)

subject to the constraints

$$
\begin{array}{r}
{\mathcal{G}_{i}\lbrack f(\mathbf{x})\rbrack = {\int_{\mathcal{X}}\Psi_{i}}\left\lbrack {f(\mathbf{x})} \right\rbrack d\mathbf{x} = 0,\quad\quad i = \overline{1,m}.} \\
\end{array}
$$

(5.42)

Here **x** ∈ *R*^(*n*), the functions *Φ*\[ • \], *Ψ*[1]\[ • \], …, *Ψ*[*m*]\[ • \] and also the desired function *f*( • ) that minimizes the functional 𝒥\[ • \] belong to the class *ℂ*¹ of all continuously differentiable functions.

Define the Lagrange functional by

$$
\begin{array}{r}
{\mathcal{L}\lbrack f(\mathbf{x})\rbrack = {\int_{\mathcal{X}}\mathcal{J}}\lbrack f(\mathbf{x})\rbrack - {\sum\limits_{i = 1}^{m}\lambda_{i}}{\int_{\mathcal{X}}\Psi_{i}}\left\lbrack {f(\mathbf{x})} \right\rbrack d\mathbf{x}.} \\
\end{array}
$$

(5.43)

The first-order optimality condition claims that the variation of this functional with respect to the function *f*(**x**) is zero, i.e.,

$$
\begin{array}{r}
{\delta\mathcal{L} = 0.} \\
\end{array}
$$

(5.44)

Because the function under variation belongs to the class ℂ¹, condition (5.44) is equivalent to the zero value of the Gateaux derivative of the functional ℒ.

Recall the definition of the Gateaux derivative. Consider a functional ℰ\[*w*(**u**)\], where *w*(**u**) ∈ ℂ¹ is a scalar function, **u** ∈ *R*^(*n*). Take an arbitrary function *h*(**u**) ∈ ℂ¹, and introduce a linear combination *w*^(\*)(**u**) + *α**h*(**u**), where *α* denotes a real variable and *w*^(\*)(**u**) is a certain fixed function from *ℂ*¹ that possesses some necessary properties (e.g., minimizes the functional ℰ). For a chosen function *h*(**u**), the functional ℰ becomes a function of the real variable *α*. The Gateaux derivative of the functional ℰ is given by

$$
\begin{array}{r}
\left. D\mathcal{E} = \frac{d}{d\alpha}\mathcal{E}\lbrack w^{\*}(\mathbf{u}) + \alpha h(\mathbf{u})\rbrack \middle| {}_{\alpha = 0}. \right. \\
\end{array}
$$

(5.45)

Getting back to the Lagrange functional (5.43), consider an arbitrary function *h*(**x**) from the class *ℂ*¹ and the real variable *α*. Denote by *f*^(\*)(**x**) the function that yields minimum in the problem (5.41, 5.42). Represent an arbitrary function *f*(**x**) as the linear combination

$$
\begin{array}{r}
{f(\mathbf{x}) = f^{\*}(\mathbf{x}) + \alpha h(\mathbf{x}).} \\
\end{array}
$$

(5.46)

Under fixed *f*^(\*)(**x**) and *h*(**x**), the Lagrange functional (5.43) turns out to be a function of the real variable *α*, i.e.,

$$
\begin{array}{r}
{\mathcal{L} = {\int_{X}\Phi}\left\lbrack {f^{\*}(\mathbf{x}) + \alpha h(\mathbf{x})} \right\rbrack d\mathbf{x} - {\sum\limits_{i = 1}^{m}\lambda_{i}}{\int_{X}\Psi_{i}}\left\lbrack {f^{\*}(\mathbf{x}) + \alpha h(\mathbf{x})} \right\rbrack d\mathbf{x}.} \\
\end{array}
$$

(5.47)

Then the first-order optimality condition for the Lagrange functional takes the form

$$
\begin{array}{r}
{D\mathcal{L} = {\int_{X}h}(\mathbf{x})\left( {\frac{d\Phi(y)}{dy} - {\sum\limits_{i = 1}^{m}\lambda_{i}}\,\frac{d\Psi_{i}(y)}{dy}} \right)d\mathbf{x} = 0,} \\
\end{array}
$$

(5.48)

where *y* is a scalar argument of the functions Φ and *Ψ*[1], …, *Ψ*[*m*]. For this integral expression to vanish, a necessary condition is that its integrand takes zero value for any function *h*(**x**) ∈ ℂ¹.

Consequently, *the first-order optimality condition in the problem (5.41, 5.42)* can be written as

$$
\begin{array}{r}
{\frac{d\Phi(y)}{dy} = {\sum\limits_{i = 1}^{m}\lambda_{i}}\frac{d\Psi_{i}(y)}{dy}.} \\
\end{array}
$$

(5.49)

Here the derivatives of the functions *Φ*, *Ψ*[1], …, *Ψ*[*m*] depend on *f*^(\*)(**x**), the function that minimizes the functional (5.41), i.e.,

$$
\begin{array}{r}
{d\Phi(y)dy = \phi\lbrack f^{\*}(\mathbf{x})\rbrack,\quad\quad d\Psi_{i}(y)dy = \psi_{i}\lbrack f^{\*}(\mathbf{x})\rbrack,\quad i = \overline{1,m}.} \\
\end{array}
$$

(5.50)

Hence, equality (5.49) can be transformed into

$$
\begin{array}{r}
{\phi\lbrack f^{\*}(\mathbf{x})\rbrack = {\sum\limits_{i = 1}^{m}\lambda_{i}}\psi_{i}\lbrack f^{\*}(\mathbf{x})\rbrack.} \\
\end{array}
$$

(5.51)
