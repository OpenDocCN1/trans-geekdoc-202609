The first two rows of the data are in p1, and the last three rows are in p2. These parts can be combined using the concat() function. For example:

```
>>> pd.concat([p1,p2])
```

The combined parts can be identified by allocating a key:

```
>>> concatenated = pd.concat([p1,p2], keys = ['p1','p2']
>>> concatenated
```

By applying the keys, the pieces can be extracted back from the combined data. For example:

```
>>> concatenated.ix['p1']
```

# Data Operations

Once you finish with the missing data, the different operations can be conducted on the data.

# Aggregation Operations

There are different aggregation operations like sum, average, and so forth, which you would like to conduct on a numerical field. Below are methods used to evaluate it:

+   - Average. To evaluate the average number of students in the ELEMENTARY school who are obese, first, you need to filter the ELEMENTARY data using the command below:

```
>>> data = df['GRADE LEVEL'] == 'ELEMENTARY']
213.41593780369291
```

Now, you can compute the mean using the command below:
>>> data['NO. OBESE'].mean()

The elementary grade level data is stored and filtered within the data object. The NO. OBESE column is chosen, which has the number of obese students and applying the mean () method; the average is determined.