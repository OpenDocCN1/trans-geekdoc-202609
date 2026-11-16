# ## 7.2.4 Guided Grad-CAM

From the description of Grad-CAM you can guess that the localization is very coarse since the last convolutional feature maps have a much coarser resolution compared to the input image. In contrast, other attribution techniques backpropagate all the way to the input pixels. They are therefore much more detailed and can show you individual edges or spots that contributed most to a prediction. A fusion of both methods is called Guided Grad-CAM. And it is super simple. You compute for an image both the Grad-CAM explanation and the explanation from another attribution method, such as Vanilla Gradient. The Grad-CAM output is then upsampled with bilinear interpolation, then both maps are multiplied element-wise. Grad-CAM works like a lense that focuses on specific parts of the pixel-wise attribution map.

# ## 7.2.5 SmoothGrad

The idea of SmoothGrad by Smilkov et. al 2017<sup>84</sup> is to make gradient-based explanations less noisy by adding noise and averaging over these artificially noisy gradients. SmoothGrad is not an standalone explanation method, but an extension to any gradient-based explanation method.

SmoothGrad works in the following way:

+   1. Generate multiple versions of the image of interest by adding noise to it.
+   2. Create pixel attribution maps for all images.
+   3. Average the pixel attribution maps.

Yes, it is that simple. Why should this work? The theory is that the derivative fluctuates greatly at small scales. Neural networks have no incentive during training to keep the gradients smooth, their goal is to classify images correctly. Averaging over multiple maps "smooths out" these fluctuations:

```
|R_{sg}(x)=\frac{1}{n}\sum\_{i=1}^n R(x+g\_i),\|
```

Here, (g\_i\sim N(0,sigma^2(2))) are noise vectors sampled from the Gaussian distribution. The "ideal" noise level depends on the input image and the network. The authors suggest a noise level of 10%-20%, which means that (\frac{1}{n}\sum\_{i=1}^n R(x+g\_i),\|) should be between 0.1 and 0.2. The limits (x\_\min\}) and (x\_\max\}) refer to minimum and maximum pixel values of the image. The other parameter is the number of samples n, for which was suggested to use n = 50, since there are diminishing returns above that.

# ## 7.2.6 Examples

Let us see some examples of what these maps look like and how the methods compare qualitatively. The network under examination is VGG-16 (Simonyan et. al 2014<sup>85</sup>) which was trained on ImageNet and can therefore distinguish more than 20,000 classes. For the following images we will create explanations for the class with the highest classification score.

These are the images and their classification by the neural network: