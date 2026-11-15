
- [9] S. Albawi, T.A. Mohammed, S. Al-Zawi, Understanding of a convolutional neural network, in: Proceedings of International Conference on Engineering and Technology, 2017, pp. 1–6.

- [10] D. Yu, H. Wang, P. Chen, Z. Wei, Mixed pooling for convolutional neural networks, in: Proceedings of International Conference on Rough Sets and Knowledge Technology, 2014.

- [11] S. Hijazi, R. Kumar, C. Rowen, et al., Using convolutional neural networks for image recognition, Cadence Design Systems (2015) 1–12.

- [12] H. Ajmal, S. Rehman, U. Farooq, Q.U. Ain, F. Riaz, A. Hassan, Convolutional neural network based image segmentation: a review, in: Proceedings of Pattern Recognition and Tracking XXIX, 2018.

- [13] Z. Wang, J. Liu, A review of object detection based on convolutional neural network, in: Proceedings of Chinese Control Conference, 2017, pp. 11104–11109.

- [14] Z.C. Lipton, A critical review of recurrent neural networks for sequence learning, arXiv:1506.00019 [abs].

- [15] J.J. Hopfield, Neural networks and physical systems with emergent collective computational abilities, Proceedings of the National Academy of Sciences 79 (8) (1982) 2554–2558.

- [16] S. Hochreiter, J. Schmidhuber, Long short-term memory, Neural Computation 9 (8) (1997) 1735–1780.

- [17] R. Dey, F.M. Salem, Gate-variants of gated recurrent unit (GRU) neural networks, in: Proceedings of IEEE International Midwest Symposium on Circuits and Systems, 2017, pp. 1597–1600.

- [18] D.M. Kline, V. Berardi, Revisiting squared-error and cross-entropy functions for training neural network classifiers, Neural Computing & Applications 14 (2005) 310–318.

- [19] M.W. Schmidt, G. Fung, R. Rosales, Fast optimization methods for L1 regularization: A comparative study and two new approaches, in: Proceedings of European Conference on Machine Learning, 2007.

- [20] P. Bühlmann, B. Yu, Boosting with the L2 loss: regression and classification, Journal of the American Statistical Association 98 (462) (2003) 324–339.

- [21] S. Singh, D. Singh, S. Kumar, Modified mean square error algorithm with reduced cost of training and simulation time for character recognition in backpropagation neural network, in: Proceedings of International Conference on Frontiers in Intelligent Computing: Theory and Applications, 2013.

- [22] W. Liu, Y. Wen, Z. Yu, M. Yang, Large-margin softmax loss for convolutional neural networks, arXiv:1612.02295 [abs].

- [23] A. Krogh, J. Hertz, A simple weight decay can improve generalization, in: Proceedings of International Conference on Neural Information Processing Systems, 1991.

- [24] E. Dogo, O. Afolabi, N. Nwulu, B. Twala, C. Aigbavboa, A comparative analysis of gradient descent-based optimization algorithms on convolutional neural networks, in: Proceedings of International Conference on Computational Techniques, Electronics and Mechanical Systems, 2018, pp. 92–99.

- [25] Y. Bengio, I. Goodfellow, A. Courville, Deep Learning, vol. 1, MIT press, Massachusetts, USA, 2017.

- [26] D.P. Kingma, J. Ba, Adam: A method for stochastic optimization, arXiv:1412.6980 [abs].

- [27] G. Hinton, N. Srivastava, K. Swersky, RMSProp: Divide the gradient by a running average of its recent magnitude, Neural Networks for Machine Learning, Coursera lecture 6e (2012) 13.

- [28] D.E. Rumelhart, G.E. Hinton, R.J. Williams, Learning representations by back-propagating errors, Nature 323 (6088) (1986) 533–536.

- [29] M. Sandler, A.G. Howard, M. Zhu, A. Zhmoginov, L.-C. Chen, MobileNetV2: Inverted residuals and linear bottlenecks, in: Proceedings of IEEE Conference on Computer Vision and Pattern Recognition, 2018.

