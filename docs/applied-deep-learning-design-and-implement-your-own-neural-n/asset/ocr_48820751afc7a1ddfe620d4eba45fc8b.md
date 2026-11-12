The advantage of convolution over correlation is that convolution has the associative property while correlation does not have this property. By the associative property, the convolution allows to convolve of multiple filters into a single filter and further convolving that filter to an image.

Suppose we have an image $I$ and a filter $F$. Then, the mathematical representation of the convolution for 1-D is given as follows:

$F * I(x) = \sum_{i=-N}^{N} F(i)I(x - i)$ (4.4)

Figure 4.11 shows an example of a 1-D convolution.

![](bbox=[0.19, 0.31, 0.83, 0.63])

Figure 4.11: Convolution in 1-dimension.

In the case of 2-D convolution, the kernel is flipped both vertically and horizontally. The mathematical representation of 2-D is as follows:

$F * I(x, y) = \sum_{j=-N}^{N} \sum_{i=-N}^{N} F(i, j)I(x - i, y - j)$ (4.5)

Example 4.2: Let us take an input image $I$ of $5 * 5$ as follows:

```
[[1 1 1 0 0]
 [0 1 1 1 0]
 [0 0 1 1 1]
 [0 0 1 1 0]
 [0 1 1 0 0]]
```