As shown in Figure 1, the feature extraction of Mel-spectrogram needs the following processes. (1) Pre-emphasis and frame-based windowing technology. The sampling frequency of voice signal is 16,000 Hz, the number of sampling points in each voice frame is N = 512, the pre-emphasis coefficient is 0.97, and the frame step is 200. (2) Fast Fourier transform. Each frame of speech signal divided by step (1) is very short, so it is considered that the frequency is in a stable state within a frame of time. The fast Fourier transform of each frame of speech signal $y_{i}(t)$ is calculated according to Equation (1) to obtain its spectrum. The multi-frame spectrum is spliced on the time dimension to form spectrogram.

$$F_{i}(k)=\sum_{n=0}^{N-1}y_{i}^{'}(n)e^{-\frac{2\pi}{N}in}\hspace{8em}(1)$$

The power spectrum of speech signal $P$ is calculated by Equation (2).

$$P=\frac{|F_{i}(k)|^{2}}{N}\hspace{8em}(2)$$

In which, $F_{i}(k)$ is the Fourier transform output of the $i$ th frame of speech signal $y_{i}^{'}(n)$. (3) Mel-filter bank. Mel-filter bank is used to convert frequency into Mel-frequency to simulate human perception. By passing the energy spectrum through multiple groups of Mel-filters bank, Mel-filters bank can approximate the human auditory system and have a certain choice of frequency, which can directly ignore the frequency signal that you do not want to perceive. The structure of Mel-filter is shown in Figure 2. Mel-spectrogram can be obtained from the spectrogram after passing through Mel-filter bank.

In this paper, the number of Mel-filter banks $M = 40$ is selected, and the response at the center frequency is 1, which gradually decreases to 0 at both ends, until the center frequency of two adjacent filters is reached, where the response is 0, and the interval between them increases with the increase of $M$ value. Mel-filter banks can be constructed from Equation (3). The energy spectrum $P$ of step (2) is passed through the Mel-filter bank $H_{m}(k)$ to obtain the Mel-spectrogram, which is shown in Figure 3.

$$H_{m}(k)=\left\{\begin{array}{cc} {0} & {k<f(m-1)} \\ {\frac{k-f(m-1)}{f(m)-f(m-1)}} & {f(m-1)\leq k<f(m)} \\ {1} & {k=f(m)} \\ {\frac{f(m+1)-k}{f(m+1)-f(m)}} & {f(m)<k\leq f(m+1)} \\ {0} & {k>f(m+1)}\end{array}\right.\hspace{4em}(3)$$

![](bbox=[0.19, 0.68, 0.76, 0.89])