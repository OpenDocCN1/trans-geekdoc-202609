```
```python
loss_tracking_metric.update_state(loss)
logs["val_loss"] = loss_tracking_metric.result()
return logs
```
```

```
```python
val_dataset = tf.data.Dataset.from_tensor_slices((val_images, val_labels))
val_dataset = val_dataset.batch(32)
reset_metrics()
for inputs_batch, targets_batch in val_dataset:
    logs = test_step(inputs_batch, targets_batch)
print("Evaluation results:")
for key, value in logs.items():
    print(f"...[{key}]: {value:.4f}")
```
```

Congrats—you've just reimplemented fit() and evaluate()! Or almost: fit() and evaluate() support many more features, including large-scale distributed computation, which requires a bit more work. It also includes several key performance optimizations.

Let's take a look at one of these optimizations: TensorFlow function compilation.

# 7.4.4 Make it fast with tf.function

You may have noticed that your custom loops are running significantly slower than the built-in fit() and evaluate(), despite implementing essentially the same logic. That's because, by default, TensorFlow code is executed line by line, eagerly, much like NumPy code or regular Python code. Eager execution makes it easier to debug your code, but it is far from optimal from a performance standpoint.

It's more performant to compile your TensorFlow code into a computation graph that can be globally optimized in a way that a code interpreted line by line cannot. The syntax to do this is very simple: just add a @tf.function to any function you want to compile before executing, as shown in the following listing.

# Listing 7.25 Adding a @tf.function decorator to our evaluation-step function

```
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
```
```

```
```python
val_dataset = tf.data.Dataset.from_tensor_slices((val_images, val_labels))
val_dataset = val_dataset.batch(32)
reset_metrics()
```
```