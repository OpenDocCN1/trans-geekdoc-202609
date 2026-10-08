# # Hands-on exercise – building and training a PyTorch model

In this hands-on exercise, you will learn how to install the PyTorch library in your local machine and train a simple deep learning model using PyTorch. Launch a Jupyter notebook that you have previously installed on your machine. If you don't remember how to do this, visit the Hands-on lab section of Chapter 3, Machine Learning Algorithms. Now, let's get started:

+   1. Create a new folder pytorch-lab in your Jupyter notebook environment and create a new notebook file called pytorch-lab.ipynb. Run the following command in a cell to install PyTorch and the torchvision package. torchvision contains a set of computer vision models and datasets. We will use the pre-built MNIST dataset in the torchvision package for this exercise:

```
```python
pip install torch
pip install torchvision
```
```

+   2. The following sample code shows the previously mentioned components. Be sure to run each code block in a separate Jupyter notebook cell for easy readability.

First, we must import the necessary library packages and load the MNIST dataset from the torchvision dataset class:

```
```python
import numpy as np
import matplotlib.pyplot as plt
import torch
from torchvision import datasets, transforms
from torch import nn, optim
```
```

```
```python
transform = transforms.Compose([transforms.ToTensor(),
transforms.Normalize((0.5,), (0.5, 0.5,))])
trainset = datasets.MNIST('pytorch_data/train/',
download=True, train=True, transform=transform)
valset = datasets.MNIST('pytorch_data/test/',
download=True, train=False, transform=transform)
trainloader = torch.utils.data.DataLoader(trainset,
batch_size=64, shuffle=True)
```
```