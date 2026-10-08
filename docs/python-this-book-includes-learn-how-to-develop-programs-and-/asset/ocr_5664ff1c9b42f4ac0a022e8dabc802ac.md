```
>>> df2 = df2.reindex(['a0', 'a1', 'a10', 'a11', 'a20', 'a21',
'a30', 'a31', 'a40', 'a41'])

>>> df2
X Y Z
a0 -1.193371 0.912654 -0.780461
a1 NaN NaN NaN
a10 1.413044 0.615997 0.947334
a11 NaN NaN NaN
a20 1.583516 1.388921 0.458771
a21 NaN NaN NaN
a30 0.479579 1.427625 1.407924
a31 NaN NaN NaN
a40 0.455510 -0.880937 1.375555
a41 NaN NaN NaN
```

In case you would like to replace the null values in the df2 DataFrame with a zero value, then run the following command:

```
>>> df2.fillna(0)
X Y Z
a0 -1.193371 0.912654 -0.780461

a1 0.000000 0.000000 0.000000
a10 1.413044 0.615997 0.947334
a11 0.000000 0.000000 0.000000
a20 1.583516 1.388921 0.458771
a21 0.000000 0.000000 0.000000
a30 0.479579 1.427625 1.407924
a31 0.000000 0.000000 0.000000
a40 0.455510 -0.880937 1.375555
a41 0.000000 0.000000 0.000000
```

# String Operations

Sometimes you may want to change the string field column in your data.
Here's a technique that describes some of the string operations:

+   - Substring: let's begin by selecting the first five rows of the AREA NAME column within the data as the sample data to edit.

```
>>> df = pd.read_csv('Data/Student_Weight_Status_Category_Reporting_Results__Beginning_2010.csv')
>>> df['AREA NAME'][:5]
```