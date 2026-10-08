*Exercise 1.1.3.* Let $\theta=(\theta_{1}, \theta_{2}, \ldots, \theta_{10}) \in \mathbb{R}^{10}$ satisfy

$\begin{equation} \theta=\left(\theta_{1}, \theta_{2}, \ldots, \theta_{10}\right)=\left(1,0,2,-1,2,0,-1,1,2,1\right) \end{equation}$

and let $m:\mathbb{R}\to\mathbb{R}$ and $q:\mathbb{R}\to\mathbb{R}$ satisfy for all $x\in\mathbb{R}$ that

$\begin{equation} m(x)=\max\left\{-x,0\} \quad \quad \mathrm{and} \quad \quad q(x)=x^{2}. \end{equation}$

Specify $\left(\mathcal{N}_{q, m, q}^{\theta, 1}\right)(0)$, $\left(\mathcal{N}_{q, m, q}^{\theta, 1}\right)(1)$, and $\left(\mathcal{N}_{q, m, q}^{\theta, 1}\right)(1/2)$ explicitly and prove that your results are correct (cf. Definition 1.1.3).!

*Exercise 1.1.4.* Let $\theta=(\theta_{1}, \theta_{2}, \ldots, \theta_{15}) \in \mathbb{R}^{15}$ satisfy

$\begin{equation} \left(\theta_{1}, \theta_{2}, \ldots, \theta_{15}\right)=\left(1,-2,0,3,2,-1,0,3,1,-1,1,-1,2,0,-1\right) \end{equation}$

and let $\Phi:\mathbb{R}^{2}\to\mathbb{R}^{2}$ and $\Psi:\mathbb{R}^{2}\to\mathbb{R}^{2}$ satisfy for all $x, y\in\mathbb{R}$ that $\Phi(x, y)=(y, x)$ and $\Psi(x, y)=(xy, xy)$. 

+   a) Prove or disprove the following statement: It holds that $\left(\mathcal{N}_{\Phi, \Psi}^{\theta, 2}\right)(1,-1)=(4,4)$ (cf. Definition 1.1.3).

+   b) Prove or disprove the following statement: It holds that $\left(\mathcal{N}_{\Phi, \Psi}^{\theta, 2}\right)(-1,1)=(-4,-4)$ (cf. Definition 1.1.3).

# 1.1.3 Weight and bias parameters of fully-connected feedforward ANN s

*Remark 1.1.5* (Weights and biases for fully-connected feedforward ANN s). Let $L\in\{2,3$, $4,\ldots\}$, $v_{0}, v_{1}, \ldots, v_{L-1}\in\mathbb{N}_{0}$, $l_{0}, l_{1}, \ldots, l_{L},\mathfrak{d}\in\mathbb{N}$, $\theta=\left(\theta_{1}, \theta_{2}, \ldots, \theta_{\mathfrak{d}}\right)\in\mathbb{R}^{\mathfrak{d}}$ satisfy for all

$k\in\{0,1,\ldots,L-1\}$ that

$\begin{equation} \mathfrak{d}\geq\sum_{i=1}^{L}l_{i}(l_{i-1}+1) \quad \quad \mathrm{and} \quad \quad v_{k}=\sum_{i=1}^{k}l_{i}(l_{i-1}+1), \end{equation}$

let $W_{k}\in\mathbb{R}^{l_{k}\times l_{k-1}}$, $k\in\{1,2,\ldots,L\}$, and $b_{k}\in\mathbb{R}^{l_{k}}$, $k\in\{1,2,\ldots,L\}$, satisfy for all $k\in\{1,2,\ldots,L\}$ that

$\begin{equation} W_{k}=\begin{pmatrix} \theta_{v_{k-1}+1} & \theta_{v_{k-1}+2} & \cdots & \theta_{v_{k-1}+l_{k-1}} \\ \theta_{v_{k-1}+l_{k-1}+1} & \theta_{v_{k-1}+l_{k-1}+2} & \cdots & \theta_{v_{k-1}+2l_{k-1}} \\ \theta_{v_{k-1}+2l_{k-1}+1} & \theta_{v_{k-1}+2l_{k-1}+2} & \cdots & \theta_{v_{k-1}+3l_{k-1}} \\ \vdots & \vdots & \vdots & \vdots \\ \theta_{v_{k-1}+(l_{k-1})l_{k-1}+1} & \theta_{v_{k-1}+(l_{k-1})l_{k-1}+2} & \cdots & \theta_{v_{k-1}+l_{k}l_{k-1}} \end{pmatrix} \end{equation}$

and

$\begin{equation} b_{k}=\left(\theta_{v_{k-1}+l_{k}l_{k-1}+1},\theta_{v_{k-1}+l_{k}l_{k-1}+2},\ldots,\theta_{v_{k-1}+l_{k}l_{k-1}+l_{k}}\right), \end{equation}$

and let $\Psi_{k}:\mathbb{R}^{l_{k}}\to\mathbb{R}^{l_{k}}$, $k\in\{1,2,\ldots,L\}$, be functions. Then