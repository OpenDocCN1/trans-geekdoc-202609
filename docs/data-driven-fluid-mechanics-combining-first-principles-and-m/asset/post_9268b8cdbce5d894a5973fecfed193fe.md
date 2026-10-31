
$$J(\mathbf{w}) = \|\mathbf{y}^{(0)} - \mathbf{H}\mathbf{w}\|_2^2 + \alpha R(\mathbf{w}), \qquad (4.53)$$

with $\alpha \in \mathbb{R}$ acting as a smoothing parameter and $R(\mathbf{w})$ a regularizing function.22 Classic choices are $R(\mathbf{w}) = \|\mathbf{w}\|_2$ ($l^2$ penalty), or $R(\mathbf{w}) = \|\mathbf{w}\|_1$ ($l^1$ penalty), or a combination of the two. The first is known as Tikhonov regularization, the second as LASSO regularization, and the third as Elastic Net. These classic tools from machine learning (see Vladimir Cherkassky 2008, Murphy 2012, Bishop 2016) are also employed in Chapter 12.

The reader should notice that the regression method can be generalized easily: one could replace the predictive equation (4.52) by a more complex model (e.g., an artificial neural network or template of polynomial nonlinearities as in Chapter 12) and minimize a cost function like (4.53) using an arsenal of optimization strategy.

## Exercise 6: Time-Series Forecasting via LTI Systems

Generate a synthetic stochastic system with coefficients $(a_1,a_2)=(-1/2,0)$ and $(b_0,b_1,b_2)=(2,1.8,-1.2)$. Consider a deterministic input signal $u[k]=u(t_k)=\sin(8\pi t_k)+3\exp(-(t_k-3)^2/2)$ with $t_k=k\Delta t$, $\Delta t=0.02$ and $k\in[0,1999]$. The stochastic contribution $y_s[k]$ is white noise in $[0,1]$. Use the set of 2 000 points in input and output to identify the set of coefficients from the data, by solving (4.53) with a Tikhonov regularization. Consider $\alpha=1$, and recall that the minimization of $J(\mathbf{w})$ in this kind of regression (known also as Ridge regression) has the simple solution

$$\mathbf{w} = (\mathbf{H}^T\mathbf{H}+\alpha\mathbf{I})^{-1}\mathbf{H}\mathbf{y}^{(0)},$$

with $\mathbf{I}$ the identity matrix. Is the expected result recovered? Is the identified LTI system capable of predicting what happens if $t_k>5$? What happens for $\alpha=0$ (i.e., ordinary least squares)?

## 4.9 What’s Next?

This chapter reviewed the fundamentals of signals and systems and presented LTI systems in case of SISO. We have seen that the input–output relation can be derived from knowledge of the impulse response of a system and via the convolution integral. It was shown that complex exponentials are eigenfunctions of these systems and that important transforms can be derived by projecting input and output signals onto these eigenfunctions. In the eigenspace of the LTI systems, convolutions become multiplications.

22 readers familiar with Lagrangian multipliers should recognize in (4.53) an augmented cost function with $\alpha$ the Lagrangian multiplier.

Chapter 10 presents LTI systems, the so-called *state-space* representation, which is more common in dynamical system theory and which allows for straightforward generalization to MIMO systems. Chapter 11 reviews the analysis of nonlinear systems, while Chapter 12 describes the system identification more broadly and also considers nonlinear systems.

This chapter reviewed the link between the continuous and the discrete world and the impact of the discretization on the eigenfunctions of an LTI system. Special values of the complex frequencies, called poles, yield infinite response of a system and are linked to the notion of stability, reviewed in Chapter 13. The reader should recognize that the identification of these poles from large data sets is the essence of the DMD described in Chapter 7.

Finally, this chapter also introduced the fundamentals of MRA, which complements wavelet theory in Chapters 5 and 8 on the multiscale proper orthogonal decomposition.

## 5 Time–Frequency Analysis and Wavelets

S. Discetti

