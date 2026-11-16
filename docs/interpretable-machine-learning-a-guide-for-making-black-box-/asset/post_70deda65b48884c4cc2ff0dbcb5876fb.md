
## 7.2.3 Grad-CAM

Grad-CAM provides visual explanations for CNN decisions. Unlike other methods, the gradient is not backpropagated all the way back to the image, but (usually) to the last convolutional layer to produce a coarse localization map that highlights important regions of the image.

Grad-CAM stands for Gradient-weighted Class Activation Map. And, as the name suggests, it is based on the gradient of the neural networks. Grad-CAM, like other techniques, assigns each neuron a relevance score for the decision of interest. This decision of interest can be the class prediction (which we find in the output layer), but can theoretically be any other layer in the neural network. Grad-CAM backpropagates this information to the last convolutional layer. Grad-CAM can be used with different CNNs: with fully-connected layers, for structured output such as captioning and in multi-task outputs, and for reinforcement learning.

Let us start with an intuitive consideration of Grad-CAM. The goal of Grad-CAM is to understand at which parts of an image a convolutional layer "looks" for a certain classification. As a reminder, the first convolutional layer of a CNN takes as input the images and outputs feature maps that encode learned features (see the chapter on Learned Features). The higher-level convolutional layers do the same, but take as input the feature maps of the previous convolutional layers. To understand how the CNN makes decisions, Grad-CAM analyzes which regions are activated in the feature maps of the last convolutional layers. There are k feature maps in the last convolutional layer, and I will call them A_1, A_2, ..., A_k. How can we "see" from the feature maps how the convolutional neural network has made a certain classification? In the first approach, we could simply visualize the raw values of each feature map, average over the feature maps and overlay this over our image. This would not be helpful since the feature maps encode information for **all classes**, but we are interested in a particular class. Grad-CAM has to decide how important each of the k feature map was to our class c that we are interested in. We have to weight each pixel of each feature map with the gradient before we average over the feature maps. This gives us a heatmap which highlights regions that positively or negatively affect the class of interest. This heatmap is sent through the ReLU function, which is a fancy way of saying that we set all negative values to zero. Grad-CAM removes all negative values by using a ReLU function, with the argument that we are only interested in the parts that contribute to the selected class c and not to other classes. The word pixel might be misleading here as the feature map is smaller than the image (because of the pooling units) but is mapped back to the original image. We then scale the Grad-CAM map to the interval [0,1] for visualization purposes and overlay it over the original image.

Let us look at the recipe for Grad-CAM Our goal is to find the localization map, which is defined as:

```
[\L^c_{\{Grad-CAM\}} \in \mathbb{R}^{\{u \times v\}} = \underbrace\{\text{ReLU}\}_{\text{Pick positive values}} \left(\sum_{\{k\} \text{ alpha\_k } \wedge c \text{ A}^k \right)]
```

Here, u is the width, v the height of the explanation and c the class of interest.

- 1. Forward propagate the input image through the convolutional neural network.
- 2. Obtain the raw score for the class of interest, meaning the activation of the neuron before the softmax layer.
- 3. Set all other class activations to zero.
- 4. Backpropagate the gradient of the class of interest to the last convolutional layer before the fully connected layers: \(\frac{\delta\{y^c\}}{\delta\{A^k\}}\).
- 5. Weight each feature map "pixel" by the gradient for the class. Indices i and j refer to the width and height dimensions: \(\alpha_k^c = \overbrace\{\frac{1}{Z} \sum_{\{i\}} \sum_{\{j\}}\}^c \{ \text{global average pooling\} } \underbrace\{ \frac{\delta y \wedge c}{\delta A_{\{ij\}} \wedge k} \} \{ \text{gradients via backprop\} }\) This means that the gradients are globally pooled.
- 6. Calculate an average of the feature maps, weighted per pixel by the gradient.
- 7. Apply ReLU to the averaged feature map.
- 8. For visualization: Scale values to the interval between 0 and 1. Upscale the image and overlay it over the original image.
- 9. Additional step for Guided Grad-CAM: Multiply heatmap with guided backpropagation.

## 7.2.4 Guided Grad-CAM

