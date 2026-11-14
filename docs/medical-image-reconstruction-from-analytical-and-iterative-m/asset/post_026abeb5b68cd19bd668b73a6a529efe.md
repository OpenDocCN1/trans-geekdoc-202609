
![](img/dd555effd38151c67af30d84800c554a_223_0.png)

Fig. 8.2: The 1D ramp filter is a central slice of the 2D ramp filter.

## 8.4.2 Landweber algorithm: FBP with view-based noise weighting

One of the most important reasons to use an iterative algorithm is to incorporate the noise model during image reconstruction. This section considers a simplified case: the noise weighting is view-based. In other words, the weighting factors for all rays at a particular view are the same.

If the initial image is zero, the closed-form Landweber algorithm is

$$X^{(k)} = (A^T W A)^{-1}[I - (I - \alpha A^T W A)^k]A^T W P.$$ (8.15)

If the noise weighting is view-based, matrix W is block-diagonal. Each block corresponds to all the rays in a view. Within each block the diagonal elements are identical.

It is not easy to see what matrix W is doing in $A^T W A$. However, a central slice at a particular angle of $A^T W A$ is simply $|\omega|$ multiplied by a scalar $w_m$, where m is the view index. Thus, the windowed ramp filter at the mth view is given as

$$\frac{|\omega|}{w_m} \left[ 1 - \left( 1 - \frac{\alpha w_m}{|\omega|} \right)^k \right].$$ (8.16)

In eq. (8.15), $A^T W P$ is weighted backprojection of the projections P. At the mth view, all the projections are first multiplied by the scalar $w_m$ and then are backprojected to the image domain. In fact, at the mth view, the projection data multiplier $w_m$ cancels the $w_m$ in the first part $|\omega|/w_m$ of eq. (8.16). The net result is that for view-based noise weighting eq. (8.15) is equivalent to

![](img/dd555effd38151c67af30d84800c554a_224_0.png)

Fig. 8.3: Images reconstructed by the iterative Landweber algorithm (left and the broken line profile) and the Landweber-FBP algorithm (right and the solid line profile). The profiles are drawn across the central horizontal line.

\( X^{(k)} = (A^T A)^{-1} \left[ I - \left( I - \alpha A^T W A \right)^k \right] A^T P. \) (8.17)

The corresponding FBP algorithm for eq. (8.17) is given as follows:

- 1. Find the 1D Fourier transform of the projections \( p(s, \theta) \) with respect to the first variable s, obtaining \( P(\omega, \theta) \).
- 2. Multiply \( P(\omega, \theta) \) with a windowed ramp filter \( |\omega| [1 - (1 - \alpha w_\theta / |\omega|)^k] \), obtaining \( Q(\omega, \theta) \).
- 3. Find the 1D inverse Fourier transform of \( Q(\omega, \theta) \) with respect to the first variable \( \omega \), obtaining \( q(s, \theta) \).
- 4. Backproject \( q(s, \theta) \) to obtain the final reconstruction.

The view-based noise weighting only changes the window function of the ramp filter. The window function depends on the iteration number k, a parameter \( \alpha \), and the view-based weighting \( w_\theta \).

## 8.4.3 Landweber algorithm: FBP with ray-based noise weighting

The FBP algorithms without noise weighting and with view-based noise weighting give shift-invariant point spread function in the reconstructed image. Using ray-based noise weighting will make the FBP algorithm have a shift-variant point spread function. The reconstruction time for ray-based noise weighting can be significantly lengthened. The advantage of using an FBP algorithm would be diminished.

In order to make the algorithm fast, let us be creative. A little deviation in the weighting function has almost no effects on the reconstruction. At each view angle, we quantize the ray-based weighting function into \( N + 1 \) values: \( w_0, w_1, \dots, w_N \), which in turn give \( N + 1 \) different filters. They are

\( W_{k, \alpha, w_n}(\omega) = 1 - \left( 1 - \frac{\alpha w_n}{|\omega|} \right)^k \, , \text{ when } \omega \neq 0, \\
W_{k, \alpha, w_n}(0) = 1, \\
(8.18) \)

for \( n = 0, 1, 2, .., N \). Using these \( N+1 \) filters, \( N+1 \) sets of filtered projections are obtained. Before backprojection, one of these \( N+1 \) projections is selected for each ray according to its proper weighting function. Only one backprojection is performed using the selected filtered projections.

As an example, let us assume that \( N \) is 10 and the measurements are transmission data. Before the projections data are ready to process, we form 11 Fourier domain filter transfer functions \( W_{k, \alpha, w_n}(\omega) \) as defined in eq. (8.18) with, say, \( w_n = \exp(-0.1 \times n \times p_{\max}) \), \( n = 0, 1, 2, .., 10 \), respectively. Here \( p_{\max} \) is the maximum value of the measured line integrals. In implementation, \( \omega \) is a discrete frequency index and takes the discrete values of between \( -0.5 \) and \( 0.5 \) (and “0.5” corresponds to the highest frequency). Note that \( w_n = \exp(-0.1 \times n \times p_{\max}) \) is for one exemplary noise model. One can use other weighting functions for other noise models. The ray-based FBP algorithm can be implemented as

