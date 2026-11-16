It can be downloaded/loaded using the
:func:`sklearn.datasets.fetch_california_housing` function.

.. topic:: References

- Pace, R. Kelley and Ronald Barry, Sparse Spatial Autoregressions,
Statistics and Probability Letters, 33 (1997) 291-297

gain, the Bunch object's data and target attributes are NumPy arrays containing
the 20,640 samples and their target values respectively. We can confirm the number of
samples (rows) and features (columns) by looking at the data array's shape attribute,
which shows that there are 20,640 rows and 8 columns:

lick here to view code image

```
In [4]: california.data.shape
Out[4]: (20640, 8)
```

Similarly, you can see that the number of target values—that is, the median house
values—matches the number of samples by looking at the target array's shape:

lick here to view code image

```
In [5]: california.target.shape
Out[5]: (20640,)
```

The Bunch's feature_names attribute contains the names that correspond to each
column in the data array:

lick here to view code image

```
In [6]: california.feature_names
Out[6]:
['MedInc',
'HouseAge',
'AveRooms',
'AveBedrms',
'Population',
'AveOccup',
'Latitude',
'Longitude']
```