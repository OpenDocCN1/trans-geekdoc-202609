# ### 5.3.2.1  Input

The image patches feed the placeholder named **“x”** in the TensorFlow model. The first dimension of **“x”** might have any number of components. This dimension is usually employed for the batch size, and isn’t fixed to enable the use of different batch sizes. For instance, assuming we want to train our model with a batch of 10 samples, we will feed the model a multidimensional array of size 10 × 16 × 16 × 4 in the placeholder **“x”** of size # × 16 × 16 × 4.

# ### 5.3.2.2  Layers

**“x”** is then processed by a succession of 2D-Convolution/Activation function (Rectified linear unit)/Pooling layers. After the last activation function, the features are processed by a fully connected layer of 8 neurons (one for each predicted class).

# ### 5.3.2.3  Estimated class

The estimated class is the index of the neuron (from the last neuron layer) that output the maximum value. This is performed in processing the outputs of the last fully connected layer with the *Argmax* operator, which is named **“prediction”** in the graph.

# ### 5.3.2.4  Loss function

The goal of the training is to minimize the cross entropy between the data distribution (real labels) and the model distribution (estimated labels). We use the cross entropy of the softmax function of the 6 neurons as the loss function. Basically, this function will measure the probability error in the discrete classification task in which the classes are mutually exclusive (each entry is in exactly one class). For this, the model implements an operation of TensorFlow known as *softmax cross entropy with logits*. This function first computes the *softmax* function of the 6-neuron outputs. The softmax function normalizes the outputs, such as their sum is equal to 1 and can be used to represent a categorical distribution, i.e, a probability distribution over *n* different possible outcomes (Equation 5.1). The Shannon cross entropy between true labels and probability-like values from the softmax is then computed (Equation 5.2), and considered as the loss function of the deep net.

$$\sigma(z)_i = \frac{e^{z_i}}{\sum_{k=1}^{n} e^{z_k}} \tag{5.1}$$

$$H(p,q) = -\sum_x p(x)\log(q(x)) \tag{5.2}$$