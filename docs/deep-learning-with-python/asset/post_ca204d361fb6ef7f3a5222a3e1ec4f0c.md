
```python
logs = {}
for metric in metrics:
    metric.update_state(targets, predictions)
    logs[metric.name] = metric.result()

loss_tracking_metric.update_state(loss)
logs["loss"] = loss_tracking_metric.result()
return logs
```

We will need to reset the state of our metrics at the start of each epoch and before running evaluation. Here's a utility function to do it.

### Listing 7.22 Writing a step-by-step training loop: resetting the metrics

```python
def reset_metrics():
    for metric in metrics:
        metric.reset_state()
    loss_tracking_metric.reset_state()
```

We can now lay out our complete training loop. Note that we use a tf.data.Dataset object to turn our NumPy data into an iterator that iterates over the data in batches of size 32.

### Listing 7.23 Writing a step-by-step training loop: the loop itself

```python
training_dataset = tf.data.Dataset.from_tensor_slices(
    (train_images, train_labels))
training_dataset = training_dataset.batch(32)
epochs = 3
for epoch in range(epochs):
    reset_metrics()
    for inputs_batch, targets_batch in training_dataset:
        logs = train_step(inputs_batch, targets_batch)
    print(f"\nResults at the end of epoch {epoch}")
    for key, value in logs.items():
        print(f"...{key}: {value:.4f}")
```

And here's the evaluation loop: a simple for loop that repeatedly calls a test_step() function, which processes a single batch of data. The test_step() function is just a subset of the logic of train_step(). It omits the code that deals with updating the weights of the model—that is to say, everything involving the GradientTape and the optimizer.

### Listing 7.24 Writing a step-by-step evaluation loop

```python
def test_step(inputs, targets):
    predictions = model(inputs, training=False)
    loss = loss_fn(targets, predictions)

    logs = {}
    for metric in metrics:
        metric.update_state(targets, predictions)
        logs["val_" + metric.name] = metric.result()

    loss_tracking_metric.update_state(loss)
    logs["val_loss"] = loss_tracking_metric.result()
    return logs
```

Congrats—you've just reimplemented fit() and evaluate()! Or almost: fit() and evaluate() support many more features, including large-scale distributed computation, which requires a bit more work. It also includes several key performance optimizations.

## 7.4.4 Make it fast with tf.function

You may have noticed that your custom loops are running significantly slower than the built-in fit() and evaluate(), despite implementing essentially the same logic. That's because, by default, TensorFlow code is executed line by line, eagerly, much like NumPy code or regular Python code. Eager execution makes it easier to debug your code, but it is far from optimal from a performance standpoint.

It's more performant to compile your TensorFlow code into a computation graph that can be globally optimized in a way that a code interpreted line by line cannot. The syntax to do this is very simple: just add a @tf.function to any function you want to compile before executing, as shown in the following listing.

### Listing 7.25 Adding a @tf.function decorator to our evaluation-step function

```python
@tf.function
def test_step(inputs, targets):
    predictions = model(inputs, training=False)
    loss = loss_fn(targets, predictions)

    logs = {}
    for metric in metrics:
        metric.update_state(targets, predictions)
        logs["val_" + metric.name] = metric.result()

    loss_tracking_metric.update_state(loss)
    logs["val_loss"] = loss_tracking_metric.result()
    return logs

val_dataset = tf.data.Dataset.from_tensor_slices((val_images, val_labels))
val_dataset = val_dataset.batch(32)
reset_metrics()
for inputs_batch, targets_batch in val_dataset:
    logs = test_step(inputs_batch, targets_batch)
print("Evaluation results:")
for key, value in logs.items():
    print(f"...{key}: {value:.4f}")
```

On the Colab CPU, we go from taking 1.80 s to run the evaluation loop to only 0.8 s. Much faster!

Remember, while you are debugging your code, prefer running it eagerly, without any @tf.function decorator. It's easier to track bugs this way. Once your code is working and you want to make it fast, add a @tf.function decorator to your training step and your evaluation step—or any other performance-critical function.

## 7.4.5 Leveraging fit() with a custom training loop

In the previous sections, we were writing our own training loop entirely from scratch. Doing so provides you with the most flexibility, but you end up writing a lot of code while simultaneously missing out on many convenient features of fit(), such as callbacks or built-in support for distributed training.

What if you need a custom training algorithm, but you still want to leverage the power of the built-in Keras training logic? There's actually a middle ground between fit() and a training loop written from scratch: you can provide a custom training step function and let the framework do the rest.

You can do this by overriding the train_step() method of the Model class. This is the function that is called by fit() for every batch of data. You will then be able to call fit() as usual, and it will be running your own learning algorithm under the hood.

Here's a simple example:

- We create a new class that subclasses keras.Model.
- We override the method train_step(self, data). Its contents are nearly identical to what we used in the previous section. It returns a dictionary mapping metric names (including the loss) to their current values.
- We implement a metrics property that tracks the model's Metric instances. This enables the model to automatically call reset_state() on the model's metrics at the start of each epoch and at the start of a call to evaluate(), so you don't have to do it by hand.

### Listing 7.26 Implementing a custom training step to use with fit()

```python
loss_fn = keras.losses.SparseCategoricalCrossentropy()
loss_tracker = keras.metrics.Mean(name="loss")

class CustomModel(keras.Model):
    def train_step(self, data):
        inputs, targets = data
        with tf.GradientTape() as tape:
            predictions = self(inputs, training=True)
            loss = loss_fn(targets, predictions)

        gradients = tape.gradient(loss, self.trainable_weights)
        optimizer.apply_gradients(zip(gradients, self.trainable_weights))

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

```python
inputs = keras.Input(shape=(28 * 28,))
features = layers.Dense(512, activation="relu")(inputs)
features = layers.Dropout(0.5)(features)
outputs = layers.Dense(10, activation="softmax")(features)
model = CustomModel(inputs, outputs)

model.compile(optimizer=keras.optimizers.RMSprop())
model.fit(train_images, train_labels, epochs=3)
```

There are a couple of points to note:

- This pattern does not prevent you from building models with the Functional API. You can do this whether you're building Sequential models, Functional API models, or subclassed models.
- You don't need to use a @tf.function decorator when you override train_step—the framework does it for you.

Now, what about metrics, and what about configuring the loss via compile()? After you've called compile(), you get access to the following:

- self.compiled_loss—The loss function you passed to compile().
- self.compiled_metrics—A wrapper for the list of metrics you passed, which allows you to call self.compiled_metrics.update_state() to update all of your metrics at once.
- self.metrics—The actual list of metrics you passed to compile(). Note that it also includes a metric that tracks the loss, similar to what we did manually with our loss_tracking_metric earlier.

We can thus write

```python
class CustomModel(keras.Model):
    def train_step(self, data):
        inputs, targets = data
        with tf.GradientTape() as tape:
            predictions = self(inputs, training=True)
            loss = self.compiled_loss(targets, predictions)
        gradients = tape.gradient(loss, self.trainable_weights)
```

Compute the loss via self.compiled_loss.
