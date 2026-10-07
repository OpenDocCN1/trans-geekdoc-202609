![](bbox=[0.157, 0.087, 0.842, 0.413])

Figure 14-5. Applying two different filters to get two feature maps

# # Stacking Multiple Feature Maps

Up now, for simplicity, I have represented the output of each convolutional layer as a 2D depth, but in reality a convolutional layer has multiple filters (you decide how many), it outputs one feature map per filter, so it is more accurately represented in 3D (see Figure 14-6). To do so, it has one neuron per pixel in each feature map, and all neurons within a given feature map share the same parameters (i.e., the same weights and bias term). However, neurons in different feature maps differ parameters. A neuron's receptive field is the same as described earlier, but extends across all the previous layers' feature maps. In short, a convolutional layer simultaneously applies trainable filters to its inputs, making capable of detecting multiple features in its inputs.

> > The fact that all neurons in a feature map share the same parameters dramatically reduces the number of parameters in the model. Moreover, the CNN has learned to recognize a pattern in one location, it can recognize it in any other location. In contrast, a regular DNN has learned to recognize a pattern in one location, it can recognize it only in that particular location.

Moreover, input images are also composed of multiple sublayers: one per color channel. There are typically three: red, green, and blue (RGB). Grayscale images have just