are inspired by the fact that under some general conditions the solution $u$ to the PDE (2.1) can be represented in the form

$$u(x) = \int_D G(x,y) f(y) \mathrm{d}y, \tag{2.29}$$

where $G: \Omega \times \Omega \to \mathbb{R}$ is the Green's function. This kernel representation led Li et al. (2020) to propose replacing the formula for a hidden layer of a standard neural network with the following operator:

$$\mathcal{L}_\ell(v)(x) = \sigma\Big(W_\ell v(x) + \int_D \kappa_\phi(x,y,a(x),a(y)) v(y) \mathrm{d}\mu_x(\mathrm{d}y)\Big), \tag{2.30}$$

where $W_\ell$ and $\phi$ are to be learned from the data, $\kappa_\phi$ is a kernel and $\mu_x$ is a Borel measure for every $x \in D$. Li et al. (2020) modelled the kernel $\kappa_\phi$ as a neural network. More generally, neural operators are mappings of the form (Li et al. 2020, Kovachki, Lanthaler and Mishra 2021)

$$\mathcal{N}: \mathcal{X} \to \mathcal{Y}: u \mapsto \mathcal{Q} \circ \mathcal{L}_L \circ \mathcal{L}_{L-1} \circ \cdots \circ \mathcal{L}_1 \circ \mathcal{R}(u), \tag{2.31}$$

for a given depth $L \in \mathbb{N}$, where $\mathcal{R}: \mathcal{X}(D;\mathbb{R}^{d_x}) \to \mathcal{U}(D;\mathbb{R}^{d_v})$, $d_v \ge d_u$, is a lifting operator (acting locally), of the form

$$\mathcal{R}(a)(x) = R a(x), \quad R \in \mathbb{R}^{d_v \times d_x}, \tag{2.32}$$

and $\mathcal{Q}: \mathcal{U}(D;\mathbb{R}^{d_v}) \to \mathcal{Y}(D;\mathbb{R}^{d_y})$ is a local projection operator, of the form

$$\mathcal{Q}(v)(x) = Q v(x), \quad Q \in \mathbb{R}^{d_y \times d_v}. \tag{2.33}$$

In analogy with canonical finite-dimensional neural networks, the layers $\mathcal{L}_1, \dots, \mathcal{L}_L$ are nonlinear operator layers, $\mathcal{L}_\ell: \mathcal{U}(D;\mathbb{R}^{d_v}) \to \mathcal{U}(D;\mathbb{R}^{d_v})$, $v \mapsto \mathcal{L}_\ell(v)$, which we assume to be of the form

$$\mathcal{L}_\ell(v)(x) = \sigma\big(W_\ell v(x) + b_\ell(x) + (\mathcal{K}(a;\theta_\ell)v)(x)\big) \quad \text{for all } x \in D. \tag{2.34}$$

Here, the weight matrix $W_\ell \in \mathbb{R}^{d_v \times d_v}$ and bias $b_\ell(x) \in \mathcal{U}(D;\mathbb{R}^{d_v})$ define an affine pointwise mapping $W_\ell v(x) + b_\ell(x)$. We conclude the definition of a neural operator by stating that $\sigma: \mathbb{R} \to \mathbb{R}$ is a nonlinear activation function that is applied component-wise, and $\mathcal{K}$ is a non-local linear operator,

$$\mathcal{K}: \mathcal{X} \times \Theta \to L(\mathcal{U}(D;\mathbb{R}^{d_v}),\mathcal{U}(D;\mathbb{R}^{d_v})), \tag{2.35}$$

that maps the input field $a$ and a parameter $\theta \in \Theta$ in the parameter set $\Theta$ to a bounded linear operator $\mathcal{K}(a,\theta): \mathcal{U}(D;\mathbb{R}^{d_v}) \to \mathcal{U}(D;\mathbb{R}^{d_v})$. When we define the linear operators $\mathcal{K}(a,\theta)$ through an integral kernel, then (2.34) reduces again to (2.30). Fourier neural operators (FNOs) (Li et al. 2021) are special cases of such general neural operators in which this integral kernel corresponds to a convolution kernel, which on the periodic domain $\mathbb{T}^d$ leads to nonlinear layers $\mathcal{L}_\ell$ of the form

$$\mathcal{L}_\ell(v)(x) = \sigma\big(W_\ell v(x) + b_\ell(x) + \mathcal{F}^{-1}(P_\ell(k) \cdot \mathcal{F}(v)(k))(x)\big). \tag{2.36}$$