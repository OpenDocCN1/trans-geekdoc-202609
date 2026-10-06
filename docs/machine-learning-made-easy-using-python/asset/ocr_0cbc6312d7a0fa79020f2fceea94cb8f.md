# DATA OPERATIONS

We can use a ndarray to create a pandas series

```
In [19]: import numpy
import pandas
ar = numpy.array([1,5,7])
sr = pandas.Series(data = ar, copy = True)
#is as same as sr = pandas.series(ar, copy = True)
print(sr)

0    1
1    5
2    7
dype: int32
```

We passed the ndarray as the data for the series [use of the data parameter isn't necessary, its just for better understanding] and also used the copy parameter to create a copy of the data. If you want to get the data, without the indexes use the values function

```
In [21]: import numpy
import pandas
ar = numpy.array([1,5,7])
sr = pandas.Series(ar)
print(sr.values)

[1 5 7]
```

You can print a more detailed version of the above using the array function

![](bbox=[0.118, 0.642, 0.856, 0.765])

You can use values or array function according to your needs whether you want just the values or summarized detail of the arrays in pandas series. Also note the difference in the array function in NumPy and Pandas.