Reconstruction of Thermophysical Parameters Based on Deep Learning 127

# 4.4.1 Conventional Denoising Approach

Nowadays, a large number of algorithms have been developed to remove noise, including singular value decomposition, wavelet transform, and so on. Taking the singular value decomposition as an example, it first decomposes the $m \times n$ noisy image matrix into the product form of three matrices:

```
$Y = U \begin{pmatrix} \Sigma & O \ O & O \end{pmatrix} V^H$
```

where $U$ and $V$ are orthogonal matrices, and $\Sigma$ is a diagonal matrix whose diagonal elements are $r$ singular values, the smaller value may be caused by noise, so it will be ignored in signal reconstruction. In general, the algorithm needs to traverse the maximum 1 to $r-1$ singular values, while the rest of the singular values are set to zero to obtain the best reconstruction result. In fact, the entire process requires multiple matrix decomposition and matrix product operations, so it requires high computing resources and is not suitable for real-time scenarios.

# 4.4.2 Deep Denoising Framework

In recent years, with the vigorous development of deep learning technology, denoising algorithms based on convolutional networks are becoming in the ascendant. As researchers use convolution-based networks to achieve the function of denoising, because it can fully extract the information of each point in space. One of the famous examples is the U-net, which was introduced to the realm of medical image processing [29] and has extensively flourished in all the cases where the input and output images are highly relevant [30, 31, 32, 33, 36]. One of the most common application for the U-net is image denoising [35, 36], where it undertakes the role of a filter.

The proposed method in this paper is a U-net, as presented in Fig.4.10, which is mainly composed of a contracting path and an expansion path. The contracting path has three sub blocks, each of which consists of two convolutional layers, an activation layer and max-pooling layer. The down-sampling strategy efficiently extracts feature from the lower layers and filters the Gaussian noise. As for the expansion path, there are also three blocks, where the pooling layers are replaced by upsampling layers. This structure realizes the reconstruction of the detailed information of the temperature. To match the input and output size, the transient temperature data is reshaped to a 2D matrix, indicating the number of probes and time-domain steps.

Considering that denoising needs to make full use of pixel level features, Long Bao et al. used the residual dense block structure. The multi-scale structure can obtain a larger receptive field, which is another way of denoising. For example, the classical U-net method performs down sampling for many