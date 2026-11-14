# 5.4.4 Three-dimensional backprojection-then-filtering algorithm for Radon data

Let the backprojected image be

b(x,y,z) = \iint_{2\pi} p(s, \overline{\theta}) \bigg|_{s=x \cdot \overline{\theta}} \sin\theta d\theta d\phi.

For the 3D Radon case, the Fourier transform of the projection/backprojection PSF is \(1/(\omega_x^2 + \omega_y^2 + \omega_z^2)\). Therefore, the Fourier transform of the image \(f(x, y, z)\) can be obtained as

F(\omega_x, \omega_y, \omega_z) = B(\omega_x, \omega_y, \omega_z) \times (\omega_x^2 + \omega_y^2 + \omega_z^2).

In the spatial domain, the backprojection-then-filtering algorithm for Radon data can be expressed as

f(x,y,z) = \Delta b(x,y,z) = \frac{\partial^2 b(x,y,z)}{\partial x^2} + \frac{\partial^2 b(x,y,z)}{\partial y^2} + \frac{\partial^2 b(x,y,z)}{\partial z^2},

where \(\Delta\) is the Laplacian operator.

![](bbox=[0.1, 0.475, 0.39, 0.635])

Fig. 5.23: The coordinate system for the 3D Radon inversion formula.

# 5.4.5 Feldkamp's algorithm

First, let us write down the fan-beam FBP reconstruction algorithm for the flat detector and express the image in polar coordinates (see Figure 5.24):

f(r, \varphi) = \frac{1}{2} \int_0^{2\pi} \left(\frac{D}{D-s}\right)^2 \int_{-\infty}^{\infty} \frac{D}{\sqrt{D^2+l^2}} g(l, \beta) h(l'-l) dl d\beta,

where \(h(l)\) is the convolution kernel of the ramp filter, \(D\) is the focal length, \(g(l, \beta)\) is the fan-beam projection, \(l\) is the linear coordinate on the detector, \(s = r \sin(\varphi - \beta)\), and \(l' = \frac{D r \cos(\varphi - \beta)}{D - r \sin(\varphi - \beta)}\). In this formula, \(D/\sqrt{D^2+l^2}\) is the cosine of the incidence angle. When