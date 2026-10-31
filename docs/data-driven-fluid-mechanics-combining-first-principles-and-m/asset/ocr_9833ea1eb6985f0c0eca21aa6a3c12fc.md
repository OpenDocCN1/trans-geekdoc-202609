![](bbox=[0.17, 0.17, 0.47, 0.3])

![](bbox=[0.55, 0.17, 0.88, 0.3])

![](bbox=[0.17, 0.34, 0.47, 0.49])

![](bbox=[0.55, 0.34, 0.88, 0.49])

Figure 5.6 Haar (top row) and Mexican-hat (bottom row) wavelets: time representation (left column) and corresponding frequency spectra (right column).

It is defined as follows:

```
ψ(t) = { 1   if 0 ≤ t < 1/2,
          -1  if 1/2 ≤ t < 1,
           0  otherwise. }  (5.11)
```

Figure 5.5 includes the mother wavelet ψ₁,₀, a scaled Haar wavelet ψ₂,₀ (i.e., with scaling parameter a = 2, thus enlarging the support of the wavelet and, consequently, the corresponding scale), a shifted Haar wavelet ψ₁,₁ (i.e., centered in t = 3/2, being b = 1) and a scaled-shifted Haar wavelet ψ₂,₋₁.

The Haar wavelet has the disadvantage of being noncontinuous (although this is not an issue for the discrete formulation); nonetheless, this turns out to be an advantage for the description of signals with sharp changes. This feature is particularly appreciated, for instance, for edge detection in image processing.

The Haar wavelet is highly localized, thus giving good time localization but poor frequency resolution. This is a direct consequence of the uncertainty principle outlined previously: a compact support in the time-domain results in a broadband frequency spectrum (see Figure 5.6(b)).

Depending on the application and on the desired properties of time–frequency resolution, there is a vast variety of mother wavelets already available in the literature and in software toolboxes. A classic example is the Mexican-hat wavelet: