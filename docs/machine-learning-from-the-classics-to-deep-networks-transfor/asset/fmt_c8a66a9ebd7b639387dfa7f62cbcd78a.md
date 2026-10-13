
# The Discrete Gabor Transform

The discrete version of the Gabor transform can be seen as a special case of the short-time Fourier transform (STFT) (e.g., [57,87]). In the standard DFT transform, the full length of a time sequence, comprising *l* samples, is used all in "one go" in order to compute the corresponding frequency content. However, the latter can be time-varying, so the DFT will provide an average information, which cannot be of much use. The Gabor transform (and the STFT in general) introduces time localization via the use of a window function, which slides along the signal segment in time, and at each time instant focuses on a different part of the signal. This is a way that allows one to follow the slow time variations which take place in the frequency domain. The time localization in the context of the Gabor transform is achieved via a Gaussian window function, that is,

$$
g(n) := \frac{1}{\sqrt{2\pi\sigma^{2}}}\exp\left( - \frac{n^{2}}{2\sigma^{2}} \right).
$$

![Equation](images/B9780443292385000160/si414.png) (10.38)

[Fig. 10.13](#Chp010_463-518_B9780443292385000160.xhtml#f0070)A shows the Gaussian window, `g(n - m)`, centered at time instant *m*. The choice of the window spreading factor, *σ*, will be discussed later on.

![Figure 10.13 (A) The Gaussian window with spreading factor σ centered at time instant m. (B) Pulses obtained by windowing three different sinusoids with Gaussian windows of different spread and applied at different time instants.](images/B9780443292385000160/gr013.jpg)

**Figure 10.13** (A) The Gaussian window with spreading factor *σ* centered at time instant *m*. (B) Pulses obtained by windowing three different sinusoids with Gaussian windows of different spread and applied at different time instants.

Let us now construct the atoms of the Gabor dictionary. Recall that in the case of the signal representation in terms of the DFT in Eq. [(10.29)](#Chp010_463-518_B9780443292385000160.xhtml#deq92), each frequency is represented only once, by the corresponding sampled sinusoid, Eq. [(10.30)](#Chp010_463-518_B9780443292385000160.xhtml#deq93). In the Gabor transform, each frequency appears *l* times; the corresponding sampled sinusoid is multiplied by the Gaussian window sequence, each time shifted by one sample. Thus, at the *i*th frequency bin, we have *l* atoms, **g**^((*m*, *i*)), *m* = 0, 1, …, *l* - 1, with elements given by

`g^((m, i))(n) = g(n - m) * ψ[i](n), n, m, i = 0, 1, …, l - 1,`

![Equation](images/B9780443292385000160/si417.png) (10.39)

where `ψ[i](n)` is the *n*th element of the vector **ψ**[i] in Eq. [(10.30)](#Chp010_463-518_B9780443292385000160.xhtml#deq93). This results in an overcomplete dictionary comprising *l*² atoms in the *l*-dimensional space. [Fig. 10.13](#Chp010_463-518_B9780443292385000160.xhtml#f0070)B illustrates the effect of multiplying different sinusoids with Gaussian pulses of different spread and at different time delays. [Fig. 10.14](#Chp010_463-518_B9780443292385000160.xhtml#f0075) is a graphical interpretation of the atoms involved in the Gabor dictionary. Each node (*m*, *i*) in this time-frequency plot corresponds to an atom of frequency equal to $\frac{2\pi}{l}i$ and delay equal to *m*.

![Figure 10.14 Each atom of the Gabor dictionary corresponds to a node in the time-frequency grid. That is, it is a sampled windowed sinusoid whose frequency and location in time are given by the coordinates of the respective node. In practice, this grid may be subsampled by factors α and β for the two axes, respectively, in order to reduce the number of the involved atoms.](images/B9780443292385000160/gr014.jpg)
