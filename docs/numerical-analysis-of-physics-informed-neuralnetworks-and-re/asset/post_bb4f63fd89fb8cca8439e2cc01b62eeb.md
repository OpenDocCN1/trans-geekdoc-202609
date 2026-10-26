
Randomly initialized weights and biases are closely connected to neural networks of which only the outer layer is trained. When the network is large then the latter model is often referred to as an extreme learning machine (ELM) (Huang, Zhu and Siew 2006).

## 2.2.2. Nonlinear models

Neural networks. A first, but very central, example of parametric models that depend nonlinearly on their parameters is that of neural networks. The simplest form of a neural network is a multilayer perceptron (MLP). MLPs get their name from their definition as a concatenation of affine maps and activation functions. As a consequence of this structure, the computational graph of an MLP is organized in layers. At the kth layer, the activation function is applied component-wise to obtain the value

$$z^k = \sigma(C_{k-1}(z^{k-1})) = \sigma(W_{k-1}z^{k-1} + b_{k-1}), \tag{2.21}$$

where $z^0$ is the input of the network, $W_k \in \mathbb{R}^{d_{k+1}\times d_k}$, $b_k \in \mathbb{R}^{d_{k+1}}$ and $C_k: \mathbb{R}^{d_k} \to \mathbb{R}^{d_{k+1}}: x \mapsto W_k x + b_k$ for $d_k \in \mathbb{N}$ is an affine map. A multilayer perceptron (MLP) with L layers, activation function $\sigma$, output function $\sigma_o$, input dimension $d_{\mathrm{in}}$ and output dimension $d_{\mathrm{out}}$ is then a function $f_\theta: \mathbb{R}^{d_{\mathrm{in}}} \to \mathbb{R}^{d_{\mathrm{out}}}$ of the form

$$f_\theta(x) = (\sigma_o \circ C_L \circ \sigma \circ \cdots \circ \sigma \circ C_0)(x) \quad \text{for all } x \in \mathbb{R}^{d_{\mathrm{in}}}, \tag{2.22}$$

where $\sigma$ is applied element-wise and $\theta = ((W_0, b_0), \ldots, (W_L, b_L))$. The dimension $d_k$ of each layer is also called the width of that layer. The width of the MLP is defined as $\max_k d_k$. Furthermore, the matrices $W_k$ are called the weights of the MLP and the vectors $b_k$ are called the biases of the MLP. Together, they constitute the (trainable) parameters of the MLP, denoted by $\theta = ((W_0, b_0), \ldots, (W_L, b_L))$. Finally, an output function $\sigma_o$ can be employed to increase the interpretability of the output, but is often equal to the identity in the setting of function approximation.

## Remark 2.8.

In some texts, the number of layers L corresponds to the number of affine maps in the definition of $f_\theta$. Of these L layers, the first L − 1 layers are called hidden layers. An L-layer network in this alternative definition hence corresponds to an (L − 1)-layer network in our definition.

Many of the properties of a neural network depend on the choice of activation function. We discuss the most common activation functions below.

- The Heaviside function is the activation that was used in the McCulloch–Pitts neuron and is defined as

  $$H(x) = \begin{cases} 0, & x < 0;\\ 1, & x \ge 0. \end{cases} \tag{2.23}$$

  Because the gradient is zero wherever it exists, it is not possible to train the network using a gradient-based approach. For this reason, the Heaviside function is no longer used.

are inspired by the fact that under some general conditions the solution $u$ to the PDE (2.1) can be represented in the form

$$u(x) = \int_D G(x,y) f(y) \mathrm{d}y, \tag{2.29}$$

where $G: D \times D \to \mathbb{R}$ is the Green's function. This kernel representation led Li et al. (2020) to propose replacing the formula for a hidden layer of a standard neural network with the following operator:

$$\mathcal{L}_\ell(v)(x) = \sigma\Big(W_\ell v(x) + \int_D \kappa_\phi(x,y,a(x),a(y)) v(y) \mathrm{d}\mu_x(y)\Big), \tag{2.30}$$

where $W_\ell$ and $\phi$ are to be learned from the data, $\kappa_\phi$ is a kernel and $\mu_x$ is a Borel measure for every $x \in D$. Li et al. (2020) modelled the kernel $\kappa_\phi$ as a neural network. More generally, neural operators are mappings of the form (Li et al. 2020, Kovachki, Lanthaler and Mishra 2021)

$$\mathcal{N}: \mathcal{X} \to \mathcal{Y}: a \mapsto \mathcal{Q} \circ \mathcal{L}_L \circ \mathcal{L}_{L-1} \circ \cdots \circ \mathcal{L}_1 \circ \mathcal{R}(a), \tag{2.31}$$

for a given depth $L \in \mathbb{N}$, where $\mathcal{R}: \mathcal{X}(D;\mathbb{R}^{d_x}) \to \mathcal{U}(D;\mathbb{R}^{d_v})$, $d_v \ge d_x$, is a lifting operator (acting locally), of the form

$$\mathcal{R}(a)(x) = R a(x), \quad R \in \mathbb{R}^{d_v \times d_x}, \tag{2.32}$$

and $\mathcal{Q}: \mathcal{U}(D;\mathbb{R}^{d_v}) \to \mathcal{Y}(D;\mathbb{R}^{d_y})$ is a local projection operator, of the form

$$\mathcal{Q}(v)(x) = Q v(x), \quad Q \in \mathbb{R}^{d_y \times d_v}. \tag{2.33}$$

