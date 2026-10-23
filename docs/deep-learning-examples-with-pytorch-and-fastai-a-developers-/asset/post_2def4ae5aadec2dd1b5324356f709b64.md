
think of a Series-object as just one column of a dataframe.

- **on** is a column or index name to join on and must be found in both dataframes.
- **left_index and right_index** uses the respective input’s index to use as a key instead
- **how**: Either left, right, outer, or inner.

Let's try this and merge the two sub-dataframes on the name-column. Be careful when choosing your on-column.

```
merge = pd.merge(df1, df2, on='name')
merge.head()
```

sibsp_x parch ticket fare cabin embarked name survived pclass sex age sibsp_y
0 1 0 A/5 21171 7.2500 NaN S Braund, Mr. Owen Harris 0 3 male 22.0 1
1 1 0 PC 17599 71.2833 C85 C Cumings, Mrs. John Bradley (Florence Briggs Thayer) 1 1 female 38.0 1
2 0 0 STON/O2. 3101282 7.9250 NaN S Heikkinen, Miss. Laina 1 3 female 26.0 0
3 1 0 113803 53.1000 C123 S Futrelle, Mrs. Jacques Heath (Lily May Peel) 1 1 female 35.0 1
4 0 0 373450 8.0500 NaN S Allen, Mr. William Henry 0 3 male 35.0 0

## 21.2.2 Appending DataFrames

As long as the dataframes contain the same columns in the same order you can append one dataframe to another. This demo grabs the first five rows of our dataframe, then the next five rows and appends them together again.

```
df_top = df.iloc[:5]
df_bottom = df.iloc[5:10]
len(df_top), len(df_bottom)
(5, 5)
df_top.append(df_bottom)
```

survived pclass name
0 0 3 Braund, Mr. Owen Harris
1 1 1 Cumings, Mrs. John Bradley (Florence Briggs Thayer)
2 1 3 Heikkinen, Miss. Laina
3 1 1 Futrelle, Mrs. Jacques Heath (Lily May Peel)
4 0 3 Allen, Mr. William Henry
5 0 3 Moran, Mr. James
6 0 1 McCarthy, Mr. Timothy J
7 0 3 Palsson, Master. Gosta Leonard
8 1 3 Johnson, Mrs. Oscar W (Elisabeth Vilhelmina Berg)
9 1 2 Nasser, Mrs. Nicholas (Adele Achem)

sex age sibsp parch ticket fare cabin embarked

male 22.0 1 0 A/5 21171 7.2500 NaN S female 38.0 1 0 PC 17599 71.2833 C85 C
female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S female 35.0 1 0 113803 53.1000 C123 S

male 35.0 0 0 373450 8.0500 NaN S male NaN 0 0 330877 8.4583 NaN Q male 54.0 0 0 17463
51.8625 E46 S male 2.0 3 1 349909 21.0750 NaN S

female 27.0 0 2 347742 11.1333 NaN S female 14.0 1 0 237736 30.0708 NaN C

## 21.3 Dropping of Columns

You can drop a specific column by passing in the name or the index of the column into the drop-function. By default pandas will return the dropped table. If you choose to do inplace, it will directly modify the dataframe. You can also pass in an axis parameter. By default it is 1, which will drop a row. 0 drops a column.

```
# drop the first row
df_top.drop(0)
```

PANDAS DATAFRAME
survived pclass name

1 1 1 Cumings, Mrs. John Bradley (Florence Briggs Thayer)
2 1 3 Heikkinen, Miss. Laina
3 1 1 Futrelle, Mrs. Jacques Heath (Lily May Peel)
4 0 3 Allen, Mr. William Henry

```
# drop a column
df_top.drop('survived', axis=1)
```

sex age sibsp parch ticket fare cabin embarked female 38.0 1 0 PC 17599 71.2833 C85 C
female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S female 35.0 1 0 113803 53.1000 C123 S
male 35.0 0 0 373450 8.0500 NaN S
pclass name sex age sibsp parch ticket fare cabin embarked

0 3 Braund, Mr. Owen Harris male 22.0 1 0 A/5 21171 7.2500 NaN S
1 1 Cumings, Mrs. John Bradley (Florence Briggs Thayer) female 38.0 1 0 PC 17599 71.2833 C85 C
2 3 Heikkinen, Miss. Laina female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S
3 1 Futrelle, Mrs. Jacques Heath (Lily May Peel) female 35.0 1 0 113803 53.1000 C123 S
4 3 Allen, Mr. William Henry male 35.0 0 0 373450 8.0500 NaN S

```
# the original dataframe was not modified
df_top.head()
```

survived pclass name

0 0 3 Braund, Mr. Owen Harris
1 1 1 Cumings, Mrs. John Bradley (Florence Briggs Thayer)
2 1 3 Heikkinen, Miss. Laina
3 1 1 Futrelle, Mrs. Jacques Heath (Lily May Peel)
4 0 3 Allen, Mr. William Henry sex age sibsp parch ticket fare cabin embarked
male 22.0 1 0 A/5 21171 7.2500 NaN S female 38.0 1 0 PC 17599 71.2833 C85 C
female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S female 35.0 1 0 113803 53.1000 C123 S male 35.0
0 0 3 373450 8.0500 NaN S

