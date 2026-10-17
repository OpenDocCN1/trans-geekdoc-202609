
\begin{align*} \mathbb{E}\left[\left\|\sum_{k=1}^{n}\left(X_{k}-\mathbb{E}\left[X_{k}\right]\right)\right\|^{2}\right] &=\mathbb{E}\left[\left\langle\sum_{k_{1}=1}^{n}\left(X_{k_{1}}-\mathbb{E}[X_{k_{1}}]\right),\sum_{k_{2}=1}^{n}\left(X_{k_{2}}-\mathbb{E}\left[X_{k_{2}}\right]\right)\right\rangle\right] \\ &=\mathbb{E}\left[\sum_{k_{1},k_{2}=1}^{n}\left\langle\left(X_{k_{1}}-\mathbb{E}\left[X_{k_{1}}\right]\right), X_{k_{2}}-\mathbb{E}[X_{k_{2}}]\right\rangle\right] \\ &=\mathbb{E}\left[\left(\sum_{k=1}^{n}\left\|X_{k}-\mathbb{E}\left[X_{k}\right]\right\|^{2}\right)+\left(\sum_{\begin{array}{c} k_{1},k_{2}\in\{1,2,\ldots,n\}, \\ k_{1}\neq k_{2}\end{array}}\left\langle X_{k_{1}}-\mathbb{E}\left[X_{k_{1}}\right], X_{k_{2}}-\mathbb{E}[X_{k_{2}}]\right\rangle\right)\right] \\ &=\left(\sum_{k=1}^{n}\mathbb{E}\left[\left\|X_{k}-\mathbb{E}\left[X_{k}\right]\right\|^{2}\right]\right)+\left(\sum_{\begin{array}{c} k_{1},k_{2}\in\{1,2,\ldots,n\}, \\ k_{1}\neq k_{2}\end{array}}\mathbb{E}\left[\left\langle X_{k_{1}}-\mathbb{E}\left[X_{k_{1}}\right], X_{k_{2}}-\mathbb{E}[X_{k_{2}}]\right\rangle\right]\right) \\ &=\sum_{k=1}^{n}\mathbb{E}\left[\left\|X_{k}-\mathbb{E}\left[X_{k}\right]\right\|^{2}\right]. \end{align*} \quad (7.31)

$$

引理 7.2.6 的证明至此完成。 $\square$

## 引理 7.2.7 (独立随机变量的分解引理)

设 $(\Omega,\mathcal{F},\mathbb{P})$ 为概率空间，设 $(\mathbb{X},\mathcal{X})$ 和 $(\mathbb{Y},\mathcal{Y})$ 为可测空间，设 $X:\Omega\rightarrow\mathbb{X}$ 和 $Y:\Omega\rightarrow\mathbb{Y}$ 为独立随机变量，设 $\Phi:\mathbb{X}\times\mathbb{Y}\rightarrow[0,\infty)$ 为 $(\mathcal{X}\otimes\mathcal{Y})/\mathcal{B}([0,\infty))$-可测，且设 $\phi:\mathbb{Y}\rightarrow[0,\infty)$ 满足对于所有 $y\in\mathbb{Y}$，有

$$

\phi(y)=\mathbb{E}[\Phi(X,y)]. \quad (7.32)

$$

则

-   i) 函数 $\phi$ 是 $\mathcal{Y}/\mathcal{B}([0,\infty))$-可测的，且

-   (ii) 有

$$

\mathbb{E}[\Phi(X,Y)]=\mathbb{E}[\phi(Y)]. \quad (7.33)

$$

引理 7.2.7 的证明. 首先，注意到 Fubini 定理（例如参见 Klenke [248, (14.6)] 中的定理 14.16）、假设函数 $X:\Omega\rightarrow\mathbb{X}$ 是 $\mathcal{F}/\mathcal{X}$-可测的，

以及假设函数 $\Phi : \mathbb{X} \times \mathbb{Y} \rightarrow [0, \infty]$ 是 $(\mathcal{X} \otimes \mathcal{Y})/\mathcal{B}([0, \infty])$-可测的，这证明了函数

$$

\forall Y \ni y \mapsto \phi(y) = \mathbb{E}[\Phi(X, y)] = \int_\Omega \Phi(X(\omega), y) \mathbb{P}(\mathrm{d}\omega) \in [0, \infty] \tag{7.34}

$$

是 $\mathcal{Y}/\mathcal{B}([0, \infty])$-可测的。这证明了条目 **(i)**。观察到积分变换定理、事实 $(X, Y)(\mathbb{P}) = (X(\mathbb{P})) \otimes (Y(\mathbb{P}))$ 以及富比尼定理确立了

$$

\begin{aligned}

\mathbb{E}\big[\Phi(X, Y)\big] &= \int_\Omega \Phi(X(\omega), Y(\omega)) \mathbb{P}(\mathrm{d}\omega)\\

