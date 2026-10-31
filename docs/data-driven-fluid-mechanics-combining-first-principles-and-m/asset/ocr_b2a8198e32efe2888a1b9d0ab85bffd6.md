# 4.7 Application I: Harmonic Analysis and Filters

BIBO stability guarantees that the output produced by a stationary input is also stationary. It is thus interesting to consider only the portion of the complex planes $s$ and $z$ associated to infinite duration signals, that is, $s = j\omega$ and $z = e^{j\theta}$. These correspond to harmonic eigenvalues of the LTI system, hence lead to a *harmonic response*. From Laplace and Z transforms, we move to continuous and discrete Fourier transforms in Section 4.7.1. A system that manipulates the harmonic content of a signal is a filter; these are introduced in Section 4.7.2 along with their fundamental role in multi-resolution decompositions.

# 4.7.1 From Laplace to Fourier

Consider the bilateral Laplace and Z transform of a signal along the imaginary axis $s = j\omega$ and the unitary circle $z = e^{j\theta}$, respectively,

$$U(j\omega) = \mathcal{F}_C\{u(t)\} = \int_{-\infty}^{\infty} u(t) e^{-j\omega t} dt, \tag{4.39a}$$ $$U(j\theta) = \mathcal{F}_D\{u[k]\} = \sum_{k=-\infty}^{+\infty} u[k] e^{-j\theta k}. \tag{4.39b}$$

These are the continuous (CT) and the discrete (time) Fourier Transforms (DTFT). Both are continuous functions, with the second being periodic of period $2\pi$ because of the conformal mapping introduced in Figure 4.3. Comparing these to (4.28) and (4.30) shows that the bilateral Laplace and Z transforms are the Fourier transforms of $u(t)e^{-\sigma t}$ and $u[k]\rho^{-k}$. Without these exponentially decaying modulations, the conditions for convergence are more stringent: signals must be absolutely integrable and absolutely summable$^{14}$.

The main consequence is that *infinite duration stationary signals do not generally admit a Fourier transform*. This explains why the manipulations of these signals by an LTI system are better investigated in terms of some of their statistical properties, such as *autocorrelation* or *autocovariance*, as illustrated in Section 4.8. A special exception are periodic signals for which (4.39a) and (4.39b) lead to Fourier *series*, and the problem of convergence becomes less stringent.

In stable continuous and discrete LTI systems, satisfying (4.30), the impulse response always admits Fourier transform: these can be obtained by replacing $s = j\omega$ and $z = e^{j\theta}$ in the transfer function. This leads to *frequency transfer functions*, which are complex functions of real numbers$^{15}$ ($\omega$ or $\theta$), customarily represented by plotting $\log(|H(x)|)$ and $\arg(H(x))$ versus $\log(x)$ in a Bode plot, with $x = \omega$ or $x = \theta$.

14 This condition is sufficient but not necessary: some non-square integral functions do admit a Fourier transform. Important examples are the constant function $u(t)=1$ or the step function $u_S(t)$. Moreover, note that the Fourier transform can be obtained from the Laplace and Z transform, only for signals that are absolutely integrable or summable. For instance, the Laplace transform of $e^{\alpha t}$ with $\alpha > 0$ has ROC $s > \alpha$, while the Fourier transform does not exist.

15 These are often called *real* frequencies as opposed to the *complex frequencies* $s$ and $z$.