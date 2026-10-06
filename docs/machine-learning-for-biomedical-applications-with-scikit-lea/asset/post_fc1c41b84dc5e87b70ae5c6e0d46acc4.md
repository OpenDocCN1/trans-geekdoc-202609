
## 9.3.4 Limitations of the single-layer perceptron

The key limitation of the models presented in this chapter is that they consist of a single linear layer. This means, that these models are inherently linear and therefore might not adapt well to complex real-world problems. In Chap. 10 we will show how this limitation can be overcome by building networks of neurons organized in multiple layers, which are interleaved with nonlinear activation functions. Such deep nonlinear models are extremely flexible and can adapt to any real-world situation. This flexibility is one of the key factors in the success of the modern deep learning.

## 9.3.5 Exercises

- 1. What is the main difference between a single neuron and a single-layer perceptron?
- 2. Describe the activation function and the loss that we use to create multi-label classification.
- 3. Load dataset heart_failure_data_complete.csv.³ Create and train a multi-label single-layer perceptron classifier in PyTorch, to diagnose no, moderate, or severe heart failure from EF and QRS. Calculate the accuracy and plot the classification result on the training set. Follow the code from Sect. 9.3.3.

> ² The data, skeleton code and solution are available from github.com/MachineLearningBiomedicalApplications/notebooks.

## CHAPTER 10

## Fully connected neural networks

The flexibility of the neural networks comes from combining many artificial neurons into a single machine-learning model organized in multiple layers. In fact, neural-works are universal approximators, and can learn a good approximation of a function of any complexity, given a sufficient number of learnable parameters.

In this chapter we will show how we can build fully connected neural networks. We will introduce the architecture of fully connected neural networks in Sect. 10.1, 10.2 we will describe how neural networks are trained using back-propagation [40]. In the final section 10.3 we will show a complete deep learning solution for prediction of age from the brain connectivity in newborn babies.

## 10.1. Fully connected network architecture

In Chap. 9 we described in detail an artificial neuron (Sect. 9.1) and how multiple neurons can be organized in a single linear layer to produce multiple outputs, resulting in a single-layer perceptron model (Sect. 9.3). Multiple output features allow us to stack several layers of neurons, resulting in a multilayer perceptron model, as illustrated in Fig. 10.1. If we add nonlinear activation functions between the layers, we will be able to create flexible nonlinear models and overcome the in-built linearity of single-layer perceptrons. If the resulting network has at least three layers, we obtain a fully connected deep neural network.

### 10.1.1 Multilayer perceptron

A major limitation of the single-layer perceptron is that it is a linear model, and therefore not suitable for complex nonlinear machine-learning problems. In Fig. 10.2, we can see the single-layer perceptron fails to separate co-centric circles, which requires a highly nonlinear boundary. We can obtain more complex models by stacking multiple linear layers, which means that the output of the previous layer is the input of the following-layer. The resulting multilayer perceptron is shown in Fig. 10.1. Importantly, we can obtain nonlinear models only if we interleave the linear layers with nonlinear activation functions. This approach allows us to separate the co-centric circles, as seen in Fig. 10.2, middle and right.

### 10.1.2 Stacking layers of neurons

Single-layer perceptron models can be stacked one after another, to produce a more complex multilayer perceptron model. We will call the outputs of the layer l1-active tions, and denote them $a_k^{(l)}$. The learnable weights of the layer $l$ will be denoted $w_{jk}^{(l)}$. The mathematical equations for the layer $l$ with $D_l$ outputs can be derived directly from the equations for the single-layer perceptron (Eqs. 9.9) and (9.10)) as follows:

```
$$z_k^{(l)} = \sum_{j=1}^{D_{l-1}} w_{jk}^{(l)} a_j^{(l-1)} \quad (10.1)$$
```

## Fully connected neural networks

$$a_k^{(l)} = fi(z_k^{(l)}), \quad k = 1, \dots, D_l.$$
(10.2)

