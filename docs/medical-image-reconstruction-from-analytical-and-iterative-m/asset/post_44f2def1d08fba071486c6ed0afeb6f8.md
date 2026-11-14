
Similar to the \(\mu = 0\) case, the notched ramp filtering can be decomposed into a derivative and a notched Hilbert transform. In the spatial domain, the Hilbert transform is a convolution with a convolution kernel \(1/s\). The notched Hilbert transform, on the other hand, is a convolution with a convolution kernel \((\cos \mu s)/s\).

In the Fourier domain, the notched Hilbert filter function is shown on the left-hand side of the graphic equation in Figure 4.21. The cosine function can be decomposed into \(\cos(\mu s) = (e^{\mu s} + e^{-\mu s})/2\). The Fourier transform has a property that multiplication by \(e^{\mu s}\) in the \(s\) domain corresponds to shifting by \(\mu/(2\pi)\) in the \(\omega\) domain (i.e., the Fourier domain). Therefore, the Fourier transform of \((\cos \mu s)/s\) is the combination of two shifted versions (one shifted to the left by \(\mu/(2\pi)\) and the other one shifted to the right by \(\mu/(2\pi)\)) of the Fourier transform of \(1/s\) (see Figure 4.21).

If \(\mu\) is nonuniform, an FBP-type algorithm exists but is rather sophisticated and will be briefly discussed in Section 4.5.4.

![](img/dd555effd38151c67af30d84800c554a_96_0.png)

Fig. 4.21: A notched Hilbert transform transfer function can be decomposed into two shifted Hilbert transform transfer functions.

## 4.4.3 SPECT: Inouye's algorithm for uniform attenuation

The Tretiak–Metz algorithm is in a beautiful FBP form. However, this algorithm generates very noisy images. The significant noise propagation from the projections to the reconstructed image is mainly contributed by the backprojector. In the Tretiak–Metz FBP algorithm, the backprojector has an exponential factor \(e^{-\mu t}\), where \(t\) can be positive or negative. This exponential factor gives a noise variance amplification factor of \(e^{-2\mu t}\). In other words, if the noise variance in the filtered sinogram is \(\sigma^2\), the noise will propagate into the reconstructed image with a variance approximately \(e^{-2\mu t}\sigma^2\). For example, let \(\mu = 0.15/cm\) and \(t = -10\) cm; these result in \(e^{-2\mu t} = 20\). A 20-fold noise amplification is huge! In the regions farther away from the center (i.e., \(|t|\) is larger), the image noise dramatically becomes larger.

The main idea in Inouye's algorithm is to convert the attenuated projections into unattenuated projections, and then use a regular FBP algorithm to reconstruct the image. The regular FBP algorithm does not have an exponential factor in the backprojector. Inouye's algorithm is summarized as follows:

- (1) Pre-scale the measured projection \(p(s, \theta)\) by \(e^{d(s, \theta)}\), where the definition of distance \(d(s, \theta)\) is given in Figure 4.18. We denote this scaled projection as \(\hat{p}(s, \theta)\). [This step is the same as in the Tretiak–Metz algorithm.]
- (2) Take the 2D Fourier transform of \(\hat{p}(s, \theta)\), obtaining \(\hat{P}(\omega, k)\). [Note that \(\hat{p}(s, \theta)\) is periodic with respect to \(\theta\), and the Fourier transform in the \(\theta\) dimension is actually the Fourier series expansion.]

![](img/dd555effd38151c67af30d84800c554a_97_0.png)

Fig. 4.22: FBP image reconstruction with uniformly attenuated SPECT projections. Left: Reconstruction by the Tretiak–Metz algorithm. Right: Reconstruction by the Inouye algorithm.

- (3) Convert \(\hat{P}(\omega, k)\) to \(P(\omega, k)\) according to

\(P(\omega, k) = \gamma^k \hat{p} \left( \sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2}, k \right)\) (4.11)

with

