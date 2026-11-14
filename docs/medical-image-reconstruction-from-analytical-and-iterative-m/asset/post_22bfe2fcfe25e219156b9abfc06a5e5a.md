
Using the definition of the ramp filter kernel $h(t) = \int_{-\infty}^{\infty} |\omega| e^{j2\pi\omega t} d\omega$, we have

```
h(D' \sin y) = \int_{-\infty}^{\infty} |\omega| e^{j2\pi \omega D' \sin y} d\omega
= \left(\frac{y}{D' \sin y}\right)^2 \int_{-\infty}^{\infty} \left| \omega \frac{\sin y}{y} \right| e^{j2\pi \omega \frac{D' \sin y}{y}} d\left( \omega \frac{\sin y}{y} \right)
= \left(\frac{y}{D' \sin y}\right)^2 \int_{-\infty}^{\infty} |\hat{\omega}| e^{j2\pi \hat{\omega} y} d\hat{\omega}
= \left(\frac{y}{D' \sin y}\right)^2 h(y).
```

If we denote h_{fan}(y) = (D/2) (y/\sin y)^2 h(y), then the fan-beam convolution backprojection algorithm is obtained as

```
f(r, \varphi) = \int_{0}^{2\pi} \frac{1}{(D')^2} \int_{-\pi/2}^{\pi/2} (\cos \gamma) g(y, \beta) h_{fan}(y' - y) dy d\beta.
```

## 3.4.2 A fan-beam algorithm using the derivative and the Hilbert transform

The general idea of decomposition of the ramp filter into the derivative and the Hilbert transform can be applied to fan-beam image reconstruction. A derivative-Hilbert transform-backprojection algorithm can be obtained by doing a coordinate transformation on the Radon inversion formula (see Section 2.6.6) as follows. Noo, Defrise, Kudo, Clackdoyle, Pan, Chen, Wang, You, and many others have contributed significantly in developing algorithms using the derivative and the Hilbert transform. We first rewrite the Radon inversion formula (see Section 2.6.6) in the polar coordinate system, that is, f(r, \varphi) can be reconstructed as

```
f(r, \varphi) = \frac{1}{2} \int_{0}^{2\pi} \int_{-\infty}^{\infty} \frac{\partial p(s, \theta)}{\partial s} \frac{1}{2\pi^2 (r \cos(\theta - \varphi) - s)} ds d\theta.
```

Changing variables from (s, \theta) to (y, \beta) and using \frac{\partial p}{\partial s} = \frac{1}{D \cos y} \frac{\partial g}{\partial y}, we have

\( f(r, \varphi) = \frac{1}{2} \int_{0}^{2\pi} \int_{-\pi/2}^{\pi/2} \frac{1}{D \cos \gamma} \frac{\partial g(y, \beta)}{\partial y} \frac{1}{2\pi^2 D' \sin(y' - y)} D \cos y \, dy \, d\beta \\
= \int_{0}^{2\pi} \frac{1}{4\pi^2 D'} \int_{-\pi/2}^{\pi/2} \frac{\partial g(y, \beta)}{\partial y} \frac{1}{\sin(y' - y)} dy \, d\beta \quad (3.16) \)

where \( D' \) is the distance from the reconstruction point to the focal point at angle \( \beta \). This \( D' \) factor is not desirable in a reconstruction algorithm. A small \( D' \) can make the algorithm unstable; this spatially variant factor also costs some computation time. In a \( 2\pi \) scan, each ray is measured twice. If proper weighting is chosen for the redundant measurements, this \( D' \) factor can be eliminated.

Let us introduce a weighting function \( w \) in the above DHB algorithm:

