
import tensorflow as tf model = tf.keras.models.Sequential([ tf.keras.layers.Dense(512, activation=tf.nn.relu), ]) 

We have three more bullet items to discuss, starting with the compilation step. Keras provides a compile() API for this step, an example of which is here:

model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

Next we need to specify a training step, and Keras provides the fit() API (as you can see, it’s not called train()), an example of which is here:

model.fit(x_train, y_train, epochs=5)

The final step is the prediction that is performed via the predict() API, an example of which is here:

pred = model.predict(x)

Keep in mind that the evaluate() method is used for evaluating a trained model, and the output of this method is accuracy or loss. However, the predict() method makes predictions from the input data.

[Listing D.1](#appD.xhtml#listD.1) displays the contents of tf2_basic_keras.py that combines the code blocks in the preceding steps into a single code sample.

***LISTING D.1: tf2_basic_keras.py***

import tensorflow as tf # NOTE: we need the train data and test data model = tf.keras.models.Sequential([ tf.keras.layers.Dense(1, activation=tf.nn.relu), ]) model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy']) model.fit(x_train, y_train, epochs=5) model.evaluate(x_test, y_test)

[Listing D.1](#appD.xhtml#listD.1) contains no new code, and we’ve essentially glossed over some of the terms such as the optimizer (an algorithm that is used in conjunction with a cost function), the loss (the type of loss function) and the metrics (how to evaluate the efficacy of a model).

Thorough explanations for these details cannot be condensed into a few paragraphs (alas), but the good news is that you can find a plethora of detailed online blog posts that discuss these terms.

## **Keras and Linear Regression**

This section contains a simple example of creating a Keras-based model in order to solve a task involving linear regression: given a positive number representing kilograms of pasta, predict its corresponding price. [Listing D.2](#appD.xhtml#listD.2) displays the contents of pasta.csv and [Listing D.3](#appD.xhtml#listD.3) displays the contents of keras_pasta.py that performs this task.

***LISTING D.2: pasta.csv***

weight,price 5,30 10,45 15,70 20,80 25,105 30,120 35,130 40,140 50,150 

***LISTING D.3: keras_pasta.py***

import tensorflow as tf import numpy as np import pandas as pd import matplotlib.pyplot as plt # price of pasta per kilogram df = pd.read_csv("pasta.csv") weight = df['weight'] price = df['price'] model = tf.keras.models.Sequential([ tf.keras.layers.Dense(units=1,input_shape=[1]) ]) # MSE loss function and Adam optimizer model.compile(loss='mean_squared_error', optimizer=tf.keras.optimizers.Adam(0.1)) # train the model history = model.fit(weight, price, epochs=100, verbose=False) # graph the # of epochs versus the loss plt.xlabel('Number of Epochs') plt.ylabel("Loss Values") plt.plot(history.history['loss']) plt.show() print("Cost for 11kg:",model.predict([11.0])) print("Cost for 45kg:",model.predict([45.0]))

[Listing D.3](#appD.xhtml#listD.3) initializes the Pandas data frame df with the contents of the CSV file pasta.csv, and then initializes the variables weight and cost with the first and second columns, respectively, of df.

The next portion of [Listing D.3](#appD.xhtml#listD.3) defines a Keras-based model that consists of a single Dense layer. This model is compiled and trained, and then a graph is displayed that shows the “number of epochs” on the horizontal axis and the corresponding value of the loss function for the vertical axis. Launch the code in [Listing D.3](#appD.xhtml#listD.3) and you will see the following output:

Cost for 11kg: [[41.727108]] Cost for 45kg: [[159.02121]]

Figure D.1 displays a graph of epochs versus loss during the training process.

![Figure D.1. ¶ A Graph of Epochs versus Loss.](images/figD.1.jpg)

Figure D.1. ¶ A Graph of Epochs versus Loss.

##**Keras, MLPs, and MNIST**

This section contains a simple example of creating a Keras-based MLP neural network that will be trained with the MNIST dataset. [Listing D.4](#appD.xhtml#listD.4) displays the contents of keras_mlp_mnist.py that performs this task.

***LISTING D.4: keras_mlp_mnist.py***

import tensorflow as tf import numpy as np # instantiate mnist and load data: mnist = tf.keras.datasets.mnist (x_train, y_train), (x_test, y_test) = mnist.load_data() # one-hot encoding for all labels to create 1x10 vectors that are compared with the final layer: y_train = tf.keras.utils.to_categorical(y_train) y_test = tf.keras.utils.to_categorical(y_test) image_size = x_train.shape[1] input_size = image_size * image_size # resize and normalize the 28x28 images: x_train = np.reshape(x_train, [-1, input_size]) x_train = x_train.astype('float32') / 255 x_test = np.reshape(x_test, [-1, input_size]) x_test = x_test.astype('float32') / 255 # initialize some hyper-parameters: batch_size = 128 hidden_units = 128 dropout_ratea = 0.20 # define a Keras-based model: model = tf.keras.models.Sequential() model.add(tf.keras.layers.Dense(hidden_units, input_dim=input_size)) model.add(tf.keras.layers.Activation('relu')) model.add(tf.keras.layers.Dropout(dropout_rate)) model.add(tf.keras.layers.Dense(hidden_units)) model.add(tf.keras.layers.Activation('relu')) model.add(tf.keras.layers.Dense(10)) model.add(tf.keras.layers.Activation('softmax')) model.summary() model.compile(loss='categorical_crossentropy', optimizer='adam', metrics=['accuracy']) # train the network on the training data: model.fit(x_train, y_train, epochs=10, batch_size=batch_size) # calculate and then display the accuracy: loss, acc = model.evaluate(x_test, y_test, batch_size=batch_size) print("\\nTest accuracy: %.1f%%" % (100.0 * acc))

[Listing D.4](#appD.xhtml#listD.4) contains the usual import statements and then initializes the variable mnist as a reference to the MNIST dataset. The next portion of [Listing D.4](#appD.xhtml#listD.4) contains some typical code that populates the training dataset and the test dataset and converts the labels to numeric values via the technique known as “one-hot” encoding.

Next, several hyperparameters are initialized, and a Keras-based model is defined that specifies three Dense layers and the relu activation function. This model is compiled and trained, and the accuracy on the test dataset is computed and then displayed. Launch the code in [Listing D.4](#appD.xhtml#listD.4) and you will see the following output:
