```
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

```
[In]: class TSLARegressor:
    """
    Class for TSLA stock price regression.
    """
```