![](bbox=[0.13, 0.13, 0.31, 0.27])

(a) Scrambled by circular row and column shifting

![](bbox=[0.36, 0.13, 0.54, 0.27])

(b) scrambled using 2D mapping

![](bbox=[0.63, 0.13, 0.81, 0.27])

(c) scrambled using bit label permutation

![](bbox=[0.13, 0.32, 0.31, 0.5])

(d) scrambled using Arnold transformation

![](bbox=[0.36, 0.32, 0.54, 0.5])

(e) scrambled using Fibonacci transformation

![](bbox=[0.63, 0.32, 0.81, 0.5])

(f) scrambled using Gray code

Figure 2.16 The Lena image scrambled using different techniques.

The Lena image in Figure 2.13c is scrambled using circular row and column shifting in Figure 2.16a, scrambled using 2D mappiing in Figure 2.16b, scrambled using bit label permutation in Figure 2.16c, scrambled using Arnold transformation in Figure 2.16d, scrambled using Fibonacci transformation in Figure 2.16f. scrambled using gray code in Figure 2.16a.

# 2.3.1 Entropy Analysis

The information entropy is defined as the degree of uncertainties in the system. The greater the entropy, the more is the randomness in the image, or the image is more uniform [25]. Thus statistical attacks become difficult. Entropy is defined in Equation 2.11 [26].

$H(m)=\sum_{i=0}^{2^{N}-1}p(m_i)\times\log_2\left[\frac{1}{p(m_i)}\right]$ (2.11)

where $p(m_i)$ are the histogram counts returned from the histogram. For an ideal random image, the entropy is calculated to be 8.