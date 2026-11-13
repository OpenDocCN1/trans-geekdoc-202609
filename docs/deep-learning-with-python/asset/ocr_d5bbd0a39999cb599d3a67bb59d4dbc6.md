```
model.compile(optimizer="rmsprop", loss="mse", metrics=["mae"])
history = model.fit(train_dataset,
                   epochs=50,
                   validation_data=val_dataset,
                   callbacks=callbacks)
model = keras.models.load_model("jena_stacked_gru_dropout.keras")
**print**(f"Test MAE: {model.evaluate(test_dataset)[1]:.2f}")
```

Figure 10.12 shows the results. We achieve a test MAE of 2.39 degrees (an 8.8% improvement over the baseline). You can see that the added layer does improve the results a bit, though not dramatically. You may be seeing diminishing returns from increasing network capacity at this point.

![](bbox=[0.19, 0.305, 0.69, 0.61])

Figure 10.12 Training and validation loss on the Jena temperature-forecasting task with a stacked GRU network

# 10.4.3 Using bidirectional RNNs

The last technique we'll look at in this section is the _bidirectional RNN_. A bidirectional RNN is a common RNN variant that can offer greater performance than a regular RNN on certain tasks. It's frequently used in natural language processing—you could call it the Swiss Army knife of deep learning for natural language processing.

RNNs are notably order-dependent: they process the timesteps of their input sequences in order, and shuffling or reversing the timesteps can completely change the representations the RNN extracts from the sequence. This is precisely the reason they perform well on problems where order is meaningful, such as the temperature-forecasting problem. A bidirectional RNN exploits the order sensitivity of RNNs: it