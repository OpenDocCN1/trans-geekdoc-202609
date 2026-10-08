The not null () function will display each row of the value as True or False. In case it's false, then there is a missing value. This particular data can be combined to count the number of missing value instances:

```
>>> d['Location 1'].isnull().value_counts()
```

The preceding command illustrates that the Location 1 column contains 24 instances of missing values. These missing values can be taken care of by removing the rows using missing values or substituting it with some values. To eliminate the rows, run the following command:

```
>>> d = d['Location 1'].dropna()
```

To remove all rows with an instance of missing values, the following command is useful:

```
>>> d = d.dropna(how='any')
```

# Complete the Missing Data

Let's define some DataFrames to use:

```
>>> df = pd.DataFrame(np.random.randn(5, 3), index=['a0', 'a10',
'a20', 'a30', 'a40'],
columns=['X', 'Y', 'Z'])
>>> df

X Y Z
a0  -0.854269 0.117540 1.515373
a10 -0.483923 -0.379934 0.484155
a20 -0.038317 0.196770 -0.564176
a30  0.752686 1.329661 -0.056649
a40 -1.383379 0.632615 1.274481
```

Next, add some extra row indexes, which will generate null values within the DataFrame: