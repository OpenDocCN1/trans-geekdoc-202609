where, f(t) is the signal, 
w(t) is the window function.

STFT gives poor time resolution and good frequency resolution for wide window, and poor frequency resolution and good time resolution for narrow window.

# Drawbacks

+   - Once window size is fixed, it cannot be changed.
- STFT cannot extract texture features from images.

# 1.2.3   WAVELET TRANSFORM

Mallat [22] proposed a mathematical tool called wavelet transform for image processing applications where wavelets give both time and frequency information of the signal. A wavelet provides multiresolution analysis i.e represents the image on more than one scale. The advantage of multiresolution analysis is that the features undetected at one scale can be detected by the other scale. Wavelets can represent discontinuity of the image with fewer coefficients.

A wavelet is a small wave with limited duration that has zero average value and is given by

![](bbox=[0.36, 0.5, 0.9, 0.54])

Here,

+   a. Scale (Dilation)
b. Translation (Position)

Generally, wavelets are characterized at scale and location. Wavelets are broadly classified as

+   - Continuous wavelet transform.
- Discrete wavelet transform.

The 1-D Continuous wavelet transform is given by

![](bbox=[0.26, 0.79, 0.9, 0.83])