# Generative Models

# Chapter 8

Creating new characters with different attributes could revolutionize the animation industry.

# 3D models from photos

We can create 3D models from 2D images by using generative models, as shown by Wu et al. (https://arxiv.org/pdf/1610.07584.pdf):

![](bbox=[0.122, 0.287, 0.876, 0.442])

Reproduced from Wu et al.

Creating 3D models from images is useful for robotics, augmented reality and in animation industries. We will learn the algorithms behind them in the following sections. In the next section, we will implement neural artistic style transfer.

# Neural artistic style transfer

The first application we will implement the **neural artistic style transfer**. Here, we will transfer the style of **Van Gogh** art onto an image. An image can be considered as a combination of style and content. The artistic style transfer technique transforms an image to look like a painting with a specific style. We will see how to code this idea up. The `loss` function will compare the generated image with the content of the photo and style of the painting. Hence, the optimization is carried out for the image pixel, rather than for the weights of the network. Two values are calculated by comparing the content of the photo with the generated image followed by the style of the painting and the generated image.

[ 213 ]