# Loading Dataset

To load this dataset in PyTorch, we first need to download the data and load it into a DataFrame using pandas. From there, we can convert the data to tensors and create a custom Dataset.

The following is an example of how you can do this:

```
import pandas as pd

import torch

from torch.utils.data import Dataset

# Define a custom Dataset

class FishDataset(Dataset):

    def __init__(self, dataframe):
```