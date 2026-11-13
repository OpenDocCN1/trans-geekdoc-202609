```
for inputs_batch, targets_batch in val_dataset:
    logs = test_step(inputs_batch, targets_batch)
print("Evaluation results:")
for key, value in logs.items():
    print(f"...{key}: {value:.4f}")
```

On the Colab CPU, we go from taking 1.80 s to run the evaluation loop to only 0.8 s. Much faster!

Remember, while you are debugging your code, prefer running it eagerly, without any @tf.function decorator. It's easier to track bugs this way. Once your code is working and you want to make it fast, add a @tf.function decorator to your training step and your evaluation step—or any other performance-critical function.

# 7.4.5 Leveraging fit() with a custom training loop

In the previous sections, we were writing our own training loop entirely from scratch. Doing so provides you with the most flexibility, but you end up writing a lot of code while simultaneously missing out on many convenient features of fit(), such as callbacks or built-in support for distributed training.

What if you need a custom training algorithm, but you still want to leverage the power of the built-in Keras training logic? There's actually a middle ground between fit() and a training loop written from scratch: you can provide a custom training step function and let the framework do the rest.

You can do this by overriding the train_step() method of the Model class. This is the function that is called by fit() for every batch of data. You will then be able to call fit() as usual, and it will be running your own learning algorithm under the hood.

Here's a simple example:

+   - We create a new class that subclasses keras.Model.
+   - We override the method train_step(self, data). Its contents are nearly identical to what we used in the previous section. It returns a dictionary mapping metric names (including the loss) to their current values.
+   - We implement a metrics property that tracks the model's Metric instances. This enables the model to automatically call reset_state() on the model's metrics at the start of each epoch and at the start of a call to evaluate(), so you don't have to do it by hand.

```
Listing 7.26 Implementing a custom training step to use with fit()
loss_fn = keras.losses.SparseCategoricalCrossentropy()
loss_tracker = keras.metrics.Mean(name="loss")

class CustomModel(keras.Model):
    def train_step(self, data):
        inputs, targets = data
        with tf.GradientTape() as tape:
            predictions = self(inputs, training=True)
            loss = loss_fn(targets, predictions)
```