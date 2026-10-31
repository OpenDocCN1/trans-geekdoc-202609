
# Accelerating NumPy Code with JAX

The `Fashion-MNIST` dataset consists of 70,000 grayscale images of various fashion items such as T-shirts, trousers, and shoes. Each image is 28x28 pixels and belongs to one of ten classes. The dataset is available to download at While `NumPy` is a powerful library for numerical computations, using it to train machine learning models on large datasets like `Fashion-MNIST` can be inefficient and slow. The lack of just-in-time (`JIT`) compilation and automatic differentiation means computations are interpreted at runtime, and gradients must be calculated manually. The challenge is to accelerate existing `NumPy` code to efficiently handle large-scale computations involved in training neural networks on the `Fashion-MNIST` dataset.

To overcome the performance limitations of `NumPy`, we can leverage Google `JAX`. By converting existing `NumPy` code to `JAX`, significant speedups in computation can be achieved, and gradient calculations can be simplified. This involves replacing `NumPy` imports with `JAX`'s `NumPy` and applying `JIT` compilation and automatic differentiation to the code.

## Setting up Environment

First, ensure that `JAX` is installed in your Python environment:

```
pip install --upgrade "jax[cpu]"
```

### Loading Fashion-MNIST Dataset

The `TensorFlow Datasets` library provides an easy interface to access standard datasets like `Fashion-MNIST`. Follow the below steps:

```
import tensorflow_datasets as tfds
# Load the dataset
data = tfds.load('fashion_mnist', split=['train', 'test'], as_supervised=True)
train_data, test_data = data
```

### Preprocessing Data

Next, you preprocess the images and labels to prepare them for training. To do this, normalize the images and convert them to `NumPy` arrays.

```
import numpy as np
def preprocess(image, label):
    image = np.array(image) / 255.0  # Normalize pixel values
    image = image.reshape(-1)        # Flatten the image
    label = np.array(label)
    return image, label
# Convert the dataset to NumPy arrays
train_images = []
train_labels = []
for image, label in tfds.as_numpy(train_data):
    img, lbl = preprocess(image, label)
    train_images.append(img)
    train_labels.append(lbl)
train_images = np.array(train_images)
train_labels = np.array(train_labels)
```

## Building a Simple Neural Network with NumPy

Now, create a simple neural network with one hidden layer using `NumPy`.

```
# Initialize parameters
input_size = 784  # 28x28 pixels flattened
hidden_size = 128
output_size = 10   # 10 classes
np.random.seed(0)
W1 = np.random.randn(input_size, hidden_size) * 0.01
b1 = np.zeros((1, hidden_size))
W2 = np.random.randn(hidden_size, output_size) * 0.01
b2 = np.zeros((1, output_size))
# Activation functions
def relu(x):
    return np.maximum(0, x)
def softmax(x):
    exp_x = np.exp(x - np.max(x, axis=1, keepdims=True))  # Stability improvement
    return exp_x / np.sum(exp_x, axis=1, keepdims=True)
```

## Defining Forward and Backward Passes

Once created, implement the forward pass and compute the loss.

```
def forward_pass(x):
    z1 = np.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = np.dot(a1, W2) + b2
    y_pred = softmax(z2)
    return y_pred, a1
def compute_loss(y_pred, y_true):
    m = y_true.shape[0]
    log_likelihood = -np.log(y_pred[range(m), y_true])
    loss = np.sum(log_likelihood) / m
    return loss
```

Implement the backward pass to compute gradients manually.

```
def backward_pass(x, a1, y_pred, y_true):
    global W1, b1, W2, b2
    m = y_true.shape[0]
    y_true_one_hot = np.zeros_like(y_pred)
    y_true_one_hot[np.arange(m), y_true] = 1
    dz2 = y_pred - y_true_one_hot
    dW2 = np.dot(a1.T, dz2) / m
    db2 = np.sum(dz2, axis=0, keepdims=True) / m
    da1 = np.dot(dz2, W2.T)
    dz1 = da1 * (a1 > 0)
    dW1 = np.dot(x.T, dz1) / m
    db1 = np.sum(dz1, axis=0, keepdims=True) / m
    # Update parameters
    learning_rate = 0.01
    W1 -= learning_rate * dW1
    b1 -= learning_rate * db1
    W2 -= learning_rate * dW2
    b2 -= learning_rate * db2
```

