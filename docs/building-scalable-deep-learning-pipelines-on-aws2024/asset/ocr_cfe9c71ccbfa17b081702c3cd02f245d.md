```
    Dense(
        128,
        activation='relu'
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

The results for this model architecture were as follows:

Test Loss: 12.7816
R2 Score: 0.9989

A deeper model has more layers with fewer neurons per layer. This architecture can help us understand the impact of deep layers on model performance compared with wider layers:

```
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
```