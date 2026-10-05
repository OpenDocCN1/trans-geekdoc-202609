
Consider a scalar continuous function `φ`(`x`, `θ`) with parameters `θ` = {`θ`[1],…,`θ`[*n*]}. Assume that this function is a characteristic of an object's model with an input `x` and an output `y`. Let `x`^((*r*)) = {`x`[1],…,`x`[*r*]} and `y`^((*r*)) = {`y`[1],…,`y`[*r*]} be given measurements. Note that the latter are obtained with random errors `ξ` = {`ξ`[1],…,`ξ`[*r*]}, in the general case, different for different time instants.

Thus, after `r` measurements the model and observations are described by the equations

$$
\begin{aligned}
\hat{\mathbf{y}} & {= \Gamma(\mathbf{x}^{(r)},\theta),} \\
\hat{\mathbf{v}} & {= \hat{\mathbf{y}} + \xi,} \\
\end{aligned}
$$

(A.1)

where the vector function `Γ`(`x`^((*r*)), `θ`) has the components $\varphi(x\lbrack t\rbrack,\theta),\, t = \overline{1,r};$ $\hat{\mathbf{v}}$ denotes the observed output of the model containing measurement noises of the object's output.

The estimation problem is stated as follows: *find the maximum entropy estimates of the PDFs `P*`(`θ`) and `Q*`(`ξ`) that maximize the generalized information entropy functional*

$$
\begin{aligned}
& {\mathcal{H}\lbrack P(\theta),Q(\xi)\rbrack = - {\int_{Q}P}(\theta)\ln P(\theta)d\theta -} \\
& \left. \quad - {\sum\limits_{t = 1}^{r}{\int_{\Xi_{t}}Q_{t}}}(\xi\lbrack t\rbrack)\ln Q_{t}(\xi\lbrack t\rbrack)\Rightarrow\max \right. \\
\end{aligned}
$$

(A.5)

*subject to*

* —the normalization conditions of the PDFs given by

$$
\begin{array}{r}
{{\int_{\Theta}P}(\theta)d\theta = 1;\quad{\int_{\Xi_{t}}Q_{t}}(\xi\lbrack t\rbrack)d\xi\lbrack t\rbrack = 1,\, t = \overline{1,r}.} \\
\end{array}
$$

(A.6)

and

* —the empirical balance conditions

$$
\begin{aligned}
& {\Phi\lbrack P(\theta),Q(\xi)\rbrack = \mathbf{y}^{(r)},} \\
{\Phi\lbrack P(\theta),Q(\xi)\rbrack =} & \left\{ \Phi_{1}\lbrack P(\theta),Q(\xi)\rbrack,\ldots,\Phi_{r}\lbrack P(\theta),Q(\xi)\rbrack \right\} \\
{\Phi_{t}\lbrack P(\theta),Q(\xi)\rbrack = \int_{\Theta}} & {\varphi(x\lbrack t\rbrack,\theta)P(\theta)d\theta + \int_{\Xi_{t}}Q_{t}(\xi\lbrack t\rbrack)\xi\lbrack t\rbrack d\xi\lbrack t\rbrack,} \\
& {\text{\quad\quad}\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.7)

The optimization problem (A.1–A.1) is of the Lyapunov type [77, 174]: such problems have an integral functional and also integral constraints. Hence, the entropy-optimal PDFs of the model parameters and measurement noises have the form

$$
\begin{aligned}
\left. P^{\*}(\theta\, \middle| \,\mathbf{y}^{(r)}\,\mathbf{x}^{(r)}) \right. & {\frac{\exp\left( {- {\sum\limits_{j = 1}^{r}\lambda_{j}}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)}{\mathcal{P}(\lambda(\mathbf{y}^{(r)}),\mathbf{x}^{(r)})},} \\
\left. Q_{t}^{\*}(\xi\lbrack t\rbrack\, \middle| \,\mathbf{y}^{(r)}\,\mathbf{x}^{(r)}) \right. & {\frac{\exp\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\xi\lbrack t\rbrack} \right)}{\mathcal{Q}_{t}(\lambda_{t}(\mathbf{y}^{(r)}),\mathbf{x}^{(r)})},\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.8)

where

$$
\begin{aligned}
{\mathcal{P}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)}) = \int_{\Theta}} & {\exp\left( {- \sum_{j = 1}^{r}\lambda_{j}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta,} \\
{\mathcal{Q}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})} & {\int_{\Xi_{t}}\exp\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\xi\lbrack t\rbrack} \right)d\xi\lbrack t\rbrack,} \\
& {\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.9)

