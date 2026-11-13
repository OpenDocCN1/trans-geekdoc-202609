A standard \( 3 \times 3 \) blur filter, which is a linear smoothing filter, gives the average of the nine surrounding pixels:

```
\(\frac{1}{9} \begin{bmatrix} 1 & 1 & 1 \\ 1 & 1 & 1 \\ 1 & 1 & 1 \end{bmatrix} \quad (2.72)\)
```

For reasons of computational simplicity, the coefficients are all one and the normalization factor is multiplied afterwards. An important characteristic of the standard blur filter is the uniformed weighting of all pixels in the kernel. It is sometimes also called a box filter.

The Gaussian blur filter is similar to the box filter but uses a weighted mean, with neighborhood pixels that are closer to the central pixel having a higher weight. The weights drop in the intensity of a Gaussian normal function. Thus, the kernel can be determined by the two-dimensional Gaussian function defined by

```
\(G(x, y) = \frac{1}{2\pi\sigma^2} e^{-\frac{x^2+y^2}{2\sigma^2}}, \quad (2.73)\)
```

with \(x\) and \(y\) being the respective distances to the horizontal and vertical center of the kernel and \(\sigma\) being the standard deviation of the Gaussian kernel. An often used approximation of the correctly calculated Gaussian blur kernel looks as follows:

```
\(\frac{1}{16} \begin{bmatrix} 1 & 2 & 1 \\ 2 & 4 & 2 \\ 1 & 2 & 1 \end{bmatrix} \quad (2.74)\)
```