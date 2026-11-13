```
# Load data set
(x, y), (x_test, y_test) = tf.keras.datasets.california_housing.load_data(
    version="large", path="california_housing.npz", test_split=0.2, seed=113
)
# Split the data into training and validation sets
# x_train is the training data, y_train is the training labels
# x_val is the validation data, y_val is the validation labels
x_train, x_val, y_train, y_val = train_test_split(x, y, test_size=0.2,
                                                  random_state=0)
# Define the network, compile, and train it
model = models.Sequential([
    layers.Dense(64, activation="relu", input_shape=(x_train.shape[1],)),
    layers.Dense(64, activation="relu"),
    layers.Dense(1)
])
model.compile(optimizer="adam",
              loss="mse",
              metrics=["mae"])
history = model.fit(x_train, y_train,
                    epochs=100,
                    validation_data=(x_val, y_val))
# Run the unseen test data through the network to determine success
test_loss, test_mae = model.evaluate(x_test, y_test)
print(f"Test data - mean-absolute-error: {test_mae}")
```

![](bbox=[0.155, 0.505, 0.395, 0.685])

# Example 3: ANN for classification

A very common Hello World-style classification problem for ANNs is the MNIST number recognition data set. It comprises 60,000 28x28 grayscale images of the ten digits, along with a test set of 10,000 images.

Examples of handwritten digits in the MNIST data set

```
Python
import tensorflow as tf
from tensorflow.keras import layers, models
from tensorflow.keras.utils import to_categorical
import matplotlib.pyplot as plt
import numpy as np
# Load data set
(x_train, y_train), (x_test, y_test) = tf.keras.datasets.mnist.load_data()
```