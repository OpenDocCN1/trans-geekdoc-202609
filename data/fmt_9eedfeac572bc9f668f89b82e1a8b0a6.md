
$$
\begin{array}{r} {\hat{\mathcal{Y}} = \mathcal{F}\left( {X,\mathbf{a},P(\mathbf{a})} \right),} \\ \\ \end{array}
$$

$$
(4.8)
$$

where $\hat{\mathcal{Y}}$ denotes an ensemble of random vectors $\hat{\mathbf{y}}.$

### 1. Linear static RPMs.

This class of the models involves a linear vector function **F** (4.6) of the form

$$
\begin{array}{r} {\hat{\mathcal{Y}} = A\, X,} \\ \\ \end{array}
$$

$$
(4.9)
$$

where *A* is a matrix of dimensions (*m* × *n*) with the randomized elements (4.4, 4.5) and the probabilistic properties characterized by a PDF *P*(*A*).

If the RPM (4.6) has *n* inputs and one output, then the output ensemble consists of the values of a random variable

$$
\begin{array}{r} {\hat{y} = \left\langle \mathbf{x},\mathbf{a} \right\rangle.} \\ \\ \end{array}
$$

$$
(4.10)
$$

### 2. Nonlinear static RPMs.

The nonlinear RPMs form a significantly wider class than the linear ones. The nonlinear processes that occur in nature are modeled using appropriate laws. If a certain relation between an input and output of an object surely exists but its form is unknown, then a more of less universal approach lies in approximation. Here it is necessary to define a structure and parameters of an approximating function. As a result, to design a nonlinear static RPM means to search for appropriate parameter values. Consider some types of approximations and also the underlying hypotheses on the properties of the “Single Input–Ensemble Output” relations.

#### 2.1. Analytical nonlinearities.

By a prevailing hypothesis, there exists an analytical relation between the input and output matrices, *X* and *Y*. This hypothesis allows us to perform approximation using the *Taylor monomial*

$$
\begin{array}{r} {\hat{\mathcal{Y}} = {\sum\limits_{h = 1}^{R}B^{(h)}}\, Z^{(h)}.} \\ \\ \end{array}
$$

$$
(4.11)
$$

Here *B*^((*h*)) denotes a matrix of dimensions (*s* × *φ*(*h*)) with interval-type randomized elements, and *Z*^((*h*)) is a matrix of dimensions (*φ*(*h*)) × *r* whose entries represent the products of degree *h* from the elements of the input matrix *X*. The matrices *B*^((*h*)) are defined on the intervals

$$
\begin{array}{r} {\mathcal{B}_{h} = \lbrack\mathcal{B}_{h}^{-},\mathcal{B}_{h}^{+}\rbrack,\text{\quad\quad}h = \overline{1,R}.} \\ \\ \end{array}
$$

$$
(4.12)
$$

For a one-dimensional static object (with one input and one output), equality (4.11) takes the simpler form

$$
\begin{array}{r} {\hat{y} = {\sum\limits_{h = 1}^{R}b_{h}}x^{h},} \\ \\ \end{array}
$$

$$
(4.13)
$$

where the parameters *b*[1], …, *b*[*R*] are randomized and independent. The domain of definition of the parameters *b*[1], …, *b*[*R*] is given by

$$
\begin{array}{r} {b_{h} \in \mathcal{B}_{h} = \lbrack b_{h}^{-},b_{h}^{+}\rbrack,\text{\quad\quad}h = \overline{1,R}.} \\ \\ \end{array}
$$

$$
(4.14)
$$

#### 2.2. Continuous nonlinearities.

In fact, the existence of an analytical relation between an input and output of a static nonlinearity is a bold hypothesis. Following a more realistic approach, assume that the input is bounded and the nonlinearity *Φ*(*x*) has no discontinuities of the second kind (infinite jumps). Numerous approximation methods with orthogonal polynomials were developed on the basis of these hypotheses.

