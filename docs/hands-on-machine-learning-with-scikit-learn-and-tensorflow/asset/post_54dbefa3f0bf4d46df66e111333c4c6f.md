
The Keras API only specifies how to use subclassing to define layers, models, callbacks, and regularizers. If you build other components (such as losses, metrics, initializers or constraints) using subclassing, they may not be portable to other Keras implementations.

Let's walk through this code:

- The constructor accepts kwargs and passes them to the parent constructor, which handles standard hyperparameters: the name of the loss and the reduction algorithm to use to aggregate instance losses. By default, it is "sum_over_batch_size", which means that the loss will be the sum of the instance losses, possibly weighted by the weights, if any, and then divide by the batch size (not by the sum of weights, so this is not the weighted mean). Other possible values are "sum" and None.
- The call() method takes the labels and predictions, computes all the instance losses, and returns them.
- The get_config() method returns a dictionary mapping each parameter to its value. It first calls the parent class's get_config() method, adds the new hyperparameters to this dictionary (note that the content {} was added in Python 3.5).

You can use this class when you compile the model:

```
model.compile(loss=HuberLoss(2.), optimizer="nadam")
```

When you save the model, the threshold will be saved along with it, and when you load the model you just need to map the class name to the class itself:

```
model = keras.models.load_model("my_model_with_a_custom_loss_class.h5",
custom_objects={'HuberLoss': HuberLoss})
```

When you save a model, Keras calls the instance_get_config() method and saves the config as JSON in the HDF5 file. When you load the model, it calls the from_config() method on the HuberLoss class: this is implemented by the base class (Loss) and creates an instance of the class, passing **config to the constructor.

That's for it losses! It was not too hard, was it? It's just simple for custom activation functions, initializers, regularizers, and constraints. Let's look at these now.

5 It would not be a good idea to use a weighted mean: if we did, two instances with the same weight but in different batches would have a different impact on training, depending on the total weight of each batch.

## Custom Activation Functions, Initializers, Regularizers, and Constraints

Mosteras functionalities, as losses, regularizers, initializers, metrics, activation functions, layers and even full models can be customized in very much the same way. Most of the time, you will just need to write a simple function, with appropriate inputs and outputs. For example, here are examples of a custom activation function (equivalent to keras.activations.softplus or tf.nn.softplus), a custom Glorot initializer (equivalent to keras.initializers.glot_normal), a custom regularizer (equivalent to keras.regularizers.l1(0.01)) and a custom constraint that ensures weights are all positive (equivalent to keras.constraints.nonneg() or tf.nn.relu).

```
def my_softplus(z): # return value is just tf.nn.softplus(z)
return tf.math.log(tf.exp(z) + 1.0)
```

```
def my_lorot_initializer(shape, dtype=float32):
stddev = tf.sqrt(2. / (shape[0] + shape[1]))
return tf.random.normal(shape, stddev=stddev, dtype=dtype)
```

```
def my_l1_regularizer(weights):
return tf.reduce_sum(abs(0.01 * weights))
```

```
def my_positive_weights(weights): # return value is just tf.nn.relu(weights)
return tf.where(weights < 0, tf.zeros_like(weights), weights)
```

As you can see, the arguments depend on the type of custom function. These custom functions can then be used by them, for example:

```
layer = keras.layers.Dense(30, activation=my_softplus,
kernel_initializer=my_lorot_initializer,
kernel_regularizer=my_l1_regularizer,
kernel_constraint=my_positive_weights)
```

The activation function will be applied to the output of the next layer. The layer's weights will be initialized using the value returned by the initializer. At each training step the weights will be passed to the regularization function to compute the regularization loss, which will be added to the main loss to get the final loss for training. Finally, the constraint function will be called after each training step, and the layer's weights will be replaced by the constrained weights.

If a function has some hyperparameters that need to be saved with the model, then you will need to subclass the appropriate class, such as keras.regularizers.Constraint, keras.initializers.Initializer or keras.layers (for any layer, including activation functions). For example, much like we did for the custom loss, here is a class for l1-regularization, saves its factor hyperparameter (this time we do not need to call the parent constructor or the get_config method, as they are not defined by the parent class):

```
class MyRegularizer(keras.regularizers.Regularizer):
    def __init__(self, factor):
        self.factor = factor
    def __call__(self, weights):
        return tf.reduce_sum(tf.abs(self.factor * weights))
    def get_config(self):
        return {'factor': self.factor}
```

Note that you use the call() method for losses, layers (including activation functions) and models, or the __call__() method for regularizers, initializers and constraints. For metrics, things are a bit different, as we will see now.

## Custom Metrics

Losses and metrics are conceptually not the same: losses are used by Gradient Descent to train a model, they must be differentiable (at least where they are evaluated) and their gradients should not be everywhere. Plus, it is okay if they are not easily interpretable by humans (e.g. cross-entropy). In contrast, metrics are used to evaluate a model, they must be more interpretable, and they can be non-differentiable or have 0 gradients everywhere (e.g. accuracy).

In that case, defining a custom metric function is exactly the same as we created earlier, or we could use the Huber loss function we created earlier would work fine and also work in the same way, not always! saving the name of the function, "huber_fn":

```
model.compile(loss='mse', optimizer='adam', metrics=[create_huber(2.0)])
```

For each batch training, Keras will compute this metric and keep track of its mean since the beginning of the epoch. Most of the time, this is exactly what we want. But not always! Consider a binary classifier's precision. As we saw in Chapter 3, precision is the number of true positives by the number of predictions (both true and false positives). Suppose the model made 5 positive predictions in the first batch, 4 were correct: 80% precision. Then suppose the model made 3 positive predictions in the second batch, they were all incorrect: 0% precision for the second batch. If you just compute the mean of these two precisions, 90%. But wait, this is not the model's precision over these two batches! Indeed, there was a total of 4 positives (4 + 0) out of 8 positive predictions (5 + 3), so the overall precision is 50%, not 40%. What we need is an object that can keep track of the number of true positives and the number of false positives, and compute their ratio when requested. This is precisely what keras.metrics.Precision does:

```
>>> precision = keras.metrics.Precision()
>>> precision.update_state([1, 1, 1, 1, 0], [1, 1, 1, 1, 0])
>>> precision.result()
0.8
>>> precision.update_state([0, 0, 0], [0, 0, 0])
>>> precision.result()
0.5
```

At any point, we can call the result() method to get the current value of the metric. We can also look at its variables (tracking the number of true and false positives) using the variables attribute, and reset these using the reset_states() method:

```
>>> precision.variables
[<Variable 'true_positives' shape=(), dtype=float32, numpy=4>,
 <Variable 'false_positives' shape=(), dtype=float32, numpy=1>]
>>> precision.reset_states()
```