\(\gamma = \frac{|\omega|}{\sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2} + \frac{\mu}{2\pi}}.\) (4.12)

- (4) Find the inverse 2D Fourier transform and obtain \(p_{new}(s, \theta)\).
- (5) Use a regular FBP to reconstruct the image using the newly estimated projections \(p_{new}(s, \theta)\).

Figure 4.22 shows the comparison of the images reconstructed by the Tretiak–Metz algorithm and the Inouye algorithm, using noisy computer-simulated uniformly attenuated emission projections. The Tretiak–Metz algorithm gives a much noisier image, and the noise gets more severe as the location is farther away from the center.

## 4.5 Mathematical expressions

### 4.5.1 Expression for Tretiak–Metz FBP algorithm

Now we give the mathematical expression of the FBP algorithm for SPECT with uniform attenuation correction. This algorithm has been outlined in Section 4.4.2. After the pre-scaling step, the scaled projection p(s, θ) can be related to the original image f(x, y) as

\(\hat{p}(s, \theta) = \int_{-\infty}^{\infty} e^{\mu t} f(\vec{s}\theta + t\vec{\theta}^\perp) dt.\)

You can refer to Section 1.5 for notation definitions. The following gives an FBP algorithm using the derivative and the notched Hilbert transform:

\(f(x, y) = \frac{1}{4\pi^2} \int_{0}^{2\pi} e^{-\mu(-x\sin\theta + y\cos\theta)} \int_{-\infty}^{\infty} \frac{\cos(\mu(s - x\cos\theta - y\sin\theta))}{s - x\cos\theta - y\sin\theta} \frac{\partial \hat{p}(s, \theta)}{\partial s} ds d\theta.\)

### 4.5.2 Derivation for Inouye's algorithm

Let f(x, y) be a density function in the x–y plane and fθ be the function f rotated by θ clockwise. After the pre-scaling step, the scaled projection p̂(s, θ) can be related to the original image f(x, y) as

\(\hat{p}(s, \theta) = \int_{-\infty}^{\infty} e^{\mu t} f_\theta(s, t) dt.\)

Taking the 1D Fourier transform with respect to s yields

\(\hat{p}_{s \to \omega}(\omega, \theta) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{\mu t} f_\theta(s, t) e^{-2\pi i s \omega} dt ds\)
\(= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f_\theta(s, t) e^{-2\pi i (\omega s + t - \frac{\mu}{2\pi})} ds dt.\)

Let

$$\omega = \hat{\omega} \cos \alpha, \quad -\frac{\mu}{2\pi i} = \hat{\omega} \sin \alpha, \tag{4.17}$$

which give

$$\hat{\omega} = \sqrt{\omega^2 - (\frac{\mu}{2\pi})^2}, \quad \alpha = \frac{i}{2} \ln \frac{\omega + \frac{\mu}{2\pi}}{\omega - \frac{\mu}{2\pi}}. \tag{4.18}$$

Changing the $s$-$t$ coordinate system to the $x$-$y$ coordinate system with $s = x \cos \theta + y \sin \theta$ and $t = -x \sin \theta + y \cos \theta$, we have

$$\hat{p}_{s \to \omega}(\omega, \theta) = \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} f(x,y) e^{-2\pi i \hat{\omega} [x \cos(\theta + \alpha) + y \sin(\theta + \alpha)]} \, dx \, dy \tag{4.19}$$
$$= F(\hat{\omega} \cos(\theta + \alpha), \hat{\omega} \sin(\theta + \alpha)).$$

Here $F$ is the 2D Fourier transform of the image $f$. Since $F(\hat{\omega} \cos(\theta + \alpha), \hat{\omega} \sin(\theta + \alpha))$ is a periodic function in $\theta$ with a period of $2\pi$, $F$ has a Fourier series expansion. Thus, we can use the Fourier series expansion on the right-hand side of eq. (4.19):

$$\hat{p}_{s \to \omega}(\omega, \theta) = \sum_n F_n(\hat{\omega}) e^{in(\theta + \alpha)}, \tag{4.20}$$

