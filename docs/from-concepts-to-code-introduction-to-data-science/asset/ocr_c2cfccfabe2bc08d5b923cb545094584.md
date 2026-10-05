![](bbox=[0.2755, 0.1585, 0.7245, 0.4035])

# ## 10.1.1 Moving Average

A common technique for denoising the data is to smooth it with a moving average. A twenty-period moving average, for example, would compute the average price over rolling twenty-day windows. Typically, the first twenty days comprise the first window, days to twenty-one comprise the second window, and so on.

The pandas module provides a function for easily doing this, so we store the prices in a dataframe and call the rolling() function like this:

+   - steps = 100

```
 # create a dataframe, passing the data as a dictionary
df = pd.DataFrame({'time':range(steps), 'price':prices})

# append the moving average column
df['ma20'] = df.price.rolling(20).mean()
```

The stock price and moving average trajectories are shown in Figure 10.2. The moving average curve is smoother than the prices, which helps to see the trend. The moving average exhibits a lag, responding to movements. This is apparent when the stock price sharply dropped around time 60, while the moving average fell much more slowly. Finally, the moving average curve does not begin until time step 20, which matches the number of points used in the average. In general, a moving average with a longer term will require more points to begin, and it will induce less smoothing over the raw data.