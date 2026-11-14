
## Problems

Problem 2.1 Let a 2D object be defined as

f(x, y) = cos(2πx) + cos(2πy).

Find its 2D Fourier transform $F(\omega_x, \omega_y)$. Determine the Radon transform of this object f(x, y) using the central slice theorem.

Problem 2.2 Let $f_1(x, y)$ and $f_2(x, y)$ be two 2D functions, and their Radon transforms are $p_1(s, \theta)$ and $p_2(s, \theta)$, respectively. If $f(x, y)$ is the 2D convolution of $f_1(x, y)$ and $f_2(x, y)$, use the central slice theorem to prove that the Radon transform of $f(x, y)$ is the convolution of $p_1(s, \theta)$ and $p_2(s, \theta)$ with respect to variable $s$.

Problem 2.3 Let the Radon transform of a 2D object f(x, y) be $p(s, \theta)$, the 2D Fourier transform of f(x, y) be $F(\omega_x, \omega_y)$, and the 1D Fourier transform of $p(s, \theta)$ with respect to the first variable s be $P(\omega, \theta)$. What is the physical meaning of the value $F(0, 0)$? What is the physical meaning of the value $P(0, \theta)$? Is it possible that $\int_{-\infty}^{\infty} \int_{0}^{\infty} g(s, 0^{\circ}) ds \neq \int_{-\infty}^{\infty} \int_{0}^{\infty} g(s, 90^{\circ}) ds$?

Problem 2.4 Prove that the Hilbert transform of the function

$$f(t) = \begin{cases} \sqrt{1-t^2}, & |t| < 1 \\ 0, & |t| \ge 1 \end{cases}$$

is

$$g(t) = \begin{cases} t, & |t| < 1 \\ t - \sqrt{t^2 - 1} \text{sgn}(t), & |t| \ge 1. \end{cases}$$

## Bibliography

- [1] Bracewell RN (1956) Strip integration in radio astronomy. Aust J Phys 9:198–217.
- [2] Bracewell RN (1986) The Fourier Transform and Its Applications, 2nd ed., McGraw-Hill, New York.
- [3] Carrier GF, Krook M, Pearson CE (1983) Functions of a Complex Variable Theory and Technique, Hod, Ithaca.
- [4] Clackdoyle R, Noo F, Guo J, Roberts J (2004) A quantitative reconstruction from truncated projections of compact support. Inverse Probl 20:1281–1291.
- [5] Deans SR (1983) The Radon Transform and Some of Its Applications, John Wiley & Sons, New York.
- [6] Defrise M, Noo F, Clackdoyle KH (2006) Truncated Hilbert transform and image reconstruction from limited tomographic data. Inverse Probl 22:1037–1053.
- [7] Hahn SL (1996) Hilbert Transforms in Signal Processing, Artech House, Boston.
- [8] Huang Q, Zeng GL, Gullberg GT (2007) An analytical inversion of the 180° exponential Radon transform with a numerically generated kernel. Int J Image Graphics 7:71–85.
- [9] Kak AC, Slaney M (1998) Principles of Computerized Tomographic Imaging, IEEE Press, New York.
- [10] Kanwal RP (1971) Linear Integral Equations Theory and Technique, Academic Press, New York.
- [11] Natterer F (1986) The Mathematics of Computerized Tomography, Wiley, New York.
- [12] Noo F, Clackdoyle R, Pack JD (2004) A two-step Hilbert transform method for 2D image reconstruction. Phys Med Biol 49:3903–3923.
- [13] Sidky EY, Pan X (2005) Recovering a compactly supported function from knowledge of its Hilbert transform on a finite interval. IEEE Trans Signal Process Lett 12:97–100.
- [14] Shepp L, Logan B (1974) The Fourier reconstruction of a head section. IEEE Trans Nucl Sci 21:21–43.
- [15] Tricomi FG (1957) Integral Equations, Interscience, New York.
- [16] Ye Y, Yu H, Wei Y, Wang G (2007) A general local reconstruction approach based on a truncated Hilbert transform. Int J Biom Imag 2007: 63634.
- [17] Ye Y, Yu H, Wang G (2007) Exact interior reconstruction with cone-beam CT. Int J Biom Imag 2007: 10693.
- [18] You J, Zeng GL (2006) Exact finite inverse Hilbert transforms. Inverse Probl 22:L7–L10.
- [19] Yu H, Yang J, Jiang M, Wang G (2009) Interior SPECT – exact and stable ROI reconstruction from uniformly attenuated local projections. Commun Numer Methods Eng 25:693–710.
- [20] Yu H, Ye Y, Wang G (2008) Interior reconstruction using the truncated Hilbert transform via singular value decomposition. J X-Ray Sci Tech 16:243–251.
- [21] Zeng GL (2007) Image reconstruction via the finite Hilbert transform of the derivative of the backprojection. Med Phys 34:2837–2843.
- [22] Zeng GL (2015) Re-visit of the ramp filter. IEEE Trans Nucl Sci 62:131–136.
- [23] Zeng GL, You J, Huang Q, Gullberg GT (2007) Two finite inverse Hilbert transform formulae for local tomography. Int J Imag Syst Tech 17:219–223.

