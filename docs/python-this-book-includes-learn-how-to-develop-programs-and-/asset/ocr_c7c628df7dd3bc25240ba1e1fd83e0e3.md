```
df['NO. OBESE'].groupby(d['GRADE LEVEL']).sum()
GRADE           LEVEL
DISTRICT TOTAL  127101
ELEMENTARY      72880
MIDDLE/HIGH     53089
```

This command selects the number of obese students column and then applies the group by a method to group the data-based group level, and lastly, the sum method totals the number. The same can be accomplished using the function below:

```
df['NO. OBESE'].groupby(d['GRADE LEVEL']).aggregate(sum)
```

In the above case, the aggregate method is applied. The sum function is passed on acquiring the results. It's also possible to get multiple types of aggregations on the same metric. This can be accomplished by the following command:

```
df['NO. OBESE'].groupby(d['GRADE LEVEL']).aggregate([sum, mean, std])
sum mean std
```

To summarize, this chapter has explored the basics of NumPy and pandas packages. You have learned the various datatypes in pandas and how to clean data and modify data. This chapter provides you with the foundation for data science, and you can explore deeper into NumPy and pandas. In the next chapter, we shall look at inferential statistics and how you can create meaning from different concepts in inferential statistics.