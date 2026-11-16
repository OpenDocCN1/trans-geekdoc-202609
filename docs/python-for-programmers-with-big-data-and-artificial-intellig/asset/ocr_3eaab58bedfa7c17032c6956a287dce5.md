you make predictions with an overfit model, new data that matches the training
data will produce perfect predictions, but the model will not know what to do with
data it has never seen.

For additional information on underfitting and overfitting, see

+   • https://en.wikipedia.org/wiki/Overfitting

+   • https://machinelearningmastery.com/overfitting-and-
+   nderfitting-with-machine-learning-algorithms/

# # 14.5 CASE STUDY: MULTIPLE LINEAR REGRESSION WITH THE CALIFORNIA HOUSING DATASET

In Chapter 10's Intro to Data Science section, we performed simple linear regression on
a small weather data time series using pandas, Seaborn's regplot function and the
SciPy's stats module's linregress function. In the previous section, we
reimplemented that same example using scikit-learn's LinearRegression estimator,
Seaborn's scatterplot function and Matplotlib's plot function. Now, we'll perform
linear regression with a much larger real-world dataset.

The California Housing dataset 7 bundled with scikit-learn has 20,640 samples,
each with eight numerical features. We'll perform a multiple linear regression that uses
all eight numerical features to make more sophisticated housing price predictions than
if we were to use only a single feature or a subset of the features. Once again, scikit-
learn will do most of the work for you—LinearRegression performs multiple linear
regression by default.

7 http://lib.stat.cmu.edu/datasets. Pace, R. Kelley and Ronald Barry,
Sparse Spatial Autoregressions, Statistics and Probability Letters, 33 (1997) 291-297.
Submitted to the StatLib Datasets Archive by Kelley Pace
( pace@unix1.sncc.lsu.edu). [9/Nov/99].

We'll visualize some of the data using Matplotlib and Seaborn, so launch IPython with
Matplotlib support:

```
ipython --matplotlib
```

# ## 14.5.1 Loading the Dataset