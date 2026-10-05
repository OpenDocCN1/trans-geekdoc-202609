# A Few Use Cases

838

We now time an approach applying wavg on each domain of weights and prices (i.e. table record). Note how we also need to transpose the lists of weights and prices to ensure that the operation can actually run by record:

```
\t res2: select sym,time, wmid: flip(( bidSize1; bidSize2; askSize1;
\taskSize2 )
wawg 'flip (bid1; bid2; ask1; ask2) from q
```

5436

```
res1~res2
```

1b

The results match. However, our recommended approach took around 800 milliseconds on a table with 10 million records and was more than 6 times faster than applying the function record by record. The ability of wavg to work in-depth across a 2-dimensional list is very welcome and reminds us that we should always use the simplest and natively supported approaches when available, instead of building our.

# 11.3 CONSECUTIVE RUNS OF

Assume we have a time series – typically a series of observed metrics such as a price – we want to calculate the time series points which obey a given rule for a number of consecutive occurrences in a row.

For example, in the following list of randomly generated prices:

```
prices: 10?5;
```

```
4 1 4 4 4 0 2 0 4
```

We want to know if the time series is outside 50 percent of its five-point moving standard deviation, for two ticks in a row.

We first calculate the indices which are outside half of the standard deviation:

```
indices: { not x within (a-d;(a:5 mdev x)+d:.5*mdev x) } prices;
```

```
0011010011b
```

How would we calculate the sequential occurrence of this rule? In other words, how do we find the indices where this rule holds for N times in a row?