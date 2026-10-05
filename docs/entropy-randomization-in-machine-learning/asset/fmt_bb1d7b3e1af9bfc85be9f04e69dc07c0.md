
Here

$$\begin{aligned} & {\mathcal{P}(\theta) = {\int_{\mathcal{A}}\exp}\left\lbrack {- {\sum\limits_{k = 0}^{N}\langle}\theta^{(k)},\mathbb{B}\left( \left. \mathbf{a},X_{(k - \varrho)} \right\rangle \right)} \right\rbrack d\mathbf{a},} \\ & {\text{\quad\quad}\mathcal{Q}_{k}(\theta^{(k)}) = {\int_{\Xi_{k}}\exp}\left( {- \left\langle \theta^{(k)},\xi\lbrack k\rbrack \right\rangle} \right)d\xi\lbrack k\rbrack,} \\ & {\text{\quad\quad}\quad k \neq k^{-},\ldots,k^{+};\quad k = \overline{0,N}.} \\ \end{aligned}$$

(2.108)

The Lagrange multipliers are determined from the system of equations

$$\begin{array}{r} {\frac{\mathbf{M}_{k}(\theta)}{\mathcal{P}(\theta)} + \frac{\mathbf{N}_{k}(\theta^{(k)})}{\mathcal{Q}_{k}(\theta^{(k)})} = \mathbf{y}\lbrack k\rbrack,\text{\quad\quad}k \neq k^{-},\ldots,k^{+};k = \overline{0,N},} \\ \end{array}$$

(2.109)

where

$$\begin{aligned} {\mathbf{M}_{k}(\theta) = \int_{\mathcal{A}}} & {\exp\left\lbrack {- {\sum\limits_{k = 0}^{T}\left\langle \theta^{(k)},\mathbb{B}\left( {\mathbf{a},X_{(k - \varrho)}} \right) \right\rangle}} \right\rbrack\mathbb{B}\left( {\mathbf{a},X_{(k - \varrho)}} \right)d\mathbf{a},} \\ \end{aligned}$$

(2.110)

$$\begin{aligned} & {\mathbf{N}_{k}(\theta^{(k)}) = {\int_{\Xi_{k}}\exp}\left( {- \left\langle \theta^{(k)},\xi\lbrack k\rbrack \right\rangle} \right)\xi\lbrack k\rbrack d\xi\lbrack k\rbrack.} \\ \end{aligned}$$

(2.111)

**b. Omissions in input data**

Restoring omissions in input data is more difficult than the ones in output data. Really, the origin mechanism of input data and the source of its excitation are both unknown. In terms of the approach adopted here, this means that the model generating input data and also the process exciting it are unknown. All these factors increase the level of uncertainty in the problem, motivating the choice of randomization.

The randomized approach consists in using a sequence of independent random vectors $\zeta\lbrack k\rbrack \in R^{q}\\, \,(k\overline{0,N})$ with special probabilistic characteristics, and a randomized parametric model, the choice of which is determined by its complexity.

Well, consider the observation interval *τ* = \[0, *N*\] and an input data set **x** ∈ *R*^(*m*) with omissions **x**\[0\], …, **x**\[*k*^− − 1\], **x**\[*k*^+ + 1\], …, **x**\[*T*\]. The data **x**\[*k*^−\], …, **x**\[*k*^+\] are missing.

To restore the missing input data, assume that they are the result of transforming a sequence of independent random vectors *ζ*\[*k*\] ∈ *R*^(*q*), *k* ∈ *τ*. Let the vectors *ζ*\[*k*\] be of the interval type, i.e.,

$$\begin{array}{r} {\zeta\lbrack k\rbrack \in \mathcal{Z}_{k} = \lbrack\zeta^{-}\lbrack k\rbrack,\zeta^{+}\lbrack k\rbrack\rbrack,\text{\quad\quad}k = \overline{0,N},} \\ \end{array}$$

(2.112)

Due to the uncertainty and insufficient knowledge about the process and its transformation, choose the randomized parametric (RPM-I) model

$$\begin{array}{r} {\hat{\mathbf{x}}\lbrack k\rbrack = \mathbb{F}\left( {\mathbf{c},Z_{(k - \rho)}} \right),} \\ \end{array}$$

(2.113)

where 𝔽 is a nonlinear vector functional with random parameters **c** ∈ *R*^(*s*) and *Z*[(*k* − *ρ*)] is the input matrix of dimensions (*q* × *ρ*) composed of the column vectors *ζ*\[*k*\] ∈ *R*^(*q*), i.e.,

$$\begin{array}{r} {Z_{(k - \rho)} = \left\lbrack {\zeta\lbrack k - \rho\rbrack,\zeta\lbrack k - \rho + 1\rbrack,\ldots,\zeta\lbrack k\rbrack} \right\rbrack.} \\ \end{array}$$

(2.114)

Introduce the matrix

$$\begin{array}{r} {Z = \left\lbrack {Z_{( - \rho)},Z_{(1 - \rho)},\ldots,Z_{(N - \rho)}} \right\rbrack,} \\ \end{array}$$

(2.115)

which characterizes the input of the RPM-I model (2.113) on the time interval $k = \overline{0,N}.$ The matrix *Z* is random and of the interval type:

