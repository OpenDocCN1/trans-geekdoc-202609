
Let's add a `MaxPooling2D` layer to our model:

Click here to view code image

```
`[28]: cnn.add(MaxPooling2D(pool_size=(2, 2)))`
```

This reduces the previous layer's output from 26-by-26-by-64 to 13-by-13-by-64. 1

1 Another technique for reducing overfitting is to add `Dropout` layers.

Though pooling is a common technique to reduce overfitting, some research suggests that additional convolutional layers which use larger strides for their kernels can reduce dimensionality and overfitting *without* discarding features. 2

2 Tobias, Jost, Dosovitskiy, Alexey, Brox, Thomas, Riedmiller, and Martin. Striving for Simplicity: The All Convolutional Net. April 13, 2015. `https://arxiv.org/abs/1412.6806.`

## Adding Another Convolutional Layer and Pooling Layer

Convnets often have many convolution and pooling layers. The Keras team's convnets tend to double the number of filters in subsequent convolutional layers to enable the model to learn more relationships between the features. 3 So, let's add a second convolution layer with 128 filters, followed by a second pooling layer to once again reduce the dimensionality by 75%:

3 `https://github.com/keras-team/keras-applications/tree/master/keras_applications.`

Click here to view code image

```
[29]: cnn.add(Conv2D(filters=128, kernel_size=(3, 3), activation='relu'))
[30]: cnn.add(MaxPooling2D(pool_size=(2, 2)))
```

The input to the second convolution layer is the 13-by-13-by-64 output of the first pooling layer. So, the output of snippet [29] will be 11-by-11-by-128. For odd dimensions like 11-by-11, Keras pooling layers round *down* by default (in this case to 10-by-10), so this pooling layer's output will be 5-by-5-by-128.

## Flattening the Results

At this point, the previous layer's output is three-dimensional (5-by-5-by-128), but the final output of our model will be a *one-dimensional* array of 10 probabilities that classify the digits. To prepare for the one-dimensional final predictions, we first need to *flatten* the previous layer's three-dimensional output. A Keras `Flatten` layer reshapes its input to one dimension. In this case, the `Flatten` layer's output will be 1-by-3200 (that is, 5 * 5 * 128):

```
[31]: cnn.add(Flatten())
```

## Adding a Dense Layer to Reduce the Number of Features

The layers before the Flatten layer learned digit features. Now we need to take all those features and learn the relationships among them so our model can classify which digit each image represents. Learning the relationships among features and performing classification is accomplished with fully connected Dense layers, like those shown in the neural network diagram earlier in the chapter. The following Dense layer creates 128 neurons (units) that learn from the 3200 outputs of the previous layer:

Click here to view code image

```
[32]: cnn.add(Dense(units=128, activation='relu'))
```

Many convnets contain at least one Dense layer like the one above. Convnets geared to more complex image datasets with higher-resolution images like Image-Net—a dataset of over 14 million images 4—often have several Dense layers, commonly with 4096 neurons. You can see such configurations in several of Keras’s pretrained Image-Net convnets 5—we list these in section 15.11.

4 http://www.image-net.org.

5 https://github.com/keras-team/keras-applications/tree/master/keras_applications.

## Adding Another Dense Layer to Produce the Final Output

Our final layer is a Dense layer that classifies the inputs into neurons representing the classes 0 through 9. The softmax activation function converts the values of these remaining 10 neurons into classification probabilities. The neuron that produces the highest probability represents the prediction for a given digit image:

Click here to view code image

```
[33]: cnn.add(Dense(units=10, activation='softmax'))
```

## Printing the Model's Summary

A model's summary method shows you the model's layers. Some interesting things to note are the output shapes of the various layers and the number of parameters. The parameters are the weights that the network learns during training. 6 7 This is a relatively small network, yet it will need to learn nearly 500,000 parameters! And this is for tiny images that have less than one quarter of the resolution of the icons on most smartphone home screens. Imagine how many features a network would have to learn to process high-resolution 4K video frames or the super-high-resolution images produced by today’s digital cameras. In the Output Shape, None simply means that the model does not know in advance how many training samples you’re going to provide—this is known only when you start the training.

6 https://hackernoon.com/everything-you-need-to-know-about-neural-networks-8988c3ee4491.

7 https://www.kdnuggets.com/2018/06/deep-learning-best-practices-eight-initialization-.html.

Click here to view code image

