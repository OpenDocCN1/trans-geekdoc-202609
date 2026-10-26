# Analysis of Kernel Methods

A number of different kernel methods have appeared in the statistics literature. One such method, which employs the so-called reproducing kernel Hilbert space (RKHS), was popularized in machine learning through support vector machines (SVMs) in the 1990s (Cortes and Vapnik, 1995). This chapter presents an overview of RKHS kernel methods and their theoretical analysis. A more detailed treatment of RKHS kernel methods can be found in Schölkopf et al. (2018).

# 9.1 Introduction to Kernel Learning

In order to motivate kernel methods, we first consider the classical linear models, with the following real-valued function class \(\mathcal{X} \to \mathbb{R}\) indexed by \(w\):

\[\mathcal{F}=\{f(w,x):f(w,x)=\langle w,\psi(x)\rangle\}. \tag{9.1}\]

where \(\psi(x)\) is a predefined (possibly infinite-dimensional) feature vector for the input variable \(x\in\mathcal{X}\), and \(\langle\cdot,\cdot\rangle\) denotes an inner product in the feature vector space. In classical machine learning, the process of constructing the feature vector (or feature map) \(\psi(x)\) is referred to as *feature engineering*, which is problem dependent. The feature vector is usually constructed by hand-crafted rules.

Given such a feature vector, we consider the following regularized ERM problem, with \(L_2\) regularization:

\[\hat{w}=\underset{w}{\arg\min}\left[\frac{1}{n}\sum_{i=1}^{n}L(\langle w,\psi(X_i)\rangle,Y_i)+\frac{\lambda}{2}\|w\|^2\right]. \tag{9.2}\]

which employs the linear function class of (9.1).

If \(\psi(x)\) is infinite dimensional (or its dimension is very large), then computationally it may not be feasible to work with \(\psi(x)\) directly. The learning of the linear model class \(\mathcal{F}\) can be achieved via an equivalent kernel formulation. We can define a kernel function \(k(x,x')\) (also called reproducing kernel) as the inner product of their feature vectors:

\[k(x,x')=\langle\psi(x),\psi(x')\rangle. \tag{9.3}\]

One important observation, referred to as the *kernel trick*, can be described by the following result.