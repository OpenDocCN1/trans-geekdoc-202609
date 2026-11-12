
```
from keras.preprocessing.image import ImageDataGenerator, array_to_img, img_to_array, load_img
datagen = ImageDataGenerator(
    rotation_range=40,
    width_shift_range=0.2,
    height_shift_range=0.2,
    shear_range=0.2,
    zoom_range=0.2,
    horizontal_flip=True,
    fill_mode='nearest')
```

Figure 5.18 Python code for data augmentation.

models, some basic representations are encoded in the lower level layers of the network and later these basic layers are used by the higher level layers to generate more abstract concepts. This hierarchical learning makes the CNNs as end-to-end learners eliminating the need for extracting the hand-designed features. For a given image, raw pixel intensities are fed into the CNNs as inputs to extract the features using a series of hidden layers. As the feature extraction is carried out in a hierarchical fashion (the output of each layer in the network is used as the input of the next layer), only simple features such as edges are extracted in the lower level layers which are then used in the next layers to determine intermediate features such as corners and contours. These corners and contours are combined to form the object parts in the higher-level layers. The final layer as the output layer is utilized for classification and achieving the label of the output class.

One of the advantages of the CNNs over the traditional machine learning-based approaches is that the feature extraction step is skipped in these models focusing only on the process of training the model. Another main advantage is the outstanding performance accuracy achieved by the CNNs due to the emergence of highly optimized GPUs, fast computers, and large labeled datasets. Nowadays, researchers are able to design the deeper neural networks with huge number of training data which results in higher classification accuracy whereas this behavior cannot be accomplished using the traditional machine learning algorithms. As compared in Figure 5.19 [30], the performance of the machine learning algorithms plateau at a specific amount of the data and increasing the size of the dataset has no influence on their performance while the performance of deep learning models follows an increasing trend.

## 5.6.3 Neural Networks

Before discussing details of the CNNs, it is essential to first know the basics of the neural networks (NNs) which are the fundamental blocks of the deep learning systems. Artificial NN architectures have been inspired by our real-life biological NNs to mimic our brain capabilities in recognizing complex patterns. A simple example of a NN architecture is illustrated in Figure 5.20. In this architecture, a simple computation is carried out in each node and the output of each computation as a signal is carried by each connection from one node to another with specified weights. Some of these weights amplify the signals as they play an important role in the final classification and others diminish the strength of the signals as they have less importance for final classification. Here, X1, X2, and X3 are the inputs as a single row from the design matrix. The value 1 is fed into the model as bias in the design matrix. Generally,

![](img/bffdb4a72252285ac92f0fad78a7f104_103_0.png)

Figure 5.19 Comparison between the performance of the deep learning-based algorithms and the traditional machine learning-based methods showing that the accuracy of the deep learning algorithms are increased by enhancing the amount of the training data.

these inputs can be the vectors of the features such as color histograms, HOG, LBP, etc., but in the deep learning models, the inputs are usually the raw pixel intensities of the images. The overall process of the system can be formulated as $f(net)$ where $net = \sum_{i=1}^n W_i X_i$ (i.e. weighted sum of the inputs) on which an activation function of $f$ is applied to determine whether the neuron fires or not.

![](img/bffdb4a72252285ac92f0fad78a7f104_103_1.png)

Figure 5.20 A simple neural network architecture with three inputs of X and one hidden layer with weights of W to compute the output class label. The weighted sum of the inputs are passed an activation function through which it is determined that whether the neuron fires or not.

Activation Functions. There are several popular activation functions broadly applied on deep learning models, six of which are illustrated in Figure 5.21. "Step function" is the most simple activation function as threshold function used by the Perceptron algorithm. It is defined as follows:

```
f(t) = \begin{cases} 1 & \text{if } net > 0 \\ 0 & \text{otherwise} \end{cases} \quad (5.4)
```

![](img/bffdb4a72252285ac92f0fad78a7f104_104_0.png)

Figure 5.21 Six activation functions commonly used in deep learning architectures [8].

Although this function is easy to use, it suffers from challenges when the gradient descent is applied in training the network as the step function is not differentiable. Sigmoid is another common activation function which follows the equation:

$$t = \sum_{i=1}^{n} W_i X_i \qquad s(t) = \frac{1}{1 + e^{-t}} \quad (5.5)$$

As the Sigmoid function is continuous, differentiable, and symmetric, it performs better than the step function for deep learning algorithms. However, it also suffers from some limitations: (i) Its outputs are not zero centered and (ii) the gradient will be degraded by saturated neurons due to extremely small delta for gradient. Having a similar shape to the Sigmoid, the hyperbolic tangent (tanh) is one of the extensively used activation functions as follows:

$$f(z) = tanh(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}} \quad (5.6)$$

In contrary to Sigmoid, it is zero centered, but still the saturated neurons kill the gradients. The better choice rather than the previously mentioned functions is the rectified linear unit (ReLU) as:

$$f(x) = max(0, x) \quad (5.7)$$

Based on its shape, it is also called "ramp function." It is zero for negative values and increases linearly for positive values. It not only outperforms the activation functions of Sigmoid and tanh, but also is computationally efficient and not saturable. However, the problem arises only when the input value is zero because the gradient cannot be taken. To overcome this limitation, another form of ReLUs is used, namely Leaky ReLUs [28], in which the small, non-zero gradient is allowed when the unit is not active:

\( f(net) = \begin{cases} net & \text{if } net >= 0 \\ \alpha \times net & \text{otherwise} \end{cases} \) (5.8)

The final activation function is the exponential linear units (ELUs) introduced [16] as follows:

\( f(net) = \begin{cases} net & \text{if } net >= 0 \\ \alpha \times (exp(net) - 1) & \text{otherwise} \end{cases} \) (5.9)

\(\alpha\) is a constant whose typical value is 1.

## 5.6.4 CNN-Based Classifiers

The introduced feedforward neural networks can be used in image processing. However, they are not efficient enough due to the many connections made between all nodes in one layer and those in the next layer. In this case, the efficiency can be improved by carefully pruning these connections according to the structure of the images which results in a better performance. A very common type of NN is CNN in which the spatial relationships in data are preserved through very few connections between layers. A typical CNN architecture applied in the field of skin disease classification and recognition is illustrated in Figure 5.22. CNNs are composed of different layers of Convolutional (CONV), Activation, Pooling (POOL), Fully connected (FC), Batch normalization (BN), and Dropout (DO), which are explained in details in the following paragraphs.

![](img/bffdb4a72252285ac92f0fad78a7f104_105_0.png)

Figure 5.22 A typical CNN model for skin disease classification and recognition [27].

### Convolutional Layers.

The fundamental building layer of the CNNs is the CONV layer including a set of K learnable filters as "kernels" (nearly always as square matrices). These small filters extend throughout the full depth of the volume. As illustrated in Figure 5.23, the input of a CONV layer passes three main steps.