Due to equalities (A.1) and (A.1), the entropy-optimal PDFs are parameterized by the Lagrange multipliers `λ`[1],…, `λ`[*r*], which represent the solutions of the empirical balance equations

$$
\begin{array}{r}
{\frac{\mathcal{G}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))}{\mathcal{P}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))} + \frac{\mathcal{E}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))}{\mathcal{Q}_{t}\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})} \right)} = y\lbrack t\rbrack,\quad t = \overline{1,r},} \\
\end{array}
$$

(A.10)

where

$$
\begin{aligned}
{\mathcal{G}(\lambda(\mathbf{y}^{(r)},\mathbf{x}^{(r)})) = \int_{\Theta}} & {\varphi(x\lbrack t\rbrack,\theta)\exp\left( {- \sum_{j = 1}^{r}\lambda_{j}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta,} \\
{\mathcal{E}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))} & {\int_{\Xi_{t}}\exp\left( {- \lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})\xi\lbrack t\rbrack} \right)d\xi\lbrack t\rbrack,} \\
& {\quad t = \overline{1,r}.} \\
\end{aligned}
$$

(A.11)

The solution `λ*`(`y`^((*r*))), `x`^((*r*))) of these equations depends on the sample (`y`^((*r*))), `x`^((*r*)) used for constructing the maximum entropy estimates of the PDFs.

## A.2 Existence of Implicit Function `θ`(`\widetilde{\mathbf{y}}^{(r)}`, `x^{(r)}`)

According to the balance equations (A.10), (A.1), their second term is the mean value of the noise in each measurement `t`. The noises and also their characteristics are often assumed to be independent of the measurements, i.e., in the expression (A.3),

$$
\begin{array}{r}
{\Xi_{t} = \Xi = \lbrack\xi^{-},\xi^{+}\rbrack.} \\
\end{array}
$$

(A.12)

Therefore, the mean value of the noise is given by

$$
\begin{array}{r}
{\overline{\xi} = \frac{\mathcal{E}_{t}(\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)}))}{\mathcal{Q}_{t}\left( {\lambda_{t}(\mathbf{y}^{(r)},\mathbf{x}^{(r)})} \right)} \in \Xi.} \\
\end{array}
$$

(A.13)

The balance equations can be written as

$$
\begin{aligned}
& \left. \quad W_{t}(\lambda\, \middle| \,\widetilde{y}\lbrack t\rbrack,\mathbf{x}^{(r)}) = {\int_{\Theta}\left( {\varphi(x\lbrack t\rbrack,\theta) - \widetilde{y}\lbrack t\rbrack} \right)} \times \right. \\
& {\times \exp\left( {- {\sum\limits_{j = 1}^{r}\lambda_{j}}({\widetilde{\mathbf{y}}}^{(r)},\mathbf{x}^{(r)})\varphi(x\lbrack j\rbrack,\theta)} \right)d\theta = 0,} \\
& {\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}\text{\quad\quad}t = \overline{1,r},} \\
\end{aligned}
$$

(A.14)

where

$$
\begin{array}{r}
{\widetilde{y}\lbrack t\rbrack = y\lbrack t\rbrack - \overline{\xi},\text{\quad\quad}{\widetilde{\mathbf{y}}}^{(r)} = \left\{ \widetilde{y}\lbrack 1\rbrack,\ldots,\widetilde{y}\lbrack r\rbrack \right\}.} \\
\end{array}
$$

(A.15)

In the vector form, equations (A.2) are described by

$$
\begin{array}{r}
\left. \mathbf{W}(\lambda\, \middle| \,,{\widetilde{\mathbf{y}}}^{(r)},\mathbf{x}^{(r)}) = \mathbf{0}. \right. \\
\end{array}
$$

(A.16)

Equation (A.16) defines an implicit function `λ`(`\widetilde{\mathbf{y}}^{(r)}`, `x^{(r)}`). The existence and properties of this implicit function depend on the properties of the Jacobian matrix

$$
\begin{array}{r}
\left. J_{\lambda}(\lambda\, \middle| \,\mathbf{y}^{(r)},\mathbf{x}^{(r)}) = \left\lbrack \frac{\partial W_{t}}{\partial\lambda_{i}},\, \middle| \,(t,i) = \overline{1,r} \right\rbrack, \right. \\
\end{array}
$$

(A.17)

which has the elements