- [30] K. He, X. Zhang, S. Ren, J. Sun, Deep residual learning for image recognition, in: Proceedings of IEEE Conference on Computer Vision and Pattern Recognition, 2016.

- [31] A. Krizhevsky, I. Sutskever, G.E. Hinton, ImageNet classification with deep convolutional neural networks, Communications of the ACM 60 (2012) 84–90.

## PART 2

### Model and algorithm

This page intentionally left blank

## CHAPTER 3

### Model design and compression

### 3.1 Background and challenges

Although convolutional neural networks have achieved good results in such fields as computer vision and natural language processing, they are daunting to many embedded device-based applications due to their massive parameters. At present, deep learning models require large amounts of computing resource and memory, often accompanied by huge energy consumption. Large models become the biggest bottleneck when we need to deploy models on terminal devices with limited computing resources for real-time inference. The training and reasoning of deep neural networks usually heavily rely on GPU with high computing ability. The huge scale of features and the deluge of model parameters also greatly increase the time. Take as an example AlexNet [1], a network containing 60 million parameters. It takes two to three days to train the entire model on the ImageNet data set using NVIDIA K40. In fact, Denil et al. [9] have shown that deep neural networks are facing severe overparameterization, and a small subset of the parameters can completely reconstruct the remaining parameters. For example, ResNet-50 [10], which has 50 convolutional layers, requires more than 95 MB of storage memory and more than 3.8 billion floating-point multiplication operations to process images. After some redundant weights are discarded, the network still works as usual, but more than 75% of the parameters and 50% of the computation time can be saved. This indicates that there is huge redundancy in the parameters of the model, which reveals the feasibility of model compression.

In the field of deep neural network study, model compression and acceleration have received great attention from researchers, and great progress has been made in the past few years. Significant advances in intelligent wearable devices and AIoT in recent years have created unprecedented opportunities for researchers to address the fundamental challenges of deploying deep learning systems to portable devices with limited resources, such as memory, CPU, energy, and bandwidth. A highly efficient deep learning method can have a significant impact on distributed systems, embedded devices, and FPGAs for artificial intelligence. For the design and compression of highly efficient deep neural network models, in this chapter, we will first analyze several categories of typical lightweight neural network models in recent years and then discuss model compression technology for neural networks, including model pruning and knowledge distillation.

### 3.2 Design of lightweight neural networks

The lightweight model aims to reduce model parameters and computational complexity from the aspect of network structure design while maintaining model performance, which is a hotspot of deep learning study. With the same accuracy, a smaller CNN architecture will consume fewer resources and be more suitable for deployment on embedded edge terminal devices with limited memory and computing resources. In this section, we mainly focus on the design of network structure and give a brief description of lightweight networks, including the following types of lightweight models.

### 3.2.1 SqueezeNet

Researchers at UC Berkeley and Stanford first proposed a small CNN architecture called SqueezeNet in 2016 [11], which was one of the early studies focusing on lightweight networks. They reduced the number of network parameters to less than 0.5 MB, 510 times smaller than that of AlexNet, but with the same accuracy as AlexNet. To do this, they used three strategies to reduce the number of parameters and maintain accuracy.

- Strategy 1: Replace the 3 × 3 convolution with the 1 × 1 convolution, so that the number of parameters for a convolutional kernel can be reduced by 9 times.
- Strategy 2: Reduce the number of input channels for the 3 × 3 filter via squeeze layer.
- Strategy 3: Delay downsampling. The higher the number of the layer, the larger the feature map, which is conducive to improving the accuracy of the model.

The basic unit in SqueezeNet is called Fire Module. A Fire Module consists of a Squeeze layer and an Expand layer, as shown in Fig. 3.1. Squeeze layer only uses a 1 x 1 convolutional kernel to realize strategy 1, whereas Expand Layer uses the convolutional combination of 1 x 1 and 3 x 3. There are three adjustable parameters in the Module, namely, the number of 1 x 1 convolutional kernels in Squeeze layer s1, the number of 1 x 1 convolutional kernels in Expand layer e1 and the number of 3 x 3
