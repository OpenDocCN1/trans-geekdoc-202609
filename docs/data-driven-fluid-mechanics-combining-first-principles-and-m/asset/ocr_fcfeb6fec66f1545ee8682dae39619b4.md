![](bbox=[0.2, 0.15, 0.85, 0.35])

Figure 5.4 Spectrogram of the signal described by (5.5) for two different values of the scaling parameter α = 0.1 (left) and α = 10.0 (right).

temporal-localization capability (i.e., good temporal resolution) but poor frequency resolution. Intuitively, a narrow window isolates short sequences during the time-shifting process, thus hindering the identification of the low-frequency component of the signal and lacking in spectral resolution. On the other hand, a large value of α delivers a broader window, which in turn has poor temporal localization, but better frequency resolution and capability of identifying the low-frequency component of the signal.

Clearly, if α → 0, the spectrogram tends to perfect temporal localization with no frequency resolution (i.e., a pure time-domain description). On the other hand, for α → ∞, the kernel of the Gabor transform tends to the kernel of the FT, thus giving up completely the time resolution in favor of full frequency resolution.

The backbone of this limit of the Gabor transform is the Heisenberg uncertainty principle. In quantum mechanics, according to the uncertainty principle, position and momentum of a particle cannot be simultaneously ascertained with arbitrary precision. In more general terms, it is not possible to arbitrarily localize both a function and its FT. If a signal is sharply localized (for instance a delta function), its FT is broadband; vice versa, a Fourier spectrum with only one non-null component corresponds to a periodic continuous sinusoidal function.

In strict mathematical terms, the uncertainty principle in the framework of time–frequency analysis can be formulated as follows:

( 1/||f||^2 ∫_{-∞}^{+∞} t^2 |f(t)|^2 dt ) ( 1/(2π ||f||^2) ∫_{-∞}^{+∞} ω^2 |f̂(ω)|^2 dω ) ≥ 1/4. (5.7)

The integrals in parentheses are also known as dispersions.

The choice of the Gaussian kernel in the Gabor transform is not accidental. It can be shown that Gaussian functions have an optimal dispersion product, thus minimizing the combined uncertainty in time–frequency localization. The reader can indeed easily verify that, if

f(t) = 1/(α√(2π)) e^{-t^2/(2α^2)}, (5.8)