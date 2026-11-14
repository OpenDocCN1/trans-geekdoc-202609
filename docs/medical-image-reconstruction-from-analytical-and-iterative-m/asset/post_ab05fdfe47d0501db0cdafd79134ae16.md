
An almost equivalent larger template can be achieved by using multiple convolutional layers with smaller templates. A larger template can capture a more complicated image pattern. In a CNN, we do not treat the 2D image input as a vector (or an n-tuple) because the 2D cross-correlation operation is sensitive to neighboring image pixels. The CNN pays attention to a pixel and its nearby pixels. On the other hand, a fully connected layer treats every input as a vector (i.e., an n-tuple).

A CNN layer has multiple channels. Each channel is associated with its own convolution kernel and produces its own feature map. We now consider a CNN with three convolution layers. The first CNN layer has three channels; this layer will produce three images each corresponding to its own convolution kernel. The second CNN layer has two channels; this second layer will generate two images, associated with two convolution kernels. The third CNN layer has one channel; this third layer will produce one output image, as illustrated in Figure 9.32. On the other hand, a fully connected layer only produces one image as the output.

![](img/dd555effd38151c67af30d84800c554a_269_0.png)

Fig. 9.32: A CNN with three convolutional layers. The first convolutional layer has three channels, the second convolution layer has two channels, and the third convolution layer has one channel.

In Figure 9.32, x1, u1, u2, u3, v1, v2, and y1 are 2D images; \( w_{ij}^{(k)} \) are 2D convolution kernels for the kth convolution layer associated with the ith input image and the jth output image; \( b_j^{(k)} \) are bias scalars for the kth convolution layer associated with the jth output image; \( \sigma \) is a nonlinear element-by-element activation function, e.g., the ReLU function; ** denotes the 2D cross-correlation operator (also known as convolution operator in machine learning community). By comparing Figure 9.32 with Figure 9.8, we can see the clear differences between a CNN and a dense network. In a dense network, a neuron is a scalar output, calculated as

\(\sigma \left( \sum_{i=1}^n X_i W_i + b \right),\)
(9.26)

where \(x_i\) is the \(i\)th scalar element of the input \(n\)-tuple, \(w_i\) is the \(i\)th scalar element of the \(n\)-tuple weights, and \(b\) is the bias scalar. Here, \(n\) is the number of neurons in the previous layer. In a CNN network, a generalized neuron is an image output, calculated as

\(\sigma \left( \sum_{i=1}^n X_i ** W_i + b \right),\)
(9.27)

where \(x_i\) is the \(i\)th image of the input images, \(w_i\) is the \(i\)th 2D convolution kernel of the \(n\) kernels in this layer, and \(b\) is the bias scalar. Here, \(n\) is the number of channels. In a CNN, a common optional trick is to change the image size from one layer to the next layer.

The universal approximation theory discussed in Section 9.2.2 only applies to dense networks; it does not apply to CNNs. Why do we believe that a CNN can give us better results than some conventional methods, for example, in denoising? At least, we know that the machine learned denoising filter should outperform the conventional filters. This is simply because the conventional filters are convolution-based and are the special cases of the machine learning models. A conventional filter can be considered as a one-layer, one-channel filter without a nonlinear activation function.

Let us look at a simple two-layer denoising CNN in action. The input of the network is a sinogram. The first convolution layer has two channels, and the second convolution layer is the output layer that has only one channel. Each convolution kernel is 3 * 3 and the activation function is the ReLU. The outputs of the channels are shown in Figure 9.33. The first layer produces two filtered sinogram images. One image contains many bright dots and looks like a result from a high-pass filter, and the other image looks like a result from a low-pass filter. The second layer further filters the two images from the first layer and combines them in a nonlinear way to produce the final denoised result. The dot-like pattern is removed by the ReLU function. On the other hand, the conventional filter is linear. A linear combination of two linear filters is a third linear filter, which is not equivalent to a nonlinear filter. Nonlinear filters have better performance than linear filters in noise reduction while keeping the sharp edges.

A machine learned filter may or may not be shift-invariant. A shift-invariant filter applies the same action in every region in the input image, regardless the location of the region. The convolution (or cross correlation) action is shift-invariant. The max pooling action makes the filter shift-variant. If you want a shift-invariant denoising filter, you need to choose a shift-invariant action to change the image dimension, for example, average pooling.

![](img/dd555effd38151c67af30d84800c554a_271_0.png)

![](img/dd555effd38151c67af30d84800c554a_271_1.png)

![](img/dd555effd38151c67af30d84800c554a_271_2.png)

Fig. 9.33: Channel outputs. Top: From channel 1 of the first layer. Middle: From channel 2 of the first layer. Bottom: From the second layer.

## 9.6 Super-resolution

In medical imaging, sometimes the measurements are undersampled. To estimate the unmeasured measurements is closely related to super-resolution image estimation. We always have doubts whether it is even possible to obtain a high-resolution image from a low-resolution image. We believe that image processing is unable to create unmeasured information. Successful evidence suggests that under some circumstances super-resolution is possible. Super-resolution images may be visually appealing, but they may not be identical to the true original high-resolution images.

The traditional linear space expansion theory may not be able to explain the machine learning models due to the nonlinearities in the models. The traditional approach is to engineer a procedure to enhance the high frequency components so that the blurred low-resolution image becomes a sharp high-resolution image. This traditional approach does not work well because noise and Gibbs oscillation artifacts will be amplified.

One explanation suggests that the neural network somehow remembers the sharp edges of the training labels and find the closest sharp edges for the new input low-resolution images. This explanation may not be what actually happens in reality.

Another hypothetical explanation of the magic of achieving super-resolution is through image mapping. A mapping is essentially a table lookup approach as illustrated in Figure 9.34. The blurred curve on the left of Figure 9.34 is the input n-tuple of the machine learning model. The sharp curve on the right of Figure 9.34 is the output n-tuple of the model. After enough training pairs are used to train the model parameters, the model is expected to output a sharp curve for an unseen blurred curve input. How satisfactory of the output will depend on how similar the unseen input is to the training inputs.

Still another explanation is that the neural networks are nonlinear combinations of edge detection filters. As a result, the high-frequency edges are enhanced. To reduce the pixelization effects in the low-resolution images, a depth-to-space transform by shifting the images from different channel outputs to form a higher-resolution image is illustrated in Figure 9.35, where the phrase “feature extraction” is another way to say “filtration.” The filtered images are sometimes referred to as feature maps. In Figure 9.35, the input is a 4 × 4 low-resolution image, and the output of the convolutional layers consists of four channels with a 4 × 4 at each channel. The depth-to-space transformation merges these four channels into one 8 × 8 high-resolution image.

![](img/dd555effd38151c67af30d84800c554a_272_0.png)

![](img/dd555effd38151c67af30d84800c554a_272_1.png)

## 9.7 Training

Model training is similar to iterative image reconstruction in the sense that it is an optimization procedure. The objective function (also known as the cost function or loss function) in model training is the distance between the model output and the label. In machine learning terminology, a label is a desired output. In denoising, a label is a noiseless image, and an input is a noisy image. In super-resolution, a label is a high-resolution image, and an input is a low-resolution image. In direct (end-to-end) image reconstruction, a label is a true image, and an input is a sinogram. A general training setup is shown in Figure 9.36. Training is to find the model parameters W by minimizing the objective function with a lot of input/label pairs. Training is an iterative procedure that goes through all input/label pairs multiple times. Each iteration is called an epoch in machine learning community. After training, the trained model is ready to accept any unseen input and to produce an output in a fast and one-pass way without any iterations.

![](img/dd555effd38151c67af30d84800c554a_273_0.png)

Fig. 9.36: A general setup for parameter training.

In machine learning, the training algorithms are mostly gradient descent-based. The gradient of the objective function with respect to the parameters is evaluated according to the chain rule, which is referred to as backpropagation in machine learning. As a toy example, let us consider a neural network shown in Figure 9.37 and find the gradient \(\partial J / \partial w_1\), where \(J\) is the objective function

```
J = \frac{1}{2} \sum_{i=1}^N (y_i - \hat{y}_i)^2, \quad (9.28)
```

where \(\{x_i, \hat{y}_i\}\) is an input/label pair, there are \(N\) input/label pairs, and \(y_i\) is the model output. The gradient \(\partial J / \partial w_1\) is calculated using the chain rule as follows:

```
\frac{\partial J}{\partial w_1} = \sum_{i=1}^N (y_i - \hat{y}_i) \frac{\partial y_i}{\partial \sigma} \left( \frac{\partial v_1}{\partial \sigma} x_i w_3 + \frac{\partial v_2}{\partial \sigma} (0) w_4 \right) \\ = \sum_{i=1}^N (y_i - \hat{y}_i) u(y_i) u(v_1) x_i w_3, \quad (9.29)
```

where \(u(\cdot)\) is the unit step function defined in eq. (9.5). Once the gradient of the objective function with respect to each parameter is known, a gradient-based iterative algorithm is ready to be implemented for training the network.