Spectral analysis is the cornerstone of some of the most celebrated turbulent flow theories. When focusing on the identification and modeling of coherent flow patterns, on the other hand, the need of localizing the spectral content in time or space often arises. Time–frequency analysis encompasses an arsenal of techniques aimed to localize the spectral content of a signal in time (although for velocity fields we could clearly refer to space and spatial frequencies). This chapter gives an overview of techniques for time–frequency analysis. We start the journey with the windowed Fourier transform (WFT) in continuous and discrete form, and introduce the concepts of shifting and stretching to localize a variety of scales. The bounds imposed by the uncertainty principle will clearly arise. Then, we adapt to those bounds introducing the continuous wavelet transform (CWT) and its link to multi-resolution analysis (MRA). The fundamentals of the discrete wavelet transform (DWT) and its intimate relation with filter banks will be outlined. Finally, two applications are presented: a time–frequency analysis of hot-wire data in a turbulent pipe flow using the WFT and the CWT; filtering and compression of velocity fields using a filter based on the DWT. MATLAB codes to practice with the provided examples are provided on the book’s webpage.¹

### 5.1 Introduction

The Fourier transform (FT) of a function f(t) is an integral transform representing its projection into harmonic functions. From the inner product introduced in Chapter 4, the FT is defined as follows:

$$\mathcal{F}(\omega) = \int_{-\infty}^{+\infty} f(t)e^{-j\omega t}\,dt.\tag{5.1}$$

The FT is a powerful and efficient technique to solve a wide variety of problems, ranging from data analysis and filtering, image compression, communications, and so on (Smith 2007b). Nonetheless, the FT has severe limitations when applied to non-stationary signals. Indeed, the FT describes the signal’s frequency content, but does not provide time localization, i.e., it does not determine the time in which a given frequency occurs in the signal. This information is lost because of the infinite integration bounds in (5.1) and the infinite support of the harmonic basis e^{-j\omega t}.

¹ www.datadrivenfluidmechanics.com/download/book/chapter5.zip

Consider, for example, the signal $x(t)$ represented in Figure 5.1, with its (discrete) FT normalized with respect to its maximum and represented as a function of the frequency $\nu = \omega/2\pi$. The signal exhibits two different frequencies in well-localized time intervals. Even though a clear signature of the two main frequencies is present in the spectrum, no information is retained on the time localization of those frequencies.

Although this example might appear extreme at first glance, there is a wide range of applications where the localization in time is relevant, for example, timescale modification, sinusoidal modeling of musical compositions, cross-synthesis, and so on. In fluid mechanics, the localization of scales in space-time has strong potential implications in the identification and modeling of the flow dynamics (Farge 1992, Schneider & Vasilyev 2010). For such cases, different implementations are sought, possibly maintaining the appeal of computationally efficient algorithms such as the fast Fourier transform (FFT, Cooley & Tukey 1965).

Chapter 4 introduced the limits of the FT and the MRA. This chapter focuses on techniques for time–frequency analysis of signals, including a discussion of the capabilities and limits of the WFT, and the wavelet-based multi-resolution methods. The relation between the DWT and filter banks is also briefly discussed. The objective is to introduce the fundamental concepts of time–frequency analysis, making no pretence of being exhaustive. For a more comprehensive mathematical background, the reader is referred to several excellent literature contributions on the topic (Strang 1989, Daubechies 1990, Daubechies 1992, Cohen 1995, Strang & Nguyen 1996, Torrence & Compo 1998, Van den Berg 2004, Mallat 2009, Kaiser 2010, Chui 1992).

### 5.2 Windowed Fourier Transform

### 5.2 Windowed Fourier Transform and Gabor Transform

The most intuitive workaround for the time localization limits of the FT is to split the signal into shorter time segments and compute the Fourier spectrum on each of them. This allows localizing in time the frequency content of the signal, with time and frequency resolution depending on the segment size. Recall that the smallest resolved frequency and the frequency resolution of the spectrum are inversely proportional to the signal’s time duration (in this case, the segment). Similarly, shorter or larger segments enable more or less precise time localization. The delicate compromise between time and frequency resolution is further discussed in this section.

The signal-splitting method outlined earlier is equivalent to pre-multiplying the signal by a top-hat window, equal to 1 in the selected time segment and 0 elsewhere. The window is then shifted along the signal to obtain a time–frequency description. This is the underlying idea of the Gabor transform (Gabor 1946) in which the kernel of the FT is multiplied by a sliding window function. This transform is defined as

$$\mathcal{G}(\tau,\omega) = \int_{-\infty}^{\infty} f(t)\overline{g}(t - \tau) e^{-j\omega t} dt, \qquad (5.2)$$