Recall some fundamental concepts of the corresponding methods. Consider a one-dimensional static object with a bounded input and a nonlinear characteristic that has no discontinuities of the second kind:

$$
\begin{array}{r} {x^{-} \leq x \leq x^{+}.} \\ \\ \end{array}
$$

By assumption, there exists a certain function *w*(*x*) on this interval, which is often interpreted as a weight characteristic for the values of the variable *x*. Since the nonlinearity *Φ*(*x*) of the static object is considered on the same interval without discontinuities of the second kind,

$$
\begin{array}{r} {{\int_{x^{-}}^{x^{+}}w}(x)\Phi^{2}(x)dx < \infty.} \\ \\ \end{array}
$$

To obtain orthogonal polynomials, choose a system of power functions 1, *x*, *x*², … and apply the following orthogonalization procedure:

$$
\begin{array}{r} {\psi_{0}(x) = c_{0},} \\ \\ \end{array}
$$

$$
\begin{array}{r} {\psi_{1}(x) = c_{0} + c_{1}x,} \\ \\ \end{array}
$$

$$
\begin{array}{r} {\psi_{2}(x) = c_{0} + c_{1}x + c_{2}x^{2},} \\ \\ \end{array}
$$

$$
\begin{array}{r} {\cdots = \cdots + \cdots + \cdots} \\ \\ \end{array}
$$

The coefficients *c*[0], *c*[1], *c*[2], … in these formulas are adjusted so that

$$
\begin{array}{r} {{\int_{x^{-}}^{x^{+}}w}(x)\psi_{i}^{2}(x)dx = 1,\text{\quad\quad}i = 0,1,2,\ldots} \\ \\ \end{array}
$$

and

$$
\begin{array}{r} {{\int_{x^{-}}^{x^{+}}w}(x)\psi_{i}(x)\psi_{i - 1}(x)dx = 0,\text{\quad\quad}i = 1,2,\ldots} \\ \\ \end{array}
$$

This procedure yields a system of orthogonal polynomials. The weight function *w*(*x*) defines the class of a corresponding orthonormal polynomial. Some classes are presented in Table 4.1.

Table 4.1: Orthonormal polynomials.

|  |
| --- |
| Class || Interval || *w*(*x*) || Polynomial |
| Lagerra || \[0, ∞) || *e*^( − *x*) || 1, 1 − *x*, 1 − 2*x* + *x*²/2, ... |
| --- | --- | --- | --- |
| Hermit || ( − ∞, ∞) || *e*^( − *x*²) || 1, 2*x*, 4*x*² − 2, ... |
| Legendre || \[ − 1, 1\] || 1 || 1, *x*, (3*x*² − 1)/2, ... |
| Chebyshev || \[ − 1, 1\] || $1/\sqrt{1 - x^{2}}$ || 1, *x*, 2*x*² − 1, ... |
|  |

Using the system of orthonormal polynomials, construct an approximating polynomial with the parameters *a*[0], …, *a*[*R*] by

$$
\begin{array}{r} {\hat{\Phi}(x) = {\sum\limits_{i = 0}^{R}a_{i}}\psi_{i}(x).} \\ \\ \end{array}
$$

$$
(4.15)
$$

In contrast to the classical approach to approximation, the parameters of an approximating function will be treated as randomized ones taking values within an interval \[**a**^−, **a**^+\].

### 4.2.2 Functional description of dynamic models

An output ensemble of dynamic models at a time *t* is characterized by a mapping 𝕄\[*P*(**a**), *τ*, *t*\] of the form (4.1) and depends on the input data on a time interval \[*t* − *τ*, *t*\] and a realization of the randomized parameters.

