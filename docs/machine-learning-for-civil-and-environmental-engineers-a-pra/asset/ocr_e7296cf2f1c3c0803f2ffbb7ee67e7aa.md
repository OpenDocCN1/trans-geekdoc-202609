![](bbox=[0.1, 0.09, 0.8, 0.28])

Autocomplete: An application that has a humanly interpretable output, while depending on both short and long-term contextual understanding. In this case, the network uses past information and understands the next word should be a country.

![](bbox=[0.13, 0.35, 0.76, 0.58])

Vanishing Gradient: where the contribution from the earlier steps becomes insignificant in the gradient for the vanilla RNN unit.

Figure 4.9 Demonstration of RNN (from [15]).

The Python and R codes for typical CNN and RNN are provided below:

# CNN Python Package

```
import tensorflow as tf
from keras.models import Sequential
from keras.layers import convolutional
from convolutional import Conv2D
model = Sequential()
model.add(Conv2D)
```

# CNN R Package:

```
>install.packages("keras")
>library(keras)
>k_convNd(x, kernel, strides = c(1, 1, 1),
```