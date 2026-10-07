![](bbox=[0.141, 0.101, 0.858, 0.545])

**Figure 5.8:** One image of each class of Traffic Signs in the dataset

Let us see the data point distribution among the different classes of Traffic Signs:

```
dfCounts = df[COLUMN_LABEL].value_counts().rename_axis(COLUMN_LABEL).
reset_index(name='counts')
```

```
fig = plt.figure(figsize=(20, 15))
plt.pie(dfCounts.counts, labels = dfCounts.Label, autopct='%1.2f%%')
plt.show()
```