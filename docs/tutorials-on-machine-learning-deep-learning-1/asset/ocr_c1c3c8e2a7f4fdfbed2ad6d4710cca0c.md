```
# third LSTM Layer with Dropout-Regularization
regressor_rnn.add(LSTM(units=50, return_sequences=True))
regressor_rnn.add(Dropout(0.2))
```

```
# Fourth LSTM (last LSTM with Dropout-Regularization)
regressor_rnn.add(LSTM(units=50))
regressor_rnn.add(Dropout(0.2))
```

```
# the output Layer
regressor_rnn.add(Dense(units=1))
```

```
# Compiling the Model
regressor_rnn.compile(optimizer='adam', loss='mean_squared_error')
```

```
# fit the model to training dataset (model Lear)
# The training will happen in this part.
regressor_rnn.fit(X_train, y_train, epochs=10, batch_size=32)
```

![](bbox=[0.197, 0.303, 0.802, 0.476])

> Notice the convergence of Loss values as we started with a loss near 4%, 0.0435 The final losses are in the last 20 epochs, it's staying around 0.0015: 0.15%.

Too small loss overfitting: If you want to try more epochs, the loss will remain around 0.0015.
That's because we used a Dropout Regularization. If you obtain a loss too small in the end well you might get some over fitting
In this case you might get some loss on the training data and really large loss on the test data. So be careful not to overfit and not to decrease the loss as much as possible.

And that's why it seems that we get really good results. We're going to make the Predictions and Visualizing the Results to observe the predictions.

# 12.3.9 Prediction from the RNN

In this part we will make the predictions and visualize the results. There are three steps:

+   - First, we're gonna get the Real Google stock price of 2017-January from Google_Stock_Price_Test.csv.
- In the second step, we're gonna get the Predicted stock price of 2017-January from our trained model.
- And in the final step, we will visualize the results.

+   - Getting the real Google stock price of January 2017: We simply get it from the dataset that we have, in the CSV file, Google_Stock_Price_Test.csv
- So we create a data-frame using Pandas
- So we will select the right column, the Open Google stock price.
- And we make it a NumPy array.