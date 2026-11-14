
\(f(x, 0) = \frac{1}{4\pi} \int_{0}^{2\pi} d\theta \int_{-1}^{1} \frac{1}{s - x \cos \theta} \frac{\partial p(s, \theta)}{\partial s} ds + h(x), |x| < 1.\)

In the above discussion, we know that we should have enough data to determine the image in region \(\Omega\). However, doing analytic continuation is easier said than done. Mathematically, the right way to do analytic continuation is by doing the Taylor expansions, but this approach is not practical. Currently iterative approaches are used for this purpose.

Another practical problem is the stability issue. In some cases we can prove mathematically that the limited data can uniquely determine an image, but the image reconstruction method can be extremely ill-conditioned and unstable. The limited angle imaging problem could be such an ill-conditioned problem. In a limited angle imaging problem, the ROI does not have full \(180^\circ\) angular measurements. It may only have, for example, \(10^\circ\) angular measurements.

## 2.6 Mathematical expressions

This section presents the mathematical expressions of the 1D Fourier transform pair, the Hilbert transform pair, and two versions of the inverse finite Hilbert transform. The proof of the central slice theorem is given. This section also derives the FBP and backprojection-then-filtering algorithms. The spatial domain filtering methods, such as the convolution backprojection algorithm and the Radon inversion formula, are also included.

### 2.6.1 The Fourier transform and convolution

The 1D Fourier transform is defined as

\(P(\omega) = \int_{-\infty}^{\infty} p(s)e^{-2\pi i s \omega} ds,\)

and the 1D inverse Fourier transform is

\(p(s) = \int_{-\infty}^{\infty} P(\omega)e^{2\pi i s \omega} d\omega.\)

The convolution of two functions \(f\) and \(g\) is defined as

\((f * g)(t) = \int_{-\infty}^{\infty} f(\tau)g(t - \tau)d\tau = \int_{-\infty}^{\infty} f(t - \tau)g(\tau)d\tau.\)

If we denote the Fourier transform operator as \(\mathbf{F}\), the convolution theorem can be stated as

\(\mathbf{F}(f * g) = \mathbf{F}(f) \times \mathbf{F}(g).\) (2.12)

### 2.6.2 The Hilbert transform and the finite Hilbert transform

The Hilbert transform is less well known than the Fourier transform. Unlike the Fourier transform that converts a real function into a complex function, the Hilbert transform converts a real function into another real function.

In this section, we use \(\mathbf{H}\) to denote the Hilbert transform operator. If you apply the Hilbert transform twice, you get the original function back, except for a sign change, that is

\(\mathbf{H}(\mathbf{H} f) = \mathbf{H}^2 f = -f.\) (2.13)

In other words, the inverse Hilbert transform is the negative value of the Hilbert transform.

A real function and its Hilbert transform are orthogonal. If \(g = \mathbf{H} f\), then

\(\int_{-\infty}^{\infty} f(t)g(t)dt = 0.\) (2.14)

For example, the Hilbert transform of \(\cos(t)\) is \(\sin(t)\). The Hilbert transform of \(\sin(t)\) is \(-\cos(t)\).

The Hilbert transform can be defined in the Fourier domain. Let the Fourier transform of a real function \(f(t)\) be \(F(\omega)\), the Hilbert transform of \(f(t)\) be \(g(t)\), and the Fourier transform of \(g(t)\) be \(G(\omega)\), then

\(G(\omega) = -i\operatorname{sgn}(\omega)F(\omega),\) (2.15)

with \(i = \sqrt{-1}\) and \(\operatorname{sgn}(\omega)\) being the signum:

\(\operatorname{sgn}(\omega) = \begin{cases} 1, & \omega > 0 \\ 0, & \omega = 0 \\ -1, & \omega < 0. \end{cases}\) (2.16)

Since the magnitude of \(-i\operatorname{sgn}(\omega)\) is 1, the Hilbert transform is an application of an all-pass filter with a \(\pm 90^\circ\) phase shift.

Equivalently, the Hilbert transform can also be expressed as convolution with the convolution kernel

\(h(t) = \frac{1}{\pi t}\)

as

\(g(t) = h(t) \star f(t) = \text{p.v.} \int_{-\infty}^{\infty} f(\tau) \frac{1}{\pi(t - \tau)} d\tau\)

where “p.v.” means principal value.

We have already seen that the ramp filter can be decomposed into the Hilbert transform and the derivative. It does not matter whether you perform the derivative first and then perform the Hilbert transform or you perform the Hilbert transform first and then perform the derivative. In fact, we have

