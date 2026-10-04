# CHAPTER 2 Exploring tabular datasets

featured in the 1983 American Statistical Association Exposition (https://mng.bz/Iya8) and the works of Ross Quinlan, Ross Quinlan is a major contributor to the development of the decision tree algorithm and the creator of the C4.5 ID3 algorithms. He quotes this dataset in 1993 paper “Combining Instance-Based and Model-Based Learning”(https://mng.bz/Bxx8), a milestone paper on regression problems in machine learning. For our purposes, it is a simple, manageable example because of its set of features and some missing data to be handled in the mpg and horsepower features.

The following is a list of the available features in the dataset:

+   - mpg: continuous
- cylinders: multivalued discrete
- displacement: continuous
- horsepower: continuous
- weight: continuous
- acceleration: continuous
- model year: multivalued discrete
- origin: multivalued discrete

+   - car name: string (unique for each example, it can be used as an index in a pandas DataFrame

In our example, the list is short, but the available features can last dozens of pages in most complex tabular datasets.

To upload our example dataset, we refer to the following list that will connect to the UCI repository, and it will dump the data into a pandas DataFrame.

# Listing 2.7 Download of Auto MPG Set from UCI repository

| StringIO reads and writes an in-memory buffer. | Requests is an HTTP library that can help you recover data from the web. |
|--- |--- |
| from import StringIO
import pandas as pd | |

```
url = "https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/"
data = "auto-mpg.data-original"
columns = ["mpg","cylinders","displacement","horsepower","weight","acceleration","model_year","origin","car_name"]
colcspecs = [(0, 4), (6, 9), (12, 17), (23, 28), (34, 39), (45, 49), (52, 55), (57, 59), (61, -21)]
data_ingestion = StringIO
```

> Derived from the documentation on the UCI machine learning repository Fixed-width data requires providing each feature with its start and end position in the input.