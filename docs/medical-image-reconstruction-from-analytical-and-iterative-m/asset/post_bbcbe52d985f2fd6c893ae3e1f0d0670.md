
transform $[Rf](s, \theta)$. Let the noisy line-integral measurements be $p(s, \theta)$. The objective function $v$ depends on the function $f(x, y)$ as follows:

```
v(f) = ||[Rf](s, \theta) - p(s, \theta)||^2 + \beta||f - g||^2,
```

where the first term enforces data fidelity, the second term imposes prior information about the image $f$, the parameter $\beta > 0$ controls the level of influence of the prior information to the image $f$, and $g$ is a reference image. Using integral expressions, $v$ in eq. (8.47) can be written as

```
v(f) = \int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} \left[ \int_{x=-\infty}^{\infty} \int_{y=-\infty}^{\infty} f(x,y) \delta(x \cos\theta + y \sin\theta - s) dy dx - p(s, \theta) \right]^2 ds d\theta + \beta \int_{x=-\infty}^{\infty} \int_{y=-\infty}^{\infty} [f(x,y) - g(x,y)]^2 dy dx.
```

Now we are ready to use the calculus of variations to find the optimal function $f(x, y)$ that minimizes the objective function $v(f)$ in eq. (8.48). The initial step is to replace the function $f(x, y)$ in eq. (8.48) by the sum of two functions: $f(x, y) + \epsilon\eta(x, y)$, where $\eta(x, y)$ can be any arbitrary function. The next step is to evaluate $\frac{dv}{d\epsilon}|_{\epsilon=0}$ and set it to zero. That is,

```
0 = 2 \int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} \left[ \left[ \int_{x=-\infty}^{\infty} \int_{y=-\infty}^{\infty} f(x,y) \delta(x \cos\theta + y \sin\theta - s) dy dx - p(s, \theta) \right] \right. \times \left. \left[ \int_{x=-\infty}^{\infty} \int_{y=-\infty}^{\infty} \eta(x,y) \delta(x \cos\theta + y \sin\theta - s) dy dx \right] ds d\theta \right\} + 2\beta \int_{x=-\infty}^{\infty} \int_{y=-\infty}^{\infty} [f(x,y) - g(x,y)] \eta(x,y) dy dx.
```

In practice, the function $f(x, y)$ is compact, bounded, and continuous almost everywhere. After changing the order of integrals, we have

```
0 = \int_{x=-\infty}^{\infty} \int_{y=-\infty}^{\infty} \eta(x,y) \times \left\{ \int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} \left[ \int_{\hat{x}=-\infty}^{\infty} \int_{\hat{y}=-\infty}^{\infty} f(\hat{x}, \hat{y}) \delta(\hat{x} \cos\theta + \hat{y} \sin\theta - s) d\hat{y} d\hat{x} - p(s, \theta) \right] \right. \left. \delta(x \cos\theta + y \sin\theta - s) ds d\theta + \beta [f(x,y) - g(x,y)] \right\} dy dx.
```

Equation (8.50) is in the form of \(\int \int \eta(x, y)c(x, y)dydx = 0\). Since \(\eta(x, y)\) can be any arbitrary function, according to the calculus of variations, one must have \(c(x, y) = 0\), which is the Euler–Lagrange equation. The Euler–Lagrange equation in our case is

\(\int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} \left[ \int_{\hat{x}=-\infty}^{\infty} \int_{\hat{y}=-\infty}^{\infty} f(\hat{x}, \hat{y})\delta(\hat{x} \cos \theta + \hat{y} \sin \theta - s)d\hat{y}d\hat{x} - p(s, \theta) \right] \delta(x \cos \theta + y \sin \theta - s)dsd\theta + \beta[f(x, y) - g(x, y)] = 0.\) (8.51)

Equation (8.51) can be further rewritten as

\(\int_{\hat{x}=-\infty}^{\infty} \int_{\hat{y}=-\infty}^{\infty} f(\hat{x}, \hat{y}) \left[ \int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} \delta(\hat{x} \cos \theta + \hat{y} \sin \theta - s)\delta(x \cos \theta + y \sin \theta - s)dsd\theta \right] d\hat{y}d\hat{x} + \beta f(x, y) = \int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} p(s, \theta)\delta(x \cos \theta + y \sin \theta - s)dsd\theta + \beta g(x, y).\) (8.52)

Notice that

\(\int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} p(s, \theta)\delta(x \cos \theta + y \sin \theta - s)dsd\theta = \int_{\theta=0}^{\pi} p(s)|_{s=x \cos \theta + y \sin \theta} d\theta = b(x, y)\) (8.53)

is the backprojection of the projection data \(p(s, \theta)\), and the backprojection is denoted as \(b(x, y)\). It must be pointed out that \(b(x, y)\) is not the same as \(f(x, y)\) even when \(p(s, \theta)\) is noiseless because no ramp filter has been applied to \(p(s, \theta)\). Also notice that

\(\int_{\theta=0}^{\pi} \int_{s=-\infty}^{\infty} \delta(\hat{x} \cos \theta + \hat{y} \sin \theta - s)\delta(x \cos \theta + y \sin \theta - s)dsd\theta = \int_{\theta=0}^{\pi} \delta((x - \hat{x}) \cos \theta + (y - \hat{y}) \sin \theta) d\theta = \frac{1}{\sqrt{(x - \hat{x})^2 + (y - \hat{y})^2}}\) (8.54)