\(\mathbf{H}(f'(t)) = \frac{d(\mathbf{H}(f(t)))}{dt}.\)

One can also change the order of the Hilbert transform and the \(180^\circ\) backprojection. To understand this property better, we will use the central slice theorem and think in the Fourier domain. Let us consider the backprojection problem

\(b(x,y) = \int_{-\pi/2}^{\pi/2} \mathbf{H}p(s, \theta)|_{s=x \cos \theta + y \sin \theta} d\theta\)

where the Hilbert transform is with respect to the variable \(s\). Let the Fourier transform of \(p(s, \theta)\) be \(P(\omega, \theta)\). The central slice theorem applied to this particular problem is shown in Figure 2.16, where \(P(\omega, \theta)\) is multiplied by either \(i\) or \(-i\) before putting it in the 2D Fourier domain.

An equivalent way to do this backprojection is to backproject \(p(s, \theta)\), then multiply the entire left half \((\omega_x, \omega_y)\) plane by \(i\) and multiply the entire right half \((\omega_x, \omega_y)\) plane by \(-i\). This multiplication action can be achieved by performing line-by-line 1D Hilbert transform in the \(x\) direction. Thus, we have

\(\mathbf{H}_x \int_{-\pi/2}^{\pi/2} p(s, \theta)|_{s=x \cos \theta + y \sin \theta} d\theta = \int_{-\pi/2}^{\pi/2} \mathbf{H}_s p(s, \theta)|_{s=x \cos \theta + y \sin \theta} d\theta\)

In the following, we will briefly introduce the concept of the finite Hilbert transform, which plays an important role in the ROI reconstruction with truncated projection data.

Without loss of generality, we assume that a real function \(f(t)\) is supported in \((-1, 1)\), that is, \(f(t) = 0\) if \(|t| \ge 1\). Then the Hilbert transform of \(f(t)\) is given as

\(g(t) = \text{p.v.} \int_{-1}^{1} f(\tau) \frac{1}{\pi(t - \tau)} d\tau\)

![](img/dd555effd38151c67af30d84800c554a_50_0.png)

Fig. 2.16: Backprojection of \(Hp(s, \theta)\) over \((-\pi/2, \pi/2)\) is equivalent to backprojection of \(p(s, \theta)\) over \((-\pi/2, \pi/2)\), then multiply \(i\) in the left half \((\omega_x, \omega_y)\) plane and multiply \(-i\) in the right half \((\omega_x, \omega_y)\) plane.

Even though \(f(t)\) is supported in a finite interval, \(g(t)\) may not have a finite support. There are some formulas that are able to recover \(f(t)\) using \(g(t)\) only on \([-1,1]\). For example

\( f(t) = \frac{1}{\pi} \sqrt{\frac{t-1}{t+1}} \text{p.v.} \int_{-1}^1 \sqrt{\frac{\tau+1}{\tau-1}} \frac{g(\tau)}{t-\tau} d\tau, \quad (2.23) \)

or

\( f(t) = \frac{1}{\pi \sqrt{1-t^2}} \left[ \int_{-1}^1 f(\tau) d\tau + \text{p.v.} \int_{-1}^1 \frac{\sqrt{1-\tau^2}}{\tau-t} g(\tau) d\tau \right]. \quad (2.24) \)

### 2.6.3 Proof of the central slice theorem

The central slice theorem is given as

\( P(\omega, \theta) = F(\omega \cos \theta, \omega \sin \theta). \quad (2.25) \)

Proof. We start with the definition of the 1D Fourier transform:

$$P(\omega) = \int_{-\infty}^{\infty} p(s) e^{-2\pi i s \omega} ds,$$ (2.26)

then use the definition of \(p(s, \theta)\) (see Section 1.5), obtaining

$$P(\omega, \theta) = \int_{-\infty}^{\infty} \left[ \int_{-\infty}^{\infty} \left[ \int_{-\infty}^{\infty} f(x,y) \delta(x \cos \theta + y \sin \theta - s) \, dx \, dy \right] e^{-2\pi i s \omega} \, ds \right].$$ (2.27)

Changing the order of integrals yields

$$P(\omega, \theta) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x,y) \left[ \int_{-\infty}^{\infty} \delta(x \cos \theta + y \sin \theta - s) e^{-2\pi i s \omega} ds \right] dx dy.$$ (2.28)

Using the property of the \(\delta\) function, the inner integral over \(s\) can be readily obtained, and we have

$$P(\omega, \theta) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x,y) e^{-2\pi i (x \cos \theta + y \sin \theta) \omega} dx dy,$$ (2.29)

that is,

$$P(\omega, \theta) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x,y) e^{-2\pi i (x u + y v)}|_{u=\omega \cos \theta, v=\omega \sin \theta} dx dy.$$ (2.30)

Finally, using the definition of the 2D Fourier transform yields

$$P(\omega, \theta) = F(\omega_x, \omega_y)|_{\omega_x=\omega \cos \theta, \omega_y=\omega \sin \theta}.$$ (2.31)

In the polar coordinate system, the central slice theorem can be expressed as

$$P(\omega, \theta) = F_{\text{polar}}(\omega, \theta).$$ (2.32)

### 2.6.4 Derivation of the FBP algorithm

We start with the 2D inverse Fourier transform in polar coordinates

$$f(x, y) = \int_{0}^{2\pi} \int_{0}^{\infty} F_{\text{polar}}(\omega, \theta) e^{2\pi i (\omega x \cos \theta + y \sin \theta)} \omega d\omega d\theta.$$ (2.33)

Because \(F_{\text{polar}}(\omega, \theta) = F_{\text{polar}}(-\omega, \theta + \pi)\), we have
