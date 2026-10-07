Name: price, dtype: float64

median price: 62000.0

correlation matrix:

| price | 1.000000 |
| lotsize | 0.535796 |
| bathrms | 0.516719 |
| stories | 0.421190 |
| garagepl | 0.383302 |
| Unnamed: 0 | 0.376000 |
| bedrooms | 0.366494 |

# PANDAS DATAFRAMES, NUMPY FUNCTIONS, AND LARGE DATASETS

Pandas DataFrames containing numeric data can be used in conjunction with NumPy functions such log, exp, and sqrt (and various other NumPy functions). Example of such functions are shown here:

```
df.exp(df)
np.asarray(df)
matrix multiplication:
df.T.dot(df)
```

The dot method on Series implements a dot product:

```
s1 = pd.Series(np.arange(5,10))
s1.dot(s1)
```

However, a Pandas DataFrame is not intended to be a direct replacement for ndarray as some of its indexing semantics are quite different from a matrix.