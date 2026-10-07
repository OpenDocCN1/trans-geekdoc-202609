A B C D
0 0.0457 -0.0141 1.3809 NaN
1 -0.9555 -1.5010 0.0372 NaN
2 -0.6627 1.5348 -0.8599 NaN
3 -2.2459 1.2373 -0.1337 NaN
4 1.1415 1.9517 -2.3204 NaN
5 -0.0499 -1.6497 -1.0846 NaN
6 -1.0476 -0.7486 -0.8055 NaN
7 NaN NaN NaN NaN
8 NaN NaN NaN NaN
9 NaN NaN NaN NaN

Keep in mind that the default behavior for operations involving a DataFrame and Series is to align the DataFrame columns; this results in a row-wise output. Here is a simple illustration:

names = pd.Series(['SF', 'San Jose', 'Sacramento'])
sizes = pd.Series([852469, 1015785, 485199])

```
df = pd.DataFrame({'Cities': names, 'Size': sizes})
df = pd.DataFrame({'City name': names,'sizes':

print(df)
```

The output of the preceding code block is here:

City name sizes
0 SF 852469
1 San Jose 1015785
2 Sacramento 485199

# PANDAS BOOLEAN DATAFRAMES