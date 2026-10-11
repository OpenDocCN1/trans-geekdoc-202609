
## 6.5 Typical convolutional neural network structure

In 1989, Yann LeCun, the inventor of the convolutional neural network structure (CNN), used the backpropagation (BP) algorithm to train a multi-layer neural network to recognize handwritten postal codes. The neural network used was later called LeNet in 1994. The convolutional neural network, although the paper does not mention convolution or convolutional neural network, it only says that the adjacent area of 5×5 is used as the receptive field. In 1998, LeCun proposed the famous LeNet5 neural network, marking the real birth of convolutional neural network. Due to the limitation of hardware conditions at that time, the training of convolutional neural network consumed machine resources and time very much. Therefore, the CNN network model did not become popular.

It was not until 2012 that Alex Krizhevsky implemented a deep convolutional neural network called AlexNet with a GPU and won the championship of the ImageNet image recognition competition that deep learning represented by deep convolutional neural networks began to develop rapidly. Subsequently, various neural network structures were proposed, such as VGG, GoogLeNet, ResNet, Inception, etc.

### 6.5.1 LeNet-5

Figure 6-55 shows the network structure of LeNet-5. A 32×32×1 image passes through six 5×5 convolution kernels with a stride of 1 and a padding of 0 to generate 6 outputs of 28×28 size. The feature map, and then through the average pooling operation with a span of 2 and a size of 2, six 14×14 feature maps are generated, that is, the length and width of the image are reduced by half. Then through 16 5×5 convolution kernels with a span of 1 and a filling of 0, 16 output feature maps of 10×10 size are generated. Then through the average pooling operation with a span of 2 and a size of 2, 16 feature maps of 5×5 are generated.

![](EPUB/media/file138.png "fig:")  
Figure 6-55 LeNet network structure

Then there is the fully connected layer, which has 120 neurons, and each neuron receives a total of 400 feature values from the previous layer's 16 5×5 feature maps (images), and each neuron produces an output value, 120 neurons generate a one-dimensional vector consisting of 120 outputs, which are output to the next fully connected layer with 84 neurons. A fully connected layer of 84 neurons feeds their 84 outputs into the final output layer, and if 10 classes are performed, the output layer will contain 10 neurons, and each neuron outputs a score for a sample belonging to the corresponding class. These 10 classifications can be used to train the neural network model by calculating the multi-class cross entropy loss through the softmax function and the true target value.

LeNet-5 is a classic structure of convolutional neural network. It adopts the mode of "first convolution and then pooling" to generate multi-channel output from multi-channel input and reduce the size of the image. As in the above example, the single channel 32×32×1 is passed A series of "convolution pooling" transformations finally produced 16 5×5 feature maps, which were finally passed through some fully connected layers to produce the final output.

### 6.5.2 AlexNet

AlexNet is a CNN network structure proposed by Alex Krizhevsky et al. It won the first place in the ImageNet image classification competition in 2012, and instantly increased the top-5 error rate by more than 10 percentage points. The author implements a parallel neural network training algorithm with CUDA GPU, which makes it possible to train deep neural networks in a reasonable time. Its network structure is shown in Figure 6-56.

![](EPUB/media/file139.png "fig:")  
Figure 6-56 AlexNet network structure

If the input is a 3-channel color image 227×227×3, after 96 11×11 convolution kernels with a span of 4, 96 feature maps of 55×55 (55×55×96) are generated, because With a stride of 4, the image is scaled down by a factor of 4. Then after a 3×3 maximum pooling layer with a span of 2, 96 27×27 feature maps (27×27×96) are output, and then 256 5×5 convolution kernels with a span of 1 and a padding of 2 Execute "same convolution" to generate 256 feature maps of 27×27 (27×27×256), and then pass through the 3×3 maximum pooling layer with a span of 2, and output 256 feature maps of 13×13 13× 13×256, and then use 384 3×3 convolution kernels with a span of 1 and a filling of 1 to perform "same convolution" to generate 384 feature maps of 13×13 (13×13×384), and then do it again The same convolution operation. Then, "same convolution" was performed with 256 3×3 convolution kernels with a stride of 1 and a padding of 1 to generate 256 feature maps of 13×13 (13×13×256). Perform another 3×3 maximum pooling with a span of 2, resulting in 256 feature maps of size 6×6 (6×6×256). Expand 6×6×256 into a 9216 vector, then output to a fully connected layer of 4096 neurons, followed by a fully connected layer of 4096 neurons, and finally a fully connected layer of 1000 neurons, and After the softmax function outputs the probability that the sample belongs to 1000 different categories.

