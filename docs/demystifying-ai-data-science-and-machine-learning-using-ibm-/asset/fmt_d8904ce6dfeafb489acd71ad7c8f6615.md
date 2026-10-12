
# Neural Network Training

![](images/ufig9_7.jpg)

331. Forward propagation and backward propagation are two fundamental processes in training feedforward neural networks. They work together to enable the network to learn from data and improve its predictions. Forward propagation is the fundamental mechanism used to process data and make predictions for a given input. It passes input data through a neural network to generate predictions or outputs. Backward propagation, also called backpropagation, is a learning algorithm used to train feedforward neural networks. It evaluates the difference between the predicted outputs and the actual target values (errors) and then adjusts the network's weights and biases to minimize the errors during the training process.

## 1. Forward propagation

*   Input data are fed into the neural network, and they pass through the layers in a forward direction, from the input layer to the output layer.
*   At each layer, the input is multiplied by the layer's weights and biases, and then an activation function is applied to the result to introduce nonlinearity.
*   The output of each layer becomes the input to the next layer, and this process continues until the final output is generated at the output layer.
*   Forward propagation is essentially the process of making predictions based on the current weights and biases of the neural network, without considering the actual target values.

## 2. Backward propagation

*   Backward propagation is the learning algorithm used to update the weights and biases of the neural network based on the prediction errors during the forward pass.
*   After the forward propagation and predictions, the prediction error is computed using a loss function, which quantifies how far off the predictions are from the true values and serves as a measure of the network's performance.
*   Backward propagation works by computing the gradients of the loss function. The gradients represent the sensitivity of the loss to changes in the network's parameters (weights and biases), indicating which direction and how much each parameter should be adjusted to reduce the error.
*   Using the computed gradients, the weights and biases are adjusted using an optimization algorithm to minimize the loss and improve the network's performance.

In summary, forward propagation passes input data through the network to generate predictions, while backward propagation computes gradients of the loss function and uses them to update the network's parameters during training. Together, these processes form the basis of training feedforward neural networks, enabling the network to learn from data and improve its predictive accuracy.

# Advantages and Disadvantages of Neural Networks

![](images/ufig9_8.jpg)

Neural networks are a very powerful machine learning algorithm. This method has been used in many areas and plays a vital role in the research and development of artificial intelligence. Nonetheless, neural networks are not perfect and still have challenges. It is important for us to understand the advantages and disadvantages of this method so that we can decide when it is the right time to use neural networks for our data mining projects.

332. **Advantages of Neural Networks**

*   **Nonlinear**: Neural networks can capture well nonlinear relationships in data, which makes this method well-suited for complex problems where traditional linear models might fail.
*   **Adaptive learning**: They can learn and adapt to new data in real time. Thus, they are quite effective for modeling dynamic environments where data are constantly changing.
*   **Unlimited information**: This method is not limited to input data since they use many hidden layers to create connections between layers. In the training process, more information is created to produce a good model.
*   **Parallel processing**: Neural networks can process multiple inputs at the same time. Hence, they can be used for tasks requiring high efficiency, such as image recognition and natural language processing.
*   **Fault tolerance**: This method is resilient to noise and errors in data. The network can still perform well even when some data are missing or corrupted because it stores information on the network instead of the database.
*   **Variable extraction**: Relevant variables can be automatically extracted from raw data, eliminating the need for manual variable selection.

**Disadvantages of Neural Networks**

*   **Black box**: A neural network is often considered a "black box" because it can be difficult to understand how the model works and how variables are correlated. In other words, we feed the input data to the model, and it predicts the values of output variables. But we do not really understand what is going on in the black box. This lack of interpretability can make the method less suitable for certain applications where transparency is required.
*   **Overfitting**: Neural networks can be prone to overfitting, especially when we use a very large amount of data. It means they perform well on the training data but not on new, unseen data. In other words, the model is not generalizable.
*   **Data requirements**: This method requires large amounts of labeled data to train effectively, which can be a significant bottleneck in some applications.
*   **Computationally intensive**: The training process can be computationally intensive, requiring high computing power and longer training time.
*   **Hyperparameter configuration**: Setting hyperparameters for a neural network can be challenging and must be done carefully to achieve optimal performance. Since there are no straightforward rules for determining the right configurations for the network architecture, the modeling process requires experimentation to achieve optimal performance.

Despite those disadvantages, neural networks are still a powerful machine learning method, and their applications are growing rapidly, especially deep learning methods. By understanding the strengths and weaknesses, we can have a good strategy to use this method for our research. Again, the purpose of this book is to provide a simple introduction and guidelines for implementing neural networks, a complex machine learning algorithm. So, we will not go deeply into the complex methods in neural network modeling.

# Basic Concepts of Neural Networks

![](images/ufig9_9.jpg)

As mentioned earlier, neural networks are a complex machine learning method. Even when focusing on the simplest forms, it can still be challenging to fully understand how the model operates. The following basic concepts form the foundation of neural networks and will help you grasp the architecture of a neural network and its training process (Table 9.2).

## Table 9.2 Basic Concepts of Neural Networks

| Terms | Description |
|---|---|
