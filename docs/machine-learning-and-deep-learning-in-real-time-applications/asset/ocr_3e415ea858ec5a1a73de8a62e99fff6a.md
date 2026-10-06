# Obtaining Deep Learning Models for Automatic Classification of Leukocytes

layer is such that it allows the resolution to be preserved after the convolution, for example, the fill is 1 pixel for convolution layers with 3*3. Spatial grouping is accomplished with 5 layers of max-pooling, which follow some of the convolution layers. Max-pooling is done with windows of 2×2and step of 2.
The set of convolution layers (which have different depths depending on the architecture) is followed by three fully-connected layers: the first two contain 4096 channels each, the third classifies the 1000 (with one for each class). The final layer is a softmax layer. The configuration of the fully-connected layers was the same in all networks tested.
All concealed layers were equipped with the ReLU activation function (Simonyan & Zisserman, 2014).

Figure 8. Visualization of the VGG generic architecture (Rosebrock, 2017)

![](bbox=[0.158, 0.335, 0.842, 0.463])

The numbers 16 and 19 represent the number of weights in the network. Some disadvantages of VGGNet is the slowness of training nodes, the width and height of the weight architecture. Due to its depth and number of fully-connected nodes, VGG16 is more than 533MB, and VGG19 is more than 574MB, which makes deploying these networks complicated.

# InceptionV3

The winner of the ILSVRC 2014 contest was GoogleLeNet (V1) from Google. It achieved a top-5 error rate of 6.67%, very close to the human-level performance, also rated by the organizers.
The network used a LeNet-inspired CNN built with a new element called the Inception module (represented in Figure 9). It used batch normalization, image distortions and optimizer RMSprop. Its architecture consists of a deep 22-layer CNN reduced the number of parameters from 60 million (from AlexNet) to 4 million (Das, 2018).
The use of average pooling allows for easy adaptation and fine-tuning for other layers. The authors came to the conclusion that switching from fully-connected layers to average pooling layers improved the top-1 results by 0.61%, with no dropout.
Given the large size of the network, the ability to propagate the gradient across all layers was a concern. Adding intermediate layer classifiers enabled discrimination at lower stages of the classifier, increasing the propagated gradient signal back and providing additional regularization. These classifiers are in the form of small convolutional networks placed at the top of the Inception modules (additional pooling paths). During training, the loss is added to the total loss of the network with a weight discount. At the inference, these auxiliary networks are discarded (Szegedy, et al., 2014).