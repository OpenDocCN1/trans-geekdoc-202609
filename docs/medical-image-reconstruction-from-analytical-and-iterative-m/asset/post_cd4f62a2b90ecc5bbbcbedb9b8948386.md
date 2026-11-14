
![](img/dd555effd38151c67af30d84800c554a_35_0.png)

Fig. 2.3: Illustration of the 2D central slice theorem.

plane and lower density at the regions away from the origin. The central region of the Fourier space represents low frequencies. Overweighting with low-frequency components blurs the image.

![](img/dd555effd38151c67af30d84800c554a_35_1.png)

Fig. 2.4: Each view adds a line in the Fourier space. The 2D inverse Fourier transform reconstructs the original image.

To counter this blurring effect, we must compensate for the nonuniformity in the Fourier space. The nonuniform density in the Fourier space is proportional to \(1/\sqrt{\omega_x^2 + \omega_y^2}\). There are two ways to do the compensation.

One way is to multiply the \(\omega_x-\omega_y\) space Fourier “image” by \(\sqrt{\omega_x^2 + \omega_y^2}\), and the resultant Fourier space “image” is \(F(\omega_x, \omega_y)\). The 2D inverse Fourier transform of \(F(\omega_x, \omega_y)\) gives the exact original image \(f(x, y)\).

The other way is to multiply the 1D Fourier transform \(P(\omega, \theta)\) of the projection data \(p(s, \theta)\) by \(|\omega|\). We then take the 1D inverse Fourier transform of \(|\omega|P(\omega, \theta)\). After this special treatment (i.e., filtering) of the projection data, the treated (i.e., filtered) projection data are backprojected, and the exact original image \(f(x, y)\) is obtained. Note that in the previous discussion (see Figure 2.3), we ignored the second variable in \(P(\omega, \theta)\) and \(p(s, \theta)\) on purpose to allow the reader to pay attention to the first variable.

These two methods (i.e., multiplying the Fourier transformed backprojected image by \(\sqrt{\omega_x^2 + \omega_y^2}\) and multiplying the Fourier transformed projections by \(|\omega|\)) will be further discussed later in this book. The second method, which is referred to as the FBP algorithm, is more popular than the first. The function \(|\omega|\) is called the *ramp filter* in tomography, named after its appearance (see Figure 2.5). It is the second method that added negative “wings” around the spikes in the projections in Chapter 1.

![](img/dd555effd38151c67af30d84800c554a_36_0.png)

Fig. 2.5: The 1D ramp filter transfer function.

## 2.3 Reconstruction algorithms

Backprojection accomplishes most of the work in image reconstruction; it converts the projection data at various views into an image, which is almost what we wanted except for the blurring effect. The blurring effect is caused by the \(1/|\omega|\) nonuniform weighting, with \(|\omega| = \sqrt{\omega_x^2 + \omega_y^2}\), in the 2D Fourier space (i.e., the \(\omega_x\omega_y\) plane). Compensation for \(1/|\omega|\) function can be realized by filtering the projection data \(p(s, \theta)\) or equivalently its 1D Fourier transform \(P(\omega, \theta)\) with a ramp filter \(|\omega|\). If the filtered projection data are backprojected, the exact image can be obtained.

### 2.3.1 Method 1

Precisely, this FBP algorithm can be implemented according to the steps shown in Figure 2.6, in which the ramp filtering is implemented as follows:

- (i) Find the 1D Fourier transform of \(p(s, \theta)\) with respect to the first variable \(s\), obtaining \(P(\omega, \theta)\).
- (ii) Multiply \(P(\omega, \theta)\) with a ramp filter \(|\omega|\), obtaining \(Q(\omega, \theta)\).
- (iii) Find the 1D inverse Fourier transform of \(Q(\omega, \theta)\) with respect to the first variable \(\omega\), obtaining \(q(s, \theta)\).

![](img/dd555effd38151c67af30d84800c554a_37_0.png)

Fig. 2.6: The procedure of the filtered backprojection (FBP) algorithm.

### 2.3.2 Method 2

There are more ways than one to do ramp filtering. In fact, we can perform ramp filtering without using the Fourier transform at all. According to the Fourier transform theory, multiplication in one domain (say, the \(\omega\) domain) corresponds to convolution in the other domain (say, the \(s\) domain) (see Figure 2.7).

Thus steps (i), (ii), and (iii) in Method 1 are equivalent to a mathematical procedure called _convolution_. The ramp-filtered data \(q(s, \theta)\) can be obtained by convolution as follows:

\(q(s, \theta) = p(s, \theta) * h(s),\) (2.1)

where “*” denotes the convolution operation, which is an integral with respect to the variable \(s\). Here \(h(s)\) is the convolution kernel and is the 1D inverse Fourier transform of \(H(\omega) = |\omega|\).

Here we give an example of convolution so that you can understand what convolution can do for you. If the convolution kernel \(h(s)\) is not symmetric, you first flip it left–right, making it \(h(-s)\). Second, you imagine that your function \(p(s)\) can be decomposed into vertical spikes (or Dirac’s delta functions). Third, replace each spike by \(h(-s)\), that is, the \(s = 0\) position of \(h(-s)\) is at the spike’s position, and scale \(h(-s)\) by the amplitude (which can be negative) of the spike. Finally, sum up all the shifted and scaled versions of \(h(-s)\), obtaining \(q(s)\) (see Figure 2.8).

