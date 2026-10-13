
where `*` denotes complex conjugation and `S_η` is the power spectral density of the noise field. Thus, we finally obtain

![Equation](images/B978044329238500010X/fx013.jpg) (4.52)

Once `W(ω₁, ω₂)` has been computed, the unknown parameters could be obtained via an inverse (two-dimensional) Fourier transform. The deblurred image then results as

```
d̂(n,m) = ∑_{i=-∞}^{+∞} ∑_{j=-∞}^{+∞} w(i,j) u(n-i, m-j)
```
(4.53)

In practice, because we are not really interested in obtaining the weights of the deconvolution filter, we implement Eq. (4.53) in the frequency domain:

```
D̂(ω₁, ω₂) = W(ω₁, ω₂) U(ω₁, ω₂)
```

and then obtain the inverse Fourier transform. Thus all processing is efficiently performed in the frequency domain. Software packages to perform Fourier transforms (via the fast Fourier transform (FFT)) of an image array are "omnipresent" on the internet.
