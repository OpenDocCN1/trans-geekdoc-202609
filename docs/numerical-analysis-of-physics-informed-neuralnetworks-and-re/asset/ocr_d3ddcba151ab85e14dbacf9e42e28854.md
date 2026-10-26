Hence, it follows that if the tangent kernel associated to $u_\theta$ and $\mathcal{L}u_\theta$ is (approximately) constant along the optimization path, then the error term $\epsilon_k$ will be small.

For neural networks this entails that the neural tangent kernels (NTK) $\Theta[u_\theta]$ and $\Theta[\mathcal{L}u_\theta]$ stay approximately constant along the optimization path. The following informal lemma from De Ryck et al. (2023), based on Wang et al. (2022b), confirms that this is indeed the case for wide enough neural networks.

# Lemma 7.8.

For a neural network $u_\theta$ with one hidden layer of width $m$ and a linear differential operator $\mathcal{L}$, we have $\lim_{m\to\infty}\Theta[u_{\theta_k}] = \lim_{m\to\infty}\Theta[u_{\theta_0}]$ and $\lim_{m\to\infty}\Theta[\mathcal{L}u_{\theta_k}] = \lim_{m\to\infty}\Theta[\mathcal{L}u_{\theta_0}]$ for all $k$. Consequently, the error term $\epsilon_k$ (7.14) is small for wide neural networks, $\lim_{m\to\infty}\max_k\|\epsilon_k\|_2 = 0$.

Now, given the much simpler structure of (7.16), when compared to (7.11), one can study the corresponding gradient descent dynamics explicitly and obtain the following convergence theorem (De Ryck et al. 2023).

# Theorem 7.9.

Let $\mathbb{A}$ in (7.16) be invertible with condition number $\kappa(\mathbb{A})$ (7.18) and let $0 < c < 1$. Set $\eta = c/\lambda_{\max}(\mathbb{A})$ and $\vartheta = \theta_0 + \mathbb{A}^{-1}\mathbb{C}$. It holds for any $k \in \mathbb{N}$ that $\|\widetilde{\theta}_k - \vartheta\|_2 \le (1 - c/\kappa(\mathbb{A}))^k \|\theta_0 - \vartheta\|_2.$ (7.20)

An immediate consequence of the quantitative convergence rate (7.20) is as follows: to obtain an error of size $\varepsilon$, i.e. $\|\widetilde{\theta}_k - \vartheta\|_2 \le \varepsilon$, we can readily calculate the number of GD steps $N(\varepsilon)$ as $N(\varepsilon) = \ln(\varepsilon/\|\theta_0 - \vartheta\|_2)/\ln(1 - c/\kappa(\mathbb{A})) = O\!\left(\kappa(\mathbb{A})\ln\frac{1}{\epsilon}\right).$ (7.21)

Hence, for a fixed value $c$, large values of the condition number $\kappa(\mathbb{A})$ will severely impede convergence of the simplified gradient descent (7.16) by requiring a much larger number of steps.

# 7.3. Training and operator preconditioning

So far, we have established that, under suitable assumptions, the rate of convergence of the gradient descent algorithm for physics-informed machine learning boils down to the conditioning of the matrix $\mathbb{A}$ (7.13). However, at first sight, this matrix is not very intuitive and we want to relate it to the differential operator $\mathcal{L}$ from the underlying PDE (2.1). To this end, we first introduce the so-called Hermitian square $\mathcal{A}$, given by $\mathcal{A} = \mathcal{L}^*\mathcal{L},$ (7.22)

in the sense of operators, where $\mathcal{L}^*$ is the adjoint operator for the differential operator $\mathcal{L}$. Note that this definition implicitly assumes that the adjoint $\mathcal{L}^*$ exists and the Hermitian square operator $\mathcal{A}$ is defined on an appropriate function space. As an example, consider as differential operator the Laplacian, i.e. $\mathcal{L}u = -\Delta u$,