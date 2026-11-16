Saturated activation functions mean the output does not change even if the input changes, which means the neural network cannot learn anymore. It happens when the activation functions, namely, sigmoid and tanh, have reached their minimum or maximum levels. When this happens, we say the activation functions are saturated. ReLU is an alternative in such situations.

# Vanishing Gradients

Vanishing gradients happen when the gradients or the incremental changes to the neural network weights are minimal or close to o during backpropagation. When this happens, the neural network will not learn much from the data. It can happen when using sigmoid or tanh, as well as when the gradients are not propagated back through the network.

> TIP Think of **saturated activation functions** as rusty gears in a machine. If they are not moving, neither is your model's learning. Similarly, vanishing gradients are like whispers in a noisy room and your model is not hearing them. Opt for RelU for activation functions and proper weight initialization to address these issues.

To resolve this situation, you can either use ReLU or use weight initialization schemes to prevent the gradients from becoming too small.

You can use a debugger tool to keep track of the network’s inputs, outputs, gradients, weights, metrics, logs, errors, and so on. The tool can also capture the state of a machine learning job at periodic intervals, such as various epochs, batches, steps, or layers.

Some examples of a debugger are the PyTorch debugger, TensorFlow debugger, SageMaker Debugger, and Azure Machine Learning debugger. ML debuggers help you to debug and profile the performance at various intervals using breakpoints, alerts, watches, visualizations, and filters.

# Training Code Container