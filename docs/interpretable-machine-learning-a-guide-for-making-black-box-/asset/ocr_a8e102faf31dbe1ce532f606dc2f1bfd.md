# 7.1 Learned Features

This chapter is currently only available in this web version. ebook and print will follow.

Convolutional neural networks learn abstract features and concepts from raw image pixels. Feature Visualization visualizes the learned features by activation maximization. Network Dissection labels neural network units (e.g. channels) with human concepts.

Deep neural networks learn high-level features in the hidden layers. This is one of their greatest strengths and reduces the need for feature engineering. Assume you want to build an image classifier with a support vector machine. The raw pixel matrices are not the best input for training your SVM, so you create new features based on color, frequency domain, edge detectors and so on. With convolutional neural networks, the image is fed into the network in its raw form (pixels). The network transforms the image many times. First, the image goes through many convolutional layers. In those convolutional layers, the network learns new and increasingly complex features in its layers. Then the transformed image information goes through the fully connected layers and turns into a classification or prediction.

![](bbox=[0.062, 0.335, 0.638, 0.425])

FIGURE 7.1: Features learned by a convolutional neural network (Inception V1) trained on the ImageNet data. The features range from simple features in the lower convolutional layers (left) to more abstract features in the higher convolutional layers (right). Figure from Olah, et al. 2017 (CC-BY 4.0) https://distill.pub/2017/feature-visualization/appendix/.

+   • The first convolutional layer(s) learn features such as edges and simple textures.
+   • Later convolutional layers learn features such as more complex textures and patterns.
+   • The last convolutional layers learn features such as objects or parts of objects.
+   • The fully connected layers learn to connect the activations from the high-level features to the individual classes to be predicted.

Cool. But how do we actually get those hallucinatory images?

# 7.1.1 Feature Visualization

The approach of making the learned features explicit is called Feature Visualization. Feature visualization for a unit of a neural network is done by finding the input that maximizes the activation of that unit.

"Unit" refers either to individual neurons, channels (also called feature maps), entire layers or the final class probability in classification (or the corresponding pre-softmax neuron, which is recommended). Individual neurons are atomic units of the network, so we would get the most information by creating feature visualizations for each neuron. But there is a problem: Neural networks often contain millions of neurons. Looking at each neuron's feature visualization would take too long. The channels (sometimes called activation maps) as units are a good choice for feature visualization. We can go one step further and visualize an entire convolutional layer. Layers as a unit are used for Google's DeepDream, which repeatedly adds the visualized features of a layer to the original image, resulting in a dream-like version of the input.