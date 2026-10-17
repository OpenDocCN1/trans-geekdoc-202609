Running the example produces the following output. First, the dataset is printed in a list-of-lists format, then the min and max for each column is printed in the format column1: min,max and column2: min,max. For example:

```
[[50, 30], [20, 90]]
[[20, 50], [30, 90]]
```

# Listing 2.4: Output of Example Calculating the Min and Max Values.

Once we have estimates of the maximum and minimum allowed values for each column, we can now normalize the raw data to the range 0 and 1. The calculation to normalize a single value for a column is:

scaled value = \(\frac{value - min}{max - min}\) (2.1)

Below is an implementation of this in a function called normalize_dataset() that normalizes values in each column of a provided dataset.

```
# Rescale dataset columns to the range 0-1
def normalize_dataset(dataset, minmax):
    for row in dataset:
        for i in range(len(row)):
            row[i] = (row[i] - minmax[i][0]) / (minmax[i][1] - minmax[i][0])
```

# Listing 2.5: Function To Normalize a Dataset.

We can tie this function together with the dataset_minmax() function and normalize the contrived dataset.

```
# Find the min and max values for each column
def dataset_minmax(dataset):
    minmax = list()
    for i in range(len(dataset[0])):
        col_values = [row[i] for row in dataset]
        value_min = min(col_values)
        value_max = max(col_values)
        minmax.append([value_min, value_max])
    return minmax

# Rescale dataset columns to the range 0-1
def normalize_dataset(dataset, minmax):
    for row in dataset:
        for i in range(len(row)):
            row[i] = (row[i] - minmax[i][0]) / (minmax[i][1] - minmax[i][0])

# Contrive small dataset
dataset = [[50, 30], [20, 90]]
print(dataset)
# Calculate min and max for each column
minmax = dataset_minmax(dataset)
print(minmax)
# Normalize columns
normalize_dataset(dataset, minmax)
print(dataset)
```

# Listing 2.6: Example of Normalize the Contrived Dataset.