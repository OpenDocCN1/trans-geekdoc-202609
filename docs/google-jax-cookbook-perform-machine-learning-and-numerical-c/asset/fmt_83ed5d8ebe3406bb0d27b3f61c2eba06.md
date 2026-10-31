
# Inspecting Intermediate Values in JIT-Compiled Functions

When developing neural networks with Google JAX on the Fashion-MNIST dataset, debugging can become challenging, especially when functions are wrapped with `jit` for just-in-time compilation. Traditional debugging methods like inserting `print` statements do not work within functions because JAX traces the function to build a computation graph, and side-effecting operations like `print` are not executed during tracing. This makes it difficult to inspect intermediate values and understand the behavior of the code during execution. The challenge is to find effective methods to inspect runtime values within functions to facilitate debugging and ensure that the model functions correctly.

To overcome the difficulty of inspecting intermediate values in functions, we can utilize JAX's debugging tools, specifically which allows printing values during JAX transformations. Additionally, alternative methods like returning intermediate values or using host callbacks can be employed to inspect runtime values successfully. These techniques enable us to debug functions wrapped with `jit` and gain insights into the internal computations of our models.

## Understanding Why `print` Statements Fail

Within functions, standard Python `print` statements are ignored because JAX operates by tracing functions to create static computation graphs. Side effects like `print` do not affect the computation graph and are therefore omitted during tracing.

Following is a quick example:

```
import jax
import jax.numpy as jnp
@jax.jit
def compute(x):
    y = x * 2
    print(f"Intermediate value y: {y}")
    return y
result = compute(3.0)
```

This code will not display the intermediate value of `y` because the `print` statement is not executed within the function.

## Using `jax.debug.print` for Debugging

Below is the refactored code using `jax.debug.print`:

```
import jax
import jax.numpy as jnp
from jax import debug
@jax.jit
def compute(x):
    y = x * 2
    debug.print("Intermediate value y: {}", y)
    return y
result = compute(3.0)
```

When running this code, the output will be:

Intermediate value y: 6.0

Here, the `debug.print` function accepts a format string and variables to display. It operates correctly within functions, allowing us to inspect intermediate values.

### Applying `jax.debug.print` in Model

Suppose we want to inspect intermediate activations within the neural network's forward pass. Following is a quick example:

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jnp.maximum(0, z1)  # ReLU activation
    debug.print("Activation a1 mean: {}", jnp.mean(a1))
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jax.nn.softmax(z2)
    return y_pred
forward_pass_jit = jax.jit(forward_pass)
```

By running `forward_pass_jit(params`, we can observe the mean value of `a1` during execution.

### Conditional Debugging

We can add conditions to the `debug.print` function to limit output to specific cases. Following is a quick example:

```
def forward_pass(params, x):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = jnp.maximum(0, z1)
    max_a1 = jnp.max(a1)
    debug.print("Max of a1: {}", max_a1, where=max_a1 > 10.0)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = jax.nn.softmax(z2)
    return y_pred
```

This will print the maximum value of `a1` only when it exceeds helping to identify abnormal activations.

## Using Host Callbacks with `jax.experimental.host_callback`

For more advanced debugging, `jax.experimental.host_callback.id_print` can be used. Following is a quick example:

```
from jax.experimental import host_callback as hcb
@jax.jit
def compute(x):
    y = x * 2
    hcb.id_print(y, result=False, what="Intermediate value y")
    return y
result = compute(3.0)
```

This method sends the value from the device to the host and prints it, providing a way to inspect values during execution.

By utilizing host callbacks, and alternative methods like returning intermediate values, we can effectively inspect runtime values within functions. These techniques enhance our ability to debug and understand the internal computations of our models.