&= \int_{\mathbb{X} \times \mathbb{Y}} \Phi(x, y) \big((X, Y)(\mathbb{P})\big)(\mathrm{d}x, \mathrm{d}y)\\

&= \int_\mathbb{Y} \Big[\int_\mathbb{X} \Phi(x, y) \big(X(\mathbb{P})\big)(\mathrm{d}x) \Big] \big(Y(\mathbb{P})\big)(\mathrm{d}y)\\

&= \int_\mathbb{Y} \mathbb{E}\big[\Phi(X, y)\big] \big(Y(\mathbb{P})\big)(\mathrm{d}y)\\

&= \int_\mathbb{Y} \phi(y) \big(Y(\mathbb{P})\big)(\mathrm{d}y) = \mathbb{E}\big[\phi(Y)\big].

\end{aligned}

\tag{7.35}

$$

这证明了条目 **(ii)**。从而完成了引理 7.2.7 的证明。$\square$

### 引理 7.2.8

令 $\mathfrak{d} \in \mathbb{N}$，令 $(S, \mathcal{S})$ 为一个可测空间，令 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^\mathfrak{d} \times S} : \mathbb{R}^\mathfrak{d} \times S \rightarrow \mathbb{R}$ 是 $(\mathcal{B}(\mathbb{R}^\mathfrak{d}) \otimes \mathcal{S})/\mathcal{B}(\mathbb{R})$-可测的，并假设对于每个 $x \in S$，函数 $\mathbb{R}^\mathfrak{d} \ni \theta \mapsto \ell(\theta, x) \in \mathbb{R}$ 是可微的。则函数

$$

\mathbb{R}^\mathfrak{d} \times S \ni (\theta, x) \mapsto \big(\nabla_\theta \ell\big)(\theta, x) \in \mathbb{R}^\mathfrak{d} \tag{7.36}

$$

是 $(\mathcal{B}(\mathbb{R}^\mathfrak{d}) \otimes \mathcal{S})/\mathcal{B}(\mathbb{R}^\mathfrak{d})$-可测的。

**引理 7.2.8 的证明。** 在整个证明过程中，令 $\boldsymbol{g} = (\boldsymbol{g}_1, \ldots, \boldsymbol{g}_\mathfrak{d}) : \mathbb{R}^\mathfrak{d} \times S \rightarrow \mathbb{R}^\mathfrak{d}$ 满足对于所有 $\theta \in \mathbb{R}^\mathfrak{d}$，$x \in S$ 有

$$

\boldsymbol{g}(\theta, x) = \big(\nabla_\theta \ell\big)(\theta, x). \tag{7.37}

$$

假设函数 $\ell : \mathbb{R}^\mathfrak{d} \times S \rightarrow \mathbb{R}$ 是 $(\mathcal{B}(\mathbb{R}^\mathfrak{d}) \otimes \mathcal{S})/\mathcal{B}(\mathbb{R})$-可测的，这意味着对于所有 $i \in \{1, 2, \ldots, \mathfrak{d}\}$，$h \in \mathbb{R} \setminus \{0\}$，函数

$$

\mathbb{R}^\mathfrak{d} \times S \ni (\theta, x) = \big((\theta_1, \ldots, \theta_\mathfrak{d}), x\big) \mapsto \bigg(\frac{\ell((\theta_1, \ldots, \theta_{i-1}, \theta_i + h, \theta_{i+1}, \ldots, \theta_\mathfrak{d}), x) - \ell(\theta, x)}{h} \bigg) \in \mathbb{R} \tag{7.38}

$$

是 $(\mathcal{B}(\mathbb{R}^\mathfrak{d}) \otimes \mathcal{S})/\mathcal{B}(\mathbb{R})$-可测的。事实是对于所有 $i \in \{1, 2, \ldots, \mathfrak{d}\}$，$\theta = (\theta_1, \ldots, \theta_\mathfrak{d}) \in \mathbb{R}^\mathfrak{d}$，$x \in S$ 有

$$

\boldsymbol{g}_i(\theta, x) = \lim_{n \rightarrow \infty} \bigg( \frac{\ell((\theta_1, \ldots, \theta_{i-1}, \theta_i + 2^{-n}, \theta_{i+1}, \ldots, \theta_\mathfrak{d}), x) - \ell(\theta, x)}{2^{-n}} \bigg) \tag{7.39}

$$

由此表明对于所有 $i \in \{1, 2, \ldots, \mathfrak{d}\}$，函数 $\boldsymbol{g}_i : \mathbb{R}^\mathfrak{d} \times S \rightarrow \mathbb{R}$ 是 $(\mathcal{B}(\mathbb{R}^\mathfrak{d}) \otimes \mathcal{S})/\mathcal{B}(\mathbb{R})$-可测的。这确保了 $\boldsymbol{g}$ 是 $(\mathcal{B}(\mathbb{R}^\mathfrak{d}) \otimes \mathcal{S})/\mathcal{B}(\mathbb{R}^\mathfrak{d})$-可测的。从而完成了引理 7.2.8 的证明。$\square$

### 引理 7.2.9

令 $d \in \mathbb{N}$，$\{\gamma_n\}_{n \in \mathbb{N}} \subseteq (0, \infty)$，$\{J_n\}_{n \in \mathbb{N}} \subseteq \mathbb{N}$，令 $\langle \cdot, \cdot \rangle : \mathbb{R}^d \times \mathbb{R}^d \to \mathbb{R}$ 为一个内积，令 $\| \cdot \| : \mathbb{R}^d \to [0, \infty)$ 满足对于所有 $v \in \mathbb{R}^d$ 有

$$

\|v\| = \sqrt{\langle v, v \rangle}, \tag{7.40}

$$

令 $(\Omega, \mathcal{F}, \mathbb{P})$ 为一个概率空间，令 $\xi : \Omega \to \mathbb{R}^d$ 为一个随机变量，令 $(S, \mathcal{S})$ 为一个可测空间，令 $X_{n,j} : \Omega \to S$，$j \in \{1, 2, \dots, J_n\}$，$n \in \mathbb{N}$，为独立同分布（i.i.d.）随机变量，假设 $\xi$ 和 $\{X_{n,j}\}_{n \in \mathbb{N}, j \in \{1, \dots, J_n\}}$ 是独立的，令 $\ell = (\ell(\theta, x))_{(\theta, x) \in \mathbb{R}^d \times S} : \mathbb{R}^d \times S \to \mathbb{R}$ 是 $\mathcal{B}(\mathbb{R}^d) \otimes \mathcal{S} / \mathcal{B}(\mathbb{R})$-可测的，假设对于所有 $x \in S$ 有 $(\mathbb{R}^d \ni \theta \mapsto \ell(\theta, x)) \in C^1(\mathbb{R}^d, \mathbb{R})$，假设对于所有 $\theta \in \mathbb{R}^d$ 有 $\mathbb{E}[\| (\nabla_\theta \ell)(\theta, X_{1,1}) \|] < \infty$（参见引理 7.2.8），令 $\mathcal{V} : \mathbb{R}^d \to [0, \infty]$ 满足对于所有 $\theta \in \mathbb{R}^d$ 有

$$

\mathcal{V}(\theta) = \mathbb{E}\big[\| (\nabla_\theta \ell)(\theta, X_{1,1}) - \mathbb{E}[ (\nabla_\theta \ell)(\theta, X_{1,1}) ] \|^2\big], \tag{7.41}

$$

并令 $\Theta : \mathbb{N}_0 \times \Omega \to \mathbb{R}^d$ 为满足对于所有 $n \in \mathbb{N}$ 有

$$

\Theta_0 = \xi \quad \text{且} \quad \Theta_n = \Theta_{n-1} - \gamma_n \left[ \frac{1}{J_n} \sum_{j=1}^{J_n} (\nabla_\theta \ell)(\Theta_{n-1}, X_{n,j}) \right]. \tag{7.42}

$$

的随机过程。则对于所有 $n \in \mathbb{N}$，$v \in \mathbb{R}^d$ 有

$$

(\mathbb{E}[\| \Theta_n - v \|^2])^{1/2} \geq \left[ \frac{\gamma_n}{(J_n)^{1/2}} \right] (\mathbb{E}[\mathcal{V}(\Theta_{n-1})])^{1/2}. \tag{7.43}

$$

**引理 7.2.9 的证明。** 在整个证明过程中，对于每个 $n \in \mathbb{N}$，令 $\phi_n : \mathbb{R}^d \to [0, \infty]$ 满足对于所有 $\theta \in \mathbb{R}^d$ 有

$$

\phi_n(\theta) = \mathbb{E}\left[ \left\| \theta - \frac{\gamma_n}{J_n} \left[ \sum_{j=1}^{J_n} (\nabla_\theta \ell)(\theta, X_{n,j}) \right] - v \right\|^2 \right]. \tag{7.44}

$$

注意到引理 7.2.3 表明对于所有 $v \in \mathbb{R}^d$ 和所有满足 $\mathbb{E}[\| Z \|] < \infty$ 的随机变量 $Z : \Omega \to \mathbb{R}^d$，有

$$

\mathbb{E}[\| Z - v \|^2] = \mathbb{E}[\| Z - \mathbb{E}[Z] \|^2] + \| \mathbb{E}[Z] - v \|^2 \geq \mathbb{E}[\| Z - \mathbb{E}[Z] \|^2]. \tag{7.45}

$$

因此，对于所有 $n \in \mathbb{N}$，$\theta \in \mathbb{R}^d$，我们得到

$$

\begin{aligned}
