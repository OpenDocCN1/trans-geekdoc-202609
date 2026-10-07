# Data-preprocessing all at once

```
# importing libraries
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Data Preprocessing
# importing the Data-set
daset = pd.read_csv("Credit_Card_Applications.csv")
X = dataset.iloc[:, :-1].values
y = dataset.iloc[:, -1].values

#feature scaling
from sklearn.preprocessing import MinMaxScaler
sc = MinMaxScaler(feature_range=(0, 1))
X = sc.fit_transform(X)
```

# 13.4.5 Training the SOM
We have two options.

+   [1]. The first option is to Implement the SOM from scratch
[2]. The second option is to use a code or class made by another developer.

**MiniSom 1.0**: SOM doesn't have an implementation in Scikit-learn. We'll need to take it from another. Fortunately there is one excellent implementation of SOM, called MiniSom 1.0.

+   MiniSom is a minimalistic and Numpy based implementation of the Self Organizing Maps (SOM) Developed by Giuseppe Vettigl
Remember, you will not always find libraries for a Deep-Learning Model. Sometimes you will need to implement your own models from scratch.
We downloaded the minimom.py (you can download from GitHub in our working directory.

```
from minimom import MiniSom
```

+   We import this MiniSom class from the minimom.py "som" is the object of this class. It is to be trained only on X and not because we are doing some unsupervised.
Are trying to find patterns inside the independent variables that are in X

MiniSom(x, y, input_len, sigma=1, learning_rate=0.5, decay_function=None, random_seed=None)
x=10 defines the size of the Map. Since our dataset is not too big we used 10 * 10 = 100 grid size.
input_len=15 specifies the number of features in feature -matrix X We have 15 features in X. (However customer_id is not on the patterns but we're gonna keep it to identify the potential candidates)
sigma is the radius of the neighborhoods in the grid. So we will keep it to default value 1.0.
learning_rate specifies how much the weights are updated during each iteration.
Hig learning rate, the convergence will fail.
Lower learning rate, SOM might build slowly. We're gonna keep it to default 0.5
decay_function is how to improve the convergence. We're gonna leave it to leave it and not use a decay.
We don't need a random_seed. That will be fine as.

Initializes Self Organizing Maps. x - dimensions of the SOM input_len - number of the vectors in the input sigma - spread of the neighborhood (Gaussian), which needs to be adequate to the dimensions of the map (at iteration we have sigma) = sigma / (1+ t) where T is number_(iteration/2) learning_rate - initial learning (at the iteration we have learning_rate) = learning_rate / (1+ t) where T is number_(iteration/2) decay_function, function that reduces learning_rate and sigma at each iteration
default function: lambda x,current_iteration,iteration_max:x/(1+current_iteration/iteration_max)
random_seed: random to use.