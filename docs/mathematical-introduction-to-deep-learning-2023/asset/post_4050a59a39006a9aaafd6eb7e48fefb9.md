
## Part I

### Artificial neural networks (ANNs)

## Chapter 1

### Basics on ANNs

In this chapter we review different types of architectures of ANNs such as fully-connected feedforward ANNs (see Sections 1.1 and 1.3), CNNs (see Section 1.4), ResNets (see Section 1.5), and RNNs (see Section 1.6). We review different types of popular activation functions used in applications such as the rectified linear unit (ReLU) activation (see Section 1.2.3), the Gaussian error linear unit (GELU) activation (see Section 1.2.6), and the standard logistic activation (see Section 1.2.7) among others. We also review different procedures for how ANNs can be formulated in rigorous mathematical terms (see Section 1.1 for a vectorized description and Section 1.3 for a structured description).

In the literature, different types of ANN architectures and activation functions have been reviewed in several excellent works; cf., for example, [4, 9, 39, 60, 63, 97, 164, 182, 189, 367, 373, 389, 431] and the references therein. The specific presentation of Sections 1.1 and 1.3 is based on [19, 20, 25, 159, 180].

#### 1.1 Fully-connected feedforward ANNs (vectorized description)

We start the mathematical content of this book with a review of fully-connected feedforward ANNs, the most basic type of ANNs. Roughly speaking, fully-connected feedforward ANNs can be thought of as parametric functions resulting from successive compositions of affine functions followed by nonlinear functions, where the parameters of a fully-connected feedforward ANN correspond to all the entries of the linear transformation matrices and translation vectors of the involved affine functions (cf. Definition 1.1.3 below for a precise definition of fully-connected feedforward ANNs and Figure 1.2 below for a graphical illustration of fully-connected feedforward ANNs). The linear transformation matrices and translation vectors are sometimes called weight matrices and bias vectors, respectively, and can be thought of as the trainable parameters of fully-connected feedforward ANNs (cf. Remark 1.1.5 below).

In this section we introduce in Definition 1.1.3 below a vectorized description of fully-connected feedforward ANNs in the sense that all the trainable parameters of a fully-connected feedforward ANN are represented by the components of a single Euclidean vector. In Section 1.3 below we will discuss an alternative way to describe fully-connected feedforward ANNs in which the trainable parameters of a fully-connected feedforward ANN are represented by a tuple of matrix-vector pairs corresponding to the weight matrices and bias vectors of the fully-connected feedforward ANNs (cf. Definitions 1.3.1 and 1.3.4 below).

![](img/dec290f673e6357c31893c67b579ffe1_21_0.png)

Figure 1.1: Graphical illustration of a fully-connected feedforward ANN consisting of $L \in \mathbb{N}$ affine transformations (i.e., consisting of $L + 1$ layers: one input layer, $L - 1$ hidden layers, and one output layer) with $l_{0} \in \mathbb{N}$ neurons on the input layer (i.e., with $l_{0}$-dimensional input layer), with $l_{1} \in \mathbb{N}$ neurons on the first hidden layer (i.e., with $l_{1}$-dimensional first hidden layer), with $l_{2} \in \mathbb{N}$ neurons on the second hidden layer (i.e., with $l_{2}$-dimensional second hidden layer), ..., with $l_{L-1}$ neurons on the $(L - 1)$-th hidden layer (i.e., with $(l_{L-1})$-dimensional $(L - 1)$-th hidden layer), and with $l_{L}$ neurons in the output layer (i.e., with $l_{L}$-dimensional output layer).

#### 1.1.1 Affine functions

**Definition 1.1.1** (Affine functions). Let $\mathbf{d}, m, n \in \mathbb{N}$, $s \in \mathbb{N}_0$, $\theta = (\theta_1, \theta_2, \ldots, \theta_s) \in \mathbb{R}^{s}$ satisfy $\mathbf{d} \geq s + mn + m$. Then we denote by $\mathcal{A}_{m,n}^{\theta,s} \colon \mathbb{R}^n \to \mathbb{R}^m$ the function which satisfies for all $x = (x_1, x_2, \ldots, x_n) \in \mathbb{R}^n$ that

$$
\mathcal{A}_{m,n}^{\theta,s}(x) = \begin{pmatrix} 
\theta_{s+1} & \theta_{s+2} & \cdots & \theta_{s+n} 
\end{pmatrix} \begin{pmatrix} 
x_1 \\
x_2 \\
\vdots \\
x_n
\end{pmatrix} + \begin{pmatrix} 
\theta_{s+mn+1} \\
\theta_{s+mn+2} \\
\vdots \\
\theta_{s+mn+m}
\end{pmatrix}
$$
$$
= \left( \left[ \sum_{k=1}^n x_k\theta_{s+k} \right] + \theta_{s+mn+1}, \left[ \sum_{k=1}^n x_k\theta_{s+n+k} \right] + \theta_{s+mn+2}, \ldots, \left[ \sum_{k=1}^n x_k\theta_{s+(m-1)n+k} \right] + \theta_{s+mn+m} \right) \tag{1.1}
$$

and we call $\mathcal{A}_{m,n}^{\theta,s}$ the affine function from $\mathbb{R}^n$ to $\mathbb{R}^m$ associated to $(\theta, s)$.

**Example 1.1.2** (Example for Definition 1.1.1). Let $\theta = (0, 1, 2, 0, 3, 3, 0, 1, 7) \in \mathbb{R}^9$. Then

$$
\mathcal{A}_{2,2}^{\theta,1}((1, 2)) = (8, 6) \tag{1.2}
$$

(cf. Definition 1.1.1).

**Proof for Example 1.1.2.** Observe that (1.1) ensures that