$$\begin{array}{r} {Z \in \mathcal{Z} = {\underset{k = 0}{\overset{N}{\cup}}\mathcal{Z}_{k}} = \lbrack Z^{-},Z^{+}\rbrack.} \\ \end{array}$$

(2.116)

The random parameters of this model are

$$\begin{array}{r} {\mathbf{c} \in \mathcal{C} = \lbrack\mathbf{c}^{-},\mathbf{c}^{+}\rbrack.} \\ \end{array}$$

(2.117)

The probabilistic properties of the parameters **c** and matrix *Z* (2.115) are characterized by a joint probability density function (PDF) *W*(**c**, *Z*) with the domain of definition

$$\begin{array}{r} {\mathcal{F} = \mathcal{C}{\cup \mathcal{Z}}.} \\ \end{array}$$

(2.118)

This function is assumed to be continuously differentiable.

Let the available input data **x**\[*k*\] contain errors *η*\[*k*\] ∈ *R*^(*m*) of the interval type:

$$\begin{array}{r} {\eta\lbrack k\rbrack \in \mathcal{E}_{k} = \lbrack\eta^{-},\eta^{+}\rbrack.} \\ \end{array}$$

(2.119)

The probabilistic properties of the errors are characterized by PDFs $G_{k}(\eta\lbrack k\rbrack),k = \overline{0,N},$ which are assumed to be continuously differentiable as well.

The observed output of the RPM-I model is given by

$$\begin{array}{r} {\mathbf{z}\lbrack k\rbrack = \hat{\mathbf{x}}\lbrack k\rbrack + \eta\lbrack k\rbrack,\text{\quad\quad}k = \overline{0,N}.} \\ \end{array}$$

(2.120)

Clearly, the missing input data are restored using a model similar to RDM-O, but with the random input *ζ*\[*k*\].

Apply the RML algorithm \[148\] for determining the PDFs *W*(**c**, *Z*) and $G_{k}(\zeta\lbrack k\rbrack),\, k = \overline{0,N}.$ In the case under consideration, this algorithm has the form

$$\begin{aligned} & {\quad\mathcal{H}\lbrack W(\mathbf{c},Z),G(\eta)\rbrack = - {\int_{\mathcal{F}}W}(\mathbf{c},Z)\ln W(\mathbf{c},Z)\, d\mathbf{c}\, dZ -} \\ & \left. - {\sum\limits_{k \in \mathcal{K}}{\int_{\mathcal{E}_{k}}G_{k}}}(\eta\lbrack k\rbrack)\ln G_{k}(\eta\lbrack k\rbrack)d\eta\lbrack k\rbrack\Rightarrow\max, \right. \\ & {\quad{\int_{\mathcal{F}}W}(\mathbf{c},Z)\, d\mathbf{c}\, dZ = 1;\quad{\int_{\mathcal{E}_{k}}G_{k}}(\eta\lbrack k\rbrack)d\eta\lbrack k\rbrack = 1,} \\ & {\quad{\int_{\mathcal{F}}W}(\mathbf{c},Z)\mathbb{F}\left( {\mathbf{c},Z_{(k - \rho)}} \right)d\mathbf{c}\, dZ + {\int_{\mathcal{E}_{k}}G_{k}}(\eta\lbrack k\rbrack)\eta\lbrack k\rbrack d\eta\lbrack k\rbrack = \mathbf{x}\lbrack k\rbrack,} \\ & {\quad k \in \mathcal{K},} \\ \end{aligned}$$

(2.121)

where the indexing set $\mathcal{K} = \overline{0,N}$ does not include *k* = *k*^−, …, *k*^+.

This problem belongs to the same class as (2.106). Its solution is given by

$$\begin{array}{rll} & {W^{\*}(\mathbf{c},Z,\lambda) = \frac{\exp\left\lbrack {- {\sum\limits_{k \in \mathcal{K}}\langle}\lambda^{(k)},\mathbb{F}\left( \left. \mathbf{c},Z_{(k - \rho)} \right\rangle \right)} \right\rbrack}{\mathcal{W}(\lambda)},} & \\ & {G_{k}^{\*}(\eta\lbrack k\rbrack,\lambda^{(k)}) = \frac{\exp\left( {- \left\langle \lambda^{(k)},\eta\lbrack k\rbrack \right\rangle} \right)}{\mathcal{G}_{k}(\lambda^{(k)})},} & \\ & {k \in \mathcal{K},} & \\ \end{array}$$

(2.122)

where

$$\begin{aligned} {\mathcal{W}(\lambda) = \int_{\mathcal{F}}} & {\exp\left\lbrack {- \sum\left\langle \lambda^{(k)},\mathbb{F}\left( \left. \mathbf{c},Z_{(k - \rho)} \right\rangle \right) \right.} \right\rbrack d\mathbf{c},\quad\mathcal{G}_{k}(\lambda^{(k)}) =} \\ & {\,\, = int_{\mathcal{E}_{k}}\exp\left( {- \left\langle \lambda^{(k)},\eta\lbrack k\rbrack \right\rangle} \right)d\eta\lbrack k\rbrack.} \\ \end{aligned}$$

(2.123)

In the equalities presented above, *λ*^((*k*)) is the vector of Lagrange multipliers corresponding to the *k*th balance constraint. This vector satisfies the system of equations