## Training Model

Now, its time to train the model using the manual forward and backward passes.

```
num_epochs = 5
batch_size = 64
for epoch in range(num_epochs):
    permutation = np.random.permutation(train_images.shape[0])
    train_images_shuffled = train_images[permutation]
    train_labels_shuffled = train_labels[permutation]
    for i in range(0, train_images.shape[0], batch_size):
        x_batch = train_images_shuffled[i:i+batch_size]
        y_batch = train_labels_shuffled[i:i+batch_size]
        y_pred, a1 = forward_pass(x_batch)
        loss = compute_loss(y_pred, y_batch)
        backward_pass(x_batch, a1, y_pred, y_batch)
    print(f"Epoch {epoch+1}, Loss: {loss}")
```

It is also observed that training the model using `NumPy` can be slow due to the manual computation of gradients and the absence of `JIT` compilation. The execution time increases significantly with larger datasets and more complex models, making it impractical for large-scale machine learning tasks.

## Converting NumPy Code to JAX

To accelerate the code, convert it to use `JAX`. This involves importing `JAX`'s `NumPy` and utilizing its `JIT` compilation and automatic differentiation features. To do this, replace `NumPy` imports with `JAX`'s `NumPy` and import necessary `JAX` functions.

```
import jax.numpy as jnp
from jax import grad, jit, random
from functools import partial
```

After this, update the activation functions and model functions to use `JAX`'s `NumPy`.

```
# Initialize parameters with JAX
key = random.PRNGKey(0)
W1 = random.normal(key, (input_size, hidden_size)) * 0.01
b1 = jnp.zeros((1, hidden_size))
W2 = random.normal(key, (hidden_size, output_size)) * 0.01
b2 = jnp.zeros((1, output_size))
def relu(x):
    return jnp.maximum(0, x)
def softmax(x):
    exp_x = jnp.exp(x - jnp.max(x, axis=1, keepdims=True))
    return exp_x / jnp.sum(exp_x, axis=1, keepdims=True)
```

Then, define the loss function using `JAX`.

```
def compute_loss(params, x, y):
    W1, b1, W2, b2 = params
    z1 = jnp.dot(x, W1) + b1
    a1 = relu(z1)
    z2 = jnp.dot(a1, W2) + b2
    y_pred = softmax(z2)
    m = y.shape[0]
    log_likelihood = -jnp.log(y_pred[jnp.arange(m), y])
    loss = jnp.sum(log_likelihood) / m
    return loss
```

Next, use `JAX`'s `grad` function to compute gradients automatically.

```
grad_loss = grad(compute_loss)
```

After that, apply `JIT` compilation to the training step function.

```
@jit
def update(params, x, y, learning_rate=0.01):
    grads = grad_loss(params, x, y)
    params = [param - learning_rate * grad for param, grad in zip(params, grads)]
    return params
```

And finally, train the model using the optimized `JAX` functions.

```
params = [W1, b1, W2, b2]
num_epochs = 5
batch_size = 64
for epoch in range(num_epochs):
    permutation = np.random.permutation(train_images.shape[0])
    train_images_shuffled = train_images[permutation]
    train_labels_shuffled = train_labels[permutation]
    for i in range(0, train_images.shape[0], batch_size):
        x_batch = train_images_shuffled[i:i+batch_size]
        y_batch = train_labels_shuffled[i:i+batch_size]
        params = update(params, x_batch, y_batch)
    current_loss = compute_loss(params, x_batch, y_batch)
    print(f"Epoch {epoch+1}, Loss: {current_loss}")
```

By converting the code to `JAX` and utilizing automatic differentiation and `JIT` compilation, significant speedups in training time are achieved. The use of `grad` simplifies gradient computations, and the `@jit` decorator accelerates the execution of the training loop. Additionally, `JAX` operations are designed to run efficiently on CPUs, GPUs, and TPUs. This makes it feasible to experiment with more complex models or larger datasets.

By following this approach, existing `NumPy` code can be effectively accelerated using Google `JAX`, enabling efficient handling of large-scale computations and complex machine learning models on datasets like `Fashion-MNIST`.