## 21.4 Grouping (GroupBy)

The groupby should look familiar to you if you have some SQL experience.
In fact, the function works like the GROUP BY-clause in SQL. With groupby we can split the data into groups and perform an aggregation function (*like average, sum, etc.*) on the groups.

```
df_top.groupby(by=None, axis=0, level=None, as_index: bool=True, sort: bool=True, group_keys: bool=True, squeeze: bool=False, observed: bool=False)
```

Parameters:
- **by**: mapping, function, string or some iterable
- **axis**: default is 0
- **level**: If the axis is hierarchical, group by levels or a particular level
- **group_keys**: Add group keys to your index to identify pieces

As an example, let’s group by survived:

```
surv = df.groupby('survived')
```

The groupby-function does **not** return a DataFrame-object but a GroupBy-object. Therefore we have to handle the object differently.
Let’s look at the first item. We see the first item from each of the groups (survived vs. not survived).

```
surv.first()
```

pclass name sex age sibsp parch ticket fare cabin embarked
0 3 Braund, Mr. Owen Harris male 22.0 1 0 A/5 21171 7.2500 E46 S
1 1 Cumings, Mrs. John Bradley female 38.0 1 0 PC 17599 71.2833 C85 C (Florence Briggs Thayer)

If we want to access the data of the entire group, we simply call get_group(n):

```
surv.get_group(1)
```

pclass name sex age sibsp parch ticket fare cabin embarked
1 1 Cumings, Mrs. John Bradley female 38.0 1 0 PC 17599 71.2833 C85 C
(Florence Briggs Thayer)
2 3 Heikkinen, Miss. Laina female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S
3 1 Futrelle, Mrs. Jacques Heath female 35.0 1 0 113803 53.1000 C123 S (Lily May Peel)
8 3 Johnson, Mrs. Oscar W female 27.0 0 2 347742 11.1333 NaN S (Elisabeth Vilhelmina Berg)
9 2 Nasser, Mrs. Nicholas (Adele female 14.0 1 0 237736 30.0708 NaN C Achem)
.... .... .... .... .... .... .... 875 3 Najib, Miss. Adele Kiamie female 15.0 0 0 2667 7.2250 NaN C “Jane”
879 1 Potter, Mrs. Thomas Jr (Lily female 56.0 0 1 11767 83.1583 C50 C Alexenia Wilson)
880 2 Shelley, Mrs. William female 25.0 0 1 230433 26.0000 NaN S (Imanita Parrish Hall)
887 1 Graham, Miss. Margaret female 19.0 0 0 112053 30.0000 B42 S Edith
889 1 Behr, Mr. Karl Howell male 26.0 0 0 111369 30.0000 C148 C

342 rows × 10 columns

We can also group by more than one column, e.g. let’s group by sex and whether they survived or not:

```
surs = df.groupby(['survived', 'sex'])
```

```
surs.first()
```

sex pclass name age sibsp parch ticket fare cabin embarked
0 female 3 Vestrom, Miss. Hulda 14.0 0 0 350406 7.8542 C49 S Amanda Adolfina
male 3 Braund, Mr. Owen Harris 22.0 1 0 A/5 21171 7.2500 E46 S
1 female 1 Cumings, Mrs. John Bradley 38.0 1 0 PC 17599 71.2833 C85 C (Florence Briggs Thayer)
male 2 Williams, Mr. Charles Eugene 34.0 0 0 244373 13.0000 D56 S

## 21.5 Map Function

The map-function can be used to map values from two different series (columns) that share the same column. Basically we can repeat our adjust values, e.g. if

we look at the column survived. This column contains 0 and 1. Now we can make this column more readable if we map a dictionary and replace 0 by dead and 1 by survived.

```
df['survived'].head()
```

0 0
1 1
2 1
3 1
4 0
Name: survived, dtype: int64

```
df['survived'].map({0:'dead', 1:'survived'}).head()
```

0 dead
1 survived
2 survived
3 survived
4 dead
Name: survived, dtype: object

## 21.6 Apply Function

With the apply function we can run a specific function on every value in a Series-object. (Remember we mentioned that a Series-object is basically a

column from a DataFrame-object.

We can rebuild our example from the map and apply a function to each value of the survived column.

```python
def lived(num):
if num == 0: return "Died"
else: return "Survived"
```

```python
new = df['survived'].apply(lived)
new.head()
```

0 Died
1 Survived
2 Survived
3 Survived
4 Died
Name: survived, dtype: object

We can also apply the function directly using a lambda expression:

```python
new = df['survived'].apply(lambda x: "Died" if x == 0 else "Survived")
new.head()
```

0 Died
1 Survived
2 Survived
3 Survived
4 Died
Name: survived, dtype: object

## Chapter 22

### Tabular Data with FastAI

Now we want to use some fastai with the tabular data. For this example we have to import all of the tabular modules:

```
! pip install fastai
from fastai.tabular.all import *
```

In this notebook we will work with the ADULTS dataset. This dataset predicts if someone will make more or less than 50.000 USD a year.

```python
path = untar_data(URLs.ADULT_SAMPLE)
list(path.ls())
```
