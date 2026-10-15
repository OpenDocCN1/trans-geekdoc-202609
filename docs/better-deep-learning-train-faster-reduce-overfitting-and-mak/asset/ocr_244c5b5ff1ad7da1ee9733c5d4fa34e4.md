![](bbox=[0.18, 0.14, 0.81, 0.49])

Figure 13.2: Line Plots of Learning Curves for Loss and Accuracy on Train and Test Datasets While Training.

# 13.3.3 MLP Model With Weight Regularization

We can add weight regularization to the hidden layer to reduce the overfitting of the model to the training dataset and improve the performance on the holdout set. We will use the L2 vector norm also called weight decay with a regularization parameter (called alpha or lambda) of 0.001, chosen arbitrarily. This can be done by adding the kernel_regularizer argument to the layer and setting it to an instance of l2.

```
model.add(Dense(500, input_dim=2, activation='relu', kernel_regularizer=l2(0.001)))
```

Listing 13.14: Updated layer to use weight regularization.

The updated example of fitting and evaluating the model on the moons dataset with weight regularization is listed below.

```
# mlp with weight regularization for the moons dataset
from sklearn.datasets import make_moons
from keras.models import Sequential
from keras.layers import Dense
from keras.regularizers import l2
from matplotlib import pyplot
# generate 2d classification dataset
```