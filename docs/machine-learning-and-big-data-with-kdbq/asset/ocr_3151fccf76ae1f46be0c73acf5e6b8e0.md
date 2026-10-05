# Joins 135

# 7.2.8.1 The Valid Join

Empirical analysis requires time to time using the tangent concept of the “next valid” value. This may arise, for example, when we analyse the outcome of an action or exploring the predictive features of the model at hand. In such a case, we may need to find the next valid quote as of given time series. Fortunately, it is easy to derive such functionality from the functions we know.

Let us consider two sets of data, each containing information about trades indicator of buy or sell as the timestamp when the trade took place – for one asset traded at distinct venues. Such an example corresponds to the stock traded at different exchanges, contract for differences (CDF) or currency pair traded at different electronic communication networks (ECNs). When proposing hypothesis we want to (dis)prove causality between trades among the data sets, namely that the buy/sell trade in one set is Granger-causing the buy/sell trade in the other data set.

We create two sample data sets such that there is no underlying law between the two data sets and any causality found would be a random coincidence. The first data set contains 100 observations while the second one contains 1000 data points

```
dataSet1: ([ time: asc "t$-100?"j$23:59:59.999; trade1:100?(-1 i));
dataSet2: ([ time: asc "t$-10000?"j$23:59:59.999; trade2:10000?(-1 i));
```

The data looks as follows:

| time | trade1 |
|---|---|
| 00:01:25.332 | 1 |
| 00:21:24.796 | -1 |
| 00:38:39.521 | 1 |
| 00:40:41.670 | -1 |
| 00:48:08.048 | 1 |
| 00:57:47.067 | 1 |
| 01:08:00.945 | 1 |
| 01:16:06.996 | 1 |
| 01:18:04.504 | -1 |
| 01:41:38.331 | 1 |
| 01:44:34.553 | 1 |
| 01:53:15.027 | 1 |
| 01:56:57.413 | 1 |
| 02:01:13.658 | 1 |
| 02:01:32.603 | 1 |
| 02:03:46.211 | 1 |
| 02:14:19.509 | 1 |
| 02:48:28.645 | 1 |
| 02:55:22.645 | 1 |
| 03:01:31.152 | -1 |

and similarly for dataSet2.