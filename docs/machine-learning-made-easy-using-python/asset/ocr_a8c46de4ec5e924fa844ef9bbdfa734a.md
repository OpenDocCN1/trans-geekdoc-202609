To get a element from a pandas series, we use the <series>[<explicit_index> or <implicit_index> syntax

```
In [4]: import pandas as pan
sr = pan.Series([1, 3, 5], index = ['a','b','c'])

print(sr['a']) #Implicit indexing
print(sr[0])    #Explicit indexing
```

If you have indexes like numbers like these

```
In [6]: import pandas as pan
sr = pan.Series([1, 3, 5], index = [2,4,6])
```

If you want the second element using the implicit index [indexing defined in index parameter] use <series>.loc<label> syntax and using the explicit indexing [ 0,1,2,... ] use <series>.iloc<index> syntax syntax

```
In [7]: import pandas as pan
sr = pan.Series([1, 3, 5], index = [2,4,6])

print(sr.loc[4])
print(sr.iloc[1])
```

We can modify or delete the elements using slicing

```
In [9]: import pandas as pan
sr = pan.Series([1, 3, 5], index = [2,4,6])

sr[4] = 7
print(sr)

del sr[6]
print(sr)

2    1
4    7
6    5
dype: int64
2    1
4    7
dype: int64
```