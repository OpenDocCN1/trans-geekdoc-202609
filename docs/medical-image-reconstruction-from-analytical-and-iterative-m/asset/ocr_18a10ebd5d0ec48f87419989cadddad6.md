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