# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

However, it is not possible to make reliable comparisons between this and other works because the datasets used in this work are not the same as the ones used in the other authors referred works, and some may have more visual quality than others.

# FUTURE RESEARCH DIRECTIONS

Among some interesting proposals in terms of neural networks, in the last couple of years, the following articles are highlighted:

+   - Identity mappings in Deep Residual Networks (He, et. al., 2016) proposes an improvement of ResNet's block design. A more direct path has been created to propagate information across the network (it moves the activation to the residual path) performance.

+   - Aggregated Residual Transformations for Deep Neural Networks (ResNext (Xie, et. al., 2017), from the creators of ResNet, presents an increase in the width of the blocks through multiple parallel paths (“cardinality”) similar to the Inception models.

+   - Deep Networks with Stochastic Depth (Huang, et. al., 2016) aims to reduce the vanishing gradients and the training time through the use of short networks during the train. They do not use sets of layers, chosen at random, during a passing. They bypass the identity function but use the network complete at the time of testing.

+   - FractalNet: Ultra-Deep Neural Networks without Residuals (Larsson, et al., 2017) argues that the key to good performance “and the ability to transition between different networks. They use fractal architectures that have little and a lot of depths up to the output. They are trained omit some paths. The complete network is used during the testing.

+   - SqueezeNet: AlexNet-accuracy with 50 fewer parameters and <0.5MB model size (Iandola, et. al., 2016) presents models that consist in a “squeeze” layer with 1x1 and 3x3 filters. The authors are able to achieve at the level of an AlexNet in Mobile with 50 fewer parameters. The network is compressed to a size 510x smaller than AlexNet (0.5 MB).

In the domain of cell identification and classification and microorganisms in general, it is expected to see an increase of AI techniques applied in hospitals and laboratories. In this specific case, the use of technology is dependent on the way the microscopy images are obtained. One hopes that this side of the equation sees an equal technological improvement, as the quality of the results depends on the quality of the images acquired, the speed of acquisition (as well as the efficiency of the preprocessing techniques).

# CONCLUSION

The primary purpose of this document is the description of the implementation of a set of neural networks in the classification of white blood cells or leukocytes. Open-source implementations were used with the Keras framework, with most implementations being available from ILSVRC winning networks. The Keras models used were the ResNet50, the VGG16, the VGG19, the InceptionV3, the Xception, the Densenet121, the Densenet169 and the Densenet201.