where the Fourier coefficients are defined as

$$F_n(\hat{\omega}) = \frac{1}{2\pi} \int_0^{2\pi} F(\hat{\omega} \cos \theta, \hat{\omega} \sin \theta) e^{-in\theta} \, d\theta. \tag{4.21}$$

Then,

$$\hat{p}_{s \to \omega}(\omega, \theta) = \sum_n F_n(\hat{\omega}) e^{in(\theta + \alpha)} \tag{4.22}$$
$$= \sum_n F_n \left( \sqrt{\omega^2 - (\frac{\mu}{2\pi})^2} \right) e^{in\theta} e^{\frac{in i}{2} \ln \frac{\omega + \frac{\mu}{2\pi}}{\omega - \frac{\mu}{2\pi}}}$$
$$= \sum_n \left( \frac{\omega - \frac{\mu}{2\pi}}{\omega + \frac{\mu}{2\pi}} \right)^{\frac{n}{2}} F_n \left( \sqrt{\omega^2 - (\frac{\mu}{2\pi})^2} \right) e^{in\theta}.$$

On the other hand, \(\hat{p}_{s \to \omega}(\omega, \theta)\) is also a periodic function with a period of \(2\pi\). It has a Fourier series expansion:

\(\hat{p}_{s \to \omega}(\omega, \theta) = \sum_n \hat{p}(\omega, n)e^{in\theta}.\)

By comparing the expansion coefficients on both sides, we have

\(\hat{P}(\omega, n) = \left( \frac{\omega - \frac{\mu}{2\pi}}{\omega + \frac{\mu}{2\pi}} \right)^{\frac{n}{2}} F_n \left( \sqrt{\omega^2 - \left( \frac{\mu}{2\pi} \right)^2} \right).\)

If we use \(P(\omega, n)\) to represent the 2D Fourier transform of the unattenuated projections \(p(s, \theta)\), the above relationship is

\(\hat{P}(\omega, n) = \left( \frac{\omega - \frac{\mu}{2\pi}}{\omega + \frac{\mu}{2\pi}} \right)^{\frac{n}{2}} P \left( \sqrt{\omega^2 - \left( \frac{\mu}{2\pi} \right)^2}, n \right)\)

or

\(\begin{aligned} P(\omega, n) &= \left( \frac{\sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2} + \frac{\mu}{2\pi}}{\sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2} - \frac{\mu}{2\pi}} \right)^{\frac{n}{2}} \hat{P} \left( \sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2}, n \right) \\ &= \left( \frac{\omega}{\sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2} - \frac{\mu}{2\pi}} \right)^n \hat{P} \left( \sqrt{\omega^2 + \left(\frac{\mu}{2\pi}\right)^2}, n \right). \end{aligned}\)

The measured attenuated data are used to compute \(\hat{P}(\omega, n)\). The above Inouye's relationship is used to estimate \(P(\omega, n)\), which gives the estimated unattenuated projections \(p(s, \theta)\). The final reconstruction is obtained from \(p(s, \theta)\) by a regular FBP algorithm. We would like to clarify that when we say 2D Fourier transform of \(p(s, \theta)\), it is really a combination of the 1D Fourier transform with respect to \(s\) and the Fourier series expansion with respect to \(\theta\).

### 4.5.3 Rullgård's derivative-then-backprojection algorithm for uniform attenuation

There are many other ways to reconstruct SPECT data with uniform attenuation corrections. We can still play the game of switching the order of filtering and backprojection. For example, we can first take the derivative and then backproject. This results in an intermediate image \(\hat{f}(x, y)\) that is closely related to the original image \(f(x, y)\):

\(\hat{f}(x, y) = f(x, y) \times \frac{\cosh(\mu x)}{x},\)

which is a 1D convolution (i.e., line-by-line convolution in the \(x\)-direction). The deconvolution of this expression to solve for \(f(x, y)\) is not an easy task because the function