| Layer (type) | Output Shape | Param # |
|---|---|---|
| conv2d_1 (Conv2D) | (None, 26, 26, 64) | 640 |
| max_pooling2d_1 (MaxPooling2D) | (None, 13, 13, 64) | 0 |
| conv2d_2 (Conv2D) | (None, 11, 11, 128) | 73856 |
| max_pooling2d_2 (MaxPooling2D) | (None, 5, 5, 128) | 0 |
| flatten_1 (Flatten) | (None, 3200) | 0 |
| dense_1 (Dense) | (None, 128) | 409728 |
| dense_2 (Dense) | (None, 10) | 1290 |
| Total params: 485,514 | | |
| Trainable params: 485,514 | | |
| Non-trainable params: 0 | | |

Also, note that there are no “non-trainable” parameters. By default, Keras trains _all_ parameters, but it is possible to prevent training for specific layers, which is typically done when you’re tuning your networks or using another model’s learned parameters in a new model (a process called _transfer learning_). 8

8 https://keras.io/getting-started/faq/#how-can-i-freeze-keras-layers.

## Visualizing a Model’s Structure

You can visualize the model summary using the plot_model function from the module tensorflow.keras.utils:

Click here to view code image

```
[35]: from tensorflow.keras.utils import plot_model
from IPython.display import Image
plot_model(cnn, to_file='convnet.png', show_shapes=True,
           show_layer_names=True)
Image(filename='convnet.png')
```

After storing the visualization in convnet.png, we use module IPython.display’s Image class to show the image in the notebook. Keras assigns the layer names in the image: 9

9 The node with the large integer value 112430057960 at the top of the diagram appears to be a bug in the current version of Keras. This node represents the input layer and should say InputLayer.

112430057960

| Layer | Type | Input | Output |
|---|---|---|---|
| conv2d_1 | Conv2D | (None, 28, 28, 1) | (None, 26, 26, 64) |
| max_pooling2d_1 | MaxPooling2D | (None, 26, 26, 64) | (None, 13, 13, 64) |
| conv2d_2 | Conv2D | (None, 13, 13, 64) | (None, 11, 11, 128) |
| max_pooling2d_2 | MaxPooling2D | (None, 11, 11, 128) | (None, 5, 5, 128) |
| flatten_1 | Flatten | (None, 5, 5, 128) | (None, 3200) |
| dense_1 | Dense | (None, 3200) | (None, 128) |
| dense_2 | Dense | (None, 128) | (None, 10) |

## Compiling the Model

Once you've added all the layers you complete the model by calling its `compile` method:

Click here to view code image

```
[36]: cnn.compile(optimizer='adam',
    loss='categorical_crossentropy',
    metrics=['accuracy'])
```

The arguments are:

- `optimizer='adam'`—The *optimizer* this model will use to adjust the weights throughout the neural network as it learns. There are many optimizers ⁰— 'adam' performs well across a wide variety of models. ¹, ²

⁰For more Keras optimizers, see `https://keras.io/optimizers/`.

¹ `https://medium.com/octavian-ai/which-optimizer-and-learning-rate-should-i-use-for-deep-learning-5acb418f9b2`.

² `https://towardsdatascience.com/types-of-optimization-algorithms-used-in-neural-networks-and-ways-to-optimize-gradient-5ae5d39529f`.

- `loss='categorical_crossentropy'`—This is the *loss function* used by the optimizer in multi-classification networks like our convnet, which will predict 10 classes. As the neural network learns, the optimizer attempts to minimize the values returned by the loss function. The lower the loss, the better the neural network is at predicting what each image is. For binary classification (which we'll use later in this chapter), Keras provides 'binary_crossentropy', and for regression, 'mean_squared_error'. For other loss functions, see `https://keras.io/losses/`.

- `metrics=['accuracy']`—This is a list of the *metrics* that the network will produce to help you evaluate the model. Accuracy is a commonly used metric in classification models. In this example, we'll use the `accuracy` metric to check the percentage of correct predictions. For a list of other metrics, see `https://keras.io/metrics/`.

## 15.6.5 Training and Evaluating the Model

Similar to Scikit-learn's models, we train a Keras model by calling its `fit` method:

- As in Scikit-learn, the first two arguments are the training data and the categorical target labels.

- `epochs` specifies the number of times the model should process the entire set of training data. As we mentioned earlier, neural networks are trained iteratively.

- `batch_size` specifies the number of samples to process at a time during each epoch. Most models specify a power of 2 from 32 to 512. Larger batch sizes can decrease model accuracy. ³ We chose 64. You can try different values to see how they affect the model's performance.

³Keskar, Nitish Shirish, Dheevatsa Mudigere, Jorge Nocedal, Mikhail Smelyanskiy and Ping Tak Peter Tang. On Large-Batch Training for Deep Learning: Generalization Gap
