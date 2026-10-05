# 9.1. CONVOLUTIONAL NEURAL NETTS

# 2. In which direction to pool?

(a) Spatial pooling values within the same channel. This has the capability of introducing translational invariance to your model.

![](bbox=[0.338, 0.175, 0.663, 0.222])

9.4: Here, the input layer of the right image is a translated version of the input layer of the left image, but because of max-pooling, the next layer looks more or less the same.

(b) Cross-channel pooling values across different channels. This has the capability of introducing translational invariance to your model.

![](bbox=[0.316, 0.335, 0.683, 0.47])

9.5c: Here, we have an example where our convolutional layer is represented by 3 kernels. Suppose they were good for detecting the number 5 in some degree of rotation. If we pooled across the three channels determined by these kernels, then no matter what orientation of the number "5" we got as input to our ConvNet, the pooling layer would have a large response!

+   3. "Lossness" of pooling. This is determined by the stride of the pooling window. If you stride by a large amount, you potentially lose more information, but you conserve memory.

If you now look back at the picture of the ConvNet near the beginning of this text, you should have a better idea of what each layer is doing. The ConvNet in that picture is Yann Lecun's LeNet, which is used to classify handwritten alphanumeric characters!

# CNN Architectures

Convolutional Neural Networks were first applied successfully to the ImageNet challenge in 2012 and continue to outperform computer vision techniques that do not use neural networks. Here are a few of the architectures that have been developed over the years.

# AlexNet (Krizhevsky, et al, 2012)

Key characteristics:

+   - Conv filters of varying sizes - for example, the first layer has 11 x 11 conv filters
- First use of ReLU, which fixed the problem of saturating gradients in the predominant tanh activation.