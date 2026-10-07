```
print("contents of foo2:")
print(df.foo2)
```

Listing 3.5 defines the Pandas DataFrame df that consists of 5
rows and 2 columns (labeled "foo1" and "foo2") of random real
numbers between 0 and 5. The next portion of Listing 3.5 displays
t contents of df and foo1. The output of Listing 3.5 is here:

```
contents of df:
foo1           foo2
0  0.274680 -0.848669
1  0.399771 -0.814679
2  0.454443 -0.363392
3  0.473753  0.550849
4 -0.211783 -0.015014
contents of foo1:
0  0.256773
1  1.204322
2  1.040515
3  -0.518414
4  0.634141
Name: foo1, dtype: float64
contents of foo2:
0  -2.506550
1  -0.896516
2  -0.222923
3  0.934574
4  0.527033
Name: foo2, dtype: float64
```

# COMBINING PANDAS DATRAMES (2)

Pandas supports the "concat" method in DataFrames in order
to concatenate DataFrames. Listing 3.6 displays the contents of