- 1. At each view angle \( \theta \), find the 1D Fourier transform of \( p(s, \theta) \) with respect to \( s \), obtaining \( P(\omega, \theta) \).
- 2. Form \( N+1 \) versions of \( Q_n(\omega, \theta) = P(\omega, \theta) \times W_{k, \alpha, w_n}(\omega) \) with \( n = 0, 1, .., N \).
- 3. Take the 1D inverse Fourier transform of \( Q_n(\omega, \theta) \) with respect to \( \omega \), obtaining \( q_n(s, \theta) \) with \( n = 0, 1, .., N \).
- 4. Construct \( q(s, \theta) \) by letting \( q(s, \theta) = q_n(s, \theta) \) if \( p(s, \theta) \simeq n \times p_{\max}/N \).
- 5. Backproject \( q(s, \theta) \) to obtain the final image.

This ray-based FBP algorithm is fast because it only performs backprojection once. Backprojection is the most time-consuming part in an FBP algorithm. We now demonstrate the effectiveness of this ray-based noise weighting FBP algorithm using a low-dose X-ray CT patient data set (see Figure 8.4). The severe horizontal streaking artifacts across the body are significantly reduced.

The noise model is \( w = \frac{1}{\sqrt{\text{variance}}} \), where “variance” is referred to as the variance of the sinogram (that is, the line integral data). We can have a more general expression of \( w = \frac{1}{\sqrt[\gamma]{\text{variance}}} \), where \( \gamma \) is a parameter. When \( \gamma = 0 \), the weighting function is a constant without any variation. In this case, the noise weighting has no effect. A larger \( \gamma \) gives a larger variation of the weighting function. When \( \gamma = 1 \), the weighting function is the so-called “correct” weighting which is widely used among researchers. Since the weighting function is affected by the “iteration number,” the “correct” weighting may not yield the best results. In practice, the readers are encouraged to use a \( \gamma \) value that is different from 1. In many cases, a \( \gamma \) value between 0 and 1 gives a better result than using \( \gamma = 1 \).

![](img/dd555effd38151c67af30d84800c554a_226_0.png)

Fig. 8.4: Reconstruction results for the clinical data: (Top) The conventional FBP reconstruction; (Bottom) the ray-based noise-weighted FBP reconstruction. Display window is from –400 to 400 HU. [Thanks Raoul M. S. Joemai of Leiden University Medical Center for the CT scan].

## 8.5 FBP algorithm with quadratic constraints

Other than being able to model the data noise, the iterative algorithm can also incorporate constraints as Bayesian optimization. If the constraints are quadratic functions of the image, an FBP algorithm can be developed to incorporate them.

The Bayesian constraints regulate the solutions and effectively control the noise propagation. Therefore, the common iterative Bayesian algorithms do not diverge and, in theory, can iterate till infinity. There is no need to stop the algorithms early.

Many researchers use both noise weighting and Bayesian constraints for iterative image reconstruction.

One can set up a Bayesian objective function

\( X^2 = \|AX - PI\|_{W}^2 + \beta \|FX - GY\|^2 \)
\( = X^T A^T W A X - 2 X^T A^T W P + P^T W P \)
\( + \beta (X^T F^T F X - 2 X^T F^T G Y + Y^T G^T G Y), \)
(8.19)

where Y is a reference image, and F and G are feature extracting matrices. This objective function pushes the selected feature of X to look like the selected feature of Y. For example, if Y is zero and F is the identity matrix, this objective function is looking for a minimum norm solution. If F and G are edge extracting matrices, this objective function is looking for an X that has edges similar to the edges of Y.

The gradient of the objective function (8.19) is

\( \nabla X^2 = 2 [A^T W A X - 2 A^T W P + \beta (F^T F X - F^T G Y)], \)
(8.20)

and its corresponding iterative Landweber algorithm can be readily obtained as

\( X^{(k)} = X^{(k-1)} - \alpha \left[ A^T W \left( A X^{(k-1)} - P \right) + \beta F^T \left( F X^{(k-1)} - G Y \right) \right] \)
\( = \left( I - \alpha A^T W A - \alpha \beta F^T F \right) X^{(k-1)} + \alpha A^T W P + \alpha \beta F^T G Y \)
\( = \left( \alpha A^T W A + \alpha \beta F^T F \right)^{-1} \left[ I - \left( I - \alpha A^T W A - \alpha \beta F^T F \right)^k \right] \left( \alpha A^T W P + \alpha \beta F^T G Y \right) \)
\( + \left( I - \alpha A^T W A - \alpha \beta F^T F \right)^k X^{(0)} \)
\( = \left( A^T W A + \beta F^T F \right)^{-1} \left[ I - \left( I - \alpha A^T W A - \alpha \beta F^T F \right)^k \right] \left( A^T W P + \beta F^T G Y \right) \)
\( + \left( I - \alpha A^T W A - \alpha \beta F^T F \right)^k X^{(0)} . \)
(8.21)

If the initial image is zero, the Landweber Bayesian algorithm becomes

\( X^{(k)} = \left( A^T W A + \beta F^T F \right)^{-1} \left[ I - \left( I - \alpha A^T W A - \alpha \beta F^T F \right)^k \right] \left( A^T W P + \beta F^T G Y \right). \)
(8.22)

The linear iterative algorithm (8.22) can be readily translated into an FBP algorithm.

### 8.5.1 Example of minimum-norm constrained FBP

In order to convert this iterative Bayesian Landweber algorithm (8.22) to an FBP algorithm, we need to know F, G, and Y. As an example, let Y be zero, and F be the identity matrix. In this case, a minimum norm solution is sought. We also assume that W is view-based noise weighting. Then eq. (8.22) becomes