Note that the layer $l$ needs to have the same number of outputs $D_{l-1}$ as the number of outputs of the layer $l-1$. Inputs of the first layer $l=1$ are the inputs $x_i$. The outputs of the last layer will depend on the type of the neural network model. If it is a regressor, we will have an identity activation, and the outputs will be the predicted target values $\hat{y}_k$. If it is a classifier, we will have a sigmoid or softmax activation, and the outputs will be predicted probabilities $\hat{p}_k$ for each class.

### 10.1.3 Activation functions

We have already introduced several activation functions (identity, Heaviside, sigmoid and softmax)—see Fig.9.2. These functions are most useful after the final linear layer of the neural network to design regressors and classifiers.

The most common activation function placed between the successive layers of the neural network is a Rectified Linear Unit (ReLU), shown in Fig. 10.3. Because this is a piece-wise linear function, the resulting function is represented by the whole neural network will also be piece-wise linear, as shown in Fig. 10.2. While this function is very simple, combining multiple layers of neurons modeling of very complex piece-wise linear functions can approximate a function of any complexity, given large enough number of neurons.

The popularity of ReLU is partly due to its efficient computation. However, it can introduce a vanishing gradient problem, because once the value $z_i^l$ turns negative, the gradient will become zero and the neuron will stop being active. This problem has been addressed by introducing a Leaky ReLU (Fig. 10.3, middle), which has a small gradient for the negative values and neurons will not die.

An alternative activation function is Tanh (Fig. 10.3, right), which produces nonlinear functions (see Fig. 10.2, right). Unlike Leaky ReLU, the Tanh activation also suffers from vanishing gradients for large negative and positive values.

img/d219b4c20ff50f4b97845dec7a9acecb_232_0.png)

**Figure 10.1** An example of a fully connected deep neural network with three layers. Yellow circles correspond to the individual artificial neurons (Fig. 9.1)

![](img/d219b4c20ff50f4b97845dec7a9acecb_232_1.png)

**Figure 10.2** Left: Single-layer perceptron failed because it is only able to find a linear decision boundary. Middle: Multilayer perceptron with two layers and a nonlinear activation function (ReLU) successfully separated the classes with a nonlinear boundary. Right: Multilayer perceptron with two layers and Tanh activation also succeeded. Note that ReLU results in a piece-wise linear boundary, while Tanh produces a smooth boundary.

img/d219b4c20ff50f4b97845dec7a9acecb_233_0.png

## 10.1.4 Multilayer perceptron architecture in PyTorch

We will now show how we can create the multi-layer architecture in PyTorch. To separate the circles in Fig. 10.1, we will create a multilayer perceptron classifier with two layers, implemented by the Classifier. The first layer has two inputs, defined by the dimension of the input data, and six outputs. The second layer has six inputs, which are the outputs of the first layer, and one output because this is a binary classifier. Between the two layers, we place a nonlinear activation function ReLU. The output of the second layer is passed through sigmoid activation function to enable binary classification. Finally, we create an instance of the network:

```
import torch.nn as nn
class MLPClassifier(nn.Module):
    def __init__(self, classifier):
        super(MLPClassifier, self).__init__()
        self.layer1 = nn.Linear(2, 6)
        self.relu = nn.ReLU()
        self.layer2 = nn.Linear(6, 1)
        self.sigmoid = nn.Sigmoid()

    def forward(self, x):
        x = self.layer1(x)
        x = self.relu(x)
        x = self.layer2(x)
        x = self.sigmoid(x)
        return x
```

```
net = MLPClassifier()
```

## 10.2. Training neural networks

### 10.2.1 Training a multilayer perceptron

To train the multilayer perceptron and also deep neural networks in general, we need to evaluate the gradients with respect to learnable weights $w_l$ in all layers so that we update them at each iteration or epoch, as we have done with single-layer perceptron (Eq. (9.13)). We do that by calculating the gradients of the weights iteratively, starting from the final layer $M$ and working our way towards the lower layers. This is called backpropagation [40]. In the practice, in Sect. 10.2.3, the backpropagation is performed in PyTorch automatically by Autograd (see Sect. 9.2.3).
