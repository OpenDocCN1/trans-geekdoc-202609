
![](img/ddadb1d3eaa6f9576eea68f95d453bca_101_0.png)

Figure 4.4 (a): Absolute value of the frequency response of an ideal (black continuous), an IIR (red dash-dotted) and an FIR (blue dashed) low-pass filter. (b): impulse responses associated to the frequency responses on the left. In the case of the FIR, the response is shifted backward by α_d.

(Oppenheim & Schafer 2009). These filters have no zeros and N poles, with N the filter order, equally spaced around the unit circle.

Once these poles are computed, the continuous frequency response function can be readily obtained in its factor form and the last step consists in identifying the associated recursive formula as in Exercise 4. However, note that mapping from s to z is usually performed using the bilinear transform¹⁶ rather than the standard mapping z = e^{Δt s} that is used in Exercise 4, since this has the advantage of mapping f_s/2 to π and thus prevents aliasing. The nonlinearity in the bilinear transform results in a wrapping of higher frequencies so the correct cutoff frequency should first be pre-warped to account for the distortion in the frequency calculation¹⁷.

Software packages such as SciPy in Python or MATLAB offer the functions BUTTERWORTH to design a Butterworth filter with given order and cutoff frequency (see PYTHON script Ex5.PY).

The red curves in Figure 4.4(a) show the amplitude response and the impulse response of a Butterworth filter of order 11. The main advantage of these filters is their capability of well approximating the ideal filter using a limited order, which requires storing few coefficients in their recursive formulation. On the other hand, these filters tend to become unstable as the order increases (and the poles approach the unit circle). Moreover, their phase delay is generally not constant, and this potentially introduces phase distortion. Finally, note that since the impulse response of these filters is infinite, these cannot be implemented in the time domain via simple convolution, but via the recursive solution of the filter's LCCDE.

16 which reads

$$ s = \frac{2}{\Delta t}\left(\frac{1 - z^{-1}}{1 + z^{-1}}\right) \longleftrightarrow z = \frac{1 + \Delta t/2\, s}{1 - \Delta t/2\, s} $$

17 The pre-warp can be achieved using f_c' = f_s / π tan(π f_c / f_s). Therefore, if the desired cutoff frequency is f_c = 200 Hz with a sampling frequency f_s = 1000 Hz, the filter should target a cutoff frequency of f_c' = 231.26 Hz to compensate for the warping due to the bilinear transform.

## 2) Finite Impulse Response Filters (FIR)

These filters are constructed in the discrete domain and have no poles (no feedback coefficients in their recursive formulation). This leads to a finite impulse response. The classic design method is the windowing technique, which consists in multiplying the impulse response of the ideal filter in (4.42) by a window w[k], which is zero outside the interval 0 ≤ k ≤ N, with N the filter order.

Taking N as an odd number, these windows are symmetric about the midpoint, that is, w[k] = w[N − k]; this results in the lag α = (N − 1)/2 in the output with respect to the input. The need for a lag in the ideal filter in (4.42)–(4.43) is now clear: if α = 0, the windowed impulse response is centered in 0, and the filter is noncausal. If the filtering is performed “off-line,” it is possible to obtain a zero-phase filter by centering the windowed impulse response in k = 0.

Common functions are the Hanning, Hamming, or Blackman and Kaiser windows. The windowing in the time domain corresponds to a convolution in the frequency domain between the ideal filter and the Fourier transform of the window function. This smooths the transition from the band-pass to the band-stop region. Software packages as SciPy in Python or MATLAB offer the functions FIRWIN and FIR1 to design FIR filters with a given order, cutoff frequency and window function.

In addition to the linear phase response, these filters are also always stable because of the lack of poles. Moreover, the finite length of their impulse response enables their implementation via convolution. Note, however, that FIR filters require much larger order to achieve performances comparable with IIR filters. Figure 4.4(b) shows, in the dashed blue line, the amplitude function and the corresponding impulse response (shifted by (N − 1)/2) of an FIR filter designed using a Hamming window of order N = 111. The higher the filter order, the larger the window multiplying the ideal impulse response, the more this filter approach is the ideal one. On the other hand, increasing the filter order increases the sensitivity of the filter to the finite duration of the signal.

An FIR formulation makes the calculation of complementary filters particularly simple thanks to the constant phase response, solely linked to the filter order. To illustrate this, consider a signal u[k], and its DFT U[n]. Let us filter this signal with a low-pass filter to obtain u_L[k] using an FIR filter with frequency transfer function H_L = |H_L| e^{iαk}. The filter operation in the frequency domain reads U_L = |H_L| e^{-iαθ} U. Let U_H = |H_H| e^{-iαθ} U denote the high-pass filter that gives the signal u_H[k] having complementary spectra (i.e., |H_L| + |H_H| = 1) and same order and thus same phase delay. Using the shifting properties of the Fourier transforms, the link between the low-pass and the high-pass counter parts in the time and frequency domain sets is
k Domain : u_H[k] = u[k + α] − u_L[k],
θ Domain : H_H(iθ)U(iθ) = U(iθ) e^{iαθ} − H_L(iθ)U(iθ)
→ H_H(iθ) = e^{iαθ} − H_L(iθ). (4.44)

Note that the backward shifting u[k + α] in the time domain cancels the phase delay produced by the low-pass filter before performing the subtraction. It is easy to show that because of the linearity of the convolution, the impulse responses of complementary high-pass ($h_H$) and low-pass ($h_L$) filters are linked by¹⁸ $\delta[n] = h_L[n] + h_H[n]$.

Finally, we close with the practical implementation of MRA in “off-line” conditions for which it is possible to release the constraints of causality and use zero-phase filters. These are usually implemented by operating on the signal twice (first on $u[k]$ and then on $u[-k]$), to artificially cancel the phase delay of the operation. In SciPy and in MATLAB this is performed using the function filtfilt.

If the phase delay is canceled, complementary filters can be computed by taking differences of the frequency transfer functions (which become real functions). Therefore, if the first scale with band-pass $[0, f_1]$ is identified by the frequency transfer function $H_1(f) = H_L(f, f_1)$, the second scale with band-pass $[f_1, f_2]$ is identified by a filter with transfer function $H_2(f) = H_L(f, f_2) - H_L(f, f_1)$. The transfer function of the general band-pass filter is $H_m(f) = H_L(f, f_m) - H_L(f, f_{m-1})$, while the last scale is identified by the high-pass filter with $H_M(f) = 1 - H_L(f, f_M)$.

This set of cascaded filters is known as a filter bank and is at the heart of the pyramid algorithm for computing the discrete wavelet transform (Strang 1996, Mallat 2009), where it is combined with sub-sampling at each scale. The general architecture of this decomposition is summarized in Figure 4.4. Observe that at the limit at which all the frequency bands become unitary, the MRA becomes a DFT.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_103_0.png)

Figure 4.5 Pyramid-like algorithm to compute the MRA of a signal. Each band-pass scale is computed as the difference of two low-pass filters and the terms in blue are preserved to form the summation in (4.41). The graph on the right shows a pictorial representation of the partitioning of the signals spectra.

18 Note that this is not the only method of obtaining a high-pass filter from a low-pass filter: another approach is to reverse the frequency response $H_L$, flipping it from left to right about the frequency $f_s/4$ for $f > 0$ and from right to left about $-f_s/4$ for $f < 0$ (see Smith (1997)). The impulse response of the resulting high-pass filter is $h_H[n] = (-1)^n h_L[n]$. The two methods are equivalent if the cutoff frequency separating the transition bands is $f_s/4$. This is the case encountered when performing MRA via dyadic wavelets as discussed in Chapter 5.