In analogy with canonical finite-dimensional neural networks, the layers $\mathcal{L}_1, \dots, \mathcal{L}_L$ are nonlinear operator layers, $\mathcal{L}_\ell: \mathcal{U}(D;\mathbb{R}^{d_v}) \to \mathcal{U}(D;\mathbb{R}^{d_v})$, $v \mapsto \mathcal{L}_\ell(v)$, which we assume to be of the form

$$\mathcal{L}_\ell(v)(x) = \sigma\big(W_\ell v(x) + b_\ell(x) + (\mathcal{K}(a;\theta_\ell)v)(x)\big) \quad \text{for all } x \in D. \tag{2.34}$$

Here, the weight matrix $W_\ell \in \mathbb{R}^{d_v \times d_v}$ and bias $b_\ell(x) \in \mathcal{U}(D;\mathbb{R}^{d_v})$ define an affine pointwise mapping $W_\ell v(x) + b_\ell(x)$. We conclude the definition of a neural operator by stating that $\sigma: \mathbb{R} \to \mathbb{R}$ is a nonlinear activation function that is applied component-wise, and $\mathcal{K}$ is a non-local linear operator,

$$\mathcal{K}: \mathcal{X} \times \Theta \to L(\mathcal{U}(D;\mathbb{R}^{d_v}),\mathcal{U}(D;\mathbb{R}^{d_v})), \tag{2.35}$$

that maps the input field $a$ and a parameter $\theta \in \Theta$ in the parameter set $\Theta$ to a bounded linear operator $\mathcal{K}(a,\theta): \mathcal{U}(D;\mathbb{R}^{d_v}) \to \mathcal{U}(D;\mathbb{R}^{d_v})$. When we define the linear operators $\mathcal{K}(a,\theta)$ through an integral kernel, then (2.34) reduces again to (2.30). Fourier neural operators (FNOs) (Li et al. 2021) are special cases of such general neural operators in which this integral kernel corresponds to a convolution kernel, which on the periodic domain $\mathbb{T}^d$ leads to nonlinear layers $\mathcal{L}_\ell$ of the form

$$\mathcal{L}_\ell(v)(x) = \sigma\big(W_\ell v(x) + b_\ell(x) + \mathcal{F}^{-1}(P_\ell(k) \cdot \mathcal{F}(v)(k))(x)\big). \tag{2.36}$$

In practice, however, this definition cannot be used, as evaluating the Fourier transform requires the exact computation of an integral. The practical implementation (i.e. discretization) of an FNO maps from and to the space of trigonometric polynomials of degree at most $N \in \mathbb{N}$, denoted by $L_N^2$, and can be identified with a finite-dimensional mapping that is a composition of affine maps and nonlinear layers of the form

$$\mathcal{L}_\ell(z)_j = \sigma\left(W_\ell z_j + b_{\ell,j} + \mathcal{F}_N^{-1}\left(P_\ell(k)\cdot\mathcal{F}_N(z)_{k,j}\right)\right). \tag{2.37}$$

where the $P_\ell(k)$ are coefficients that define a non-local convolution operator via the discrete Fourier transform $\mathcal{F}_N$; see Kovachki *et al.* (2021).

It has been observed that the proposed operator learning models above may not behave as operators when implemented on a computer, questioning the very essence of what operator learning should be. Bartolucci *et al.* (2023) contend that in addition to defining the operator at the continuous level, some form of continuous–discrete equivalence is necessary for an architecture to genuinely learn the underlying operator rather than just discretizations of it. To this end, they introduce the unifying mathematical framework of *representation-equivalent neural operators* (ReNOs) to ensure that operations at the continuous and discrete level are equivalent. Lack of this equivalence is quantified in terms of aliasing errors.

## *Gaussian processes.*

Deep neural networks and their operator versions are only one possible nonlinear surrogate model for the true solution $u$. Another popular class of nonlinear models is *Gaussian process regression* (Rasmussen 2003), which belongs to a larger class of so-called Bayesian models. Gaussian process regression (GPR) relies on the assumption that $u$ is drawn from a Gaussian measure on a suitable function space, parametrized by

$$u_\theta(x) \sim \mathrm{GP}\bigl(m_\theta(x), k_\theta(x,x')\bigr), \tag{2.38}$$

where $m_\theta(x)=\mathbb{E}[u_\theta(x)]$ is the mean, and the underlying covariance function is given by $k_\theta(x,x')=\mathbb{E}[(u_\theta(x)-m_\theta(x))(u_\theta(x')-m_\theta(x'))]$.

Popular choices for the covariance function in (2.38) are the squared exponential kernel (which is a radial function as for RBFs) and Matérn covariance functions:

$$k_{\mathrm{SE}}(x,x')=\exp\left(-\frac{\lVert x-x'\rVert^2}{2\ell^2}\right), \tag{2.39}$$

$$k_{\mathrm{Matern}}(x,x')=\frac{2^{1-\nu}}{\Gamma(\nu)}\left(\sqrt{2\nu}\frac{\lVert x-x'\rVert}{\ell}\right)^\nu K_\nu\left(\sqrt{2\nu}\frac{\lVert x-x'\rVert}{\ell}\right). \tag{2.40}$$

Here $\lVert\cdot\rVert$ denotes the standard Euclidean norm, $K_\nu$ is the modified Bessel function of the second kind and $\ell$ is the *characteristic length*, describing the length scale of the correlations between the points $x$ and $x'$. The parameter vector then consists of the hyperparameters of $m_\theta$ and $k_\theta$, such as $\nu$ and $\ell$.