From the description of Grad-CAM you can guess that the localization is very coarse since the last convolutional feature maps have a much coarser resolution compared to the input image. In contrast, other attribution techniques backpropagate all the way to the input pixels. They are therefore much more detailed and can show you individual edges or spots that contributed most to a prediction. A fusion of both methods is called Guided Grad-CAM. And it is super simple. You compute for an image both the Grad-CAM explanation and the explanation from another attribution method, such as Vanilla Gradient. The Grad-CAM output is then upsampled with bilinear interpolation, then both maps are multiplied element-wise. Grad-CAM works like a lens that focuses on specific parts of the pixel-wise attribution map.

## 7.2.5 SmoothGrad

The idea of SmoothGrad by Smilkov et. al 2017^84 is to make gradient-based explanations less noisy by adding noise and averaging over these artificially noisy gradients. SmoothGrad is not a standalone explanation method, but an extension to any gradient-based explanation method.

SmoothGrad works in the following way:

- 1. Generate multiple versions of the image of interest by adding noise to it.
- 2. Create pixel attribution maps for all images.
- 3. Average the pixel attribution maps.

Yes, it is that simple. Why should this work? The theory is that the derivative fluctuates greatly at small scales. Neural networks have no incentive during training to keep the gradients smooth, their goal is to classify images correctly. Averaging over multiple maps "smooths out" these fluctuations:

```
|R_{sg}(x) = \frac{1}{n} \sum_{i=1}^n R(x+g_i),|
```

Here, (g_i \sim N(0, \sigma^2)) are noise vectors sampled from the Gaussian distribution. The "ideal" noise level depends on the input image and the network. The authors suggest a noise level of 10%-20%, which means that (\frac{1}{n}\sum_{i=1}^n R(x+g_i),|) should be between 0.1 and 0.2. The limits (x_min) and (x_max) refer to minimum and maximum pixel values of the image. The other parameter is the number of samples n, for which was suggested to use n = 50, since there are diminishing returns above that.

## 7.2.6 Examples

Let us see some examples of what these maps look like and how the methods compare qualitatively. The network under examination is VGG-16 (Simonyan et. al 2014^85) which was trained on ImageNet and can therefore distinguish more than 20,000 classes. For the following images we will create explanations for the class with the highest classification score.

These are the images and their classification by the neural network:

### Greyhound (vanilla)

![](img/9328bf422a53c0f374079f63527c081f_236_0.png)

### Soup Bowl (vanilla)

![](img/9328bf422a53c0f374079f63527c081f_236_1.png)

### Eel (vanilla)

![](img/9328bf422a53c0f374079f63527c081f_236_2.png)

The image on the left with the honorable dog guarding the Interpretable Machine Learning book was classified as "Greyhound" with a probability of 35% (seems like "Interpretable Machine Learning book" was not one of the 20k classes). The image in the middle shows a bowl of yummy ramen soup and is correctly classified as "Soup Bowl" with a probability of 50%. The third image shows an octopus on the ocean floor, which is incorrectly classified as "Eel" with a high probability of 70%.

And these are the pixel attributions that aim to explain the classification:

### Greyhound (vanilla)

![](img/9328bf422a53c0f374079f63527c081f_236_3.png)

### Soup Bowl (vanilla)

![](img/9328bf422a53c0f374079f63527c081f_236_4.png)

### Eel (vanilla)

![](img/9328bf422a53c0f374079f63527c081f_236_5.png)

### Greyhound (Smoothgrad)

![](img/9328bf422a53c0f374079f63527c081f_236_6.png)

### Soup Bowl (Smoothgrad)

![](img/9328bf422a53c0f374079f63527c081f_236_7.png)

### Eel (Smoothgrad)

![](img/9328bf422a53c0f374079f63527c081f_236_8.png)

### Greyhound (Grad-Cam)

![](img/9328bf422a53c0f374079f63527c081f_236_9.png)

### Soup Bowl (Grad-Cam)

![](img/9328bf422a53c0f374079f63527c081f_236_10.png)

### Eel (Grad-Cam)

![](img/9328bf422a53c0f374079f63527c081f_236_11.png)
