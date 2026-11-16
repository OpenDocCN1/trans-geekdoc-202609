$g_{\theta_i}^i$ is a simple function with parameters $\theta_i$. Then the parameters of f is simply the combined parameters of all the layers $\theta = (\theta_i, ..., \theta_l)$. Common functions used in deep learning include

+   1) Matrix multiplication g(x) = Ax + b where the parameters are matrix A and vector b.

+   2) Rectified Linearity (ReLU) [22]
+   
+   g(x) = \begin{cases} x & x > 0 \\ o & x < 0 \end{cases}

This function does not contain a parameter.

+   3) Softmax function: the softmax function “squashes” a n-dimensional vector of arbitrary real values to a n-dimensional vector of real values in the range [0, 1] that add up to 1. The function applied to an n-dimensional input vector z is given by
+   
+   Sigmoid($z_j$) = $\frac{e^{z_j}}{\sum_{k=1}^n e^{z_k}}$

Note that sigmoid naturally produces a distribution because the output sum to 1

$\sum_j \text{Sigmoid}(z_j) = 1$

+   4) Convolution [23] [24] [25] [26]: the convolution function takes as input an array z of size M x N x K and output an array o of size M x N x C. The first two dimensions can be interpreted as width and height, while the third is the number of “channels”. This function takes as input z, and applies a 2D-convolution operation defined as
+   
+   $o_{x,y,c} = \sum_{i=0}^S \sum_{j=0}^S w_{i,j,k}^c * z_{x+i, y+j, k}, \forall 1 \le x, y, c \le M, N, C$

where S is called the size of the filter map, and each $w^c$ is an array of size S x S x K. All the $w^c$ combined $\{w^c, c=1, \cdots, C\}$ is the set of parameters of the convolution function.

+   5) Pooling: Pooling is a process which reduces a M x N x K array into a smaller array, e.g. of size $M/2 \times N/2 \times C$. Usually we keep the number of “channels” unchanged. For example, in the digit classification task, it can reduce the scale of a clearer picture into a more ambiguous one, making it easier to process in the later steps.