# 2.2. Tutorial

```
# Estimate mean and standard deviation
means = column_means(dataset)
stdevs = column_stdevs(dataset, means)
print(means)
print(stdevs)
```

Listing 2.14: Example of Calculating Statistics from the Contrived Dataset.

Executing the example provides the following output, matching the numbers calculated in the spreadsheet.

```
[[50, 30], [20, 90], [30, 50]]
[33.333333333333336, 56.666666666666664]
[15.275252316519467, 30.550504633038933]
```

Listing 2.15: Example Output From Calculating Statistics from the Contrived Dataset.

Once the summary statistics are calculated, we can easily standardize the values in each column. The calculation to standardize a given value is as follows:

standardized_value_i = \frac{value_i - mean}{stdev} (2.4)

Below is a function named `standardize_dataset()` that implements this equation

```
# standardize dataset
def standardize_dataset(dataset, means, stdevs):
    for row in dataset:
        for i in range(len(row)):
            row[i] = (row[i] - means[i]) / stdevs[i]
```

Listing 2.16: Function To Standardize a Dataset.

Combining this with the functions to estimate the mean and standard deviation summary statistics, we can standardize our contrived dataset.

```
# Example of standardizing a contrived dataset
from math import sqrt

# calculate column means
def column_means(dataset):
    means = [0 for i in range(len(dataset[0]))]
    for i in range(len(dataset[0])):
        col_values = [row[i] for row in dataset]
        means[i] = sum(col_values) / float(len(dataset))
    return means

# calculate column standard deviations
def column_stdevs(dataset, means):
    stdevs = [0 for i in range(len(dataset[0]))]
    for i in range(len(dataset[0])):
        variance = [pow(row[i]-means[i], 2) for row in dataset]
        stdevs[i] = sum(variance)
    stdevs = [sqrt(x/(float(len(dataset)-1))) for x in stdevs]
    return stdevs

# standardize dataset
def standardize_dataset(dataset, means, stdevs):
```