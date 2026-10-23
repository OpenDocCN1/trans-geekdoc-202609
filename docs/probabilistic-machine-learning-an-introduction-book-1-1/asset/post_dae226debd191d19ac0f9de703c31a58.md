
![](img/ea9d4e848ba303d6c19c90b8606f3bf6_467_0.png)

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_467_1.png)

*Figure 14.6: Illustration of padding and strides in 2D convolution. (a) We apply “same convolution” to a 5 × 7 input (with zero padding) using a 3 × 3 filter to create a 5 × 7 output. (b) Now we use a stride of 2, so the output has size 3 × 4. Adapted from Figures 14.3–14.4 of [Gér19].*

input. This is called **strided convolution**. This is illustrated in Fig. 14.6b, where we convolve a 5 × 7 image with a 3 × 3 filter with stride 2 to get a 3 × 4 output.

In general, if the input has size \(x_h \times x_w\), we use a kernel of size \(f_h \times f_w\), we use zero padding on each side of size \(p_h\) and \(p_w\), and we use strides of size \(s_h\) and \(s_w\), then the output has the following size [DV16]:

\[
\left\lfloor \frac{x_h + 2p_h - f_h + s_h}{s_h} \right\rfloor \times \left\lfloor \frac{x_w + 2p_w - f_w + s_w}{s_w} \right\rfloor
\tag{14.10}
\]

For example, consider Fig. 14.6(a). We have \(p = 1\), \(f = 3\), \(s = 1\), \(x_h = 5\) and \(x_w = 7\), so the output has size

\[
\left(\left\lfloor \frac{5 + 2 - 3 + 1}{1} \right\rfloor, \left\lfloor \frac{7 + 2 - 3 + 1}{1} \right\rfloor\right) = \left(\left\lfloor \frac{5}{1} \right\rfloor, \left\lfloor \frac{7}{1} \right\rfloor\right) = 5 \times 7
\tag{14.11}
\]

In general, if we use padding which is half the filter size, \(p = \lfloor f/2 \rfloor\) (where \(f\) is odd), then the output will have the same size as the input.

Now consider Fig. 14.6(b), where we set the stride to \(s = 2\). Now the output is smaller than the input.

\[
\left(\left\lfloor \frac{5 + 2 - 3 + 2}{2} \right\rfloor, \left\lfloor \frac{7 + 2 - 3 + 2}{2} \right\rfloor\right) = \left(\left\lfloor \frac{6}{2} \right\rfloor, \left\lfloor \frac{8}{2} \right\rfloor\right) = 3 \times 4
\tag{14.12}
\]

### 14.2.4.1 Multiple input and output channels

In Fig. 14.5, the input was a gray-scale image. In general, the input will have multiple **channels** (e.g., RGB, or hyper-spectral bands for satellite images). We can extend the definition of convolution to this case by defining a kernel for each input channel; thus now \(\mathbf{W}\) is a 3D weight matrix or **tensor**.

We compute the output by convolving channel \(c\) of the input with kernel \(\mathbf{W}_{:,:,c}\), and then summing over channels:

\[
z_{i,j} = b + \sum_{u=0}^{H-1} \sum_{v=0}^{W-1} \sum_{c=0}^{C-1} x_{s i + u, s j + v, c} w_{u, v, c}
\tag{14.13}
\]

where \(s\) is the stride (which we assume is the same for both height and width, for simplicity), and \(b\) is the bias term. This is illustrated in Fig. 14.7.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_468_0.png)

*Figure 14.7: Illustration of 2D convolution applied to an input with 2 channels. Adapted from Figure 6.4.1 of [Zha+19a].*

Each weight matrix can detect a single kind of feature. We typically want to detect multiple kinds of features, as illustrated in Fig. 14.1. We can do this by making \(\mathbf{W}\) into a 4D weight matrix. The filter to detect feature type \(d\) in input channel \(c\) is stored in \(\mathbf{W}_{:,:,c,d}\). We extend the definition of convolution to this case as follows:

\[
z_{i,j,d} = b_d + \sum_{u=0}^{H-1} \sum_{v=0}^{W-1} \sum_{c=0}^{C-1} x_{s i+u, s j+v, c} w_{u,v,c,d}
\tag{14.14}
\]

This is illustrated in Fig. 14.8. Each vertical cylindrical column denotes the set of output features at a given location, \(z_{i,j,1:D}\); this is sometimes called a hypercolumn. Each element is a different weighted combination of the \(C\) features in the receptive field of each of the feature maps in the layer below.²

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_468_1.png)

*Figure 14.8: Illustration of a CNN with 2 convolutional layers. The input has 3 color channels. The feature maps at internal layers have multiple channels. The cylinders correspond to hypercolumns, which are feature vectors at a certain location. Adapted from Figure 14.6 of [Gér19].*

2. In TensorFlow, a filter for 2D CNNs has shape \((H,W,C,D)\), and a minibatch of feature maps has shape (batch-size, image-height, image-width, image-channels); this is called NHWC format. Other systems use different data layouts.

### 14.2.4.2 1 × 1 (pointwise) convolution

Sometimes we just want to take a weighted combination of the features at a given location, rather than across locations. This can be done using 1 × 1 convolution, also called pointwise convolution, as illustrated in Fig. 14.9. This changes the number of channels from \(C\) to \(D\), without changing the spatial dimensionality:

\[
z_{i,j,d} = b_d + \sum_{c=0}^{C-1} x_{i,j,c} w_{0,0,c,d}
\tag{14.15}
\]

