| name | survived | sex | age | class |
| :--- | :--- | :--- | :--- | :--- |
| Allen, Miss. Elisabeth Walton | yes | female | 29.00 | 1st |
| Allison, Master. Hudson Trevor | yes | male | 0.92 | 1st |
| Allison, Miss. Helen Loraine | no | female | 2.00 | 1st |
| Allison, Mr. Hudson Joshua Crei | no | male | 30.00 | 1st |
| Allison, Mrs. Hudson J C (Bessi | no | female | 25.00 | 1st |

# # 9.12.4 Simple Data Analysis with the Titanic Disaster Dataset

Now, you can use pandas to perform some simple analysis. For example, let’s look at some descriptive statistics. When you call `describe` on a DataFrame containing both numeric and non-numeric columns, `describe` calculates these statistics _only for the numeric columns_—in this case, just the `age` column:

```
```python
In [8]: titanic.describe()
Out[8]:
       age
count  1046.00
mean    29.88
std     14.41
min      0.17
25%     21.00
50%     28.00
75%     39.00
max     80.00
```
```

Note the discrepancy in the `count` (1046) vs. the dataset’s number of rows (1309—the last row’s index was 1308 when we called `tail`). Only 1046 (the `count` above) of the records contained an age value. The rest were _missing_ and marked as `NaN`, as in row 1305. When performing calculations, Pandas _ignores missing data_ (`NaN`) _by default_. For the 1046 people with valid ages, the average (`mean`) age was 29.88 years old. The youngest passenger (`min`) was just over two months old (0.17 * 12 is 2.04), and the oldest (`max`) was 80. The median age was 28 (indicated by the 50% quartile). The 25% quartile is the median age in the first half of the passengers (sorted by age), and the 75% quartile is the median of the second half of passengers.

Let’s say you want to determine some statistics about people who survived. We can compare the `survived` column to 'yes' to get a new Series containing `True`/`False` values, then use `describe` to summarize the results:

lick here to view code image

```
```python
In [9]: (titanic.survived == 'yes').describe()
```
```