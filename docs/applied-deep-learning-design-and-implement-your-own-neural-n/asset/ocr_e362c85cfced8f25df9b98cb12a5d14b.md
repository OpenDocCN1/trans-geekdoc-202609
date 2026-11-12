# Implementation of the DCGAN

Here, we are showing the complete working implementation of a DCGAN model over the celebrity faces dataset to train an instance of a generator model to generate fake images of the human faces and a discriminator model to detect between real and fake images. This code has been implemented in google co-lab (at colab. research.google.com). Most of the code discussed here is taken from (https://github. com/pytorch/examples) for DCGAN implementation. This section gives a thorough explanation of how things work in a practical way.

# Importing the libraries

To start with, initially, some relevant PyTorch libraries are imported, which are important to train the model. All the necessary libraries are shown here to support datasets, plotting, and other functions.

```
from __future__ import print_function
import argparse
import os
import random
import torch
import torch.nn as nn
import torch.nn.parallel
import torch.backends.cudnn as cudnn
import torch.optim as optim
import torch.utils.data
import torchvision.datasets as dset
import torchvision.transforms as transforms
import torchvision.utils as vutils
import numpy as np
import matplotlib.pyplot as plt
import matplotlib.animation as animation
```

# Set random seed for reproducibility

Here seed_val is set to an initial value, and with its help, the results can be reproduced. In order to generate new results random.randint() function can be used, with a range of value from 1 to 10,000 for initialization of the seed_val:

```
Seed_val = 999
print("Random Seed: ", Seed_val)
random.seed(Seed_val)
torch.manual_seed(Seed_val)
```