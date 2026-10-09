It is called supervised learning because the process of an algorithm learning from the training dataset can be thought of as a teacher supervising the learning process. We know the correct answers; the algorithm iteratively makes predictions on the training data and is corrected by making updates. Learning stops when the algorithm achieves an acceptable level of performance. Supervised learning problems can be further grouped into regression and classification problems.

+   * **Classification:** A classification problem is when the output variable is a category, such as **red** and **blue** or **disease** and **no disease**.
* **Regression:** A regression problem is when the output variable is a real value, such as **dollars** or **weight**. The contrived example above is a regression problem.

# ## 3.2 Sliding Window

Time series data can be phrased as supervised learning. Given a sequence of numbers for a time series dataset, we can restructure the data to look like a supervised learning problem. We can do this by using previous time steps as input variables and use the next time step as the output variable. Let’s make this concrete with an example. Imagine we have a time series as follows:

```
```
time, measure
1,   100
2,   110
3,   108
4,   115
5,   120
```
```

Listing 3.2: Example of a small contrived time series dataset.

We can restructure this time series dataset as a supervised learning problem by using the value at the previous time step to predict the value at the next time-step. Re-organizing the time series dataset this way, the data would look as follows:

```
```
x,    y
?,    100
100, 110
110, 108
108, 115
115, 120
120, ?
```
```

Listing 3.3: Example of time series dataset as supervised learning.

Take a look at the above transformed dataset and compare it to the original time series. Here are some observations:

+   * We can see that the previous time step is the input (X) and the next time step is the output (y) in our supervised learning problem.
* We can see that the order between the observations is preserved, and must continue to be preserved when using this dataset to train a supervised model.
* We can see that we have no previous value that we can use to predict the first value in the sequence. We will delete this row as we cannot use it.