This can be thought of as a single layer MLP applied to each feature column in parallel.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_469_0.png)

*Figure 14.9: Illustration of 1 × 1 × 3 × 2 convolution. Adapted from Figure 6.4.2 of [Zha+19a].*

### 14.2.5 Pooling layers

Convolution will preserve information about the location of input features (modulo reduced resolution), a property known as equivariance. In some cases we want to be invariant to the location. For example, when performing image classification, we may just want to know if an object of interest (e.g., a face) is present anywhere in the image.

One simple way to achieve this is called max pooling, which just computes the maximum over its incoming values, as illustrated in Fig. 14.10. An alternative is to use average pooling, which replaces the max by the mean. In either case, the output neuron has the same response no matter where the input pattern occurs within its receptive field. (Note that we apply pooling to each feature channel independently.)

If we average over all the locations in a feature map, the method is called global average pooling. Thus we can convert a \(H \times W \times D\) feature map into a \(1 \times 1 \times D\) dimensional feature map; this can be reshaped to a \(D\)-dimensional vector, which can be passed into a fully connected layer to map it to a \(C\)-dimensional vector before passing into a softmax output. The use of global average pooling means we can apply the classifier to an image of any size, since the final feature map will always be converted to a fixed \(D\)-dimensional vector before being mapped to a distribution over the \(C\) classes.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_470_0.png)

*Figure 14.10: Illustration of maxpooling with a 2 × 2 filter and a stride of 1. Adapted from Figure 6.5.1 of [Zha+19a].*

### 14.2.6 Normalization layers

In Sec. 13.4.5 we discussed batch normalization, which standardizes all the activations within a given feature channel to be zero mean and unit variance. This can significantly help with training. However, although batch normalization works well, it struggles when the batch size is small, since the estimated mean and variance parameters can be unreliable.

One solution is to compute the mean and variance by pooling statistics across other dimensions of the tensor, but not across examples in the batch. More precisely, let \(z_i\) refer to the \(i\)’th element of a tensor; in the case of 2D images, the index \(i\) has 4 components, indicating batch, channel, height and width: \(i=(i_N,i_C,i_H,i_W)\). We compute the mean and standard deviation for each element \(z_i\) as follows:

\[
\mu_i=\frac{1}{|S_i|}\sum_{k\in S_i} z_k, \quad \sigma_i=\sqrt{\frac{1}{|S_i|}\sum_{k\in S_i}(z_k-\mu_i)^2+\epsilon}
\tag{14.16}
\]

where \(S_i\) is the set of elements we average over. We then compute \(\bar{z}_i=(z_i-\mu_i)/\sigma_i\) and \(\tilde{z}_i=\gamma_c\bar{z}_i+\beta_c\), where \(c\) is the channel corresponding to index \(i\).

In batch norm, we pool over batch, height, width, so \(S_i\) is the set of all locations in the tensor that match the channel index of \(i\). To avoid problems with small batches, we can instead pool over channel, height and width, but match on the batch index. This is known as **layer normalization** [BKH16]. Alternatively, we can have separate normalization parameters for each example in the batch and for each channel. This is known as **instance normalization** [UVL16].

A natural generalization of the above methods is known as **group normalization** [WH18], where we pool over all locations whose channel is in the same group as \(i\)’s. This is illustrated in Fig. 14.11. Layer normalization is a special case in which there is a single group, containing all the channels. Instance normalization is a special case in which there are \(C\) groups, one per channel. In [WH18], they show experimentally that it can be better (in terms of training speed, as well as training and test accuracies) to use groups that are larger than individual channels, but smaller than all the channels.

![](img/ea9d4e848ba303d6c19c90b8606f3bf6_470_1.png)

*Figure 14.11: Illustration of different activation normalization methods for a CNN. Each subplot shows a feature map tensor, with \(N\) as the batch axis, \(C\) as the channel axis, and \((H, W)\) as the spatial axes. The pixels in blue are normalized by the same mean and variance, computed by aggregating the values of these pixels. Left to right: batch norm, layer norm, instance norm, and group norm (with 2 groups of 3 channels). From Figure 2 of [WH18]. Used with kind permission of Kaiming He.*

### 14.2.7 Putting it all together

A common design pattern is to create a CNN by alternating convolutional layers with max pooling layers, followed by a final linear classification layer at the end. This is illustrated in Fig. 14.12. (We omit normalization layers in this example, since the model is quite shallow.) This design pattern first appeared in Fukushima’s **neocognitron** [Fuk75], and was inspired by Hubel and Wiesel’s model of simple and complex cells in the human visual cortex [HW62]. In 1998 Yann LeCun used a similar design in his eponymous LeNet model [LeC+98], which used backpropagation and SGD to estimate the parameters. This design pattern continues to be popular in neurally-inspired models of visual object recognition [RP99], as well as various practical applications (see Sec. 14.3 and Sec. 14.4).

## 14.3 Image classification using CNNs

It is common to use CNNs to perform image classification, which is the task of estimating the function \(f:\mathbb{R}^{H\times W\times K}\to\{0,1\}^{C}\), where \(K\) is the number of input channels (e.g., \(K=3\) for RGB images), and \(C\) is the number of class labels. In this section, we discuss various commonly used datasets and models for this task.

### 14.3.1 Common datasets

The ML literature frequently uses various standard labeled image datasets in order to benchmark models and algorithms. We discuss some of these below.
