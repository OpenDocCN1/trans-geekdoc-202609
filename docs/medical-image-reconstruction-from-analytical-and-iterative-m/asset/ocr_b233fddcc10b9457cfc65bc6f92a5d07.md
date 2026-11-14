# ### 2.3.3 Method 3

There is a third way to implement ramp filtering. Let us factor the ramp filter into two parts:

\( H(\omega) = |\omega| = i2\pi\omega \times \frac{1}{i2\pi} \text{sgn}(\omega), \quad (2.2) \)

where \( i = \sqrt{-1} \), \(\text{sgn}(\omega) = 1\) if \( \omega > 0 \), \(\text{sgn}(\omega) = -1\) if \( \omega < 0 \), and \(\text{sgn}(\omega) = 0\) if \( \omega = 0 \). Here we will use two properties of the Fourier transform.

Fact 1: Multiplication by \( i2\pi\omega \) in the Fourier domain (i.e., the \( \omega \) domain) corresponds to the derivative with respect to \( s \) in the spatial domain (i.e., the s domain).

Fact 2: The inverse Fourier transform of \( -i \text{sgn}(\omega) \) is \( 1/(\pi s) \). Convolution with \( 1/(\pi s) \) is called the Hilbert transform.

Using the relationship shown in Figure 2.7, the ramp filtering can be realized as

\( q(s, \theta) = \frac{dp(s, \theta)}{ds} * \frac{-1}{2\pi^2 s}, \quad (2.3) \)

which is a combination of the derivative and the Hilbert transform.

# ### 2.3.4 Method 4

If we switch the order of ramp filtering and backprojection, we can get another way to reconstruct the image – _backprojection then filtering_. After backprojection, we get a blurred image _b_(_x_, _y_), which is 2D. We need to apply a 2D ramp filter to it. One way to do it is as follows:

+   (i) Find the 2D Fourier transform of \( b(x, y) \), obtaining \( B(\omega_x, \omega_y) \).
+   (ii) Multiply \( B(\omega_x, \omega_y) \) with a ramp filter \( |\omega| = \sqrt{\omega_x^2 + \omega_y^2} \), obtaining \( F(\omega_x, \omega_y) \).
+   (iii) Find the 2D inverse Fourier transform of \( F(\omega_x, \omega_y) \), obtaining \( f(x, y) \).

# ### 2.3.5 Method 5

Method 3 consists of three components: the derivative, the Hilbert transform, and the backprojection. If we switch the order, we obtain yet another reconstruction algorithm:

+   (i) Find the derivative of the projection data \( p(s, \theta) \) with respect to _s_, obtaining \( dp(s, \theta)/ds \).
+   (ii) Backproject \( dp(s, \theta)/ds \) over \( 180^\circ \).
+   (iii) Perform the line-by-line Hilbert transform, in the direction parallel to the detector at the \( 90^\circ \) position.