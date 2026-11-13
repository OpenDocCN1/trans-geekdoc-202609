combination with ModelCheckpoint, which lets you continually save the model during training (and, optionally, save only the current best model so far: the version of the model that achieved the best performance at the end of an epoch).

# Listing 7.19 Using the callbacks argument in the fit() method

```
Callbacks are passed to the model via the callbacks argument in fit(), which takes a list of callbacks. You can pass any number of callbacks.

callbacks_list = [
  keras.callbacks.EarlyStopping(
      monitor="val_accuracy",
      patience=2,
  ),
  keras.callbacks.ModelCheckpoint(
      filepath="checkpoint_path.keras",
      monitor="val_loss",
      save_best_only=True,
  )
]

model = get_mnist_model()
model.compile(optimizer="rmsprop",
              loss="sparse_categorical_crossentropy",
              metrics=["accuracy"])
model.fit(train_images, train_labels,
          epochs=10,
          callbacks=callbacks_list,
          validation_data=(val_images, val_labels))
```

Note that you can always save models manually after training as well—just call model.save('my_checkpoint_path'). To reload the model you've saved, just use

```
model = keras.models.load_model("checkpoint_path.keras")
```

# 7.3.3 Writing your own callbacks

If you need to take a specific action during training that isn't covered by one of the built-in callbacks, you can write your own callback. Callbacks are implemented by subclassing the keras.callbacks.Callback class. You can then implement any number of the following transparently named methods, which are called at various points during training:

+   - **Called at the start of every epoch**: `on_epoch_begin(epoch, logs)`
+   - **Called at the end of every epoch**: `on_epoch_end(epoch, logs)`
+   - **Called right before processing each batch**: `on_batch_begin(batch, logs)`
+   - **Called right after processing each batch**: `on_batch_end(batch, logs)`
+   - **Called at the start of training**: `on_train_begin(logs)`
+   - **Called at the end of training**: `on_train_end(logs)`