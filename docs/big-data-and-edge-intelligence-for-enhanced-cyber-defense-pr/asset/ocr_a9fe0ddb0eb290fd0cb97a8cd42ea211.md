# Big Data and Edge Intelligence for Enhanced Cyber Defense

field of digital forensics. DL models can be implemented to the network edge using EdgeAI, enabling real-time analysis and decision-making closer to the source of data collection.

CNNs are well-suited to evaluating and extracting features from visual and spatial data, making them useful in applications like image and video analysis in forensics. They can recognize objects, faces, text, and other visually important aspects in digital media, assisting in the identification of key evidence. RNNs, on the other hand, are well-suited to assessing sequential and temporal data, making them useful for tasks such as analysing user behaviour, network connections, and communication patterns.

Let's consider a DL architecture with multiple layers, where each layer consists of neurons. We'll focus on a single neuron in the last layer, denoted as neuron j. We want to minimize the difference between the predicted output (ŷ) and the true output (y) using an objective function, such as mean squared error (MSE).

In Forward Pass, Input: x = [x₁, x₂, ..., x_ⱼ] (input features)
Weighted sum for neuron j (3.14):

```
$z_j = w_j \cdot x + b_j$$
```

where w_j is the weight vector and b is the bias term.
Activation function (ReLU) (3.15):

```
$a_j = \max(0, z_j) = \max(0, w_j \cdot x + b_j)$
```

Output of the neural network is (3.16):

```
$(\hat{y}) : \\hat{y} = a_j$$
```

For objective function, MSE is (3.17):

```
$E = \frac{1}{2} * (\hat{y} - y)^2$$
```

where \hat{y} is the predicted output and y is the true output.
For Backpropagation, let's calculate the gradient of the objective function (3.18) with respect to the output layer

```
$\frac{\partial E}{\partial \hat{y}} = \hat{y} - y$$
```

Calculate the gradient of the ReLU activation function (3.19) as follows:

```
$$\frac{\partial a_j}{\partial z_j} = 1 \text{ if } z_j > 0, 0 \text{ otherwise}$$$
```