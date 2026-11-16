![](bbox=[0.125, 0.092, 0.873, 0.473])

FIGURE 25.2: Intelligent apps provide intelligent services to users.
Source: ImagineDesign / Adobe Stock

# Compressed Models

Compressed models are about compressing the models in size and complexity without losing accuracy and performance. They open new possibilities concerning the deployment of the models on the edge. Model compression results in reduced storage, reduced bandwidth requirements, improved performance, lower cost, and improved security. However, it is not without drawbacks because, with the reduced size, it can lose accuracy, is also challenging to develop, and is available for only some models. As technology develops, some of these drawbacks may be eliminated, making this more effective.

Some examples of model compression techniques are defined here:

+   - Pruning the weights: Involves removing certain connections (weights) between the nodes of a neural network to reduce the size of the network.
+   - Quantization: Reduces the number of bits used to identify a weight. For example, using 8-bit integers instead of 32-bit floating-point numbers can reduce the model size and increase the speed of arithmetic operations.
+   - Activations: Refer to the outputs of the neural network. Reducing the size of the activations can also reduce the compute power required to train or use