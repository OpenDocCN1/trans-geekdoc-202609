# 15.3.2 AE-architecture: StackedAutoEncoder class - __init__()

The class that we're going to make that will contain the instructions on how to build the auto-encoder.

+   We're making this class, to make an auto-encoder, we will need to define multiple things:
* How many layers we want to have
* How many nodes in the layers
* We also need an activation function,
* A criterion,
* An optimizer function

To make an auto-encoder, we not need some variables, that'll get, for example, the info of the layers, and some functions, for the activation and the optimizer. To get all this in one recipe, we can only use a class, or at least, that's the simple solution.

+   We could also a module contains several classes.
* Even some libraries, which contain several modules
* But the simplest solution is to make a class. And simple function wouldn't be enough.

The first reason to make this class: a class which can gather these features, and functions to make the auto-encoder.

But then there is a second reason, and this is very important, because this is related to PyTorch\Inheritance:We're going to create a class that we're gonna call StackedAutoEncoders (SAE in short).
That is actually going to be the child of an existing parent class in PyTorch this class will be called Module.
And this Module is taken from the nn module that we imported here: torch.nn as nn.
We are doing this so that we can use all the variables and functions from the class Module, and that's what inheritance is all about.

Because this parent class Module contains all the tools to make an auto-encoder. Basically, it contains বাড়িতে we need to make an auto-encoder.

+   * It contains an optimizer function,
* It contains a criterion,
* It contains tools to make full connections between the layers.

Our auto-encoder is a stacked auto-encoder, because we will have several hidden layers, so we will have several encodings of the input vector features.
We're gonna call this class StackedAutoEncoders, with capital S-A-E, because we use capitals for classes.
In the parentheses of StackedAutoEncoders(), we're going to input the parent class which is Module.

```
class StackedAutoEncoders(nn.Module):
```

__init__(); We define the __init__() function because we need to initialize the objects that were created from this SAE- We define it as:

```
def __init__(self, :):
    super(StackedAutoEncoders, self), __init__()
```

We add a comma, and then joining (self, :), because this will consider the variables of the Module class, because doing inheritance it is something like variable arguments.

Now using the function we got the methods from the Module class.

```
def __init__(self, :):
    super(StackedAutoEncoders, self), __init__()
super(StackedAutoEncoders, self), __init__() will make we get all the inherited classes and methods of the parent class nn.Module.
```

We're gonna use nn.Linear() class to make the full connections between the layers.

Full Connection - ENCODING (first hidden layer) Now we are starting the architecture of the neural network, by choosing the number of layers and the hidden neurons in each of the hidden layers.

+   * The first part of the neural network is the full connection between the input vector of features (ratings of all the movies for one specific user)
* The first hidden layer

The first hidden layer in AutoEncoders is a shorter vector than the input vector, that's the technique of auto-encoders.

We're encoding the input into a shorter vector. That will take place in the first hidden layer.