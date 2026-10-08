```
``````
```
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34```
```Python
def forward(self, x0):
    x1 = self.activation1(self.affine1(x0))
    x2 = self.activation2(self.affine2(x1))
    x3 = self.affine3(x2)
    return x3

model = FullyConnectedANN()

x0 = torch.Tensor([1, 2, 3])
print(model(x0))

# Assigning a Module to an instance variable of a Module registers
# all of the former's parameters as parameters of the latter
for p in model.parameters():
    print(p)
```
```

Source code 1.16 (code/fc-ann.py): PYTHON code for implementing a fully-connected feedforward ANN in PYTORCH. The model implemented here represents a fully-connected feedforward ANN with two hidden layers, 3 neurons in the input layer, 20 neurons in the first hidden layer, 30 neurons in the second hidden layer, and 1 neuron in the output layer. Unlike Source code 1.15, this code uses the torch.nn.Linear class to represent the affine transformations.

```
``````
```
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18```
```Python
import torch
import torch.nn as nn

# A Module whose forward method is simply a composition of Modules
# can be represented using the torch.nn.Sequential class
model = nn.Sequential(
    nn.Linear(3, 20),
    nn.ReLU(),
    nn.Linear(20, 30),
    nn.ReLU(),
    nn.Linear(30, 1),
)

# Prints a summary of the model architecture
print(model)

x0 = torch.Tensor([1, 2, 3])
print(model(x0))
```
```

Source code 1.17 (code/fc-ann2.py): PYTHON code for creating a fully-connected feedforward ANN in PyTorch. This creates the same model as Source code 1.16 but uses the torch.nn.Sequential class instead of defining a new subclass of torch.nn.Module.