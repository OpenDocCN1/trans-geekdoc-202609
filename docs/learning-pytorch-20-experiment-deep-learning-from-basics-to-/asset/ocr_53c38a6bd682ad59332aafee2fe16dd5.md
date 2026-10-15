# Define Model Architecture

A linear regression model is one of the simplest types of neural networks and forms the basis for many more complex models. It's particularly useful for understanding the relationship between input and output variables.

In the context of neural networks, a linear regression model can be thought of as a network with just a single layer and no activation function, or equivalently a network with a single layer followed by a linear activation function.

In the case of the fish dataset, if we're trying to predict the weight of the fish (a continuous variable), a linear regression model would be appropriate.

Now, this is the best way how you might define a simple linear regression model in PyTorch:

```
import torch.nn as nn
```