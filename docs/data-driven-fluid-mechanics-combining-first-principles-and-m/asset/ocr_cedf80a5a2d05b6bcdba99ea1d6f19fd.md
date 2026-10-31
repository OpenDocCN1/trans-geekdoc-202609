![](bbox=[0.17, 0.14, 0.9, 0.57])

Figure 5.2 Example of application of the Gabor transform on the signal in (5.5). In both cases α = 0.5, while τ = 2.0,4.5 for the left and the right column, respectively. From top to bottom: raw signal with superposed sliding window of the Gabor transform in thick black line; premultiplied signal; Fourier spectrum of the signal premultiplied by the Gaussian kernel at τ = 2.0,4.5.

This is the same signal analyzed with FT in Figure 5.1. A Gaussian kernel with α = 0.5 is here chosen. The selected kernel is expected to have sufficient width to capture the low-frequency oscillations and to be reasonably well localized to identify the high-frequency oscillations occurring on a shorter time segment. The Gabor kernel is then centered at τ = 2.0 and τ = 4.5, i.e., at the center of the regions interested by the two sinusoidal oscillations. Observing the spectrum of the Gabor transform coefficients, the two frequencies are well localized both in the frequency and time domain, with a single sharp peak in the spectrum at ν = 3 and ν = 10 at the two selected time instants, respectively.

# 5.2.2 Discrete Gabor Transform

In real applications the signals are discretized, thus needing the definition of a discrete Gabor transform. In addition to the discretization of time and frequencies introduced in Chapter 4, we have to include also a discretization of the time shift τ = nτ0, with