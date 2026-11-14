output. Recall that a dense feedforward neural network is implementing the following equation:

$z = \sigma(xw + b)$

where $\sigma$ is some activation function such as the sigmoid function. $x$ typically represents a vector input in batches, while $w$ and $b$ are weight matrices and bias vectors, respectively.

The class `KerasDeepFactorizationMachine` contains a set of methods to implement the mathematical formulations of DeepFM and returns a Keras Model object in the `build_model` method via Keras’ functional API. Of course, one can also choose to subclass the `keras.Model` class for its implementation and create another build function separately in order to take advantage of the `model.fit` and `model.evaluate` APIs later on.

```
from typing import List

from keras import Model, Input
import keras.backend as K
from keras.layers import (
    Concatenate,
    Flatten,
    Lambda,
    Embedding,
    Reshape,
    Dense,
    Dropout,
    Add,
    Activation,
)

from keras.regularizers import l2

class KerasDeepFactorizationMachine:
    """
    Parameters:
    --------
    * feature_name: name of the features. For the purpose of
    distinguishing between feature names in each keras steps
    * feature_size: a list of size of each features, in the correct
    order. This is the number of unique categories of the feature.
    If the feature is continuous, use 0.
    * num_label: a list of integers, in the correct order of the
    features, that indicates the number of labels applied to a
    multilabel categorical feature.
    - For non-multilabel categorical features, use 1;
    - For continuous features, use 1;
    - Otherwise, specify the maximum number of multi-labels
    * emb_size: embedding size
    * hidden_layer_dim: list of hidden layer dimensions for
    Multilayer perceptron part of the Deep Factorization Machine.
    If None or empty [], DPM becomes FM.
```