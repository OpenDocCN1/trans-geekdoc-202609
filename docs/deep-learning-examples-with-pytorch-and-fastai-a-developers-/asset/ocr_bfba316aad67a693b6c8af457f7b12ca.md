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

sex pclass name age sibsp parch ticket fare cabin embarked 0 female 3 Vestrom, Miss. Hulda 14.0 0 0 350406 7.8542 C49 S Amanda Adolfina male 3 Braund, Mr. Owen Harris 22.0 1 0 A/5 21171 7.2500 E46 S 1 female 1 Cumings, Mrs. John Bradley 38.0 1 0 PC 17599 71.2833 C85 C (Florence Briggs Thayer) male 2 Williams, Mr. Charles Eugene 34.0 0 0 244373 13.0000 D56 S

# 21.5 Map Function

The map-function can be used to map values from two different series (columns) that share the same column. Basically we can repeat our adjust values, e.g. if PANDAS DATAFRAME

we look at the column survived. This column contains 0 and 1. Now we can make this column more readable if we map a dictionary and replace 0 by dead and 1 by survived.

```
df['survived'].head()
```

0 0 1 1 2 1 3 1 4 0 Name: survived, dtype: int64

```
df['survived'].map({0:'dead', 1:'survived'}).head()
```

0 dead 1 survived 2 survived 3 survived 4 dead Name: survived, dtype: object

# 21.6 Apply Function

With the apply function we can run a specific function on every value in a Series-object. (Remember we mentioned that a Series-object is basically a