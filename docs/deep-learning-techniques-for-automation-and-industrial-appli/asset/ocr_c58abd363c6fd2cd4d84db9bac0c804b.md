such as data augmentation, regularization, and transfer learning can be used to improve the performance of the model.

# 10.1.4.2 Residual Network

Researchers at Microsoft introduced Residual Network (ResNet), a deep convolutional neural network architecture, in 2015. It was made to deal with the issue of disappearing gradients in deep neural networks, which can make training extremely deep networks challenging. After achieving cutting-edge performance on the ImageNet dataset, the ResNet architecture has gained popularity as a transfer learning method for a range of computer vision tasks.

The ResNet architecture consists of several residual blocks shown in Figure 10.3, which contain skip connections that allow information to bypass one or more layers. By allowing the gradients to continue, these skip connections help solve the vanishing gradient problem by allowing the gradients to flow directly to earlier layers, which can help prevent the gradients from becoming too small or too large.

The basic building block of the ResNet architecture is the residual block, which contains two convolutional layers with batch normalization and ReLU activation functions. The first convolutional layer processes the input into the residual block, while the second convolutional layer processes the output. The second convolutional layer's output is added by the residual connection, and the combined output is then subjected to batch normalization and ReLU activation algorithms.

![](bbox=[0.1, 0.6, 0.9, 0.9])

Figure 10.3 ResNet-50 architecture [12].