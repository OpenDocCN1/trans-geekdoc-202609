could use loc to lock for rows matching a given date(range).

If we want to **select different columns** we just pass in one or many columns (or indices of columns).

```
df['survived'].head()
0 0 1 1 2 1 3 1 4 0 Name: survived, dtype: int64
df[['sex', 'age', 'survived']].head()
sex age survived

0 male 22.0 0
1 female 38.0 1
2 female 26.0 1
3 female 35.0 1
4 male 35.0 0
```

And to pass as an index, first do the number of rows followed by the column index

```
df.iloc[:,0:3]
survived pclass name

0 0 3 Braund, Mr. Owen Harris
1 1 1 Cumings, Mrs. John Bradley (Florence Briggs Thayer)
2 1 3 Heikkinen, Miss. Laina
3 1 1 Futrelle, Mrs. Jacques Heath (Lily May Peel)
4 0 3 Allen, Mr. William Henry .... .... .... ....
886 0 2 Montvila, Rev. Juozas 887 1 1 Graham, Miss. Margaret Edith
888 0 3 Johnston, Miss. Catherine Helen “Carrie”
889 1 1 Behr, Mr. Karl Howell 890 0 3 Dooley, Mr. Patrick

891 rows × 3 columns
```

# 21.1.3 Selection based on Values

We can also select rows by passing in some kind of condition:
df.loc[df['column_name'] == some_value]. E.g. let’s get a list of all *female* passengers: