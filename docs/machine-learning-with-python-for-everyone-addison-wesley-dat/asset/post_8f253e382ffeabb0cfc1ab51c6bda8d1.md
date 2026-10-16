
concrete, but what is the fixed value we are using to convert these? Well, that comes from the formula for converting temperatures: C = 5(F-32)/9. A little algebra turns that into C = 5/9 F − 17.7, which is our friendly old y = mx + b in a different form. If you never noticed, converting values with a linear formula simply stretches and shifts the values; m is responsible for the stretching and b is responsible for the shift.

In [2]:

```
fig, ax = plt.subplots(1,1,figsize=(4,3))
f_temps = np.linspace(0, 212, 100)
c_temps = (5/9) * (f_temps - 32)
plt.plot(f_temps, f_temps, 'r',  # F -> F
    f_temps, c_temps, 'b');  # F -> C
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_354_0.png)

Notice how the upper red line is compressed vertically from 0 to 212 to around −18 to 100 on the lower blue line. The central value also moves from 106 to 59. Outside of unit conversions—Celsius to Fahrenheit or meters to feet—the most common fixed scalings are mapping {min, max} values to {0, 1} or to {−1, 1} and spreading the other values out evenly between them.

Standardization, a statistical rescaling, is a bit trickier. Instead of stretching out from the source to the target based on a fixed, prior value (like 5/9 to convert Fahrenheit to Celsius), it compresses values based on the spread—measured by the variance or standard deviation—of the source values. The difference is probably best explained with a graphic. Here we use sklearn’s StandardScaler to do the heavy lifting. fit_transform evaluates the training data and modifies it in one go. It is similar to our usual model.fit().predict() except it does not use a separate target in the fit() step. It simply learns—in this case, a mean and a standard deviation—and then applies itself to them. After being fit, it can also transform testing data. I’ve colored bins of data points so you can see how the points move around due to the transformation.

In [3]:
fig, ax = plt.subplots(1,1,figsize=(4,3))
original = np.random.uniform(-5, 5, 100)
scaled = skpre.StandardScaler().fit_transform(original.reshape(-1,1))[:,0]
bins = np.floor(original).astype(np.uint8) + 5

df = pd.DataFrame({'original':original,
                   'scaled':scaled,
                   'hue':bins})
df = pd.melt(df, id_vars='hue', var_name='scale')
sns.swarmplot(x='scale', y='value', hue='hue', data=df).legend_.remove()
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_355_0.png)

Here, the unit of measurement isn’t Fahrenheit or Celsius: it’s units of the standard deviation. The standard deviation tells us about the spread of our data. The more spread-out our data is, the bigger the standard deviation is. We are still on a linear scale after we standardize. That might be surprising. Here’s the formula: scaled = (orig−mean(orig))/stdev(orig) = 1/stdev(orig) orig − mean(orig)/stdev(orig). There’s a y = mx + b hidden in there. The new center of our data is zero.

In a curious twist of events, standardization doesn’t change the overall shape of the data—it may not look the same at first sight, but here’s another take. In our example, we had data from a uniform or flat-ish distribution. When we standardize it, it is still uniform. Visually, the shape has relatively flat sides. It just happens to be more compressed. As another example—try it yourself—if the data looks like a two-humped camel and we standardize it, it would still have two humps. Basically, we can evenly stretch or squeeze the graph of the data, but we can’t distort it more than that.

Let’s look into the how of scaling. Here are simple examples of MinMaxScaler and StandardScaler. To follow the example points as they move around, I’m going to color them by their percentile bin. I’m using Pandas cut method to do this. I don’t want to get
hung up on that, but just know that it is similar to the encoding technique we used when we made our piecewise constant regression model in Section 9.3. Here, we make use of Pandas *categorical* capabilities to create a coloring value:

In [4]:

```
```python
iris_df = pd.DataFrame(iris.data, columns=iris.feature_names)

bins = pd.cut(iris_df['sepal width'],
    np.percentile(iris_df['sepal width'],
        [25, 50, 75, 100])).cat.codes

df = pd.DataFrame({'orig':iris_df['sepal width'],
    'hue':bins})

scalers = [('std', skpre.StandardScaler()),
    ('01', skpre.MinMaxScaler()),
    ('-1,1', skpre.MinMaxScaler((-1,1)))]

for name, scaler in scalers:
    # ugly: [[]] to keep 2D for sklearn
    # reshape(-1) to go back to 1D for seaborn :(
    df[name] = scaler.fit_transform(df[['orig']]).reshape(-1)

df = pd.melt(df, id_vars='hue', var_name='scale')
sns.swarmplot(x='scale', y='value', hue='hue', data=df).legend_.remove()
```
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_356_0.png)

