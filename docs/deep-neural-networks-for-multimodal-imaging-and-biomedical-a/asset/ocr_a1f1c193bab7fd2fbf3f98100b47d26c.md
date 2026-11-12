# ZF Net

In 2013, Zeiler and Fergus introduced a multilayer deconvolutional neuron network known as (ZF NET) (Matthew D Zeiler, 2013), where they proposed a new visualization technique that provides a quantitative overview of network performance. The idea of visualizing network activity is to discover the contribution of different model layers to performance by monitoring the learning pattern during training and using these results to extract the problem associated with the model. Experimentally validating this idea was done on AlexNet (Matthew D Zeiler, 2013). Experimental results showed that only a few neurons were active, unlike other neurons that were inactive in the first two layers of the model. Based on these results, the authors modify the CNN topology and optimize CNN learning by reducing both the size of the first layer size (11 x 11) filters (Stride: 4) to the size (7 x 7) (Stride: 2). In addition, they increased the numbers of the kernel of the 3rd convolutional layer from 384 to 512 kernel, the 4th convolutional layer from 384 to 1024 kernel, the 5th layer of convolution of 256 to 512 kernel. This readjustment of the CNN topology resulted in an improvement in performance where this architecture achieved an Image Net “TOP 5” error rate equivalent to 11.7% instead of 16.4% for (Y. LeCun, 2015). Feature visualization can be exploited to extract design problems and adjust settings in a timely manner.

# VGG Net

In 2014, the VGGNET architecture (figure 5) proposed in (Zisserman, 2015) won part of the ILSVRC 2014 challenge with an error rate equivalent to TOP 5 equivalent to ImageNET 7.4% and nearly 138 million parameters knowing that it uses fully connected layers. There are several topologies with different numbers of layers ranging from 11 to 19 layers (the VGG-16 topology with very regular structure of 16 layers). This architecture replaced the 7x7 convolution filters with a pitch of 2 by three (3) convolution filters of sizes 3x3 (stride 1, pad 1) in order to keep almost the same resultant dimension of convolution 7x7 while decreasing the number of parameters (calculation complexity) and increasing the number of activation functions used. In addition, this architecture uses a maximum sub-sampling of size 2 x 2. VGG16 (Zisserman, 2015) is based on convolution filters of sizes 3x3 and a network width which starts from 64 and increases by a factor of two every two layers of convolution. It is noted that VGG (Zisserman, 2015) is the most expensive architecture in terms of both computational requirements and number of parameters. This model is formed for about 74 epochs (370K) using a stochastic gradient descent (SGD) with:

+   - Momentum: 0.9.
+   - Decreased weight: 0.0001.
+   - Batch size: 256.

The learning rate was initialized to 0.01 and reduced three times before the end where it is divided by 10 when the validation error rate stopped improving with the current learning rate.

# GoogLeNet

Introduced by Christian Szegedy et al, (al, 2015). She won the 2014-ILSVRC contest. The GoogLeNet contains 22 layers and achieves an ImageNet TOP 5 error rate equivalent to 6.67% while requiring only