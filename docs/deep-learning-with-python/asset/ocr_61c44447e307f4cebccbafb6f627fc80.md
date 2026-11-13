```
gradients = tape.gradient(loss, model.trainable_weights)
optimizer.apply_gradients(zip(gradients, model.trainable_weights))
```

```
loss_tracker.update_state(loss)
return {"loss": loss_tracker.result()}

@property
def metrics(self):
return [loss_tracker]
```

We update the loss tracker metric that tracks the average of the loss.

We return the average loss so far by querying the loss tracker metric.

Any metric you would like to reset across epochs should be listed here.

We can now instantiate our custom model, compile it (we only pass the optimizer, since the loss is already defined outside of the model), and train it using fit() as usual:

```
inputs = keras.Input(shape=(28 * 28,))
features = layers.Dense(512, activation="relu")(inputs)
features = layers.Dropout(0.5)(features)
outputs = layers.Dense(10, activations="softmax")(features)
model = CustomModel(inputs, outputs)

model.compile(optimizer=keras.optimizers.RMSprop())
model.fit(train_images, train_labels, epochs=3)
```

There are a couple of points to note:

+   - This pattern does not prevent you from building models with the Functional API. You can do this whether you're building Sequential models, Functional API models, or subclassed models.
+   - You don't need to use a @tf.function decorator when you override train_step—the framework does it for you.

Now, what about metrics, and what about configuring the loss via compile()? After you've called compile(), you get access to the following:

+   - self.compiled_loss—The loss function you passed to compile().
+   - self.compiled_metrics—A wrapper for the list of metrics you passed, which allows you to call self.compiled_metrics.update_state() to update all of your metrics at once.
+   - self.metrics—The actual list of metrics you passed to compile(). Note that it also includes a metric that tracks the loss, similar to what we did manually with our loss_tracking_metric earlier.

We can thus write

```
class CustomModel(keras.Model):
def train_step(self, data):
    inputs, targets = data
    with tf.GradientTape() as tape:
        predictions = self(inputs, training=True)
        loss = self.compiled_loss(targets, predictions)
    gradients = tape.gradient(loss, model.trainable_weights)
```

Compute the loss via self.compiled_loss.