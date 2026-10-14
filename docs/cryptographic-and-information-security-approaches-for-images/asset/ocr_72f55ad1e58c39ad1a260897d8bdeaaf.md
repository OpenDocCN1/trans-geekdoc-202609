Wavelets are defined by the wavelet function Ψ(t) (i.e. the mother wavelet) and scaling function Φ(t), the father wavelet in the time domain [10].

Image filtering is necessary for image smoothing and noise removal. Since a low pass filter is used to decrease the disparity between pixel values, thus an orthogonal wavelet low pass FIR filter is used for noise removal/image smoothing. The general formula for filter will be:

F(t) = 1 ; if  f < (threshold − ω)
F(t) = 0 ; if  f > (threshold − ω)

+   - f is representing the filter
+   - ω is representing the wavelength of wavelet
+   - threshold value is used for wavelet co-efficient thersholding

Among different types of wavelet transforms, DWT is critically sampled and most widely used [5,11].

The following dilation and wavelet equations are used to represent a multi-resolution framework: also scaling function and wavelets are represented through it.

φ(t) = √2 Σ₁ⁿ h0(n) φ(2t − n)
Ψ i(t) = √2 Σ₁ⁿ hi(n) φ(2t − n)

+   - i = 1, 2
+   - hi(n), n ∈ ℤ

φ(t) is representing as scaling function and Ψ i(t) is representing wavelet after dilation while hi is depicting as filters of digital filter bank. If hi(n) satisfy the perfect reconstruction conditions given below and if φ(t) is sufficiently regular, then the dyadic dilations and translations of Ψ i(t) form a tight frame for L²(R).

Researchers discussed about the expansive wavelet transform that oversample the time and frequency by some factor, in this case it is 2. The transform has intermediate scales as one scale between each pair of scales of the critically sampled DWT. The wavelet frame has two generators (t); where i = 1, 2 that means the spectrum of the first wavelet is concentrated between the spectrum of the second wavelet and the spectrum of its dilated versions i.e. Ψ i(t) is concentrated between Ψ 2(t) and Ψ 2(2t). The second wavelet is translated by integer multiples of one half rather than whole integers.