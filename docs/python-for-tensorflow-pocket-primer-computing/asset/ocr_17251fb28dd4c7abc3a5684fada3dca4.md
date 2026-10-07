```
>>> s = pd.Series(data, index=index)
```

However, if no index is passed, an index will be automatically created with the values [0, ..., len(data) - 1]. Here is another example:

```
>>> s = pd.Series(np.random.randn(5), index=['a', 
'b', 'c', 'd', 'e'])
>>> s
```

The output of the preceding code snippet in the Python REPL here:

```
a 0.4691
b -0.2829
c -1.5091
d -1.1356
e 1.2121
dype: float64
>> s.index
```

The output of the preceding code snippet in the Python REPL here:

```
Index(['a', 'b', 'c', 'd', 'e'], dtype='object')
>>> pd.Series(np.random.randn(5))
```

The output of the preceding code snippet in the Python REPL here:

```
0 -0.1732
1 0.1192
2 -1.0442
3 -0.8618
4 -2.1046
```