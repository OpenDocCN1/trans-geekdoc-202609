sex age sibsp parch ticket fare cabin embarked

male 22.0 1 0 A/5 21171 7.2500 NaN S female 38.0 1 0 PC 17599 71.2833 C85 C
female 26.0 0 0 STON/O2. 3101282 7.9250 NaN S female 35.0 1 0 113803 53.1000 C123 S

male 35.0 0 0 373450 8.0500 NaN S male NaN 0 0 330877 8.4583 NaN Q male 54.0 0 0 17463
51.8625 E46 S male 2.0 3 1 349909 21.0750 NaN S

female 27.0 0 2 347742 11.1333 NaN S female 14.0 1 0 237736 30.0708 NaN C

# 21.3 Dropping of Columns

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