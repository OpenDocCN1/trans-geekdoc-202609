
| `outputs_collections` || `None` || Collections to store the normalization outputs |
| `trainable` || `True` || Whether to add normalization variables to the graph's trainable collection |
| `batch_weights` || `None` || Weights to scale the batch mean and variance |
| `fused` || `False` || Whether to use fused normalization (faster) |
| `data_format` || `DATA_FORMAT_NHWC` || Format of the input data |
| `zero_debias_moving_mean` || `False` || Factor for updating the moving mean |
| `scope` || `None` || Scope to contain normalized variables |
| `renorm` || `False` || Whether to use extra variables during normalization |
| `renorm_clipping` || `None` || Dictionary that provides values for renormalization |
| `renorm_decay` || `0.99` || Factor to update moving mean/variance during renormalization |

TensorFlow uses the `decay` parameter to compute the population's mean and variance. The following equations show how the computation is performed:

![images](images/eq07017.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mtable columnalign="left"><m:mtr><m:mtd><m:msub><m:mi>&#956;</m:mi><m:mi>P</m:mi></m:msub><m:mo>=</m:mo><m:msub><m:mi>&#956;</m:mi><m:mi>P</m:mi></m:msub><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi><m:mo>+</m:mo><m:msub><m:mi>&#956;</m:mi><m:mi>B</m:mi></m:msub><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:msubsup><m:mi>&#963;</m:mi><m:mi>P</m:mi><m:mn>2</m:mn></m:msubsup><m:mo>=</m:mo><m:msubsup><m:mi>&#963;</m:mi><m:mi>P</m:mi><m:mn>2</m:mn></m:msubsup><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi><m:mo>+</m:mo><m:msubsup><m:mi>&#963;</m:mi><m:mi>B</m:mi><m:mn>2</m:mn></m:msubsup><m:mrow><m:mo>(</m:mo><m:mrow><m:mn>1</m:mn><m:mo>&#45;</m:mo><m:mi>d</m:mi><m:mi>e</m:mi><m:mi>c</m:mi><m:mi>a</m:mi><m:mi>y</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mtd></m:mtr></m:mtable></m:math>

The `center` and `scale` parameters determine whether the values of the inputs parameter should be shifted and scaled. The function will shift the input values if `center` is `True` and will scale the input values if `scale` is `True`.

It's important to see the difference between `is_training` and `trainable`. Setting `is_training` to `True` tells the function that the normalization is being performed during a training run, which means it should update the population's mean and variance. Setting `trainable` to `True` tells the function to store its normalization variables in the graph collection represented by the `TRAINABLE_VARIABLES` key.

The last three parameters of `batch_norm` relate to *renormalization*. This process improves normalization when an application's batches are small or dependent on one another.

### Regularization

One of the most difficult tasks in machine learning involves finding the right structure for a neural network. If you add too few nodes, your network will be too simple to classify data accurately. This is called *underfitting*.

If you add too many nodes, your network will tailor itself specifically for your training set and will be unsuitable for analyzing general data. This problem is called *overfitting,* and it’s a serious issue in machine learning.

The process of updating a neural network (or other machine learning algorithm) to analyze general data is called *regularization*. Researchers have devised many methods for regularizing networks, and this section focuses on two:

*   **Dropout:** Randomly removes nodes from the network
*   **L1/L2 regularization:** Reduces weights by increasing the loss

For both methods, I explain how the regularization works and how you can perform it using TensorFlow.

#### Dropout

The dropout process randomly removes one or more nodes from a network. For each node removed, dropout removes the node’s incoming and outgoing connections and their weights.

In TensorFlow, you can configure dropout for a neural network by adding a dropout layer. Adding this layer involves calling the `tf.nn.dropout` function:

```
dropout(x, keep_prob, noise_shape=None, seed=None, name=None)
```

In this function, `x` is the tensor containing values from the preceding layer, and `keep_prob` is a scalar with the same type as `x`. The function returns a tensor with the same size as `x`.

`dropout` sets each of its output values to 0 or `1/keep_prob` times the corresponding input value. More precisely, `dropout` sets an output value to 0 with a probability of `1-keep_prob` and sets the output value to `1/keep_prob` times the input value with a probability of `keep_prob`.

#### L1/L2 regularization

L1 and L2 regularization prevent overfitting by reducing the network's weights. Both methods increase the loss by a value that depends on two factors: the network’s weights and a constant denoted λ.

L1 regularization increases the loss by λ multiplied by the absolute value of the weight to be updated. Therefore, when the algorithm updates the weight w[0] through backpropagation, it adds a value to the loss equal to λ|w[0]|.

L2 regularization increases the loss by λ/2 multiplied by the square of the weight to be updated. Therefore, when the algorithm updates w[0], it adds λ|w[0]|²/2 to the loss.

In both cases, the loss increases when the weights increase and decreases when the weights decrease. Therefore, the regularization process tends to reduce non-essential weights to zero, thereby simplifying the model and (hopefully) avoiding overfitting.

To perform L1/L2 regularization in TensorFlow, you can call `tf.contrib.layers.l1_regularizer` or `tf.contrib.layers.l2_regularizer`:

*   `l1_regularizer(lambda, scope=None)`: Returns a function that performs L1 regularization
*   `l2_regularizer(lambda, scope=None)`: Returns a function that performs L2 regularization

These functions return special functions called *regularizers*. After you've obtained a regularizer, you can regularize a set of weights by calling `tf.contrib.layers.apply_regularization`:

```
apply_regularization(regularizer, weights_list=None)
```

Many TensorFlow functions accept regularizers as arguments. One important function is `tf.contrib.layers.fully_connected`, which I discuss in the “[Improving the Deep Learning Process](#12_9788126592555-ch07.xhtml#c07-sec-0028)” section.

## Managing Variables with Scope

When building applications with neural networks, keeping track of weights is a major priority. Hidden layers accept weighted inputs and produce weighted outputs. Without proper management, it's easy for the names of one layer’s weights to clash with the names of another layer’s weights.

### Variable scope

In deep learning applications, layers frequently assign the same names to their weights. To keep the variables separate, TensorFlow makes it possible to define a variable’s *scope*. An application can define a scope by calling `tf.variable_scope`:

```
tf.variable_scope(name_or_scope, default_name=None, values=None, initializer=None, regularizer=None, caching_device=None, partitioner=None, custom_getter=None, reuse=None, dtype=None, use_resource=None)
```

Applications commonly call this function as part of a `with` statement, as in the following code:

```
with tf.variable_scope("MyScope")
```

```
…
```

If an application creates variables using `tf.get_variable` inside a `with` block, TensorFlow will prepend the scope's name to the variable’s name. That is, if the application creates a new variable named `MyVar`, the variable’s full name will be `MyScope/MyVar`.

[Chapter 5](#09_9788126592555-ch05.xhtml) explains how to create variables with `tf.Variable`, but if an application wants to create a variable inside a scope, the function to call is `tf.get_variable`:
