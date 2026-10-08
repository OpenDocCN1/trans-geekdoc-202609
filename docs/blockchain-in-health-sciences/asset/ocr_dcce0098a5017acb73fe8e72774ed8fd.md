# IMPLEMENTING CNN ALGORITHM FOR MEDICAL IMAGE ANALYSIS 353

striking similarities with a human brain [1, 2]. The small circles in the figures are neurons. Neurons are the basic functioning unit in the CNN, similar to neurons in the human brain. Each neuron is connected to multiple other neurons to aggregate the result and come to a common result. A collection of neurons makes a layer. Referring to Figure 17.1, there are 5 layers. Again, there are different types of layers which are used collectively to bring different functionalities together [3]. Some common layers used in image processing are:

+   - Input Layer: This is the first layer in a convolutional neural network, which takes in the input from the user and processing it the requirement of the next layer. This layer does not do any computation [1, 3]. In Figure 17.1, the layer prior to convolution layer is the input layer.
- Hidden Layers: The neural layers which do the computation and do not interact directly with the user are hidden layers because they are “hidden” between the input and the output layers [4]. These layers extract the patterns in the image. Optimal feature extraction from data requires hidden layers to perform different functionalities, depending on the requirement. The three main types of hidden layers are:
- Convolutional Layers – Extracting Low-Level Features: This is the heart of a CNN. It uses a smaller filter (kernel) that slides across the input image, extracting features like edges, lines, and shapes. The filter learns weights that determines the importance of specific features in the image. Multiple filters can be applied in a single layer,

![](bbox=[0.173, 0.696, 0.912, 0.893])

Figure 17.1 Layers in CNN.