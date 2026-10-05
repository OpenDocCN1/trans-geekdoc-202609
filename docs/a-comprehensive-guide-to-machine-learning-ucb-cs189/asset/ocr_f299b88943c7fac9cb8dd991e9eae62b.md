# 9.1. CONVOLUTIONAL NEURAL NETS

# GoogLeNet (Szegedy et al, 2014)

Also codamed as “Inception.”2 Published in CVPR 2015 as “Going Deeper with Convolutions.”
Key characteristics:

![](bbox=[0.118, 0.198, 0.882, 0.375])

Figure 9.7: Inception Module

+   - Unlike previous networks (22 layers), but more computationally efficient (5 million parameters - no fully connected).
- Network is composed of stacked sub-networks called “Inception modules.” The naive Inception module (a) runs convolutional layers in parallel and concatenates the filters together. However, this can be computationally inefficient. The dimensionality reduction Inception module (b) performs 1 x1 convolutions that act as dimensionality reduction. This lowers the computational cost and makes it tractable to stack many Inception modules.

ResNet (He et al, 2015)

![](bbox=[0.118, 0.646, 0.882, 0.773])

Figure 9.8: Building block for the ResNet from “Deep Residual Learning for Image Recognition,” CVPR 2016. If the desired function to be learned is H(x), we instead learn the residual F(x) := H(x)-x, so the output of the network is F(x) + x = H(x).

Key characteristics:

> In this paper, we will focus on an efficient deep neural network architecture for computer vision, codename Inception, which derives its name from the Network in network paper by Lin et al [12] in conjunction with the famous we need to go deeper internet meme [1]. The authors seem to be meme-friendly.