\( f(r, \varphi) = \frac{1}{4\pi^2} \int_{0}^{2\pi} \frac{w(y', \beta, r, \varphi)}{D'} \int_{-\pi/2}^{\pi/2} \left( \frac{\partial}{\partial y} + \frac{\partial}{\partial \beta} \right) g(y, \beta) \frac{1}{\sin(y' - y)} dy \, d\beta. \quad (3.17) \)

If we use \( \hat{g} \) to denote the result of the derivative and Hilbert transform of the fan-beam data:

\( \hat{g}(y', \beta) = \int_{-\pi/2}^{\pi/2} \left( \frac{\partial}{\partial y} + \frac{\partial}{\partial \beta} \right) g(y, \beta) \frac{1}{\sin(y' - y)} dy, \quad (3.18) \)

then

\( f(r, \varphi) = \frac{1}{4\pi^2} \int_{0}^{2\pi} \frac{w(y', \beta, r, \varphi)}{D'} \hat{g}(y', \beta) \, d\beta. \quad (3.19) \)

It can be shown that \( \hat{g}/D' \) has the same redundancy property as the original fan-beam data \( g \) (see Figure 3.8). Therefore, it is required that the weighting function satisfies the condition

\( w(y', \beta, r, \varphi) + w(y'_c, \beta_c, r, \varphi) = 2, \quad (3.20) \)

with \( y'_c = -y' \) and \( \beta_c = \beta + 2\gamma + \pi \). If we define \( w(y', \beta, r, \varphi) = D'/(D \cos y') \), then the above condition is satisfied because \( D' + D'_c = 2D \cos y' \) (see Figure 3.12). Finally,

\( f(r, \varphi) = \frac{1}{2} \left\{ \frac{1}{4\pi^2} \int_{0}^{2\pi} \left[ \frac{w(y', \beta, r, \varphi)}{D'} + \frac{w(y''_c, \beta_c, r, \varphi)}{D''_c} \right] \hat{g}(y', \beta) \, d\beta \right\} \\
= \frac{1}{4\pi^2 D} \int_{0}^{2\pi} \frac{1}{\cos y} \hat{g}(y', \beta) \, d\beta. \quad (3.21) \)

![](img/dd555effd38151c67af30d84800c554a_76_0.png)

**Fig. 3.12:** Proper weighting can make the distance-dependent factor disappear from the backprojector in a 360° full scan.

This result can be derived without introducing a weighting function _w_ (see a paper listed at the end of this chapter by You and Zeng [14]).

## 3.4.3 Expression for the Parker weights

Short scan in fan-beam tomography has wide applications in industry and health care; it can acquire sufficient line-integral measurements by scanning the object 180° plus the full fan angle.

In short-scan fan-beam imaging, the projections \(g(\gamma, \beta)\) are acquired when the fan-beam rotation angle \(\beta\) is in the range of [0°, 180° + 2\(\delta\)] or in a larger range, where \(\delta\) is half of the fan angle. The redundant measurements in the range of [0°, 180° + 2\(\delta\)] are weighted by the Parker weights:

```
\(\begin{aligned} w(\gamma, \beta) = \left\{ \begin{aligned} \sin^2\left( \frac{\pi}{4} \frac{\pi+2\delta-\beta}{\delta+\gamma} \right), \quad \text{if} \quad \pi - 2\delta \le \beta \le \pi + 2\delta \quad \text{and} \quad 0 \le \frac{\pi+2\delta-\beta}{\delta+\gamma} \le 2, \\ \sin^2\left( \frac{\pi}{4} \frac{\beta}{\delta+\gamma} \right), \quad \text{if} \quad 0 \le \beta \le 4\delta \quad \text{and} \quad 0 \le \frac{\beta}{\delta-\gamma} \le 2, \\ 1, \quad \text{otherwise} \end{aligned} \right. 
\end{aligned}\)
```

One then uses the scaled fan-beam projections \(w(\gamma, \beta)g(\gamma, \beta)\) in place of \(g(\gamma, \beta)\) in the fan-beam FBP image reconstruction algorithm.

Short-scan weighting is not unique. A function \(w(\gamma, \beta)\) is a valid short-scan weighting function as long as it satisfies

```
\(w(\gamma, \beta) + w(-\gamma, \beta + 2\gamma + \pi) = 1.\)
```

For discrete data, the weighting function \(w(\gamma, \beta)\) must be very smooth, otherwise artifacts will appear. If the weighting function is not smooth enough, a sudden change in the projections can cause a spike in the ramp-filtered projections. In an ideal situation, an opposite spike will also be created and this opposite spike should be able to cancel the other spike. When data are discretely sampled, the positive spike and the negative spike do not match well. The uncanceled residue causes image artifacts. The main strategy of Parker's method is to make the weighting function as smooth as possible so that the weighting function does not introduce any undesired components.

## 3.4.4 Errors caused by finite bandwidth implementation

In the derivation of the fan-beam FBP algorithm in Section 3.4.1, the bandwidth of the ramp filter is assumed to be infinity:

$$h(\gamma) = \int_{-\infty}^{\infty} |\omega| e^{i2\pi\omega\gamma} d\omega.\tag{3.24}$$

It has a property that

$$h(a\gamma) = \int_{-\infty}^{\infty} |\omega| e^{i2\pi\omega\gamma} d\omega = \frac{1}{a^2} h(\gamma).\tag{3.25}$$

In practice, the data are discretely sampled and the bandwidth is bounded. The band-limited ramp filter is expressed as

$$h_{\Omega}(\gamma) = \int_{-\Omega}^{\Omega} |\omega| e^{i2\pi\omega\gamma} d\omega.\tag{3.26}$$

Let $x = a\omega$ and we have

$$h_{\Omega}(a\gamma) = \frac{1}{a^2} \int_{-a\Omega}^{\Omega} |x| e^{i2\pi x\gamma} dx = \frac{1}{a^2} h_{\Omega \doteq a}(\gamma) \neq \frac{1}{a^2} h_{\Omega}(\gamma).\tag{3.27}$$

Therefore, for band-limited fan-beam data, the derivation of the fan-beam FBP algorithm in Section 3.4.1 is not valid. Fortunately, for the full-scan fan-beam projections, the errors in the FBP reconstruction are not significant and are usually noticeable. However, the errors can be significant for short-scan fan-beam data when the fan-beam focal length is short and the Parker weights are used. Figure 3.13 illustrates a short-scan fan-beam FBP reconstruction when a short focal length of 270 units is used. The object is a uniform disk with a radius of 230 units. The true image value within the disk is 1. The image display window is [0.76, 1.57].