## 3 Fan-beam image reconstruction

The image reconstruction algorithms discussed in Chapter 2 are for parallel-beam imaging. If the data acquisition system produces projections that are not along parallel lines, the image reconstruction algorithms presented in Chapter 2 cannot be applied directly. This chapter uses the flat detector and curved detector fan-beam imaging geometries to illustrate how a parallel-beam reconstruction algorithm can be converted to user's imaging geometry for image reconstruction.

### 3.1 Fan-beam geometry and the point spread function

The fan-beam imaging geometry is common in X-ray computed tomography (CT), where the fan-beam focal point is the X-ray source. A fan-beam imaging geometry and a parallel-beam imaging geometry are compared in Figure 3.1.

For the parallel-beam geometry, we have a central slice theorem to derive reconstruction algorithms. We do not have an equivalent theorem for the fan-beam geometry. We will use a different strategy – converting the fan-beam imaging situation into the parallel-beam imaging situation and modifying the parallel-beam algorithms for fan-beam use.

In Chapter 2, when we discussed parallel-beam imaging problems, it was not mentioned, but we always assumed that the detector rotates around at a constant speed and has a uniform angular interval when data are taken. We make the same assumption here for the fan beam.

For the parallel-beam imaging geometry, this assumption results in a shift-invariant point spread function (PSF) for projection/backprojection. In other words, if you put a point source in the x–y plane (it does not matter where you put it), calculate the projections, and perform the backprojection, then you will always get the same star-like pattern (see Figure 3.2). This pattern is called the *point spread function* of the projection/backprojection operation.

In the parallel-beam case, when you find the backprojection at the point (x, y), you draw a line through this point and perpendicular to each detector. This line meets the detector at a point, say, s*. Then add the value p(s*, θ) to the location (x, y).

In the fan-beam case, when you find the backprojection at the point (x, y), you draw a line through this point and each focal-point location. This line has an angle, say, γ*, with respect to the central ray of the detector. Then add the value g(γ*, β) to location (x, y).

It can be shown that if the fan-beam focal-point trajectory is a complete circle, the PSF is shift invariant (i.e., the pattern does not change when the location of the point source changes) and has the same PSF pattern as that for the parallel-beam case (see Figure 3.3).

![](img/dd555effd38151c67af30d84800c554a_66_0.png)

![](img/dd555effd38151c67af30d84800c554a_66_1.png)

Fig. 3.1: Comparison of the parallel-beam and the fan-beam imaging geometries.

This observation is important. It implies that if you project and backproject an image, you will get the same blurred version of that image, regardless of the use of parallel-beam or fan-beam geometry.

If the original image is $f(x, y)$ and if the backprojection of the projection data is $b(x, y)$, then the PSF can be shown to be $1/r$, where $r = \sqrt{x^2 + y^2}$. Then $f(x, y)$ and $b(x, y)$ are related by

$b(x, y) = f(x, y) ** \frac{1}{r}$, (3.1)

where “**” denotes 2D convolution. The Fourier transform of $b$ is $B$, and the Fourier transform of $f$ is $F$. Thus the above relationship in the Fourier domain becomes

![](img/dd555effd38151c67af30d84800c554a_67_0.png)

![](img/dd555effd38151c67af30d84800c554a_67_1.png)

$B(\omega_x, \omega_y) = F(\omega_x, \omega_y) \times \frac{1}{\sqrt{\omega_x^2 + \omega_y^2}}$,

because the 2D Fourier transform of $1/\sqrt{x^2+y^2}$ is $1/\sqrt{\omega_x^2 + \omega_y^2}$.

We already know that if a 2D ramp filter is applied to the backprojected image b(x, y), the original image f(x, y) can be obtained. The same technique can be used for the fan-beam backprojected image b(x, y). The backprojection-then-filtering algorithm is the same for the parallel-beam and fan-beam imaging geometries. If we apply the 2D
