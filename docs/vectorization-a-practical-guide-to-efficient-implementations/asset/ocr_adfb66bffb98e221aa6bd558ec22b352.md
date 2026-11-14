```
faster way to compute Pearson's correlation
between each combination of pairs of two matrices
returns a cross-correlation matrix
[(x1:y1, x1:y2, x1:y3,..., x1:ym],
[x2:y1, x2:y2, x2:y3,..., x1:ym],
[...]
[xn:y1, xn:y2, xn:y3,..., xn:ym]
"""
X = X - np.mean(X, axis=0, keepdims=True) # zero mean
Y = Y - np.mean(Y, axis=0, keepdims=True) # zero mean
X = X / np.sqrt(np.sum(X**2, axis=0, keepdims=True)) # L2 normalization
Y = Y / np.sqrt(np.sum(Y**2, axis=0, keepdims=True)) # L2 normalization
R = X.T.dot(Y)
return R
```

Notice that the code was almost identical to what we implemented in Chapter 2, except in Line 15. Instead of doing element-wise multiplication and reducing along axis=1, we perform a matrix multiplication using the dot operator.

> **Note**
> I originally implemented this algorithm in MATLAB, so I kept the convention that each column corresponds to a feature. I also often apply this function to my pandas dataframe to compute feature cross-correlations, where each feature is also in a column of `pd.Series` within the data frame. However, it may not be the most efficient in NumPy since its vectors and matrices are stored using the row-major convention. Nonetheless, at least historically and for the majority of use cases, this custom cross-correlation function that I implemented here appears to be more efficient than `pd.DataFrame.corr`. We leave this as a homework exercise to compare the performance of `faster_cross_corr` with `pd.DataFrame.corr` and `np.corrcoef`.

# ## 4.6 Case Study: Hausdorff Distance

Back in 2012–2013, I was a research scientist doing schizophrenia studies using brain functional magnetic resonance imaging (fMRI) scans. A common problem with fMRI is that the patients undergoing a brain scan may move their heads, thus weakening the functional signal collected during the scan. As an analogy, this is