The most common motivation for rescaling is that we don't want arbitrary measurement scales to influence our outcomes. For example, if we measure someone's height in meters, instead of nanometers, the values will be much smaller—one meter is an awful lot of nano-whatevers. But that shouldn't really effect the fundamental information in the measurements. The easiest way to keep things fair between values measured on very different scales is to rescale them to an approximately common scale. Another example occurs when different types of measurements are in the same model. For example, household income is often tens of thousands of dollars—but cars per household is typically measured in single digits. Numerically, these values have very different weight. We offset that by placing them on a common scale. Some of the benefits of rescaling become more prominent when we move beyond predictive modeling and start making statistical or causal claims.

## 10.4 Discretization

We’ve already seen discretization—the process of sorting a range of continuous values into some finite, or discrete, buckets of values—when we implemented piecewise constant regression. There, we had to pick an output value—a line segment—based on the input value’s bucket. Discretization also shows up as part of decision tree value splits: height > 5’7” is either true or false. There are a number of automated methods for discretizing data; some of them look at the relationship between a feature’s values, the ideal split points to break those features at, and the value of those breaks to good classification. It is crucial that these methods be used inside of cross-validation to prevent overfitting on the training data. You can think of sufficiently advanced discretization strategies as micro-learners of their own—imagine if they could discretize right into the correct classification buckets! For now, let’s consider some manual approaches to discretization with the iris data.

In [5]:

```
iris_df = pd.DataFrame(iris.data, columns=iris.feature_names)
iris_df['species'] = iris.target_names[iris.target]
display(iris_df.iloc[[0,50,100]])
```

|  | sepal length | sepal width | petal length | petal width | species |
|---|---|---|---|---|---|
| 0 | 5.1000 | 3.5000 | 1.4000 | 0.2000 | setosa |
| 50 | 7.0000 | 3.2000 | 4.7000 | 1.4000 | versicolor |
| 100 | 6.3000 | 3.3000 | 6.0000 | 2.5000 | virginica |

If we look at a smoothed plot of the sepal lengths, we see it is a pretty well-behaved bump.

In [6]:

plt.subplots(1,1,figsize=(4,3))
ax = sns.distplot(iris_df['sepal length'], hist=False, rug=True)
ax.set_ylabel("Approximate %");
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_358_0.png)

A simple way to discretize is to break the values into low and high at the mean or median.

In [7]:

```
# apply binary threshold to numeric with sklearn is tricky
column = iris_df[['sepal length']] # keep 2Dness because sk complains
col_mean = column.mean().values   # and sk fails with Series/DF

both = column.copy()
both['> Mean'] = skpre.binarize(column, col_mean).astype(np.bool)

print('Column Mean:', col_mean)
display(both.iloc[[0,50,100]])
```

Column Mean: [5.8433]

|  | sepal length | > Mean |
|---|---|---|
| 0 | 5.1000 | False |
| 50 | 7.0000 | True |
| 100 | 6.3000 | True |

We can also do the same discretization using the pd.cut function we showed off a minute or two ago.
