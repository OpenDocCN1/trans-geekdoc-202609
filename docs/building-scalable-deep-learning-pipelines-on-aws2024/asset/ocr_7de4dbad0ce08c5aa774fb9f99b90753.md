With this modified architecture, we obtained the following results:

Test Loss: 10.7748  
R2 Score: 0.9991

We also experimented with an intermediate capacity:

```
[In]: def create_and_train_model(
        self,
        train_features,
        train_labels,
        epochs=100,
        batch_size=32
    ):
    self.input_shape = (train_features.shape[1],)
    self.model = Sequential([
    Dense(
        96,
        activation='relu',
        input_shape=self.input_shape
    ),
    Dense(
        48,
        activation='relu'
    ),
    Dense(
        24,
        activation='relu'
    ),
    Dense(1)
    ])
```