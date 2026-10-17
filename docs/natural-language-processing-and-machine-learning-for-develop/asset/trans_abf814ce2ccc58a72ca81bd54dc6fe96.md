
on`\_train\_begin` on`\_train\_begin` Epoch 1/50 on`\_batch\_begin` on`\_batch\_end`   32/1000 \[..............................\] - ETA: 4s - loss: 0.2489 - mae: 0.4170on`\_batch\_begin` on`\_batch\_end` on`\_batch\_begin` on`\_batch\_end` // details omitted for brevity on`\_batch\_begin` on`\_batch\_end` on`\_batch\_begin` on`\_batch\_end` 992/1000 \[============================>.\] - ETA: 0s - loss: 0.2468 - mae: 0.4138on`\_batch\_begin` on`\_batch\_end` on`\_batch\_begin` on`\_batch\_end` 1000/1000 \[==============================\] - 0s 335us/sample - loss: 0.2466 - mae: 0.4136 - val`\_loss`: 0.2445 - val`\_mae`: 0.4126 on`\_train\_begin` Epoch 2/50 on`\_batch\_begin` on`\_batch\_end`   32/1000 \[..............................\] - ETA: 0s - loss: 0.2465 - mae: 0.4133on`\_batch\_begin` on`\_batch\_end` on`\_batch\_begin` on`\_batch\_end` // details omitted for brevity on`\_batch\_end` on`\_epoch\_end` 1000/1000 \[==============================\] - 0s 51us/sample - loss: 0.2328 - mae: 0.4084 - val`\_loss`: 0.2579 - val`\_mae`: 0.4241 on`\_train\_begin`   32/1000 \[..............................\] - ETA: 0s - loss: 0.2295 - mae: 0.4030 1000/1000 \[==============================\] - 0s 22us/sample - loss: 0.2313 - mae: 0.4077 (1000, 10) 

## `Keras` and `Metrics`

Many `Keras`-based models only specify “accuracy” as the metric for evaluating a trained model, as shown here:

model.compile(optimizer='adam',               loss='sparse\_categorical\_crossentropy',               metrics=\['accuracy'\]) 

However, there are many other built-in `metrics` available, each of which is encapsulated in a `Keras` class in the `tf.keras.metrics` namespace. An inventory of many such `metrics` are displayed in the following list:

*   class `Accuracy`: how often predictions match labels

*   class `BinaryAccuracy`: how often predictions match labels

*   class `CategoricalAccuracy`: how often predictions match labels

*   class `FalseNegatives`: the number of false negatives

*   class `FalsePositives`: the number of false positives

*   class `Mean`: the (weighted) mean of the given values

*   class `Precision`: the precision of the predictions wrt the labels

*   class `Recall`: the recall of the predictions wrt the labels

*   class `TrueNegatives`: the number of true negatives

*   class `TruePositives`: the number of true positives

Earlier in this chapter you learned about the “confusion matrix” that provides numeric values for TP, TN, FP, and FN; each of these values has a corresponding `Keras` class `TruePositive`, `TrueNegative`, `FalsePositive`, and `FalseNegative`, respectively. Perform an online search for code samples that use the `metrics` in the preceding list.

## `Saving` and `Restoring` `Keras` Models

[Listing D.9](#appD.xhtml#listD.9) displays the contents of `tf2\_keras_save_model.py` that creates, trains, and saves a `Keras`-based model, then creates a new model that is populated with the data from the saved model.

***LISTING D.9: tf2\_keras_save_model.py***

```python
import tensorflow as tf
import os

def create_model():
    model = tf.keras.models.Sequential([
        tf.keras.layers.Flatten(input_shape=(28, 28)),
        tf.keras.layers.Dense(512, activation=tf.nn.relu),
        tf.keras.layers.Dropout(0.2),
        tf.keras.layers.Dense(10, activation=tf.nn.softmax)
    ])
    model.compile(optimizer=tf.keras.optimizers.Adam(),
                  loss=tf.keras.losses.sparse_categorical_crossentropy,
                  metrics=['accuracy'])
    return model

# Create a basic model instance
model = create_model()
model.summary()

checkpoint_path = "checkpoint/cp.ckpt"
checkpoint_dir = os.path.dirname(checkpoint_path)

# Create checkpoint callback
cp_callback = tf.keras.callbacks.ModelCheckpoint(checkpoint_path, save_weights_only=True, verbose=1)

# => model #1: create the first model
model = create_model()

mnist = tf.keras.datasets.mnist
(X_train, y_train), (X_test, y_test) = mnist.load_data()
X_train, X_test = X_train / 255.0, X_test / 255.0
print("X_train.shape:", X_train.shape)

model.fit(X_train, y_train,
          epochs=2,
          validation_data=(X_test, y_test),
          callbacks=[cp_callback])

# pass callback to training

# => model #2: create a new model and load saved model
model = create_model()
loss, acc = model.evaluate(X_test, y_test)
print("Untrained model, accuracy: {:5.2f}%".format(100 * acc))

model.load_weights(checkpoint_path)
loss, acc = model.evaluate(X_test, y_test)
print("Restored model, accuracy: {:5.2f}%".format(100 * acc))
```

The final code block in [Listing D.8](#appD.xhtml#listD.8) creates a new `Keras`-based model by invoking the Python method `create_model()` again, evaluating this new model on the test-related data, and displaying the value of the accuracy. Next, the model is loaded with the saved model weights via the `load_weights()` API. The relevant code block is reproduced here:

model = create_model()
loss, acc = model.evaluate(X_test, y_test)
print("Untrained model, accuracy: {:5.2f}%".format(100 * acc))
model.load_weights(checkpoint_path)
loss, acc = model.evaluate(X_test, y_test)
print("Restored model, accuracy: {:5.2f}%".format(100 * acc))

Now launch the code in [Listing D.8](#appD.xhtml#listD.8) and you will see the following output:
