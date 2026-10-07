So, now we have 4,982 data points in 4,800 features.

# Balancing the dataset

We noticed 4,582 data points for clean JPEG files and 400 data points for JPEG containing malware. So is less than 10% of the clean JPEG files. Such datasets are called Imbalanced datasets.

Generally, any dataset regarding fraud is imbalanced. This is because the number of instances of fraud is very few compared to the cases of clean transactions. In the credit card fraud scenario, we may get less than 1% of the data regarding fraudulent transactions from a dataset of all the transactions.

Imbalanced datasets pose a problem: The class or classes of data with less representation may get less weighty by the algorithm. As a result, the classification generally becomes inaccurate. So, in most cases, we balance the dataset.

There are two ways to balance a dataset. The first way is called over-sampling. We try to create artificial data points for the class with fewer data points so that the data points in this class with fewer data points become the same (or almost the same) as the class with more data points. The other way is called under-sampling. In the under-sampling technique, we reduce the data points in the class with more data points so that the number of data points in all the classes becomes nearly the same.

In our case, we have only 5,000 data points; we cannot afford to reduce the number of data points. So, we will use the over-sampling technique.

An imbalanced dataset can be over-sampled using the algorithm Synthetic Minority Over-Sampling Technique (SMOTE). We will apply SMOTE to our dataset.

```
import imlearn as ib
```

```
# Transform the dataset
oversample = ib.over_sampling.SMOTE(random_state = 42)
X, y = oversample.fit_resample(X, y)
X.shape
(9164, 4800)
y.value_counts()
```