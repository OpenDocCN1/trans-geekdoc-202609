
$$\\begin{array}{l} {g(\\mathbf{x}) = \\sum\\limits\\_{n = 0}^{N - 1}\\mathbf{x}\\lbrack n\\rbrack\\mathbf{w}\\lbrack n\\rbrack} \\\\ \\end{array}$$  

(2.1)

$$\\begin{array}{l} {y = \\sigma\\left( g(\\mathbf{x}) + b \\right)} \\\\ \\end{array}$$  

(2.2)

The neurons are organized in layers. In feedforward networks, each neuron of layer `l` receives inputs from layer `l - 1` and sends its activation to the neurons of layer `l + 1`. The number of stacked layers indicates the depth. A neural network is typically called a `Deep Neural Network` (`DNN`) \[[13](#refbib.xhtml#refbib13)\] if there are more than three hidden layers.

### 2.1.1 Layers and Operations

The layers are categorized based on the types of connections. The following list contains the most common types of layers in DNNs.

*   **Fully-Connected (FC) layers:** each neuron of layer `l` receives as inputs all the activations of layer `l - 1` (see [Figure 2.2a](#chapter2.xhtml#fig2_2)). Since all the connections are present, the number of parameters of an FC layer is potentially huge. However, in practice, it is not always necessary for an output neuron to receive information from all the input neurons. For this reason, the convolutional layers have been designed.

*   **Convolutional (Conv) layers:** the neurons are organized in a 2D grid, i.e., a `feature map`, and every neuron of layer `l` does not receive all the activations of the layer `l - 1`, but it is connected to a small receptive field \[[118](#refbib.xhtml#refbib118)\] (see [Figure 2.2b](#chapter2.xhtml#fig2_2)). The receptive field size, which corresponds to the weight matrix, is commonly called `kernel size` and the stride parameter `S` defines the distance between adjacent receptive fields. In Conv layers with shared weights, all the neurons of layer `l` have the same matrix of weights and detect the same feature in different locations of layer `l - 1`. To detect multiple features, a Conv layer has multiple channels, i.e., there are multiple feature maps.

*   **Pooling layers:** similar to Conv layers, Pooling layers have receptive fields. For the group of neurons in each receptive field, their output is a single value that contains a statistic of the group, e.g., the maximum or the average value. An example of a MaxPooling layer is shown in [Figure 2.2c](#chapter2.xhtml#fig2_2). The stride parameter is typically set equal to the dimension of the receptive field to have non-overlapping windows. Pooling layers reduce the number of activations of a layer and consequently decrease the memory requirements and the number of computations while achieving invariance to small local translations. Pooling layers down-sample the Conv layer outputs, whose values heavily depend on the position of the input. Hence, Pooling layers make DNNs more robust to minor input variations.

*   **Normalization layers:** the input activations are usually preprocessed to have a normal distribution, i.e., zero mean and unit variance. The normalization is beneficial since it keeps different inputs within the same range of values to ease the computations and avoids saturating the non-linear activation functions. Typically, Normalization layers are inserted between Conv and FC layers. Moreover, the activations’ normalization speeds up the training since the layers do not need to adapt to different distributions at each training step. The most common type of normalization is the `Batch Normalization` \[[94](#refbib.xhtml#refbib94)\].

*   **Activation functions:** without a non-linear activation function, the DNN would be a simple cascade of linear algebra operations. To solve complex non-linear problems, different non-linear functions are applied to the weighted sum of a neuron. In the first developments of DNNs, the Sigmoid and Hyperbolic Tangent functions were adopted, but their usage was reduced over the years due to their computational complexity. The most common function is the `Rectified Linear Unit (ReLU)`, which forces the activations to be greater than or equal to zero. Its newer variants, such as Leaky-ReLU and Exponential Linear Unit (ELU), aim at introducing a negative slope for negative values. Moreover, the `Softmax` function is typically used in output layers of DNNs for classification since it bounds the values in the range (0, 1) to represent the probabilities associated with the output classes.

![Figure 2.2: (a) Example of an FC layer. (b) Example of a Conv layer. (c) Example of a MaxPooling layer.](images/fig2_2.jpg)

[Figure 2.2:](#chapter2.xhtml#b2fig2_2) **(a)** Example of an FC layer. **(b)** Example of a Conv layer. **(c)** Example of a MaxPooling layer.

### 2.1.2 Training and Inference

DNNs learn how to perform a specific task by properly determining its parameters (weights and biases), which are continuously updated during the `training` phase. Afterward, during the `inference` phase, the parameters are kept constant, and the DNN makes the prediction. The dataset is typically split into training, validation, and testing sets. The training set is used for updating the parameters, while the validation set is used to fine-tune the hyperparameters. The inference is conducted on the testing set, which contains previously unseen data. There are different approaches for training DNNs:

*   **Supervised learning:** A set of labeled input-output pairs is required. In supervised learning, the DNNs’ parameters are updated to minimize the differences between the output labels and the DNN predictions. This approach is widely used nowadays in many applications due to its good performance. A common supervised learning algorithm for training DNNs is the `gradient backpropagation`. The DNN's outputs are compared with the labels, and a `loss` score is calculated with a `loss function`, such as the Euclidean distance or the Mean Squared Error (MSE). The parameters are updated accordingly by an amount proportional to the partial derivative (i.e., the gradient) of the loss w.r.t. the parameters. The gradients are computed through the backpropagation algorithm, which is based on the `chain rule` of calculus. The actual update is done with an `optimization algorithm`, such as the gradient descent or the Adam \[[110](#refbib.xhtml#refbib110)\]. A common problem when training DNNs is `overfitting`, i.e., high performance on the train set and low performance on the test set. The techniques used to overcome this issue include L1 and L2 regularization \[[188](#refbib.xhtml#refbib188)\], which add a regularizing term to the loss function, and dropout \[[256](#refbib.xhtml#refbib256)\], which randomly removes some neurons in the DNN.

*   **Unsupervised learning:** When only non-labeled data are available, the goal is to find common patterns or data grouping without any guidance. The most popular unsupervised learning approaches are based on clustering, a data mining technique that groups unlabeled data based on attribute similarities or differences. Common DNNs that apply unsupervised learning are autoencoders and Generative Adversarial Networks (GANs).

*   **Reinforcement learning:** Reinforcement learning is the third primary type of learning. Similar to unsupervised learning, it does not need labeled data. It is based on autonomous agents who decide to travel across states in a given environment. The agent gets a reward in case of success but will not receive any reward in case of failure. Hence, the agent learns how to maximize the reward from the environment.

### 2.1.3 DNN Models
