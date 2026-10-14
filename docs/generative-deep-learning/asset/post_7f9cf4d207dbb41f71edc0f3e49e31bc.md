
that sum to 1, which can be interpreted as the likelihood that the image belongs to each class.

In Keras, activation functions can be defined within a layer (Example 2-5) or as a separate layer (Example 2-6).

### Example 2-5. A ReLU activation function defined as part of a Dense layer

```
x = layers.Dense(units=200, activation = 'relu')(x)
```

### Example 2-6. A ReLU activation function defined as its own layer

```
x = layers.Dense(units=200)(x)
x = layers.Activation('relu')(x)
```

In our example, we pass the input through two Dense layers, the first with 200 units and the second with 150, both with ReLU activation functions.

## Inspecting the model

We can use the model.summary() method to inspect the shape of the network at each layer, as shown in Table 2-1.

Table 2-1. Output from the model.summary() method

| Layer (type) | Output shape | Param # |
|---|---|---|
| InputLayer | (None, 32, 32, 3) | 0 |
| Flatten | (None, 3072) | 0 |
| Dense | (None, 200) | 614,600 |
| Dense | (None, 150) | 30,150 |
| Dense | (None, 10) | 1,510 |
| Total params | 646,260 |  |
| Trainable params | 646,260 |  |
| Non-trainable params | 0 |  |

Notice how the shape of our Input layer matches the shape of x_train and the shape of our Dense output layer matches the shape of y_train. Keras uses None as a marker for the first dimension to show that it doesn't yet know the number of observations that will be passed into the network. In fact, it doesn't need to; we could just as easily pass 1 observation through the network at a time as 1,000. That's because tensor operations are conducted across all observations simultaneously using linear algebra—this is the part handled by TensorFlow. It is also the reason why you get a performance increase when training deep neural networks on GPUs instead of CPUs: GPUs are optimized for large tensor operations since these calculations are also necessary for complex graphics manipulation.

The summary method also gives the number of parameters (weights) that will be trained at each layer. If ever you find that your model is training too slowly, check the summary to see if there are any layers that contain a huge number of weights. If so, you should consider whether the number of units in the layer could be reduced to speed up training.

![](img/f0f0f5d89818fdddf117bbe758ac8143_61_0.png)

Make sure you understand how the number of parameters is calculated in each layer! It's important to remember that by default, each unit within a given layer is also connected to one additional bias unit that always outputs 1. This ensures that the output from the unit can still be nonzero even when all inputs from the previous layer are 0.

Therefore, the number of parameters in the 200-unit Dense layer is 200 * (3,072 + 1) = 614,600.

## Compiling the Model

In this step, we compile the model with an optimizer and a loss function, as shown in Example 2-7.

### Example 2-7. Defining the optimizer and the loss function

```
from tensorflow.keras import optimizers

opt = optimizers.Adam(learning_rate=0.0005)
model.compile(loss='categorical_crossentropy', optimizer=opt,
    metrics=['accuracy'])
```

Let's now look in more detail at what we mean by loss functions and optimizers.

## Loss functions

The loss function is used by the neural network to compare its predicted output to the ground truth. It returns a single number for each observation; the greater this number, the worse the network has performed for this observation.

Keras provides many built-in loss functions to choose from, or you can create your own. Three of the most commonly used are mean squared error, categorical cross-entropy, and binary cross-entropy. It is important to understand when it is appropriate to use each.

If your neural network is designed to solve a regression problem (i.e., the output is continuous), then you might use the mean squared error loss. This is the mean of the squared difference between the ground truth $y_i$ and predicted value $p_i$ of each output unit, where the mean is taken over all $n$ output units:

MSE = $\frac{1}{n} \sum_{i=1}^{n} (y_i - p_i)^2$

If you are working on a classification problem where each observation only belongs to one class, then *categorical cross-entropy* is the correct loss function. This is defined as follows:

- $\sum_{i=1}^{n} y_i \log(p_i)$

Finally, if you are working on a binary classification problem with one output unit, or a multilabel problem where each observation can belong to multiple classes simultaneously, you should use *binary cross-entropy*:

- $\frac{1}{n} \sum_{i=1}^{n} (y_i \log(p_i) + (1 - y_i) \log(1 - p_i))$

