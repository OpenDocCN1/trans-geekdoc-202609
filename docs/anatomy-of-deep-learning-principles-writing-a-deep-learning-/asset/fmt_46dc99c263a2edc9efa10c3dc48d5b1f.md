
![](EPUB/media/file144.png)

Figure 7-5 Training loss curve of 2-layer fully connected neural network

### 7.1.8 Long-term forecast and short-term forecast

For autoregressive sequence data, the output `x[T]` of the next time T can be predicted from the sample features composed of an initial real data sequence `x[0]`, `x[1]`, ⋯, `x[T−1]`, and then from `x[1]`, `x[2]`, ⋯, `x[T]` predict `x[T+1]`, predict `x[T+2]` from `x[2]`, `x[3]`, ⋯, `x[T+1]`, keep predicting like this. That is, the initial sequence `x[0]`, `x[1]`, ⋯, `x[T−1]` can be used to predict multiple subsequent moments. This type of forecast is called a **long-term forecast** (or **long-term forecast**). Since the prediction is not necessarily accurate, it will be more inaccurate to use the predicted value as the real value to predict the next value, that is, as time goes by, the error between the predicted value and the real value will become larger and larger. The other is **short-term forecasting**, the extreme case is that each moment always uses the real data corresponding to the time window of this moment (such as this moment and the previous T-1 moment) to predict the data of the next moment. Short-term prediction is because the input data samples are all real data and only predict the data at the next moment. The prediction effect is good, but the data used for prediction at each moment must be real data rather than the predicted data at the previous moment.

The following code adopts the method of long-term forecasting to predict the data of subsequent series of time points from the real data sample at the initial time point. And visually compare these predicted values with the corresponding target values of the test set. To observe the predictive performance of this model.

```
x = x_test[0].copy()
x = x.reshape(1,-1)
ys =[]
for i in range(400):
    y = nn.forward(x)   
    ys.append(y[0][0])
    x = np.delete(x,0,1)
    x = np.append(x, y.reshape(1,-1), axis=1)    
ys  = ys[:]
plt.plot(ys[:400])
plt.plot(y_test[:400])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y','y_real'])
```

![](EPUB/media/file145.png "fig:")  
Figure 7-6 Long-term forecasting with a trained model with time window length T=50

It can be seen that the predicted result is very close to the real target value, because this is a periodic curve, and T=50 is basically close to the period of the curve (`50*0.1 = 5` is close to `2*π`∼6.28). If the time window is relatively short, such as the prediction result when T=10 is shown in Figure 7-7, the prediction result will be poor.

And it can be found that the accuracy of the prediction is lower the further the future is, because the predicted value is used as the real data value to predict the value of the subsequent time, due to the continuous accumulation of errors, the error will become larger and larger.

![](EPUB/media/file146.png)

Figure 7-7 Long-term forecasting with a trained model with time window length T=10

The following code is to use the trained neural network for short-term prediction, that is, each time the real data is used to predict the data value of the next moment:

```
ys =[]
for i in range(400):
    x = x_test[i].copy()
    x = x.reshape(1,-1)
    y = nn.forward(x)   
    ys.append(y[0][0])   
ys  = ys[:]
plt.plot(ys[:400])
plt.plot(y_test[:400])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y','y_real'])
```

![](EPUB/media/file147.png)

Figure 7-8 Short-term forecasting with a training model with a time window length T=50

Obviously, short-term forecasts are more accurate.

### 7.1.9 Stock Price Prediction

Using the previous closing price of the stock as the sequence data, the time window method can also be used to sample training or test samples. The following code uses the time window of 100 to generate a training data set and a test data set, that is, use the price of the previous 100 days to predict the price of the next day.

```
x = np.array(data.iloc[:,-1])
print(x.shape)
x = x.reshape(-1,1)
print(x.shape)
x_train, y_train, x_test, y_test = gen_data_set(x, 100)
y_train = y_train.reshape(-1,1)
print(x_train.shape,y_train.shape)
```

```
(4697,)
(4697, 1)
(4136, 100, 1) (4136, 1)
```

Likewise, train a neural network model with the training set:

```
hidden_dim = 500
n = x_train.shape[1]
print("n",n)
nn = NeuralNetwork()
nn.add_layer(Dense(n, hidden_dim))
nn.add_layer(Relu())
nn.add_layer(Dense(hidden_dim, 1)) 
learning_rate = 0.1
momentum = 0.8 #0.9
optimizer = SGD(nn.parameters(),learning_rate,momentum)
epochs=60
batch_size = 500 # len(train_x) #200   
reg = 1e-6
print_n=50
losses = train_nn(nn,x_train,y_train,optimizer,util.mse_loss_grad,epochs,batch_size,reg,print_n)
plt.plot(losses)
```

```
n 100
0 iter: 0.04027576839624083
50 iter: 0.0005585708338086856
100 iter: 0.0004103264701123903
150 iter: 0.0003765723130633676
200 iter: 0.0003516184170804334
250 iter: 0.00035039658640954825
300 iter: 0.00030599817269094394
350 iter: 0.00031335621767435775
400 iter: 0.000308409636035205
450 iter: 0.0003134471927653575
```

![](EPUB/media/file148.png)

Figure 7-9 Network model training loss curve of stock data with time window length T=100

Use the first sample of the test set as a starting point for long-term prediction, that is, to continuously use the predicted value to construct new data features to predict the stock price of the next day:

```
x = x_test[0].copy()
x = x.reshape(1,-1)
ys =[]
num = 400
for i in range(num):
    y = nn.forward(x)    
    ys.append(y[0][0])
    x = np.delete(x,0,1)
    x = np.append(x, y.reshape(1,-1), axis=1)    
ys  = ys[:]
plt.plot(ys[:num])
plt.plot(y_test[:num])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y','y_real'])
```

![](EPUB/media/file149.png)

Figure 7-10 Long-term forecasting with a trained model with time window length T=100

The results show that for the sequence data with few regularities like stocks, even if the time window is large (100), the prediction results are not ideal. The following code uses short-term forecasting, that is, always uses the real data of the first 100 days to predict the stock price on the 101st day:

```
ys =[]
num = 400
for i in range(num):
    x = x_test[i].copy()
    x = x.reshape(1,-1)
    y = nn.forward(x) 
    ys.append(y[0][0])
    x = np.delete(x,0,1)
    x = np.append(x, y.reshape(1,-1), axis=1)    
ys  = ys[:]
plt.plot(ys[:num])
plt.plot(y_test[:num])
plt.xlabel("time")
plt.ylabel("value")
plt.legend(['y','y_real'])
```
