
## Web resources

- 理解 LSTM https://colah.github.io/posts/2015-08-Understanding-LSTMs/.
- 情感分析的 LSTM 网络 http://deeplearning.net/tutorial/lstm.html.
- 使用 Python 和 Keras 的 LSTM 循环神经网络进行时间序列预测 https://machinelearningmastery.com/time-series-prediction-lstm-recurrent-neural-networks-python-keras/.
- 动画 RNN、LSTM 和 GRU https://towardsdatascience.com/animated-rnn-lstm-and-gru-ef124d06cf45

## 动手实践

### 1. 用于训练模型的 LSTM 代码

```
import numpy
import matplotlib.pyplot as plt
from pandas import read_csv
import math
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import LSTM
from sklearn.preprocessing import MinMaxScaler
from sklearn.metrics import mean_squared_error
# convert an array of values into a dataset_new matrix
def create_dataset_new(dataset_new, look_back=1):
    data_new_X, data_new_Y = [], []
    for i in range(len(dataset_new)-look_back-1):
        a = dataset_new[i:(i+look_back), 0]
        data_new_X.append(a)
        data_new_Y.append(dataset_new[i + look_back, 0])
    return numpy.array(data_new_X), numpy.array(data_new_Y)
# fix random seed for reproducibility
numpy.random.seed(7)
# load the dataset_new
dataframe = read_csv('airline-passengers.csv', usecols=[1],
engine='python')
dataset_new = dataframe.values
dataset_new = dataset_new.astype('float32')
# normalize the dataset_new
scaler = MinMaxScaler(feature_range=(0, 1))
dataset_new = scaler.fit_transform(dataset_new)
# split into train and test sets
train_size = int(len(dataset_new) * 0.67)
test_size = len(dataset_new) - train_size
train, test = dataset_new[0:train_size,:], dataset_new[train_size:len(dataset_new),:]
# reshape into X=t and Y=t+1
look_back = 1
train_new_X, train_new_Y = create_dataset_new(train, look_back)
test_new_X, test_new_Y = create_dataset_new(test, look_back)
# reshape input to be [samples, time steps, features]
train_new_X = numpy.reshape(train_new_X, (train_new_X.shape[0], 1,
train_new_X.shape[1]))
test_new_X = numpy.reshape(test_new_X, (test_new_X.shape[0], 1,
test_new_X.shape[1]))
# create and fit the LSTM network
model = Sequential()
model.add(LSTM(4, input_shape=(1, look_back)))
model.add(Dense(1))
model.compile(loss='mean_squared_error', optimizer='adam')
model.fit(train_new_X, train_new_Y, epochs=100, batch_size=1,
verbose=2)
# make predictions
train_Predict = model.predict(train_new_X)
test_Predict = model.predict(test_new_X)
# invert predictions
train_Predict = scaler.inverse_transform(train_Predict)
train_new_Y = scaler.inverse_transform([train_new_Y])
test_Predict = scaler.inverse_transform(test_Predict)
test_new_Y = scaler.inverse_transform([test_new_Y])
# calculate root mean squared error
train_Score = math.sqrt(mean_squared_error(train_new_Y[0], train_Predict[:,0]))
print('Train Score: %.2f RMSE' % (train_Score))
test_Score = math.sqrt(mean_squared_error(test_new_Y[0], test_Predict[:,0]))
print('Test Score: %.2f RMSE' % (test_Score))
# shift train predictions for plotting
train_Predict_Plot = numpy.empty_like(dataset_new)
train_Predict_Plot[:, :] = numpy.nan
train_Predict_Plot[look_back:len(train_Predict)+look_back, :] = train_Predict
# shift test predictions for plotting
test_Predict_Plot = numpy.empty_like(dataset_new)
test_Predict_Plot[:, :] = numpy.nan
test_Predict_Plot[len(train_Predict)+(look_back*2)+1:len(dataset_new)-1, :] = test_Predict
# plot baseline and predictions
plt.plot(scaler.inverse_transform(dataset_new))
plt.plot(train_Predict_Plot)
plt.plot(test_Predict_Plot)
plt.show()
```

### 2. 使用窗口方法进行回归的 LSTM

