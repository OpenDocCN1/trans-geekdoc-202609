Then I tried, 50 still not some convergence.

Finally I tried 100, and I observed some convergence of the loss.

So I 100 is the right number of epochs. For this problem, besides we don't have that data. We only have the Google stock price for 5 years.

batch_size: We set this so that our RNN trained on batches of observations/stock prices going into the NN. Instead of updating the weight for each epoch (stock price) using forward-propagation generating error and back-propagation, we do that, keep 32 stock prices.

If you can train this RNN on more than 5 years. The data is available, it is the Google stock price that can take from many financial sources. One of them is for example, Yahoo finance. Feel free to play with it and experiment even more to create some more robust RNN.

Anyway with 5 years of training well 10 epochs proved to be a good choice, with some convergence.

# All code at once (only fit)

Recurrent Neural Network: RNN

```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

```
# Data Preprocessing
dataset_train = pd.read_csv("Google_Stock_Price_Train.csv") # Notice train-set is now our main dataset
training_set = dataset_train.iloc[:1,2]:values
```

```
# feature scaling
from sklearn.preprocessing import MinMaxScaler
sc = MinMaxScaler(feature_range=(0, 1))
train_set_sled = sc.fit_transform(training_set)
```

```
print("Size of train set : {train_set_sled.shape}")
print(f"No. of data-points : {train_set_sled.shape[0]}")
```

```
# creating a structure with 60 time-steps and 1 output.
data_size = train_set_sled.shape[0]
X_train = []
y_train = []
```

```
for i in range(60, data_size):
X_train.append(train_set_sled[i-60:i,:]) # append a list of 60 data-points in list (data_size-60) rows
y_train.append(train_set_sled[i,0]) # vector of (data_size-60) rows
```

```
# Convert X_train and y_train to NumPy array.
X_train, y_train = np.array(X_train), np.array(y_train)
```

```
# Reshaping
X_train = np.reshape(X_train, (X_train.shape[0], X_train.shape[1], 1))
```

```
# Building RNN
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import LSTM
from keras.layers import Dropout
```

```
# Initialize the RNN
regressor_rnn = Sequential()
```

```
# adding LSTM Layer with Dropout-Regularization
regressor_rnn.add(LSTM(units=50, return_sequences=True, input_shape=X_train.shape[1], 1))
regressor_rnn.add(Dropout(rate=0.2))
```

```
# second LSTM with Dropout-Regularization
regressor_rnn.add(LSTM(units=50, return_sequences=True))
regressor_rnn.add(Dropout(rate=0.2))
```