
![](img/dd555effd38151c67af30d84800c554a_274_0.png)

## 9.8 Attention

There is a strategy in machine learning called *attention*. In a network layer, a pixel in the output is strongly influenced by some certain pixels in the input image. The network will pay more attention to those input pixels. In image denoising and super-resolution applications, the neighboring pixels have the most influence. The CNN architecture has a built-in attention scheme to focus only the nearby input image pixels covered by the convolution kernel. The uncovered pixels are ignored, as illustrated by Figure 9.38.

For a direct end-to-end reconstruction network, a pixel in the reconstructed image is strongly influenced by the sinogram data along a particular sinewave, as illustrated by Figure 9.39. The reconstruction network should pay more attention to those sinogram pixels along this particular sinewave. The sinewave attention region in the input varies with the output image pixel location.

A general attention architecture is illustrated in Figure 9.40, which looks like the residual network shown in Figure 9.27 excepting that the addition operator $\oplus$ is replaced by an element-by-element multiplication operator $\otimes$. Attention can help the network pay more attention to the high-frequency features. The high-frequency components usually are edges, texture, and other details. The output of the assisting network is called the *attention map* (also known as the *attention mask*). The values in an attention map range from 0 to 1. A value close to 1 in the attention map indicates that

![](img/dd555effd38151c67af30d84800c554a_274_1.png)

![](img/dd555effd38151c67af30d84800c554a_275_0.png)

Fig. 9.39: The attention region marked as a sinewave in the left input sinogram strongly influences the marked pixel in output reconstruction image on the right.

![](img/dd555effd38151c67af30d84800c554a_275_1.png)

Fig. 9.40: Architecture of an attention branch that generates an attention map.

the associated pixel value in the feature map (i.e., the output of the main network) at the same location has more contribution to the main task in mind.

## 9.9 Perspectives

The original theoretical foundation of neural networks is to treat everything as an n-tuple to m-tuple mapping. The universal approximation theory is the backbone to support the field of neural network research. A neural network with sufficient parameters is able to approximate this mapping. Machine learning is to approximate this underlying function (mapping) through a large amount of data.

In practice, however, the universal approximation theory may not be needed. To approximate an n-D function on [0,1]^n using a coarse (sparse) sampling of 10 samples in each dimension, a model may need as many as 10^n parameters. For a small image of size 32 × 32, we need as many as 10^1024 parameters. This number of 10^1024 is astronomical!

The success of neural networks in classification tasks may be credited to the inner product operation. In Section 9.4, we have used the matched filter perspective to explain how a CNN can be used to recognize a pattern (for example, a bicycle). The application of a matched filter is the same as the inner product operation, where one operand is an input image and the other operand is a desired image pattern. The main difference between a fully connected (also known as dense) neural network layer and a CNN layer is that a CNN kernel (i.e., the desired pattern) traverses all over the input image and looks for a match. In a dense layer, nothing moves. We now use the MNIST handwritten digit dataset to illustrate this point. This dataset is as basic and as famous as phrase “Hello, World!” as a test message for a beginner in programming.

For example, the digit “4” can be written in different ways, some examples are illustrated in Figure 9.41. It is difficult to find a universal pattern W such that if the input image X is “4” then the inner product W · X is greater than a threshold b, and if the input image X is not “4” then the inner product W · X is less than the threshold b.

![](img/dd555effd38151c67af30d84800c554a_276_0.png)

Fig. 9.41: Handwritten samples of digit “4”.

![](img/dd555effd38151c67af30d84800c554a_276_1.png)

Fig. 9.42: The first dense layer has multiple patterns for each digit; each subcategory of a digit belongs to one neuron. In the second dense layer, each neuron corresponds to a unique digit that collects all its subcategories in the first layer.

One solution to resolve this difficulty is to have multiple subcategories of the digit “4.” Each subcategory represents similar styles of “4” and uses a pattern $W_i$ and a threshold $b_i$. We can build a dense layer neuron, $\text{ReLU}(W_i \cdot X - b_i)$, for the ith subcategory of “4.” The next dense layer collects all the subcategories of “4” into one neuron; all subcategories of other digits are clumped up in the similar manner, as shown in Figure 9.42.

The toy example of a dense neural network shown in Figure 9.42 tries to classify three handwritten digits: “4,” “5,” and “6.” Each digit is subdivided into four subcategories according to different handwriting styles. The output of each neuron in the first layer is a scalar, calculated by ReLU(⟨Wi · X − bi⟩), where Wi is the pattern for the subcategory and bi is a threshold value. If the input X is a handwritten “4,” some of the pink neurons are activated with positive values.

Each layer is fully connected. An image X or its corresponding pattern image Wi can be represented in the vector format (in any order without any effect on training) so that the inner product ⟨Wi · X⟩ makes sense.

The second layer is, in fact, a dense layer. The links with zero weights are not shown in Figure 9.42. Each neuron in the second layer essentially sums up the output from all its corresponding subcategories from the first layer. This gives the one-hot result in the second layer. Here by one-hot, we imply that the neuron with the maximum output value is referred to as hot with a binary value 1 and other neurons are assigned a binary value 0. Optionally, a “softmax” activation function is used in the second layer. The softmax function normalizes the neuron output values into a probability-like distribution.

The actual MNIST handwritten digit dataset has 60,000 training image/label pairs. It contains handwritten digits from “0” to “9.” If a fully connected neural network (similar to that shown in Figure 9.42) is used for the classification task, the first hidden layer may contain as many as 2,000 neurons and the second contains 10 neurons.

For the end-to-end image reconstruction, the input is a raw measurement-domain sinogram, and the output is a tomographic image. The image reconstruction is a regression (instead of classification) task. The image can be implemented as using a dense layer to perform the backprojection and then using a series of convolutional layers to perform image processing, which includes the ramp filtering. This dense layer can be considered as a “hardwired” backprojection on the pixel-by-pixel base. A backprojector for one image pixel can be readily represented as an inner product between the input sinogram and a sinewave pattern. There is no need for a threshold or for a nonlinear activation function for this dense backprojection layer. In fact, this dense layer is not dense at all. Almost all the weights are zeros except for the sinewave pattern.

For an MRI end-to-end image reconstruction task with a general k-space sampling scheme, the same neural network architecture as above can be used. The dense layer performs the k-space re-gridding and the 2D inverse Fourier transform. An inner product expression can be readily obtained for the re-gridding and inverse Fourier transform. Notice that the k-space measurements are complex with real parts and imaginary parts. Our neural network commonly performs real number calculations. We can simply store a complex number as two real numbers, one for the real part and the other for the imaginary part, in any order, taking advantage of the full connectivity.
