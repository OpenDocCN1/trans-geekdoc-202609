```
```
        Dense(
            32,
            activation='relu',
            kernel_regularizer=l2(0.01)
        ),
        Dense(
            16,
            activation='relu',
            kernel_regularizer=l2(0.01)
        ),
        Dense(1)
    ])
    self.model.compile(optimizer='adam', loss='mse')
    history = self.model.fit(
        train_features,
        train_labels,
        epochs=epochs,
        batch_size=batch_size,
        verbose=0
    )
    return history
```
```

In this modification, we have added the following to the baseline model:

+   - from tensorflow.keras.regularizers import l2

+   - In each dense layer definition, we added the kernel_regularizer parameter and set it to l2(0.01). This applies L2 regularization to the weights of each dense layer with a regularization strength of 0.01. We can adjust the regularization strength as needed.