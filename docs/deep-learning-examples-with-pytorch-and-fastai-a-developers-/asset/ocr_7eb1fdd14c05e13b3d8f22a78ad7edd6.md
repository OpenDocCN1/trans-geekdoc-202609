```
learn.export('21-tabular-model.pkl')
del learn
learn = load_learner('21-tabular-model.pkl')
```

Now we build the new test-dataloader. This dataloader can or cannot include the y-values. We just need to pass in the y-values and get a labelled dataloader.

```
dl = learn.dls.test_dl(df.iloc[:100])
dl.show_batch()
```

workclass education marital-status occupation relationship race education-num _na age fnlwgt education-num salary

0 Private
1 Private
2 Private
3 Self-emp-inc
4 Self-emp-not-inc
5 Private
6 Private
7 Private
8 Private
9 Self-emp-inc Assoc-acdm Masters HS-grad Prof-school 7th-8th
HS-grad Some-college 11th
HS-grad HS-grad Married-civ-spouse Divorced
Divorced
Married-civ-spouse Married-civ-spouse Never-married Divorced
Married-civ-spouse Married-civ-spouse Married-civ-spouse #na#
Exec-managerial #na#
Prof-specialty Other-service Handlers-cleaners #na#
#na#
Craft-repair #na#
Wife White False 49.0 101319.997683 12.0 >=50k Not-in-family White False 44.0 236745.999632 14.0 >=50k Unmarried Black True 38.0 96185.000914 10.0 <50k Husband Asian-Pac-Islander False 38.0 112847.000492 15.0 >=50k Wife Black True 42.0 82297.000425 10.0 <50k Own-child White False 20.0 63209.999914 9.0 <50k Other-relative White False 49.0 44434.003696 10.0 <50k Husband White False 37.0 138939.998692 7.0 <50k Husband White False 46.0 328215.999739 9.0 >=50k Husband White True 36.0 216711.000929 10.0 >=50k

We can also drop the salary-column and still build our dataloader. This time the loader isn’t labelled.

```
df2 = df.iloc[:100].drop('salary', axis=1)
df2.head()
```

age workclass fnlwgt education education-num marital-status
0 49 Private 101320 Assoc-acdm 12.0 Married-civ-spouse
1 44 Private 236746 Masters 14.0 Divorced
2 38 Private 96185 HS-grad NaN Divorced