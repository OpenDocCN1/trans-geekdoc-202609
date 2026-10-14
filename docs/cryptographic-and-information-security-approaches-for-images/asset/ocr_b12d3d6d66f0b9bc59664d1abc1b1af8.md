introduced as two criterions to measure the effect of space scrambling and statistic distribution Using correlation analysis and uniform analysis.

# 3.5.3.1 Correlation Analysis

To test the correlation of the plain and encryption, pairs of pixels horizontally adjacent (HA) $(x, x+1)$, vertically adjacent (VA) $(y, y+1)$, and diagonally adjacent (DA) $(x+1, y+1)$ with their correlation coefficients $R(x, x+1), R(y, y+1), R(x+1, y+1)$ are calculated respectively. The pairs are chosen randomly. The correlation coefficients of each pair are calculated by using the following formulas:

$R(x, y) = \frac{\operatorname{cov}(x, y)}{\sqrt{D(x)}\sqrt{D(y)}}$ (3.18)

where

$E(x) = \frac{1}{N} \sum_{i=1}^{N} x_i$ (3.19)

$D(x) = \frac{1}{N} \sum_{i=1}^{N} (x_i - E(x))^2$ (3.20)

$\operatorname{cov}(x, y) = \frac{1}{N} \sum_{i=1}^{N} (x_i - E(x))(y_i - E(y))$ (3.21)

x and y are grey values of two adjacent pixels in the image. We choose correlation coefficient $R(x, y)$ as criteria to measure the disorder mixture of space domain distribution. The correlation coefficient is the inverse proportion to mixture of the image.

# 3.5.3.2 Uniform Analysis

In order to assess statistic uniformness of the results, we introduce the criteria volatility to calculate the stationary with the histogram; thus, assessing how fairly uniform the ciphered results are so as to know how much the result approximates the white noise, in which the real information can hide inside. The criteria volatility is defined as:

$V(h) = \operatorname{cov}(h) - E(h)$ (3.22)

where $h$ is the series vector of histogram value.