用 **x**(*τ*) 表示由独立观测 *x*1, …, *x**n* 组成 的输入向量，它们定义在时间区间 𝒯[*t*] = [0, *t*] 上，其中 *τ* ∈ 𝒯[*t*]。在每个时间 *t* > 0 时，模型输出一个由观测 *ŷ*1, …, *ŷ**m* 组成的向量 $\hat{\mathbf{y}}(t)$，其中 *t* ∈ 𝒯 = [0, *T*]。输入 **x**(*τ* | *τ*∈𝒯[*t*]) 与输出 $\hat{\mathbf{y}}(t)$ 之间的关系由泛函 ℬ 描述，即

$$
\begin{array}{r}
\left.
\hat{\mathbf{y}}(t) = \mathcal{B}(\mathbf{x}(\tau),\mathbf{a}\, \middle| \,\tau \in \mathcal{T}_{t}),\quad\quad t \in \mathcal{T} = \lbrack 0,T\rbrack.
\right.
\\
\end{array}
$$

$$
(4.16)
$$

假设该泛函由随机元向量 **a** = {*a*[1],…,*a*[*r*]} 参数化，它们属于区间

$$
\begin{aligned}
\mathcal{A}_{i} & {= \lbrack a_{i}^{-},a_{i}^{+}\rbrack,\quad\quad i \in \lbrack 1,r\rbrack;} \\
\mathcal{A} & {= {\prod\limits_{i = 1}^{r}\mathcal{A}_{i}}.}
\\
\end{aligned}
$$

$$
(4.17)
$$

将考虑三类动态“单输入-集合输出”RPM，即线性模型，以及具有幂非线性和多项式非线性的非线性模型。

### 4.2.3 线性动态模型

考虑一个具有输入 **x**(*τ*), *τ* ∈ 𝒯[*t*] 和输出 $\hat{\mathbf{y}}(t),\, t \in \mathcal{T}.$ 的动态 RPM。输入向量元素 $x_{i}(\tau),\, i = \overline{1,n},$ 是 *连续时变函数*。该 RPM 输入与输出之间的关系由具有参数 **a** 的 *线性* 泛函 ℬ 描述 (4.16)，即

$$
\begin{array}{r}
{\hat{\mathbf{y}}(t) = {\int_{0}^{t}B}(t,\tau,\,\mathbf{a})\mathbf{x}(\tau)d\tau.}
\\
\end{array}
$$

$$
(4.18)
$$

在此式中，矩阵 *B*(*t*, *τ*, **a**) 的维数为 (*m* × *n*)，由脉冲特性 $\left. \lbrack b_{ij}(t,\tau\, \middle| \,\mathbf{a}^{(ij)}),\, \middle| \, i = \overline{1,m},\, j = \overline{1,n}\rbrack \right.$ 组成，其中随机参数 $\mathbf{a}^{(ij)} = \{a[1]^{(ij)},\dots,a[k[ij]]^{(ij)}\}$，*k*[*i**j*] 为脉冲特性 *b**i**j* 的参数个数。

根据一般概念，参数 **a**^((*i**j*)) 为区间型，即

$$
\begin{array}{r}
{\mathbf{a}^{(ij)} \in \mathcal{A}^{(ij)} = \lbrack\mathbf{a}_{-}^{(ij)},\mathbf{a}_{+}^{(ij)}\rbrack,\quad\mathbf{a} \in \mathcal{A} = {\prod\limits_{i = 1}^{m}{\prod\limits_{j = 1}^{n}\mathcal{A}^{(ij)}}}.}
\\
\end{array}
$$

$$
(4.19)
$$

模型 (4.19) 生成随机轨迹 $\hat{\mathbf{y}}(t),\, t \in \mathcal{T}.$ 的集合 ${\hat{\mathcal{Y}}}_{\mathcal{T}}$。这些脉冲特性可以以不同方式参数化。下面将讨论其中一些。

#### 1.1. 具有未知参数的给定函数

通常，脉冲特性是指数函数或具有指数衰减的谐波函数，即

$$
\begin{array}{r}
