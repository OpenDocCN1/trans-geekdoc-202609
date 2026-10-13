
\[*Σ*\][*i**j*] = cov[*f*](**x**[(*i*)], **x**[(*j*)]), *i*, *j* = 1, 2, …, *N*.

![Equation](images/B9780443292385000196/si640.png)

Because *Σ* is a positive semidefinite matrix, this guarantees that the covariance function is a *kernel* function (Section [11.5.1](#Chp011_519-582_B9780443292385000172.xhtml)). To stress this, from now on we will use the notation

cov[*f*](**x**, **x**^′) = *κ*(**x**, **x**^′),

![Equation](images/B9780443292385000196/si641.png)

and the covariance matrix becomes the corresponding *kernel matrix* denoted as 𝒦 (Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml)). This change of notation will make the connections with RKHSs readily spotted. Some typical examples of kernel functions used for Gaussian processes are:

*   **Linear kernel**:

    *κ*(**x**, **x**^′) = **x**^(*T*)**x**^′.

    ![Equation](images/B9780443292385000196/si643.png)

*   Note that this kernel does not correspond to a stationary process.

*   **Squared exponential or Gaussian kernel**:

    $$\\kappa(\\mathbf{x},\\mathbf{x}^{\\prime}) = \\exp\\left( - \\frac{{\\|\\mathbf{x} - \\mathbf{x}^{\\prime}\\|}^{2}}{2h^{2}} \\right),$$

    ![Equation](images/B9780443292385000196/si644.png)

*   where *h* is a parameter determining the *length scale* of the process. The larger the value of *h*, the larger the “statistical” similarity (stronger correlation) of two points having a distance *d* = ||**x** − **x**^′|| apart.

    ![Equation](images/B9780443292385000196/si645.png)

*   **Ornstein–Uhlenbeck kernel**:

    $$\\kappa(\\mathbf{x},\\mathbf{x}^{\\prime}) = \\exp\\left( - \\frac{\\|\\mathbf{x} - \\mathbf{x}^{\\prime}\\|}{h} \\right).$$

    ![Equation](images/B9780443292385000196/si646.png)

*   **Rational quadratic kernel**:
