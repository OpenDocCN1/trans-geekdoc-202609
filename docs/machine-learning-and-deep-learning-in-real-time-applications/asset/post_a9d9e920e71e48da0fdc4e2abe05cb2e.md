
Deep Learning With PyTorch

```
(0, 0, 0, 0),
(0, 0, 0, 0))))
```

## torch.ones(dimension)

This creates a tensor populated with ones of a given dimension.

Example:

```python
>>> torch.ones(2, 3)
tensor([[1., 1., 1.],
        [1., 1., 1.]])
```

## torch.rand(dimension)

This creates a tensor populated with random digits of given dimension.

Example:

```python
>>> torch.rand(2, 3)
tensor([[0.3273, 0.1834, 0.5345],
        [0.2946, 0.4208, 0.7635]])
```

The default data type of tensors is torch.float32, which is generally used in deep learning to store information without loss. To change the default data type, an extra parameter is passed as `dtype=<data_type>`.

Example:

```python
>>> torch.rand(2,3, dtype=torch.float64)
tensor([[0.3187, 0.7623, 0.3013],
        [0.1027, 0.4982, 0.1452]], dtype=torch.float64)
```

## <tensor>.size()

This is used to get the dimension of a declared tensor.

Example:

```python
>>> x = torch.rand(2, 3)
>>> x.size()
torch.Size([2, 3])
```

## Integration with NumPy

Conversion between NumPy and PyTorch tensors is shown below:

## Converting Torch Tensor to NumPy ndarray

```python
>>> x = torch.rand(2, 3)
>>> x
tensor([[0.2778, 0.0672, 0.2158],
        [0.4721, 0.5770, 0.4593]])
>>> y = x.numpy()
>>> y
array([[0.27776885, 0.06151792, 0.21575862],
       [0.47211725, 0.57698375, 0.45925605]], dtype=float32)
```

## Converting NumPy ndarray to Torch Tensor

```python
>>> import torch
>>> import numpy as np
>>> x = np.random.rand(2, 3)
>>> x
array([[0.52806884, 0.18309049, 0.54894101],
       [0.55006161, 0.09386833, 0.71446432]])
>>> y = torch.from_numpy(x)
>>> y
tensor([[0.5281, 0.1831, 0.5489],
        [0.5501, 0.0984, 0.7145]], dtype=torch.float64)
```

## Shifting Tensor from CPU to GPU

```python
>>> import torch
>>> if torch.cuda.is_available():#checks if cuda enabled gpu is
... device = torch.device('cuda')
>>> x = torch.rand(2, 3, device='cuda')
>>> x
tensor([[0.9473, 0.4240, 0.4360],
        [0.5120, 0.0520, 0.4360]]), device='cuda:0') #directly initializing tensor in GPU
>>> y = torch.rand(2, 3)
>>> y = y.to(device) #shifting tensor from CPU to GPU
>>> y
tensor([[0.9082, 0.8258, 0.5843],
        [0.8274, 0.1618, 0.6526]], device='cuda:0')
```

## Computational Graphs and Autograd Package

The Autograd package in PyTorch is the backbone of the whole framework. It is responsible for calculating derivatives of tensors automatically using the chain rule. Autograd does this by creating computational graphs under the hood. These graphs are created on run time and can be different on each iteration depending on how the code is run.

To understand Autograd, first a neural network is discussed and later it is discussed how to train it.

## Neural Network

A neural network is a type of mathematical algorithm that learns the patterns in data and can predict the output when shown new data on its own. The brain loosely inspired the design of a neural network.

Figure 1. A simple neural network (Fadja et al., 2018)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_88_0.png)

Each circle in figure 1 is called a node or neuron. The arrows connecting nodes of one layer to the nodes of another layer are called weights. These weights are the parameters that the neural network learns to predict the output.

A neural network has three types of layers: input, hidden, and output. The input layer takes in data. The output layer gives the predicted output. The number of nodes in the output layer determines the number of possible outcomes. The hidden layer is the intermediary layer that learns the complex functions. There can be several hidden layers depending on the size of the data.

In Figure 2, the value of a node is determined by the sum of values of previous nodes multiplied by its corresponding weight.

```
z = Σwⱼ * xj + b; a=f(z).
```

z is passed through a non-linearity function f, also known as activation function, such as Relu, sigmoid, or softmax, so that the neural network can learn complex functions and not just linear functions.

Figure 2. A single node of a neural network (CS231n)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_89_0.png)

Put to simply, a single node in the neural network acts as a simple logistic regression unit. Put together several of these units and the result is neural learning more complex functions. Hence, more number of nodes and layers result in.
