
## 2D Convolution

To demonstrate a 2D convolution, assume, for illustration purposes, a 6 × 6 gray-scaled input tensor (in practice, the input is usually much bigger) and a 5 × 5 filter, as shown in [Figure 2.4](#12_Chapter02.xhtml#fig2-4). The input is padded with zeros to ensure the output size equals the input size. The upper left value of the 2D output array is the dot product of the 5 × 5 filter with the upper-left 5 × 5 pixels in the zero-padded input tensor (marked in red). Note that in this book and the DL literature, the dots product’s definition includes the aggregated sum of the Hadamard product (element-wise multiplication) of two 2D arrays. The next output value is computed using the next 5 × 5 values in the input tensor (marked in green). This pattern continues across the entire input array to compute all the output values.

![image](images/fig2_3.png)

Figure 2.3: (a) `K` 1D convolutions and (b) `K` 2D convolutions. The results across all filters are concatenated across a new dimension. Thus, the output tensor of the `K` 2D convolutions has a depth (number of channels) of `K`.

![image](images/fig2_4.png)

Figure 2.4: A 2D convolution operation. The top-left value in the output tensor (right) is the dot product of the values in the filter (center) with the upper left values in input tensor (left) in the red square. The input tensor is first zero-padded so the output tensor height and width dimensions equal those of the input tensor. Credit: Joanne Yuan.

![image](images/fig2_5.png)

Figure 2.5: `K` 2D convolutions with an `H` × `W` input with `C` channels. Each filter also has `C` channels. The output tensor has `K` channels, each one corresponding to the convolution output of each filter with the input tensor.

An `H` × `W` color image has 3 channels (red, green, blue), also known as feature channels or tensor depth. The dimension of the image is represented as 3 × `H` × `W`. The filters have the same number of channels as the input, as illustrated in [Figure 2.5](#12_Chapter02.xhtml#fig2-5). Assuming `K` 5 × 5 filters with 3 channels (represented as 3 × 5 × 5), each one of the `K` 2D convolutions is the dot product between a 3 × 5 × 5 filter and all the 3 × 5 × 5 subsets of the input shifted across the height and width. In 2D convolution, the filters do not shift across the depth (channels). Note that filter sizes are often described only by their height and width; the depth is inferred: it is the number of channels of the input tensor.

A convolutional layer has a bank of filters, each detecting different features in the input. To illustrate, suppose the input is a 3 × 224 × 224 tensor, and the layer has a bank of 64 filters. Each filter produces one 224 × 224 output. Each output contains the features detected in the input by the corresponding filter. The aggregated layer output is a 64 × 224 × 224 tensor, and all the filters in the next convolutional layer have 64 channels.

In practice, a convolution layer typically uses 4D input, filter, and output tensors. The usual way tensors are arranged in (1D) memory, known as the *data layout*, is as `NCHW` or `NHWC` for the input tensors, where `N` is the number of samples in the batch, `C` is the input depth (or equivalently, the number of channels or features), `W` is the input width, and `H` is the input height. The filters are arranged as `RSCK` or `KCRS`, where `K` is the number of filters (also known as the number of output feature channels), `R` is the filter height, and `S` is the filter width. The `C` in `NCWH` and `KCRS` are the same. Note that `KCRS` is sometimes denoted as `OIHW` in some literature but not in this book to avoid confusion with the `H` and `W` used for the input tensor. In the example above, the input has `NCHW` dimensions 1 × 3 × 224 × 224, the filter has `KCRS` dimensions 64 × 3 × 5 × 5, and the output has ![image](images/nh.png)dimensions 1 × 64 × 224 × 224.

The convolution is computed along seven dimensions: batch size `N`, output channels `K`, input channels `C`, output height ![image](images/h.png), output width ![image](images/w.png), filter height `R`, and filter width `S`. It can be implemented naively as seven `for loops`, as shown in Algorithm 2.1, where `k`, ![image](images/sh.png), and ![image](images/wo.png), represent the channel, height, and width indices of the output tensor `Z`. For simplicity, the stride is assumed to be 1. There are more efficient implementations that account for a device’s memory hierarchy and parallel computing capabilities \[DAM+16\].

![image](images/pg33_1.png)

A convolutional filter can be implemented as a `GEMM` by duplicating some of the input values, as shown in [Figure 2.6](#12_Chapter02.xhtml#fig2-6), and converting the filter into a vector. This is called an `im2col-`based convolution implementation. This implementation enables the use of a `GEMM` library (which is typically well optimized). However, it comes at the expense of additional memory requirements for the input tensor and extra compute cycles to transform the input. Conversely, an affine layer can be represented as a convolution layer where `C` is the number of input activations, `K` is the number of output activations, `H` = `W` = 1, and `R` = `S` = 1 using the `NCHW` and `KCRS` data layout representations.

In addition, a convolution operation can be implemented in the Winograd domain and also in Fourier domain using the Fast Fourier transform (`FFT`) algorithm \[HR15, LG16\]. `oneDNN` and `cuDNN` support Winograd convolutions, which may be beneficial for 3 × 3 convolutions (the maximum theoretical gain is 2.25x over regular convolutions). However, using the Winograd transform may reduce the numeric accuracy of the computations, which can impact the overall accuracy of the model \[LG16\]. Sparsifying the Winograd domain (increasing the number of zero values in the Winograd domain) can lead to higher gains, but also higher accuracy loss \[LPH+18\]. Winograd requires additional memory and consumes more bandwidth; thus, when sufficient compute is available, the conversion overhead may result in overall slower performance. The `FFT` primarily benefits large filter sizes, which are uncommon in DL. Therefore, Winograd- and FFT-based convolutions are rarely used in production.

![image](images/fig2_6.png)

Figure 2.6: A convolution operation can be implemented as a matrix multiplication. In this simple illustration, the input is not zero-padded so the output dimensions are smaller than the input dimensions.

[Section 3.2](#13_Chapter03.xhtml#sub3-2) introduces other variants of convolution, including the 1 × 1 convolution, group convolution, and depthwise separable convolutions, when discussing influential computer vision topologies.

## 2.4 Pooling

Pooling or subsampling reduces the size of the input tensor across the height and width, typically without affecting the number of channels. Pooling often follows a convolutional layer. The common implementation, known as `max pooling`, is to select the maximum value in a small region. A 2D pooling layer uses 2 × 2 nonoverlapping regions and reduces the tensor size by a factor of 4, as illustrated in [Figure 2.7](#12_Chapter02.xhtml#fig2-7).

The main benefit of pooling is that filters after a pooling layer have a larger receptive field or coverage on the original input image. For example, a 3 × 3 filter maps to a 6 × 6 portion of the input image after one 2 × 2 pooling layer. A 3 × 3 filter deeper in the model, after five convolutional and pooling layers, maps to a 96 × 96 (note that 3 × 2⁵ = 96) portion of the input image and can learn more complex features. Another benefit of pooling is that it reduces the number of operations.
