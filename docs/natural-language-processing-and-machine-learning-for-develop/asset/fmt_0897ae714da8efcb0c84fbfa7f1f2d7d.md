
import tensorflow as tf import numpy as np import imageio import matplotlib.pyplot as plt # use any image that has 3 channels inp = tf.keras.layers.Input(shape=(None, None, 3)) out = tf.keras.layers.Lambda(lambda image: tf.image.resize(image, (128, 128)))(inp) model = tf.keras.Model(inputs=inp, outputs=out) model.summary() # read the contents of a PNG or JPG X = imageio.imread('sample3.png') out = model.predict(X[np.newaxis, ...]) fig, axes = plt.subplots(nrows=1, ncols=2) axes[0].imshow(X) axes[1].imshow(np.int8(out[0, ...])) plt.show() 

[Listing D.6](#appD.xhtml#listD.6) contains the usual import statements and then initializes the variable inp so that it can accommodate a color image, followed by the variable out that is the result of resizing inp so that it has dimensions 28×23. Next, inp and out are specified as the values of inputs and outputs, respectively, for the Keras model, as shown in this code snippet:

model = tf.keras.Model(inputs=inp, outputs=out) 

Next, the variable X is initialized as a reference to the result of reading the contents of the image sample3.png. The remainder of [Listing D.6](#appD.xhtml#listD.6) involves displaying two images: the original image and the resized image. Launch the code in [Listing D.6](#appD.xhtml#listD.6) and you will see a graph of an image and its resized image as shown in [Figure D.2](#appD.xhtml#figD.2).

![Figure D.2 ¶ A Graph of an Image and its Resized Image.](images/figD.2.jpg)

Figure D.2 ¶ A Graph of an Image and its Resized Image.

## **Keras and Early Stopping (1)**

After specifying the training set and the test set from a dataset, you also decide on the number of training epochs. A value that’s too large can lead to overfitting, whereas a value that’s too small can lead to underfitting. Moreover, model improvement can diminish and subsequent training iterations become redundant.

*Early stopping* is a technique that allows you to specify a large value for the number of epochs, and yet the training will stop if the model performance improvement drops below a threshold value.

There are several ways that you can specify early stopping, and they involve the concept of a *callback function*. [Listing D.7](#appD.xhtml#listD.7) displays the contents of tf2\_keras\_callback.py that performs early stopping via a callback mechanism.

***LISTING D.7: tf2\_keras\_callback.py***

import tensorflow as tf import numpy as np model = tf.keras.Sequential() model.add(tf.keras.layers.Dense(64, activation='relu')) model.add(tf.keras.layers.Dense(64, activation='relu')) model.add(tf.keras.layers.Dense(10, activation='softmax')) model.compile(optimizer=tf.keras.optimizers.Adam(0.01), loss='mse', # mean squared error metrics=\['mae'\]) # mean absolute error data = np.random.random((1000, 32)) labels = np.random.random((1000, 10)) val_data = np.random.random((100, 32)) val_labels = np.random.random((100, 10)) callbacks = [ # stop training if "val_loss" stops improving for over 2 epochs tf.keras.callbacks.EarlyStopping(patience=2, monitor='val_loss'), # write TensorBoard logs to the ./logs directory tf.keras.callbacks.TensorBoard(log_dir='./logs') ] model.fit(data, labels, batch_size=32, epochs=50, callbacks=callbacks, validation_data=(val_data, val_labels)) model.evaluate(data, labels, batch_size=32) 

[Listing D.7](#appD.xhtml#listD.7) defines a Keras‑based model with three hidden layers and then compiles the model. The next portion of [Listing D.7](#appD.xhtml#listD.7) uses the np.random.random function in order to initialize the variables data, labels, val_data, and val_labels.

The interesting code involves the definition of the callbacks variable that specifies tf.keras.callbacks.EarlyStopping class with a value of 2 for patience, which means that the model will stop training if there is an insufficient reduction in the value of val_loss. The callbacks variable includes the class tf.keras.callbacks.TensorBoard to specify the logs subdirectory as the location for the TensorBoard files.

Next, the model.fit() method is invoked with a value of 50 for epochs (shown in bold), followed by the model.evaluate() method. Launch the code in [Listing D.7](#appD.xhtml#listD.7) and you will see the following output:

Epoch 1/50 1000/1000 \[==============================\] - 0s 354us/sample - loss: 0.2452 - mae: 0.4127 - val_loss: 0.2517 - val_mae: 0.4205 Epoch 2/50 1000/1000 \[==============================\] - 0s 63us/sample - loss: 0.2447 - mae: 0.4125 - val_loss: 0.2515 - val_mae: 0.4204 Epoch 3/50 1000/1000 \[==============================\] - 0s 63us/sample - loss: 0.2445 - mae: 0.4124 - val_loss: 0.2520 - val_mae: 0.4209 Epoch 4/50 1000/1000 \[==============================\] - 0s 68us/sample - loss: 0.2444 - mae: 0.4123 - val_loss: 0.2519 - val_mae: 0.4205 1000/1000 \[==============================\] - 0s 37us/sample - loss: 0.2437 - mae: 0.4119 (1000, 10) 

Notice that the code stopped training after four epochs, even though 50 epochs are specified in the code.

## **Keras and Early Stopping (2)**

The previous section contains a code sample with minimalistic functionality with respect to the use of callback functions in Keras. However, you can also define a custom class that provides finer-grained functionality that uses a callback mechanism.

[Listing D.8](#appD.xhtml#listD.8) displays the contents of tf2\_keras\_callback2.py that performs early stopping via a callback mechanism (the new code is shown in bold).

***LISTING D.8: tf2\_keras\_callback2.py***

import tensorflow as tf import numpy as np model = tf.keras.Sequential() model.add(tf.keras.layers.Dense(64, activation='relu')) model.add(tf.keras.layers.Dense(64, activation='relu')) model.add(tf.keras.layers.Dense(10, activation='softmax')) model.compile(optimizer=tf.keras.optimizers.Adam(0.01), loss='mse', metrics=\['mae'\]) data = np.random.random((1000, 32)) labels = np.random.random((1000, 10)) val_data = np.random.random((100, 32)) val_labels = np.random.random((100, 10)) **class MyCallback(tf.keras.callbacks.Callback):** **def on_train_begin(self, logs={}):** **print(“on_train_begin”)** **def on_train_end(self, logs={}):** **print(“on_train_begin”)** **return** **def on_epoch_begin(self, epoch, logs={}):** **print(“on_train_begin”)** **return** **def on_epoch_end(self, epoch, logs={}):** **print(“on_epoch_end”)** **return** **def on_batch_begin(self, batch, logs={}):** **print(“on_batch_begin”)** **return** **def on_batch_end(self, batch, logs={}):** **print(“on_batch_end”)** **return** callbacks = [MyCallback()] model.fit(data, labels, batch_size=32, epochs=50, callbacks=callbacks, validation_data=(val_data, val_labels)) model.evaluate(data, labels, batch_size=32) 

The new code in [Listing D.8](#appD.xhtml#listD.8) differs from [Listing D.7](#appD.xhtml#listD.7) in that it is limited to the code block that is displayed in bold in [Listing D.8](#appD.xhtml#listD.8). This new code defines a custom Python class with several methods, each of which is invoked during the appropriate point during the Keras lifecycle execution. The six methods consists of three pairs of methods for the start event and end event associated with training, epochs, and batches, as listed here:

*   def on_train_begin()

*   def on_train_end()

*   def on_epoch_begin()

*   def on_epoch_end()

*   def on_batch_begin()

*   def on_batch_end()

The preceding methods contain just a print() statement in [Listing D.8](#appD.xhtml#listD.8), and you can insert any code you wish in any of these methods. Launch the code in [Listing D.8](#appD.xhtml#listD.8) and you will see the following output:
