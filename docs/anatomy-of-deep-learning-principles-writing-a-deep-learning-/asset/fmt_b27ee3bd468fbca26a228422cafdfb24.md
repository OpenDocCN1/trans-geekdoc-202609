
# 7.1.1 Stock Price Data and Sequence Prediction

```python
import pandas as pd

data = pd.read_csv('sp500.csv')

data.head()
```

**Output:**

```
Date Open High Low Close Volume
0 03-01-00 1469.250000 1478.000000 1438.359985 1455.219971 931800000
1 04-01-00 1455.219971 1455.219971 1397.430054 1399.420044 1009000000
2 05-01-00 1399.420044 1413.270020 1377.680054 1402.109985 1085500000
3 06-01-00 1402.109985 1411.900024 1392.099976 1403.449951 1092300000
4 07-01-00 1403.449951 1441.469971 1400.729980 1441.469971 1225200000
```

Among them, each column represents: date, opening price, highest price, lowest price, closing price, trading volume. In order to facilitate the training of machine learning algorithms, the data needs to be normalized. The following code normalizes data other than dates:

```python
data = data.iloc[:,1:6]
data = data.values.astype(float)
data = pd.DataFrame(data)
data = data.apply(lambda x: (x - np.mean(x)) / (np.max(x) - np.min(x)))
print(data[:3])
```

The above code for reading stock data can be expressed as a function:

```python
import pandas as pd

def read_stock(filename, normalize=True):    
    data = pd.read_csv(filename)
    data = data.iloc[:,1:6]
    data = data.values.astype(float)
    data = pd.DataFrame(data)   
    if normalize:
        data = data.apply(lambda x: (x - np.mean(x)) / (np.max(x) - np.min(x)))
    return data

data = read_stock('sp500.csv')
print(data[:3])
```

**Output:**

```
          0         1         2         3         4
0 -0.005973 -0.005916 -0.015676 -0.012310 -0.191184
1 -0.012266 -0.016172 -0.034017 -0.037249 -0.184230
2 -0.037292 -0.035058 -0.042867 -0.036047 -0.177338
```

Stock price forecasting is to predict the next day's stock price such as the closing price based on the historical stock data of each day, such as the opening price, the highest price, the lowest price, the closing price, and the trading volume. For this sequence data prediction problem, the data `x[t]` at each moment includes data characteristics such as opening price, highest price, lowest price, closing price, trading volume, etc. The target value `y[t]` to be predicted is the closing price of the stock on the next day.

If the data `x[t]` at each moment only contains the feature of the closing price, and the `y[t]` to be predicted is also the closing price, that is, they are the same type of data, then such a stock price prediction problem is an autoregressive problem. The following code plots a curve of closing prices:

```python
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline

x = np.array(data.iloc[:,-2])
print(x.shape)
plt.plot(x)
```

**Output:**

```
(4697,)
```

![](EPUB/media/file141.png)

**Figure 7-1 Stock Closing Price Trend Chart**

## 7.1.2 Probabilistic Sequence Model, Language Model

### 1. Probabilistic Sequence Model

The prediction problem of sequence data sometimes does not need to directly model the functional relationship between the sequence data and its target value, but predicts the probability of the target value according to the sequence data, that is, determines the following conditional probability:

`y[t] ~ p(y[t] | x[1], … x[t])`

That is, according to all the sequence data `(x[1], x[2], ⋯, x[t])` before `t`, the value probability of the target value `y[t]` is predicted. There are usually many or even infinite target values. The prediction problem is to determine each probability of possible `y[t]` values as target values. This kind of model that predicts the probability of the target value based on sequence data is called **probabilistic sequence model**. For autoregressive problems, this probabilistic sequence model is expressed as:

`x[t] ~ p(x[t] | x[1], … x[t−1])`

### 2. Language Model

The basis of natural language processing is to build a language model. The so-called language model is to model the probability of a sentence, that is, to determine the probability of a sentence appearing. For example, the probability of "I am Chinese" is obviously greater than that of "I am Chinese". A sentence is a series of words, which is an ordered sequence of words, such as "I am Chinese" is an ordered sequence composed of four words: "I", "Yes", "China", and "People". Suppose a sentence `S` is composed of words `w[1], w[2], w[3], ⋯, w[n]`, the probability of sentence `S` is represented by `P(w[1], w[2], w[3], ⋯, w[n])`. According to probability theory, this probability can be expressed as:

`P(w[1], w[2], w[3], ⋯, w[n]) = P(w[1]) * P(w[2]|w[1]) * P(w[3]|w[1], w[2]) * ⋯ * P(w[n]|w[1], w[2], ⋯, w[n−1])`

It is the product of the conditional probabilities of occurrences of a sequence of words. The probability of `w[1]` appearing first is `P(w[1])`, and the probability of `w[2]` appearing when `w[1]` appears is `P(w[2]|w[1])`. The probability of `w[3]` in the case of `w[1], w[2]` is `P(w[3]|w[1], w[2])`, and the probability of `w[n]` in the case of `⋯, w[1], w[2], ⋯, w[n−1]` is `P(w[n]|w[1], w[2], ⋯, w[n−1])`.

According to this formula (7-3), if these conditional probabilities can be known, that is, in the case of known words `w[1], w[2], ⋯, w[i−1]`, the probability of the next word `w[i]` appearing `P(w[i]|w[1], w[2], ⋯, w[i−1])`, you can know the probability of a sentence consisting of a series of words. Therefore, the language model is to predict the next word or the probability of each word in the word list based on the existing word sequence.

## 7.1.3 Autoregressive Model

For the prediction target at the current moment is the autoregressive problem of the data at the next moment, the established prediction model is called **autoregressive model** (**Auto regressive model**, referred to as **AR** model). This model can be a probabilistic sequence model or a functional model. If `x[t]` depends on `x[1], ⋯, x[t−1]`, the autoregressive model can be a function model `f : (x[1], ⋯, x[t−1]) → y[t]` or probability sequence model `P(x[t] | x[1], ⋯, x[t−1])`.

If the real data `x[t]` only depends on the data `(x[t−τ], ⋯, x[t−1])` at the previous fixed-length `τ` moment, then this sequence data is said to satisfy **Markov** properties. Such autoregressive models are also known as **Markov models**.

The simplest autoregressive model assumes that `x[t−τ], … x[t−1]` and `x[t]` satisfy a linear relationship:

`x[t] = a[0] + a[1]x[t−1] + ⋯ + a[τ]x[t−τ] + ϵ`

where `ϵ` is sampled random noise (also known as white noise).

## 7.1.4 Generate Autoregressive Data

When studying sequence models, we can use actual sequence data such as stock prices and natural language texts, or generate some simulated sequence data for sequence model research by means of simulation. For example, the following code forms a function by combining the sine function and the cosine function, and then samples the y-coordinate value of the function curve to form a sequence data:

```python
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline

def gen_seq_data_from_function(f, ts):
    return f(ts)

T = 5000
x = gen_seq_data_from_function(lambda ts: np.sin(ts*0.1) + np.cos(ts*0.2), np.arange(0, T))

plt.plot(x[:500])
plt.show()
```