```
import numpy
import matplotlib.pyplot as plt
from pandas import read_csv
import math
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import LSTM
from sklearn.preprocessing import MinMaxScaler
from sklearn.metrics import mean_squared_error
# convert an array of values into a dataset_new matrix
def create_dataset_new(dataset_new, look_back=1):
    data_new_X, data_new_Y = [], []
    for i in range(len(dataset_new)-look_back-1):
        a = dataset_new[i:(i+look_back), 0]
        data_new_X.append(a)
        data_new_Y.append(dataset_new[i + look_back, 0])
    return numpy.array(data_new_X), numpy.array(data_new_Y)
# fix random seed for reproducibility
numpy.random.seed(7)
# load the dataset_new
dataframe = read_csv('airline-passengers.csv', usecols=[1],
engine='python')
dataset_new = dataframe.values
dataset_new = dataset_new.astype('float32')
# normalize the dataset_new
scaler = MinMaxScaler(feature_range=(0, 1))
dataset_new = scaler.fit_transform(dataset_new)
# split into train and test sets
train_size = int(len(dataset_new) * 0.67)
test_size = len(dataset_new) - train_size
train, test = dataset_new[0:train_size,:], dataset_new[train_size:len(dataset_new),:]
# reshape into X=t and Y=t+1
look_back = 3
train_new_X, train_new_Y = create_dataset_new(train, look_back)
test_new_X, test_new_Y = create_dataset_new(test, look_back)
# reshape input to be [samples, time steps, features]
train_new_X = numpy.reshape(train_new_X, (train_new_X.shape[0], 1,
train_new_X.shape[1]))
test_new_X = numpy.reshape(test_new_X, (test_new_X.shape[0], 1,
test_new_X.shape[1]))
# create and fit the LSTM network
model = Sequential()
model.add(LSTM(4, input_shape=(1, look_back)))
model.add(Dense(1))
model.compile(loss='mean_squared_error', optimizer='adam')
model.fit(train_new_X, train_new_Y, epochs=100, batch_size=1,
verbose=2)
# make predictions
train_Predict = model.predict(train_new_X)
test_Predict = model.predict(test_new_X)
# invert predictions
train_Predict = scaler.inverse_transform(train_Predict)
train_new_Y = scaler.inverse_transform([train_new_Y])
test_Predict = scaler.inverse_transform(test_Predict)
test_new_Y = scaler.inverse_transform([test_new_Y])
# calculate root mean squared error
train_Score = math.sqrt(mean_squared_error(train_new_Y[0], train_Predict[:,0]))
print('Train Score: %.2f RMSE' % (train_Score))
test_Score = math.sqrt(mean_squared_error(test_new_Y[0], test_Predict[:,0]))
print('Test Score: %.2f RMSE' % (test_Score))
# shift train predictions for plotting
train_Predict_Plot = numpy.empty_like(dataset_new)
train_Predict_Plot[:, :] = numpy.nan
train_Predict_Plot[look_back:len(train_Predict)+look_back, :] = train_Predict
# shift test predictions for plotting
test_Predict_Plot = numpy.empty_like(dataset_new)
test_Predict_Plot[:, :] = numpy.nan
test_Predict_Plot[len(train_Predict)+(look_back*2)+1:len(dataset_new)-1, :] = test_Predict
# plot baseline and predictions
plt.plot(scaler.inverse_transform(dataset_new))
plt.plot(train_Predict_Plot)
plt.plot(test_Predict_Plot)
plt.show()
```

### 3. 使用时间戳进行回归的 LSTM

```
import numpy
import matplotlib.pyplot as plt
from pandas import read_csv
import math
from keras.models import Sequential
from keras.layers import Dense
from keras.layers import LSTM
from sklearn.preprocessing import MinMaxScaler
from sklearn.metrics import mean_squared_error
# convert an array of values into a dataset_new matrix
def create_dataset_new(dataset_new, look_back=1):
    data_new_X, data_new_Y = [], []
    for i in range(len(dataset_new)-look_back-1):
        a = dataset_new[i:(i+look_back), 0]
        data_new_X.append(a)
        data_new_Y.append(dataset_new[i + look_back, 0])
    return numpy.array(data_new_X), numpy.array(data_new_Y)
# fix random seed for reproducibility
numpy.random.seed(7)
# load the dataset_new
dataframe = read_csv('airline-passengers.csv', usecols=[1],
engine='python')
dataset_new = dataframe.values
dataset_new = dataset_new.astype('float32')
# normalize the dataset_new
scaler = MinMaxScaler(feature_range=(0, 1))
dataset_new = scaler.fit_transform(dataset_new)
# split into train and test sets
train_size = int(len(dataset_new) * 0.67)
test_size = len(dataset_new) - train_size
train, test = dataset_new[0:train_size,:], dataset_new[train_size:len(dataset_new),:]
# reshape into X=t and Y=t+1
look_back = 3
train_new_X, train_new_Y = create_dataset_new(train, look_back)
test_new_X, test_new_Y = create_dataset_new(test, look_back)
```
