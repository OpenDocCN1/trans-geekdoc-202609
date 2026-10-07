
single convolutional layer does), this pair of convolutional layers sweeps across the image.

In short, you can think of the whole inception module as a convolutional layer on steroids, able to output feature maps that capture complex patterns at various scales. The number of convolutional kernels for each convolutional layer is a hyperparameter. Unfortunately, this means you have six more hyperparameters to tweak for every inception layer you add.

img/0684d2da98e09085c0a622d4fd69aaad_479_0.png

Now let's look at the architecture of GoogNet (see Figure 14-14). The number of feature maps output by each convolutional layer and each pooling layer is shown before kernel size. The architecture is so deep that it has to be represented in three columns, but GoogNet is actually one stack, including nine inception modules (the boxes) in the same order as in Figure 14-13. Note that all convolutional layers use the ReLU activation function.

img/0684d2da98e09085c0a622d4fd69aaad_480_0.png

Figure 14-14. GoogNet architecture

Let’s go through this network:

- The first two layers divide the image's height and width by 4 (so its area is divided by 16), to reduce computational load. The first layer uses a large kernel size so that much of the information is still preserved.
- Then local response normalization ensures that the previous layers learn a wide variety of features (as discussed earlier).
- Two convolutional layers follow, where the first acts like a bottleneck layer. Again, local response normalization ensures that the previous layers capture a wide variety of patterns.
- Next max pooling layer reduces the image height and width by 2, again to speed up computations.
- Then comes the tall stack of nine inception modules, interleaved with a couple max pooling layers to reduce dimensionality and speed up the net.
- Next, global average pooling simply outputs the output of each feature map: this drops any remaining spatial information, which is fine since it is a classification task. Indeed, GoogNet input images are expected to be 224 × 224 pixels; after 5 pooling layers, each dividing the height and width by 2, the feature maps are down to 7 × 7. Moreover, it does not matter where the object is. Thanks to the dimensionality reduction brought by this layer, there is no need to have several fully connected layers at the top (like in AlexNet), and this considerably reduces the risk of overfitting.
- The last layers are self-explanatory: dropout for regularization, a fully connected layer with 1,000 units, since there are 1,000 classes, and a softmax activation function to output class probabilities.

This diagram is slightly simplified: the original GoogNet architecture also included two auxiliary classifiers plugged on top of the third and sixth inception modules. They were both composed of one average pooling layer, one convolutional layer, two fully connected layers, and a softmax activation layer. During training, their loss was scaled down and added to the overall loss. The goal was to fight the vanishing gradients problem and regulate the network. However, it was later shown that their effects were relatively minor.

Several variants of the GoogNet architecture were later proposed by Google researchers, including Inception-v3 and Inception-v4, using deeper inception modules, reaching even better performance.

## VGGNet

The runner up in the ILSVRC 2014 challenge was VGGNet, developed by K. Simonyan and A. Zisserman. It had a very simple and classical architecture, with 2 or 3 convolutional layers, a pooling layer, then again 2 or 3 convolutional layers, a pooling layer, and so on (with a total of 16 convolutional layers), plus a final dense network with 2 hidden layers and the output layer. It used only 3 × 3 filters, but many filters.

"Very Deep Convolutional Networks for Large-Scale Image Recognition," K. Simonyan and A. Zisserman (2015).

## ResNet

The ILSVRC 2015 challenge was won using a Residual Network (or ResNet), developed by Kaiming He et al., which delivered an astounding top-5 error rate under 3.6%, using an extremely deep CNN composed of 152 layers. It confirmed the general trend: models are getting deeper and deeper, with fewer and fewer parameters. The key to being able to train such a deep network is skip connections (also called shortcut connections): the signal feeding into a layer is also added to the output of a layer located a bit higher up. Let's see why this is useful

When training a neural network, the goal is to make it a target function h(x). If you add the input x to the output of the network (i.e., add a skip connection), then the network will be forced to model f(x) = h(x) - x rather than h(x). This is called residual learning (see Figure 14-15).

img/0684d2da98e09085c0a622d4fd69aaad_482_0.png

Figure 14-15. Residual learning

When you initialize the residual network, the weights are close to zero. If you add the skip connection, the output is close to the input, which makes it easier to train the network at the start. This is why residual learning is so effective for deep networks.

The number of feature maps output by each convolutional layer is a hyperparameter. Unfortunately, this means you have six more hyperparameters to tweak for every inception layer you add.

img/0684d2da98e09085c0a622d4fd69aaad_479_0.png

The number of feature maps output by each convolutional layer is a hyperparameter. Unfortunately, this means you have six more hyperparameters to tweak for every inception layer you add.

img/0684d2da98e09085c0a622d4fd69aaad_480_0.png

The number of feature maps output by each convolutional layer is a hyperparameter. Unfortunately, this means you have six more hyperparameters to tweak for every inception layer you add.

img/0684d2da98e09085c0a622d4fd69aaad_483_0.png

The number of feature maps output by each convolutional layer is a hyperparameter. Unfortunately, this means you have six more hyperparameters to tweak for every inception layer you add.

img/0684d2da98e09085c0a622d4fd69aaad_483_1.png