AlexNet is very similar to LeNet, but its depth and scale are much larger than LeNet. LeNet has about 60,000 parameters, while AlexNet has about 60 million parameters. The most important improvement of AlexNet over the LeNet network is the use of the Relu activation function, which avoids the "gradient disappearance" problem of the deep neural network. Another improvement to improve performance is the Dropout technology, that is, in a hidden layer with a certain probability, the output of some neurons is 0, and does not participate in network propagation. In each iteration, it is equivalent to defining a different function. This regularization technique actually uses a combination of simpler network functions to represent the trained model function. In addition, the "Local Response Normalization" (Local Response Normalization) is proposed, which is to normalize the values of all channels at a certain position of the feature map in a certain layer. But later it was found that LRU has little effect.

The success of the AlexNet network has refocused the computer vision and artificial intelligence communities on neural networks that have been dormant for many years, especially CNN deep convolutional networks. The depth can become deeper, and the deep neural network with simple principles can surpass the mathematically complex artificial intelligence technology. Deep learning has begun to become the most important branch of machine learning. Modern artificial intelligence mainly refers to deep learning.

### 6.5.3 VGG

The VGG-16 network is a simplified convolutional network structure proposed by Oxford's Visual Geometry Group (VGG for short). Its main contribution is to prove that increasing the depth of the network can improve the final performance of the network to a certain extent. The size of the convolution kernel of different convolution layers of the general convolutional network is different, and the size of all convolution kernels in the VGG network is the same, for example, a convolution kernel with 3×3 span of 1 is used , the same is true for the pooling layer, using a 2×2 maximum pooling kernel with a span of 2. Therefore, it simplifies the structure of the convolutional neural network. As long as the depth of the VGG-16 network is deep enough, it can achieve the same or even better performance than the complex neural network structure. The 16 of VGG-16 means that the convolutional layer and the fully connected layer in the neural network have a total of 16 layers. Figure 6-57 is a convolutional network structure of VGG-16

![](EPUB/media/file140.png "fig:")  
Figure 6-57 VGG network structure

The convolution kernels are all 3×3 with a span of 1, and the pooling kernels are all 2×2 with a span of 2. However, the number of output channels of the initial convolutional layer is 64, and the number of output channels of the subsequent convolutional layers is doubled in order of 128, 256, and 512. When it reaches 512, the number of output channels of the subsequent convolutional layer will no longer increase. Yes, as the number of 512 channels is considered to be large enough. The VGG network structure is very regular, but the amount of data required will be large. Later, VGG-19 was proposed, but there is no difference in performance between VGG-19 and VGG-16.

### 6.5.4 Gradient Explosion and Vanishing Problems of Deep Neural Networks

Very deep neural networks are difficult to train due to the problem of gradient explosion and disappearance, because the gradient can only be passed layer by layer from back to front, and if a number is continuously multiplied by a number whose absolute value is less than 1, this number will getting closer to 0. Let a number be `y`, multiplied by `c[i]` continuously, and finally become `c[i] * ... * c[L] * y`, this value will tend to 0. Similarly, when a number is multiplied by a number whose absolute value is greater than 1, this number will get closer and closer to infinity ∞.

Consider a simplified neural network, in which the neurons are `z = x * w`, if there is an L layer, the forward calculation is:

```
x → z[1] = x * w[1] → z[2] = z[1] * w[2] = x * w[1] * w[2] → ⋯ → z[L] = z[L−1] * w[L] = x * w[1] * w[2] ⋯ * w[L]
```

If you know that the gradient of the last `z[L]` of the loss function is `dz[L]`, then the gradient of the loss function about `z[L−1]` `dz[L−1] = w[L] * dz[L]`, about `z[i]` The gradient of `dz[i] = w[i+1] ⋯ w[L] * dz[L]`, the gradient of the loss function on `w[i]` `dw[i] = dz[i] * z[i−1] = w[i+1] ⋯ w[L] * dz[L] * z[i−1]`.

If `‖w[i]‖ < ρ < 1`, then `dz[i]` decays exponentially as `L−i` increases, and the larger `L−i`, the faster the decay, so that the value of `dw[i]` It may become very small, and the gradient is too small, making the update of the parameter `w[i]` almost stagnant, and the convergence becomes very slow. Similarly, if `‖w[i]‖ > ρ > 1`, then `dz[i]` increases exponentially with the increase of `L−i`, and thus becomes very large, making the parameter update sharply larger and oscillating , so it cannot converge.

As the depth of the neural network becomes deeper, the gradient explosion and attenuation of the neural network are inevitable, which makes the training of the deep neural network very difficult. In order to prevent gradient explosion, the technique L of gradient clipping can be used, that is, the absolute value of the gradient is limited to a predetermined range. Let `g` be the gradient, `θ` be the clipping threshold, and clip the gradient according to the following formula:

`min(θ / ‖g‖, 1) * g`

That is, the gradient value is limited to `[-θ, θ]`.

If `grads` contains gradients of multiple weight parameters, the following code can limit their gradients to `[-c, c]`:

```
```
