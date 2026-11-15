# Disadvantages of Deep Learning

+   1. High computational requirements: Deep Learning models require large amounts of data and computational resources to train and optimize.
+   2. Requires large amounts of labeled data: Deep Learning models often require a large amount of labeled data for training, which can be expensive and time- consuming to acquire.
+   3. Interpretability: Deep Learning models can be challenging to interpret, making it difficult to understand how they make decisions.
+   4. Over fitting: Deep Learning models can sometimes over fit to the training data, resulting in poor performance on new and unseen data.
+   5. Black-box nature: Deep Learning models are often treated as black boxes, making it difficult to understand how they work and how they arrived at their predictions.

# 5.2 ARTIFICIAL NEURAL NETWORKS (ANNS)

Artificial Neural Networks (ANNs) are computational models inspired by the structure and functioning of the human brain's neural networks. They are a fundamental component of deep learning, a subfield of artificial intelligence. ANNs consist of interconnected nodes, known as artificial neurons or perceptrons, organized into layers. These neurons receive input data, process it through weighted connections, and produce output signals. The structure of an ANN typically comprises an input layer, one or more hidden layers, and an output layer.

The operation of an artificial neural network involves a process known as forward propagation. During this process, input data is fed into the network, and the neurons process the data through activation functions, which introduce non-linearity into the network. The output of the network is then compared to the desired output (labels) using a predefined loss function, which quantifies the difference between the predicted output and the actual output. The network's goal is to minimize this loss by adjusting the weights and biases of the neurons through a process called backpropagation.

Backpropagation is a critical training algorithm in ANNs. It calculates the gradients of the loss function with respect to each weight and bias in the network and uses these gradients to update the parameters,