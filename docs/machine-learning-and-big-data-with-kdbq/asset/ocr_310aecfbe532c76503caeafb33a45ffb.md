# 136 DATA OPERATIONS

We shall try to reverse the data as the next valid join is equal to the last valid concept in inverse. We can achieve this by doing exactly that: we revert the time series ...t1 > t2 > t3... will turn into ...t1 < t2 < t3.... Such operation can be done by multiplying the time by -1. This is possible as the underlying type timestamp is either float or integer:

```
exampleTime:12:34:56.789
"j$exampleTime
```

4529689j

while

```
exampleTime:12:34:56.789;
(neg exampleTime; "j$exampleTime);
```

```
(-12:34:56.789; -45296789j)
```

The multiplication by -1 is achieved by applying the neg function. The negative time is then sorted in ascending order. We can achieve the “next valid” join using the following construction:

```
dataSetCombined: aj[
  `time`;n  `time xasc update time from dataSet1`;
  `time xasc update time from dataSet2` );
dataSetCombined: `time xasc update time from dataSetCombined`;
dSetCombined
```

| time trade1 trade2 |
|---|---|---|
| 00:16:31.025 -1 | 1 |
| 00:42:09.536 -1 | 1 |
| 00:44:37.591 -1 | 1 |
| 00:53:31.660 1 | 1 |
| 01:11:57.854 -1 | -1 |
| 01:26:29.905 1 | 1 |
| 01:53:42.097 -1 | -1 |
| 02:24:40.646 1 | -1 |
| 03:13:22.778 -1 | -1 |
| 03:13:29.907 1 | 1 |
| 03:22:49.917 -1 | 1 |
| 04:07:07.565 1 | 1 |
| 04:22:58.062 -1 | -1 |
| 04:35:02.468 -1 | -1 |
| 04:42:08.234 -1 | 1 |

In the previous insert, we have inverted the sign of the timestamp column after join and further sorted the table. The result is a table which has the same number of rows as dataSet1 and contains the next valid trade from dataSet2.