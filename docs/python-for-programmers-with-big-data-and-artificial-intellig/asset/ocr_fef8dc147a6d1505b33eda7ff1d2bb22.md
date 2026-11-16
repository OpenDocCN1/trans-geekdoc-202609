etworks-8988c3ee4491.

7 https://www.kdnuggets.com/2018/06/deep-learning-best-practices-eight-initialization-.html.

lick here to view code image

```
[34]: cnn.summary()

Layer (type)                 Output Shape              Param #
=================================================================
conv2d_1 (Conv2D)            (None, 26, 26, 64)        640
_________________________________________________________________
max_pooling2d_1 (MaxPooling2 (None, 13, 13, 64)        0
_________________________________________________________________
conv2d_2 (Conv2D)            (None, 11, 11, 128)       73856
_________________________________________________________________
max_pooling2d_2 (MaxPooling2 (None, 5, 5, 128)         0
_________________________________________________________________
flatten_1 (Flatten)          (None, 3200)              0
_________________________________________________________________
dense_1 (Dense)              (None, 128)               409728
_________________________________________________________________
dense_2 (Dense)              (None, 10)                1290
=================================================================
Total params: 485,514
Trainable params: 485,514
Non-trainable params: 0
```

Also, note that there are no “non-trainable” parameters. By default, Keras trains _all_ parameters, but it is possible to prevent training for specific layers, which is typically done when you’re tuning your networks or using another model’s learned parameters in a new model (a process called _transfer learning_). 8

8 https://keras.io/getting-started/faq/#how-can-i-freeze-keras-layers.

# Visualizing a Model’s Structure

You can visualize the model summary using the plot_model function from the module tensorflow.keras.utils:

lick here to view code image

```
[35]: from tensorflow.keras.utils import plot_model
from IPython.display import Image
plot_model(cnn, to_file='convnet.png', show_shapes=True,
           show_layer_names=True)
Image(filename='convnet.png')
```

After storing the visualization in convnet.png, we use module IPython.display’s Image class to show the image in the notebook. Keras assigns the layer names in the image: 9

9 The node with the large integer value 112430057960 at the top of the diagram appears to be