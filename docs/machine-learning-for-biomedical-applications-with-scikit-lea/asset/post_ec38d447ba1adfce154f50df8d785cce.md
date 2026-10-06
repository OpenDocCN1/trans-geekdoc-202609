
The partial derivative of the sum-of-squared-error loss with respect to the weights, therefore is

```
$$\frac{\partial L(\mathbf{w})}{\partial w_j} = -\sum_{i=0}^{N} (y_i - \hat{y}_i)x_{ij}. \quad (9.7)$$
```

We have already derived a similar equation in a matrix form in Sect. 3.2.4.

# Training logistic regression

Logistic regression is trained by minimizing the cross entropy loss

```
$L_i = -y_i \log(\hat{p}_i) - (1 - y_i) \log(1 - \hat{p}_i).
```

and the partial derivative

```
$$\frac{\partial L}{\partial \hat{p}_i} = \frac{y_i}{\hat{p}_i} + \frac{1 - y_i}{1 - \hat{p}_i} = \frac{-(y_i - \hat{p}_i)}{\hat{p}_i(1 - \hat{p}_i)}$
```

The activation function is sigmoid $f(z) = \sigma(z)$ (Fig. 9.2), with the derivative

```
$$\frac{\partial \sigma}{\partial z_i} = \sigma(z_i)(1 - \sigma(z_i)) = \hat{p}_i(1 - \hat{p}_i).$$
```

The partial derivative of the cross entropy loss with respect to the weights, therefore is

```
$$\frac{\partial L(\mathbf{w})}{\partial w_j} = -\sum_{i=0}^{N} (y_i - \hat{p}_i)x_{ij}. \quad (9.8)$$
```

Note the similarity to Eq. (9.7).

From Eqs. (9.7) and (9.8), it becomes obvious why we need the forward pass (Eq. (9.5)) to train the artificial neuron: We need the latest predicted outputs to calculate the derivatives of the loss and update the weights during the backward pass (Eq. (9.6)).

# 9.1.3 Exercises

- 1. Describe the following components of the artificial neuron:
    a. Inputs;
    b. Weights;
    c. Activation function;
    d. Output.
- 2. Which loss and activation functions can you use to create a single artificial neuron classifier and regressor?
- 3. Describe the main steps for training the artificial neuron.
- 4. Given an artificial neuron with the sum-of-squared-error loss and sigmoid activation function, calculate the following:
    - a. Given the feature vector $x_i = (x_{i1}, \dots, x_{Id})$, give the prediction $\hat{p}_i$.
    - b. Given the true label $y_i$, give the expression for the loss $L_i$ for this sample.
    - c. Calculate the derivative of the loss $L_i$ with respect to the weight $w_i$. Note that derivative of the sigmoid function is $\sigma'(z) = \sigma(z)(1 - \sigma(z))$.
    - d. Give the update equation for the weight $w_i$ of the artificial neural model.

# 9.2. Starting with Pytorch

In this section we will introduce the Pytorch environment [33] and implement our first neural network, consisting of a single artificial neuron.

# 9.2.1 Install Pytorch

Installing Pytorch is very simple. Assuming you have already installed your Python and Anaconda environments as recommended in Chap. 1, you now need to go to the Pytorch website
pytorch.org/get-started/locally/

The website will automatically detect your system and provide the command for installation that you need to copy to your command line window, which can be accessed for example through the application called Anaconda Prompt. Once installed Pytorch, you can import it in the Jupyter notebook, or another preferred Pytorch environment using command

```
import torch
```

By default Pytorch will run on the CPU, and this will be sufficient for the example code in this chapter. For more computational intensive deep learning problems, we usually need access to a GPU to speed up computations. To do that, we need to explicitly specify our data and models to the available CUDA device. You can check whether you have CUDA available on your computer by calling

```
print('Cuda available:', torch.cuda.is_available())
>>> CUDA available: True
```

# 9.2.2 Pytorch tensors

Pytorch tensors are multidimensional arrays that are used to store the data and the parameters (weights) of the deep learning models. They are very similar to NumPy arrays, but have some additional features, including the ability to run on a GPU, and features to enable automatic differentiation. We can create a random tensor of a particular shape by calling

```
import torch
tensor = torch.rand(2, 2)
print(tensor)
>>> tensor([[[0.9697, 0.8595],
[0.3722, 0.4119]],
[[0.1956, 0.0055],
[0.0683, 0.2933]]])
```

In comparison, the NumPy array can be created in very similar

```
import numpy as np
np_array = np.random.rand(2, 2)
print(np_array)
>>> [[[0.57826831, 0.2639664 ], [0.95591113, 0.67097702]],
[0.24742113, 0.62599913],
[0.46188619, 0.43755346]]]
```

We can access the elements of tensors through indexing just like the NumPy arrays:

```
tensor([0,0,0])
>>> tensor(0.9697),
```

print out the shape:

```
tensor.shape
>>> torch.Size([2, 2, 2]),
```

and easily convert NumPy arrays to tensors and the other way:

```
tensor2 = torch.from_numpy(np_array)
np_array2 = tensor.numpy()
```

A useful function to change the shape of the tensor, while not copying the data, is view:

```
tensor.view(2,4)
>>> tensor([[[0.1443, 0.7539, 0.1976, 0.9976]],
```

By default the tensors are on the CPU:

```
tensor.device
>>> device('cpu')
```

but unlike NumPy, PyTorch tensors can be sent to GPU:

```
tensor.to('cuda')
>>> device('cuda:0')
```

# 9.2.3 Autograd

An important feature of PyTorch is that it offers automatic differentiation to enable training. For tensors we want to learn, we can set the requires_grad attribute to True:

```
a = torch.tensor([1., 2.]], requires_grad=True)
```

When the function backward() is called on the root of the computational graph (loss), the functions stored in grad_fn will calculate the gradients by moving backward through the graph, as shown in the figure below.

Now we are ready to create our first neural network model. PyTorch offers the module torch.nn with functionality to create neural network models. Our first model will be a single-neuron linear regressor will be derived from the base class torch.nn.Module as follows

```python
import torch.nn as nn
class ANRegressor(nn.Module):
    def __init__(self):
        super(ANRegressor, self).__init__()
        self.layer = nn.Linear(1, 1)
    def forward(self, x):
        x = self.layer(x)
        return x
```

# 9.2.4 Creating models in PyTorch

# Regression in PyTorch

Now we are ready to create our first neural network model. PyTorch offers the module torch.nn with functionality to create neural network models. Our first model will be a single-neuron linear regressor with only one linear layer, which implements torch.nn.Linear(D, 1):

```
torch.nn.Linear(D, 1)
```

Note that this layer has D inputs and one output. We will now the univariate regression example of predicting the brain volume of the newborn depending on gestational age, introduced in Sect. 2.1.1. For this reason our model will have only one input feature D=1.
