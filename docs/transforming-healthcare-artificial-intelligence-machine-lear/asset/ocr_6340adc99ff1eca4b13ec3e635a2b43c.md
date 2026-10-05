# Applications of AI & ML in diagnostics and disease treatment 63

minimise the reconstruction error, which is typically measured using Mean

Squared Error (MSE) between X and the reconstructed output $\hat{X}$.

```
$L(X, \hat{X}) = \frac{1}{n} \sum_{i=1}^{n} (X_i - \hat{X}_i)^2 \quad (3.3)$
```

where $n$ is the number of pixels in the image, $X_i$ is the pixel value of the

original input, and $\hat{X}$ is the corresponding pixel value of the reconstructed

# ## 3.4.2 Autism prediction using a convolutional neural network

Autism prediction with a convolutional neural network (CNN) in deep
can be represented mathematically through several key steps,
including convolution operations, activation functions, and loss calcula-

tions are typically applied in the context of predicting autism from
medical data. The input is a 2D image or signal, which we can represent as
a matrix $X \in R^{m \times n}$, where $m \times n$ are the dimensions of the input image.
CNN, a convolution layer applies filters (or kernels) to the input to extract
features. Let $X^{(l)} \in R^{m \times n \times c_l}$ be the input to the $l$-th layer, where $c_l$ is the number of
channels. Each filter $F_k^{(l)} \in R^{f \times f}$ (where $f$ is the filter size) slides over
the input with a stride of $s$, and the convolution is given by:

```
$Y_k^{(l)}(i, j) = \sum_{p=1}^{f} \sum_{q=1}^{f} X^{(l)}(i+ps, j+qs, r) F_k^{(l)}(p, q, r) \quad (3.4)$
```

where $Y_k^{(l)}$ is the output of the $k$-th filter applied to the location $(i, j)$.
After the convolution, ReLU is applied.

```
$A_k^{(l)}((i, j) = ReLU(Y_k^{(l)}(i, j)) = max(0, Y_k^{(l)}(i, j)) \quad (3.5)$
```

Pooling layers reduce the spatial dimensions (downsampling). Max pooling
is commonly used, and it can be represented as:

```
$P^{(l)}(i, j) = max_{p,q} (A^{(l)}(i+p, j+q)) \quad (3.6)$
```

where $i, j$ represents the location in the pooled matrix, and the max opera-
tion taken over a pooling window of size (e.g., $2 \times 2$). The next feature
maps undergoes a series of pooling and convolutional layers before being
transformed into a 1D vector and sent through a series of fully-
nected layers. Let $Z^{(l)} \in R^n$ be the input vector to the fully connected layer,
and then the output is: