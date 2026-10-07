
# In [8]: housing.describe()

| | longitude | latitude | housing_median_age | total_rooms | total_bedrooms |
|---|---|---|---|---|---|
| count | 20640.00000 | 20640.00000 | 20640.00000 | 20640.00000 | 20433.00000 |
| mean | -119.569704 | 35.631861 | 28.639486 | 2635.763081 | 537.870533 |
| std | 2.003532 | 2.135952 | 12.586558 | 2181.615252 | 421.385070 |
| min | -124.350000 | 32.540000 | 1.000000 | 2.000000 | 1.000000 |
| 25% | -121.810000 | 33.930000 | 18.000000 | 1447.750000 | 296.000000 |
| 50% | -118.490000 | 34.260000 | 29.000000 | 2127.000000 | 435.000000 |
| 75% | -118.010000 | 37.710000 | 37.000000 | 3148.000000 | 647.000000 |
| max | -114.310000 | 41.950000 | 52.000000 | 3932.000000 | 6445.000000 |

Figure 2-7. Summary of each numerical attribute

The count, mean, min, and max rows are self-explanatory. Note that the null values are ignored (so, for example, count of total_bedrooms is 20,433, not 20,640). The row shows the standard deviation, which measures how dispersed the values are.¹

The 25%, 50%, and 75% rows show the corresponding percentiles: a percentile calculates the value below which a percentage of observation in a group of observations falls. For example, 25% of the districts have a housing_median_age longer than 18, while 50% are lower than 29 and 75% are lower than 37. These are often called the 25th percentile (or *1st quartile*), the median, and the 75th percentile (or *3rd quartile*).

Another way to get a feel of the type of data you are dealing with is to plot a histogram for each numerical attribute. A histogram shows the number of instances (on the vertical axis) that have a given value range (on the horizontal axis). You can either plot one attribute at a time, or you call the hist() method on the whole dataset, and it will plot a histogram for each numerical attribute (see Figure 2-8). For example, you can see that slightly over 800 districts have a median_house_value equal to $100,000.

```python
%matplotlib only in a Jupyter notebook
import matplotlib.pyplot as plt
housing.hist(bins=50, figsize=(20,15))
```

> 12 The standard deviation is generally denoted σ (the Greek letter sigma), and it is the square root of the variance, which is the average of the squared deviation from mean. When a feature has a bell-shaped normal distribution (also called a Gaussian distribution), which is very common, the '68-95-99.7%' rule applies about 68% of the values within 1σ of the mean, within 2σ, and 99.7% within 3σ.

The hist() method relies on Matplotlib, which in turn relies on a user-specified graphical backend to draw on your screen. Before you can plot anything, you need to specify which backend Matplotlib should use. The simplest option is to use Jupyter's magic command %matplotlib inline. This tells Jupyter to set up Matplotlib so it uses Jupyter's own backend. Plots are then rendered within the notebook. Note that calling show() is optional in a Jupyter notebook, as Jupyter will automatically display plots when a cell is executed.

![](img/0684d2da98e09085c0a622d4fd69aaad_78_0.png)

Figure 2-8. A histogram for each numerical attribute

Notice a few things in these histograms:

- 1. First, the median income attribute does not look like it is expressed in US dollars (USD). After checking with the team that collected the data, you are told that the data has been scaled and capped at 15 (actually 15.0001) for higher median incomes, and at 0.5 (actually 0.4999) for lower median incomes. The numbers represent roughly tens of thousands of dollars (e.g., 3 actually means about $30,000). Working with preprocessed attributes is common in Machine Learning, and it is necessarily a problem, but you should try to understand how the data was computed.

- 2. The housing median age and the median house value were also capped. The latter may be a serious problem if it is your target attribute (your labels). Your Machine Learning algorithms may learn that prices never go beyond limit. You need to check with your client team (the team that will use your system the output) to see if this is a problem or not. If you tell them that they need precise predictions beyond $500,000, then you have mainly two options:

    - a. Collect proper labels for the districts whose labels were capped.
    - b. Remove those districts from the training set (and also from the test set, your system should not be evaluated poorly if it predicts values beyond $500,000).

- 3. [Text seems to be fragmented/disrupted in original, but following context]

- 4. Finally, some histograms are different; we will discuss this later.

![](img/0684d2da98e09085c0a622d4fd69aaad_78_0.png)

Creating a Test Set

Wait, but this is not perfect: if you run the program again, it will generate a different test set, which is what you want to avoid. One solution is to save the test set on the first run and load it in subsequent runs. Another option is to set the random number generator's seed (e.g., np.random.seed(42)) before calling np.permutation(), so that always generates the same shuffled indices. Here is a possible implementation:

```python
import numpy as np
from zlib import crc32
```

```python
def test_set_check(identifier, test_ratio):
    return crc32(np.int64(identifier)) & 0xffffffff < test_ratio * 2***32
```

```python
def split_train_test_by_id(data, test_ratio, id_column):
    ids = data[id_column]
```

You can use this function like this:

```python
>>> train_set, test_set = split_train_test(housing, 0.2)
>>> len(train_set)
16512
>>> len(test_set)
4128
```
