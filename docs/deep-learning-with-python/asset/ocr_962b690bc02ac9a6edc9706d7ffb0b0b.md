# ## 2.5.1 Reimplementing our first example from scratch in TensorFlow

What better demonstrates full, unambiguous understanding than implementing everything from scratch? Of course, what “from scratch” means here is relative: we won’t reimplement basic tensor operations, and we won’t implement backpropagation. But we’ll go to such a low level that we will barely use any Keras functionality at all.

Don’t worry if you don’t understand every little detail in this example just yet. The next chapter will dive in more detail into the TensorFlow API. For now, just try to follow the gist of what’s going on—the intent of this example is to help crystalize your understanding of the mathematics of deep learning using a concrete implementation. Let’s go!

# ### A SIMPLE DENSE CLASS

You’ve learned earlier that the Dense layer implements the following input transformation, where `W` and `b` are model parameters, and `activation` is an element-wise function (usually `relu`, but it would be `softmax` for the last layer):

```
output = activation(dot(W, input) + b)
```

Let’s implement a simple Python class, `NaiveDense`, that creates two TensorFlow variables, `W` and `b`, and exposes a `__call__()` method that applies the preceding transformation.

```
```python
import tensorflow as tf

class NaiveDense:
    def __init__(self, input_size, output_size, activation):
        self.activation = activation

        w_shape = (input_size, output_size)
        w_initial_value = tf.random.uniform(w_shape, minval=0, maxval=1e-1)
        self.W = tf.Variable(w_initial_value)

        b_shape = (output_size,)
        b_initial_value = tf.zeros(b_shape)
        self.b = tf.Variable(b_initial_value)

    def __call__(self, inputs):
        return self.activation(tf.matmul(inputs, self.W) + self.b)

@property
def weights(self) :
    return [self.W, self.b]
```
```

# ### A SIMPLE SEQUENTIAL CLASS

Now, let’s create a `NaiveSequential` class to chain these layers. It wraps a list of layers and exposes a `__call__()` method that simply calls the underlying layers on the inputs, in order. It also features a `weights` property to easily keep track of the layers’ parameters.