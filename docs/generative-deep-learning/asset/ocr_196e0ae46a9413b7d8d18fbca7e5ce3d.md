# Example 2-3. Building our MLP using a Sequential model

```
from tensorflow.keras import layers, models

model = models.Sequential([
    layers.Flatten(input_shape=(32, 32, 3)),
    layers.Dense(200, activation = 'relu'),
    layers.Dense(150, activation = 'relu'),
    layers.Dense(10, activation = 'softmax'),
])
```

Many of the models in this book require that the output from a layer is passed to multiple subsequent layers, or conversely, that a layer receives input from multiple preceding layers. For these models, the Sequential class is not suitable and we would need to use the functional API instead, which is a lot more flexible.

![](bbox=[0.15, 0.36, 0.25, 0.48])

> I recommend that even if you are just starting out building linear models with Keras, you still use the functional API rather than Sequential models, since it will serve you better in the long run as your neural networks become more architecturally complex. The functional API will give you complete freedom over the design of your deep neural network.

Example 2-4 shows the same MLP coded using the functional API. When using the functional API, we use the Model class to define the overall input and output layers of the model.

# Example 2-4. Building our MLP using the functional API

```
from tensorflow.keras import layers, models

input_layer = layers.Input(shape=(32, 32, 3))
x = layers.Flatten()(input_layer)
x = layers.Dense(units=200, activation = 'relu')(x)
x = layers.Dense(units=150, activation = 'relu')(x)
output_layer = layers.Dense(units=10, activation = 'softmax')(x)
model = models.Model(input_layer, output_layer)
```

Both methods give identical models—a diagram of the architecture is shown in Figure 2-5.