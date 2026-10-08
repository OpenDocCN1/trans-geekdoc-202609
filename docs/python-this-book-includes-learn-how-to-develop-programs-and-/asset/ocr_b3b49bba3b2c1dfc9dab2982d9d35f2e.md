```
>>> height_data = np.array([ 186.0, 180.0, 195.0, 189.0, 191.0,
177.0, 161.0, 177.0, 192.0, 182.0, 185.0, 192.0,
173.0, 172.0, 191.0, 184.0, 193.0, 182.0, 190.0, 185.0, 181.0,
188.0, 179.0, 188.0,
170.0, 179.0, 180.0, 189.0, 188.0, 185.0, 170.0, 197.0, 187.0,
182.0, 173.0, 179.0,
184.0, 177.0, 190.0, 174.0, 203.0, 206.0, 173.0, 169.0, 178.0,
201.0, 198.0, 166.0,
171.0, 180.0])
```

When you plot the distribution, it contains a normal distribution:

```
>>> plt.hist(height_data, 30, normed=True)
>>> plt.show()
```

The average of the distribution includes:
>>> height_data.mean()
183.24000000000001

Therefore, the mean height of a man from the sample is 183.4 cm.
To compute the confidence interval, you'll now define the standard error of the mean.

The standard error of the mean refers to the derivation of the sample mean from the population mean. It's defined by applying the following formula:

$SE_{\bar{x}} = \frac{s}{\sqrt{n}}$

In the following case, s refers to standard deviation of the sample, and n is the number of elements within the sample.
This can be computed using the following sem() function of the SciPy package:

```
>>> stats.sem(height_data)
1.37871871900005252
```

Thus, there is a normal error of the mean of 1.38cm. The lower and upper limit of the confidence interval can be computed by entering this formula.

```
Upper/Lower limit = mean(height) + / - sigma * SEmean(x)
```