$$
\mathcal{A}_{2,2}^{\theta,1}((1, 2)) = \begin{pmatrix} 1 & 2 \\ 0 & 3 \end{pmatrix} \begin{pmatrix} 1 \\ 2 \end{pmatrix} + \begin{pmatrix} 3 \\ 0 \end{pmatrix} = \begin{pmatrix} 1 + 4 \\ 0 + 6 \end{pmatrix} + \begin{pmatrix} 3 \\ 0 \end{pmatrix} = \begin{pmatrix} 8 \\ 6 \end{pmatrix}. \tag{1.3}
$$

The proof for Example 1.1.2 is thus complete.

**Exercise 1.1.1.** Let $\theta = (3, 1, -2, 1, -3, 0, 5, 4, -1, -1, 0) \in \mathbb{R}^{11}$. Specify $\mathcal{A}_{2,3}^{\theta,2}((-1, 1, -1))$ explicitly and prove that your result is correct (cf. Definition 1.1.1)!

#### 1.1.2 Vectorized description of fully-connected feedforward ANNs

**Definition 1.1.3** (Vectorized description of fully-connected feedforward ANNs). Let $\mathbf{d}, l \in \mathbb{N}$, $l_0, l_1, \ldots, l_L \in \mathbb{N}$, $\theta \in \mathbb{R}^{\mathbf{d}}$ satisfy

$$
\mathbf{d} \geq \sum_{k=1}^L l_k(l_{k-1} + 1) \tag{1.4}
$$

and for every $k \in \{1, 2, \dots, L\}$ let $\Psi_k : \mathbb{R}^{l_k} \rightarrow \mathbb{R}^{l_k}$ be a function. Then we denote by $\mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta, l_0}$ the function which satisfies for all $x \in \mathbb{R}^{l_0}$ that

$$
\left(\mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta, l_0}\right)(x) = \left(\Psi_L \circ \mathcal{A}_{L, L-1}^{\theta, \sum_{k=1}^{L-1} l_k(l_{k-1}+1)} \circ \Psi_{L-1} \circ \mathcal{A}_{L-1, L-2}^{\theta, \sum_{k=1}^{L-2} l_k(l_{k-1}+1)} \circ \cdots \right) \circ \left(\cdots \circ \Psi_2 \circ \mathcal{A}_{2,1}^{\theta, l_1(l_0+1)} \circ \Psi_1 \circ \mathcal{A}_{1,0}^{\theta, l_0}\right)(x)
$$

and we call $\mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta, l_0}$ the realization function of the fully-connected feedforward ANN associated to $\theta$ with $L+1$ layers with dimensions $(l_0, l_1, \dots, l_L)$ and activations $(\Psi_1, \Psi_2, \dots, \Psi_L)$ (we call $\mathcal{N}_{\Psi_1, \Psi_2, \dots, \Psi_L}^{\theta, l_0}$ the realization of the fully-connected feedforward ANN associated to $\theta$ with $L+1$ layers with dimensions $(l_0, l_1, \dots, l_L)$ and activations $(\Psi_1, \Psi_2, \dots, \Psi_L)$) (cf. Definition 1.1.1).

**Example 1.1.4** (Example for Definition 1.1.3). Let $\theta = (1, -1, 2, -2, 3, -3, 0, 1, 1) \in \mathbb{R}^9$ and let $\Psi: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ satisfy for all $x = (x_1, x_2) \in \mathbb{R}^2$ that

$$
\Psi(x) = (\max\{x_1, 0\}, \max\{x_2, 0\}). \tag{1.6}
$$

Then

$$
\left(\mathcal{N}_{\Psi, \mathrm{id}_\mathbb{R}}^{\theta, 1}\right)(2) = 12 \tag{1.7}
$$

(cf. Definition 1.1.3).

**Proof for Example 1.1.4.** Note that (1.1), (1.5), and (1.6) assure that

$$
\left(\mathcal{N}_{\Psi, \mathrm{id}_\mathbb{R}}^{\theta, 1}\right)(2) = \left(\mathrm{id}_\mathbb{R} \circ \mathcal{A}_{1, 2}^{\theta, 4} \circ \Psi \circ \mathcal{A}_{2, 1}^{\theta, 0}\right)(2) = \left(\mathcal{A}_{1, 2}^{\theta, 4} \circ \Psi\right)\left(\left(\begin{matrix}1 \\ -1\end{matrix}\right)(2) + \left(\begin{matrix}2 \\ -2\end{matrix}\right)\right)
$$

$$
= \left(\mathcal{A}_{1, 2}^{\theta, 4} \circ \Psi\right)\left(\left(\begin{matrix}4 \\ -4\end{matrix}\right)\right) = \mathcal{A}_{1, 2}^{\theta, 4}\left(\left(\begin{matrix}4 \\ 0\end{matrix}\right)\right) = \left(\begin{matrix}3 & -3\end{matrix}\right)\left(\left(\begin{matrix}4 \\ 0\end{matrix}\right)\right) + (0) = 12
$$

(cf. Definitions 1.1.1 and 1.1.3). The proof for Example 1.1.4 is thus complete. $\square$

**Exercise 1.1.2.** Let $\theta = (1, -1, 0, 0, 1, -1, 0) \in \mathbb{R}^7$ and let $\Psi: \mathbb{R}^2 \rightarrow \mathbb{R}^2$ satisfy for all $x = (x_1, x_2) \in \mathbb{R}^2$ that

$$
\Psi(x) = (\max\{x_1, 0\}, \min\{x_2, 0\}). \tag{1.9}
$$

Prove or disprove the following statement: It holds that

$$
\left(\mathcal{N}_{\Psi, \mathrm{id}_\mathbb{R}}^{\theta, 1}\right)(-1) = -1 \tag{1.10}
$$

(cf. Definition 1.1.3).