Multiplication: \(Q(\omega) = P(\omega) \times H(\omega)\)

Convolution: \(q(s) = p(s) * h(s)\)

Fig. 2.7: An important property of Fourier transform: multiplication in one domain is equivalent to convolution in the other domain.

![](img/dd555effd38151c67af30d84800c554a_38_0.png)

Fig. 2.8: An illustration of the procedure of convolution.

### 2.3.3 Method 3

There is a third way to implement ramp filtering. Let us factor the ramp filter into two parts:

\( H(\omega) = |\omega| = i2\pi\omega \times \frac{1}{i2\pi} \text{sgn}(\omega), \quad (2.2) \)

where \( i = \sqrt{-1} \), \(\text{sgn}(\omega) = 1\) if \( \omega > 0 \), \(\text{sgn}(\omega) = -1\) if \( \omega < 0 \), and \(\text{sgn}(\omega) = 0\) if \( \omega = 0 \). Here we will use two properties of the Fourier transform.

Fact 1: Multiplication by \( i2\pi\omega \) in the Fourier domain (i.e., the \( \omega \) domain) corresponds to the derivative with respect to \( s \) in the spatial domain (i.e., the s domain).

Fact 2: The inverse Fourier transform of \( -i \text{sgn}(\omega) \) is \( 1/(\pi s) \). Convolution with \( 1/(\pi s) \) is called the Hilbert transform.

Using the relationship shown in Figure 2.7, the ramp filtering can be realized as

\( q(s, \theta) = \frac{dp(s, \theta)}{ds} * \frac{-1}{2\pi^2 s}, \quad (2.3) \)

which is a combination of the derivative and the Hilbert transform.

### 2.3.4 Method 4

If we switch the order of ramp filtering and backprojection, we can get another way to reconstruct the image – _backprojection then filtering_. After backprojection, we get a blurred image _b_(_x_, _y_), which is 2D. We need to apply a 2D ramp filter to it. One way to do it is as follows:

- (i) Find the 2D Fourier transform of \( b(x, y) \), obtaining \( B(\omega_x, \omega_y) \).
- (ii) Multiply \( B(\omega_x, \omega_y) \) with a ramp filter \( |\omega| = \sqrt{\omega_x^2 + \omega_y^2} \), obtaining \( F(\omega_x, \omega_y) \).
- (iii) Find the 2D inverse Fourier transform of \( F(\omega_x, \omega_y) \), obtaining \( f(x, y) \).

### 2.3.5 Method 5

Method 3 consists of three components: the derivative, the Hilbert transform, and the backprojection. If we switch the order, we obtain yet another reconstruction algorithm:

- (i) Find the derivative of the projection data \( p(s, \theta) \) with respect to _s_, obtaining \( dp(s, \theta)/ds \).
- (ii) Backproject \( dp(s, \theta)/ds \) over \( 180^\circ \).
- (iii) Perform the line-by-line Hilbert transform, in the direction parallel to the detector at the \( 90^\circ \) position.

### 2.3.6 Method 6

By switching the order of the first two steps in Method 5, we can obtain still another method to reconstruct an image – the finite Hilbert transform of the derivative of the backprojection:

- (i) Backproject \( p(s, \theta) \) to obtain two blurred images \( b_x(x, y) \) and \( b_y(x, y) \), where \( -\sin \theta \) is used as the weighting function in creating \( b_x(x, y) \) and \( \cos \theta \) is used as the weighting function in creating \( b_y(x, y) \).
- (ii) Perform partial derivatives and obtain \( b(x, y) = \partial b_x(x, y)/\partial x + \partial b_y(x, y)/\partial y \).
- (iii) Perform the line-by-line Hilbert transform, in the direction parallel to the detector at the \( 90^\circ \) position.

One distinctive feature of Method 6 is that no filtering is applied to the raw projection data. This feature is important when the list-mode projection data are acquired, for example, in nuclear medicine. In the list-mode data, every event is stored independently and usually there is no easy way to find a neighboring event with which to take a derivative. This algorithm can be easily applied to other imaging geometries and to some situations where the projection data are truncated (i.e., not fully measured).

You must have noticed that we are playing the order changing game to create more and more reconstruction algorithms. We simply change the order of ramp filtering and backprojection, or change of the order of performing derivative, the Hilbert transform, and backprojection. If we keep playing this game, we can make a list of some possible image reconstruction algorithms (see Figure 2.9). Each algorithm has its advantages and disadvantages.

The table in Figure 2.9 does not exhaust all possibilities. For example, the Hilbert transform can be implemented as convolution in the spatial domain or as multiplication in the Fourier domain. The Hilbert transform has another form, which is not convolution but is an integral over a finite interval. The finite Hilbert transform has an important application in handling truncated projection data.

You may see that the backprojection is used in all algorithms. This does not have to be the case. You do not have to use a spatial domain backprojector in a reconstruction algorithm. You can use the central slice theorem by assigning the Fourier domain projection data \( P(\omega, \theta) \) at the proper \( \omega_x\)-\( \omega_y \) locations. This is the Fourier domain implementation of the backprojection. However, this Fourier domain backprojection has limited applications because large interpolation errors could be introduced in the polar coordinate \( (\omega, \theta) \) system to the Cartesian \( (\omega_x-\omega_y) \) system transformation.
