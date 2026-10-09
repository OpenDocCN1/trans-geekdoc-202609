```
step=16
        ),
        activation='relu'
    )
)
model.add(
    Dense(
        units=hp.Int(
            'units_3',
            min_value=8,
            max_value=64,
            step=8
        ),
        activation='relu'
    )
)
model.add(Dense(1))

model.compile(
    optimizer=tf.keras.optimizers.Adam(
        learning_rate=hp.Choice(
            'learning_rate',
            values=[1e-2, 1e-3, 1e-4]
        )
    ),
    loss='mse'
)
return model
```

In this step, we define a custom TSLAHyperModel class that extends the *HyperModel* class. This class specifies the architecture of our neural network and the hyperparameters to be tuned. The build method is where