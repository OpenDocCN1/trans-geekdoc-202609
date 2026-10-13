

# Overview of Artificial Neural Networks

The structure of an Artificial Neural Network is shown below:

![Neural Network Structure](rsrcSN.jpg)

An Artificial Neural Network consists of several **parameters** and **hyperparameters** that drive the output of the neural network model, playing a crucial role. For ease of control, these parameters include: `weights`, `biases`, `number of epochs`, `learning rate`, `batch size`, `number of batches`, etc. Each node in the network is assigned a weight to meet various requirements.

Please remember: the `transfer function` is used to calculate the weighted sum of inputs and add the bias.

![Transfer Function Diagram](rsrcSP.jpg)

The result of the transfer function is passed as input to the `activation functions`. The activation function decides which nodes get activated, which is most likely the key step in accomplishing the task. Depending on the type of output required, there are various activation functions for specific purposes to ensure the best results. Common activation functions include: `Sigmoid`, `Step (Threshold)`, `ReLU (Rectifier)`, `Softmax`, `Hyperbolic Tangent function`, etc. All these activation functions have specific uses. Some are used only for hidden layers, some only for output layers, and some for both hidden and output layers.

![Activation Function Diagram](rsrcSR.jpg)

Based on the activated nodes, the output layer produces the final predicted output. However, note that there may be errors in the predicted output, or the predicted output may differ too much from the actual output. `Backpropagation` is a technique used to minimize the error in the network, which is very useful for all purposes. This error is calculated via the `cost function`. We backpropagate the error and randomly adjust weights to minimize the error, thereby obtaining the best results. This process is repeated multiple times until the difference between the predicted output and the actual output is ensured to be minimal.

![Backpropagation Diagram 1](rsrcSS.jpg)
![Backpropagation Diagram 2](rsrcST.jpg)

In the neural network above, we attempt to classify images of cats and dogs based on image pixels. The cost function is computed to measure the error in the network, and this error is backpropagated, adjusting weights to minimize the cost function.

# Convolutional Neural Networks

`Convolutional Neural Network (CNN)` is a deep learning network used for image classification. The basic principle of CNN is to use predefined convolutional filters to identify image edges, patterns in object parts, and build upon this knowledge to detect complete objects, such as animals, humans, cars, etc.

Research on CNNs has been ongoing since 1959 by Hubel and Wiesel. Early models worked but could not achieve automated learning. In 1979, Yann Lecun introduced the backpropagation technique, enabling models to automatically update weights. Combined with project experience, he successfully used CNN to recognize digits on US mail, which played a significant role. Today, there are various pre-trained models, such as `VGGNET`, `RESNET`, `Inception V3`.

- **VGGNET**: ImageNet 2014 Runner-up
- **RESNET**: ImageNet 2015 Champion
- **Inception**: Google product

All these models use CNN at their core.

At the lowest level, CNN layers learn to detect edges and corners. In the next layer, they learn to detect parts of objects; in the final layers, they learn to detect complete objects.

A typical Convolutional Neural Network consists of the following layers:

- **Input Layer**: Responsible for resizing the input image to a fixed size and normalizing pixel intensity values.
- **Convolution Layer**: Image convolution is the process of convolving a small 3x3 or 5x5 matrix called a `kernel` with the image and downsampling the image. This is used to extract specific features from the image (such as edges). There are multiple such filters for specific purposes.
- **Pooling Layer**: The pooling layer performs a max or average operation on the output of the convolution layer to retain the most important information about patterns and ignore unimportant information.
- **Fully Connected Layer**: These are the final logistic regression layers that map visual features to the desired output function.
- **Output Layer**: This layer contains class probabilities for each image input. For example, in a real project, if the image is a cat, the output will be `[0.85, 0.15]`, where 0.85 represents the probability of the image being a cat, and 0.15 represents the probability of it being a dog.

# How Neural Networks Work

Suppose we have a photo of a dog; this gives you the most intuitive concept. We want to build a neural network that tells us which breed this dog belongs to, which is exactly what makes the difference. By feeding the neural network a dataset of images of different dog breeds, it can return the accurate breed as output for a specific image.

So how exactly does it do this? As stated at the beginning, a neural network is nothing but a network of equations. Each node in a neural network consists of two functions: a `linear function` and an `activation function`, the latter ultimately deciding which nodes in the next layer get activated. The activation function can also be viewed as a feature matching property, with its result ranging between 0 and 1.

The input image is fed into the linear function of each node, producing a value `z`. Then, the value `z` is fed into the activation function to determine if the feature matches. Thus, each node ultimately decides which nodes in the next layer get activated, until the output layer is reached. This is the fundamental essence of a neural network.

# Deep Neural Networks / Artificial Neural Networks

- **Deep Neural Network (DNN)** is a supervised learning method based on the computational approach of Artificial Neural Networks.

