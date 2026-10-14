
These two rules form a trend-following strategy that seeks to capture the momentum of an asset.

### Momentum strategy with machine learning

To implement this moving average crossover strategy using machine learning, we will first have to modify the problem to be suitable for an ML approach. Rather than creating explicit rules for when to buy and sell, we would use ML to learn these rules based on past data.

In fact, this is exactly the promise of what machine learning is capable of offering: rules extracted from data during a learning phase.

Here is an example using supervised learning, and in particular, a classification approach. Classification means that we are trying to learn how to predict a category.

The following gives an idea of what machine learning can do for trading. We will return to the methodological points concerning implementation in the next section (Implementing supervised trading systems).

These are the steps that lead to a trading system powered by a machine learning algorithm:

1. **Preprocessing and data**: First, we download the data, then calculate the same moving averages (`SMA50` and `SMA200`) on historical price data. On the other hand, we use the same data as in the traditional approach (without ML), which is why we calculate the moving averages in the same way to include them in the inputs that will be submitted to the model for the search for recurring patterns. We then create a target variable that is `+1` when the next day's closing price is higher than the day before (bullish signal) and `-1` for the opposite (bearish signal). This target variable is what we will train our model to predict.

2. **Feature creation**: Next, we create features for our model. These could include the current price, volume, the values of the two moving averages, and potentially many others. A big part of ML is selecting and engineering these features. We will return to this point in [Chapter 6](#chap06.xhtml), Improving Model Capability with Features.

3. **Model training**: We then split our data into a training set and a test set, and train our ML model (for example, a decision tree, logistic regression, to start with, and then move on to more complex models) on the training set. The model learns to predict the target variable based on the features.

4. **Model testing**: After our model is trained, we test its performance on the test set to make sure it generalizes well to new data. We can adjust our model parameters or try different models based on this performance.

5. **Trading rule**: We now have an ML model that, given the current features, predicts whether the short-term moving average will be above or below the long-term moving average in the future. We can use these predictions to trade: if the prediction is `+1`, we buy, and if the prediction is `-1`, we sell.

Regarding model training, modern machine learning systems utilize proven and optimized APIs. For our purposes, we have chosen the `scikit-learn` machine learning library. This is the most widely used machine learning library in the world, along with Google's `TensorFlow`. Furthermore, in addition to its intrinsic qualities, the Scikit-Learn license permits the code to be reused for commercial purposes, and the code is open-source, available for consultation on GitHub.

Here is the code that illustrates each of these points:

The study concerns the General Motors share (GM ticker) over the last 5 years (1000 daily data). Let us start by preprocessing and downloading data from Yahoo Finance:

```python
import pandas as pd
import numpy as np
import yfinance as yf

yf.pdr_override()

symbol = 'GM'
ticker = yf.Ticker(symbol)

# Valid intervals: [1m, 2m, 5m, 15m, 30m, 60m, 90m, 1h, 1d, 5d, 1wk, 1mo, 3mo]
df = ticker.history(period='1000d', interval='1d')
```

The next step is to create the features given as input to the machine learning algorithm. This stage is known as feature engineering:

```python
# Compute moving averages
df['SMA50'] = df['Close'].rolling(window=50).mean()
df['SMA200'] = df['Close'].rolling(window=200).mean()
df['MA_cross'] = df['SMA50'] - df['SMA200']

# Create target variable
df['target'] = pd.DataFrame(np.zeros(len(df)))
df['target'] = np.where(df['Close'].pct_change() > 0, 1, -1)
df['target'] = df['target'].shift(-1)

# Remove NaNs
df.dropna(inplace=True)

# Create features
X = df[['Open', 'High', 'Low', 'Close', 'SMA50', 'SMA200', 'MA_cross']]
```

The ML method consists of providing the ML algorithm with the same ingredients as for the MA-cross over strategy, but without going so far as to give it the rules of this strategy (respective positions of the moving averages). The purpose of the machine learning algorithm is to extract these rules. To do this, it is guided by the output (`target` column), which represents the goal to be achieved.

During the training phase, the ML algorithm scans the features submitted to it (input) in search of repetitions and complex correlations that will enable it to predict the supervision column (output) appropriately.

Model training: `train_test_split()` function splits the data into a training and a test set. In this way, only the training set is submitted during the training phase of the algorithm.

```python
# Train-test split
X_train, X_test, y_train, y_test = train_test_split(X, df['target'], shuffle=False)

# Create and train decision tree classifier
clf = DecisionTreeClassifier(random_state=42)
clf.fit(X_train, y_train)
```

And, finally, model testing, the output of the function is as follows:

```python
from sklearn.metrics import classification_report
print(classification_report(clf.predict(X_test), y_test))
```

| | | precision | recall | f1-score | support |
| --- | --- | --- | --- | --- | --- |
| -1.0 | | 0.24 | 0.50 | 0.33 | 46 |
| 1.0 | | 0.78 | 0.53 | 0.63 | 154 |
| accuracy | | | | 0.53 | 200 |
| macro avg | | 0.51 | 0.52 | 0.48 | 200 |
| weighted avg | | 0.66 | 0.53 | 0.56 | 200 |

It is important to note that all the performance metrics are calculated on data to which the algorithm does not have access during training (`X_test`). So, it has not been trained with it. These data reasonably illustrate the expected performance on new and unpublished data, such as what might be encountered in a production and live trading environment. This is a crucial point. We will come back later to the meaning and interpretation of the metrics (the higher, the better) we have in front of us.

The percentage of correct predictions for the class positive (`+1`: rising period) is much higher than the uninformed random prediction (coin toss), which in this case is 0.5. In fact, the precision is 0.78.

However, this is not the case for the other class (`-1`). The prediction of down periods is not good.

Now, we need to compare it with the metrics of the traditional cross-over system. The trading rule is implemented to calculate the associated performance metrics.

As mentioned in the introduction, the simplest possible rule is the cross-over rule, which can be expressed as follows:

```python
# cross-over rules : +1 MA(50 days) > MA(200) ; -1 : MA(50 days) < MA(200)
ma_cross = np.where(X_test['MA_cross'] > 0, 1, -1)
print(classification_report(ma_cross, y_test))
```

```
              precision    recall  f1-score   support

          -1.0       0.55      0.46      0.50       114
           1.0       0.41      0.50      0.45        86

    accuracy                           0.48       200
   macro avg       0.48      0.48      0.47       200
weighted avg       0.49      0.47      0.48       200
```

The cross-over system without the help of ML does not do - significantly - better than a random prediction. Metrics are around 50% (0.5).