is the point spread function of the projection/backprojection operator at point \((x, y)\) if the point source is at \((\hat{x}, \hat{y})\). Using eqs. (8.53) and (8.54), eq. (8.52) becomes

\(\int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(\hat{x},\hat{y}) \left[ \frac{1}{\sqrt{(x-\hat{x})^2 + (y-\hat{y})^2}} + \beta \cdot \delta(x-\hat{x}, y-\hat{y}) \right] d\hat{y}d\hat{x} = b(x,y) + \beta g(x,y).\) (8.55)

The left-hand side of eq. (8.55) is a 2D convolution. Taking the 2D Fourier transform of eq. (8.55) yields

\(F(\omega_x, \omega_y) \times \left[ \frac{1}{\sqrt{\omega_x^2 + \omega_y^2}} + \beta \right] = B(\omega_x, \omega_y) + \beta G(\omega_x, \omega_y), \quad (8.56)\)

or

\(F(\omega_x, \omega_y) = [B(\omega_x, \omega_y) + \beta G(\omega_x, \omega_y)] / \left[ \frac{1}{\sqrt{\omega_x^2 + \omega_y^2}} + \beta \right]. \quad (8.57)\)

Here the uppercase letters are used to represent the Fourier transform of their spatial domain counterparts, which are represented in lowercase letters; \(\omega_x\) and \(\omega_y\) are the frequency variables for x and y, respectively.

Equation (8.57) is in the form of “backprojection first, then 2D filtering” reconstruction approach and the Fourier domain 2D filter is \(\sqrt{\omega_x^2 + \omega_y^2} / (1 + \beta \cdot \sqrt{\omega_x^2 + \omega_y^2})\). By using the central slice theorem, an FBP algorithm, which performs 1D filtering first and then backprojects, can be obtained. The Fourier domain 1D filter for this new FBP algorithm is the central slice of the 2D filter \(\sqrt{\omega_x^2 + \omega_y^2} / (1 + \beta \cdot \sqrt{\omega_x^2 + \omega_y^2})\), which gives

\(\text{RAMP}(\omega) = |\omega| / [1 + \beta \cdot |\omega|]. \quad (8.58)\)

When \(\beta = 0\), eq. (8.58) reduces to the ramp filter \(\omega\) of the conventional FBP algorithm.

## 8.9 Noise-weighted FBP algorithm for uniformly attenuated SPECT projections

If the attenuator in SPECT imaging is uniform, Sections 4.5.1 and 4.5.2 of this book introduce two analytical image reconstruction algorithms: the Tretiak–Metz algorithm and Inouye's algorithm. The main difference between these two algorithms is that the Tretiak–Metz algorithm uses an exponential weighting function in the backprojector, while Inouye's algorithm uses a backprojector that is used as a regular FBP algorithm without the exponential weighting function. The backprojector plays an important role in noise amplification. The exponential weighting function in the backprojector worsens the image noise. Therefore, Inouye's algorithm is the preferred algorithm between these two algorithms.

As presented in Section 4.5.2, Inouye's algorithm converts the uniformly attenuated Radon transform into unattenuated Radon transform, as expressed by eq. (4.26). Therefore, the regular FBP algorithm can be used for image reconstruction.

In order to further control noise, the Landweber-FBP algorithm presented in Section 8.4.3 as well as the algorithms presented in Sections 8.5, 8.6, and 8.7 can be directly applied to the corrected, unattenuated projections provided by eq. (4.26).

## 8.10 Other applications of the Landweber-FBP algorithm

### 8.10.1 The Landweber-FBP version of the iterative FBP algorithm

In a regular iterative image reconstruction algorithm, the projection-domain data is directly backprojected into the image domain. Before backprojection, a noise-weighting function, w, is assigned to projection-domain data, which is the projection-domain discrepancy in an iterative Landweber algorithm.

In an iterative FBP algorithm, the projection-domain data is filtered with prespecified filter. This filter can be chosen as the ramp filter, a Laplacian filter, or a lowpass filter. In a Bayesian algorithm, the Bayesian terms in the objective function can also contain filters. As an example, an objective function can be expressed as follows:

```
\(\chi^2 = (AX - P)^T M (AX - P) + \beta(FX)^T \hat{M} (FX),\quad (8.59)\)
```

where \(M\) and \(\hat{M}\) are two Toeplitz square matrices. We must point out that if the matrix \(M\) is a diagonal matrix, it acts as noise weighting instead of a filter. Noise weighting only scales a value up or down. On the other hand, a filter uses neighboring values as well.

A linear convolution can always be expressed as a Toeplitz matrix multiplication. A Landweber algorithm can be used to minimize this objective function. Using the similar method in Section 8.5, a Landweber Bayesian algorithm can be obtained as

```
\(X^{(k)} = (A^TMA + \beta F^T\hat{M}F)^{-1} \left[ I - \left( I - \alpha A^TMA - \alpha \beta F^T\hat{M}F \right)^k \right] A^TMP\)
\(+ \left( I - \alpha A^TMA - \alpha \beta F^T\hat{M}F \right)^k X^{(0)},\quad (8.60)\)
```

To illustrate how this can be translated into the Fourier domain, let's consider an example of \(\beta = 0\), \(X^{(0)} = 0\), and \(M\) is the Laplacian filter (that is, a second-order derivative filter). The transfer function of the 1D Laplacian filter is \(\omega^2\), and the transfer function of the 2D Laplacian filter is \(\|\vec{\omega}\|^2\). Thus, eq. (8.60) has a 2D transfer function of
