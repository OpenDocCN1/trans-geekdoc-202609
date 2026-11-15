Fig. 1.26 Perceptron neural network

![](bbox=[0.478, 0.081, 0.881, 0.203])

Fig. 1.27 Feedforward neural network

![](bbox=[0.39, 0.234, 0.881, 0.342])

# 1.6.2 Feedforward Neural Network

Feed Forward Neural Networks are also considered to be old members of the neural network family, and the approach related to them originates from the 50s. The performance of this algorithm is that all nodes are fully connected, the activation flows from the input layer to the output, without having a backward loop, and there is also a layer (hidden layer) between the input and output. Most of the time, this type of neural networks are trained using Backpropagation method. Feedforward Neural Network shown in Fig. 1.27.

# 1.6.3 Radial Basis Neural Network

Radial Basis Networks are actually Feedforward (FF) neural networks that use the Radial Basis Function, instead of the Logistic Function, as the activation function. The question that arises at this point is what is the difference between the basic radial neural network and the feedforward neural network?
The logistic function maps some arbitrary value to a 0–1 interval to answer a “yes or no” question (binary question). These types of neural networks are suitable for Classification and Decision Making Systems, but they perform poorly for continuous values. Meanwhile, basic radial functions answer the question, “How far are we from the goal?” And this makes these neural networks suitable for function estimation and machine control. In short, it should be said that basic radial neural networks are actually a kind of feedforward neural networks with different activation functions and characteristics. Radial Basis Neural Network shown in Fig. 1.28.