## Optimizers

The *optimizer* is the algorithm that will be used to update the weights in the neural network based on the gradient of the loss function. One of the most commonly used and stable optimizers is *Adam* (Adaptive Moment Estimation).³ In most cases, you shouldn’t need to tweak the default parameters of the Adam optimizer, except the *learning rate*. The greater the learning rate, the larger the change in weights at each training step. While training is initially faster with a large learning rate, the downside is that it may result in less stable training and may not find the global minimum of the loss function. This is a parameter that you may want to tune or adjust during training.

Another common optimizer that you may come across is *RMSProp* (Root Mean Squared Propagation). Again, you shouldn’t need to adjust the parameters of this optimizer too much, but it is worth reading the Keras documentation to understand the role of each parameter.

We pass both the loss function and the optimizer into the `compile` method of the model, as well as a `metrics` parameter where we can specify any additional metrics that we would like to report on during training, such as accuracy.

## Training the Model

Thus far, we haven’t shown the model any data. We have just set up the architecture and compiled the model with a loss function and optimizer.

To train the model against the data, we simply call the fit method, as shown in Example 2-8.

### Example 2-8. Calling the fit method to train the model

```
model.fit(x_train
    , y_train
    , batch_size = 32
    , epochs = 10
    , shuffle = True
)
```

- 1. The raw image data.
- 2. The one-hot encoded class labels.
- 3. The batch_size determines how many observations will be passed to the network at each training step.
- 4. The epochs determine how many times the network will be shown the full training data.
- 5. If shuffle = True, the batches will be drawn randomly without replacement from the training data at each training step.

This will start training a deep neural network to predict the category of an image from the CIFAR-10 dataset. The training process works as follows.

First, the weights of the network are initialized to small random values. Then the network performs a series of training steps. At each training step, one batch of images is passed through the network and the errors are backpropagated to update the weights. The batch_size determines how many images are in each training step batch. The larger the batch size, the more stable the gradient calculation, but the slower each training step.

![](img/f0f0f5d89818fdddf117bbe758ac8143_63_0.png)

It would be far too time-consuming and computationally intensive to use the entire dataset to calculate the gradient at each training step, so generally a batch size between 32 and 256 is used. It is also now recommended practice to increase the batch size as training progresses.⁴

This continues until all observations in the dataset have been seen once. This completes the first epoch. The data is then passed through the network again in batches as part of the second epoch. This process repeats until the specified number of epochs have elapsed.

During training, Keras outputs the progress of the procedure, as shown in Figure 2-7. We can see that the training dataset has been split into 1,563 batches (each containing 32 images) and it has been shown to the network 10 times (i.e., over 10 epochs), at a rate of approximately 2 milliseconds per batch. The categorical cross-entropy loss has fallen from 1.8377 to 1.3696, resulting in an accuracy increase from 33.69% after the first epoch to 51.67% after the tenth epoch.

```
model.fit(x_train, y_train, batch_size=32, epochs=10, shuffle=True)
Epoch 1/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.8377 - accuracy: 0.3369
Epoch 2/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.6552 - accuracy: 0.4076
Epoch 3/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.5743 - accuracy: 0.4396
Epoch 4/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.5288 - accuracy: 0.4549
Epoch 5/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.4888 - accuracy: 0.4706
Epoch 6/10
1563/1563 [==============================] - 2s 2ms/step - loss: 1.4542 - accuracy: 0.4851
Epoch 7/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.4332 - accuracy: 0.4908
Epoch 8/10
1563/1563 [==============================] - 2s 2ms/step - loss: 1.4094 - accuracy: 0.4992
Epoch 9/10
1563/1563 [==============================] - 2s 2ms/step - loss: 1.3896 - accuracy: 0.5045
Epoch 10/10
1563/1563 [==============================] - 3s 2ms/step - loss: 1.3696 - accuracy: 0.5167
```

Figure 2-7. The output from the fit method

## Evaluating the Model

We know the model achieves an accuracy of 51.9% on the training set, but how does it perform on data it has never seen?

To answer this question we can use the evaluate method provided by Keras, as shown in Example 2-9.

### Example 2-9. Evaluating the model performance on the test set

```
model.evaluate(x_test, y_test)
```
