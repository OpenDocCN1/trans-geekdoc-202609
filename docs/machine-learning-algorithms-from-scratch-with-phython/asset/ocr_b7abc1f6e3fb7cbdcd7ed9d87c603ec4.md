The sample standard deviation is calculated as the mean difference from the mean value. This can be calculated as:

standard deviation = \(\sqrt{\frac{\sum_{i=1}^n (x_i - mean(x))^2}{count(x) - 1}}\) (12.3)

You can see that we square the difference between the mean and a given value, calculate the average squared difference from the mean, then take the square root to return the units back to their original value. Below is a small function named `standard_deviation()` that calculates the standard deviation of a list of numbers. You will notice that it calculates the mean. It might be more efficient to calculate the mean of a list of numbers once and pass it to the `standard_deviation()` function as a parameter. You can explore this optimization if you're interested later.

```
```python
from math import sqrt

# Calculate the standard deviation of a list of numbers
def stdev(numbers):
    avg = mean(numbers)
    variance = sum([(x-avg)**2 for x in numbers]) / float(len(numbers)-1)
    return sqrt(variance)
```
```

# Listing 12.6: Function To Calculate the Standard Deviation of a List of Numbers.

We require the mean and standard deviation statistics to be calculated for each input attribute or each column of our data. We can do that by gathering all of the values for each column into a list and calculating the mean and standard deviation on that list. Once calculated, we can gather the statistics together into a list or tuple of statistics. Then, repeat this operation for each column in the dataset and return a list of tuples of statistics.

Below is a function named `summarize_dataset()` that implements this approach. It uses some Python tricks to cut down on the number of lines required.

```
```python
# Calculate the mean, stdev and count for each column in a dataset
def summarize_dataset(dataset):
    summaries = [(mean(column), stdev(column), len(column)) for column in zip(*dataset)]
    del(summaries[-1])
    return summaries
```
```

# Listing 12.7: Function To Summarize Each Column in a Dataset.

The first trick is the use of the `zip()` function that will aggregate elements from each provided argument. We pass in the dataset to the `zip()` function with the `*` operator that separates the dataset (that is a list of lists) into separate lists for each row. The `zip()` function then iterates over each element of each row and returns a column from the dataset as a list of numbers. A clever little trick.

We then calculate the mean, standard deviation and count of rows in each column. A tuple is created from these 3 numbers and a list of these tuples is stored. We then remove the statistics for the class variable as we will not need these statistics. Let's test all of these functions on our contrived dataset from above. Below is the complete example.

```
```python
# Example of summarizing a dataset
from math import sqrt
```
```