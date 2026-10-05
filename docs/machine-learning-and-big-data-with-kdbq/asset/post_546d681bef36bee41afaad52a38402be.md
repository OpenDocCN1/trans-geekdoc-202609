
## Parallelisation

and then execute

```
timeseriesForDates: { 10000000 ? 10f } each til 5;
getDailySpread: { 0N!(.z.n; count x ); avg x };
t: getDailySpread timeseriesForDates
```

```
(001523:08:08.109042000;100000000)
(001523:08:08.122165000;100000000)
(001523:08:08.133187000;100000000)
(001523:08:08.144300000;100000000)
(001523:08:08.156924000;100000000)
57
```

```
pr: getDailySpread peach timeseriesForDates
```

```
(001523:15.051134000;100000000)
(001523:15.051123000;100000000)
(001523:15.051174000;100000000)
(001523:15.066006000;100000000)
(001523:15.068296000;100000000)
27
```

r~pr

The thread assignment described in the previous paragraph may on occasion be suboptimal: the different items in the list may be computationally different, and slaves may receive an overall imbalanced list of tasks. For example, having N = 5 and market activity on Wednesdays may be on average the lightest tasks computationally, only as opposed to other days. Thus, 2 will finish much earlier than slaves. It is the responsibility of the user to know the function and think whether distributing the data for parallelisation makes sense or not, depending on use case.

In addition to threads, there is another option which allows for a uniform parallelisation, coming from .Q namespace. .Q cuts the vector and executes the function in chunks in parallel. The parallelisation works by splitting list homogeneously, assigning the function and each sub-vector to thread for computation and finally flattening the results. Let's slightly modify the previous example to be a single vector of data values and compare the single-threaded approach to multithreaded, using .Q:

```
timeseries: raze timeseriesForDates
avg timeseries
50002
```

So here we see that calling .Q has split the vector into N = 3 lists (equal to threads we have) and returned the application of avg function to those 3 sub-vectors. So calling .Q in this example is similar to map-reduce paradigm and we need to therefore reapply avg function to get the final result:

```
avg .Q[avg; timeseries]
50002
```

Let us now time the two calls: this reveals that using threads is not always optimal.

```
avg timeseries
58
```

```
avg .Q[avg; timeseries]
110
```

The reason for this is that the overhead of splitting the vector and serialising back and forth between threads is not justified, especially since the computation is relatively simple: an average function which is natively optimised by q to work on large vectors. Replace the above with a computationally heavier function and the benefits of parallelisation begin to emerge:

```
heavyFunc: { sqrt[x] }
r: heavyFunc 100000#timeseries
37
```

```
r~.Q[heavyFunc; timeseries]
18
```

.Q has also ensured that our data was uniformly split and therefore equal resources were used across our thread pool. The above illustrates that parallelisation itself carries a trade-off between parallel execution and the overhead needed to set parallel execution. This is true for both threads and .Q. We should aim in parallelising computationally heavy tasks as q is powerful enough to handle simple vector tasks in a single thread. In later chapters we will provide more examples of parallelisation when solving practical problems.

## 8.2 PARALLELISATION OVER PROCESSES

There is an alternative to threads for parallelisation in the kdb+/q framework, which we are going to motivate briefly: parallelisation across processes. This means that instead of specifying a list of single-threaded slaves, we specify a list of processes over which the computation can be parallelised. This is achieved by running -s with negative integer:

```
> q -s -N
```

which allows our instance to connect to other q process with N threads, each one linked to process from a list of ports specified by a function .pz which returns unique integers, each representing a handle to slave slave process. The parallelisation over processes is specified by the minus sign in front of N.

In this case, the data have to be present on each of the processes or as arguments of the function. There is no implicit memory management for parallelisation across processes unless those are using the -w flag. In this setup, one ought to be careful in terms of data size transferred or required memory, which may significantly increase the overhead.

The parallelisation over processes is useful for partitioned databases with .Q map[] which keeps the partitions mapped to memory to prevent overhead when the historical data is being repeatedly called with select. Besides, we may use this option to distribute a heavy computation across different servers with grid-like fashion. In such a case, the data and memory have to be managed appropriately, for example a copy of the underlying data being stored on each server with only a relatively small output being transferred.

## 8.3 MAP-REDUCE

For partitioned tables, q has another property which makes parallelisation more useful. Let us assume that we have built our historical database as a partitioned table over dates as we demonstrated in Chapter 6. Our goal is to calculate the average spread over a list of dates for table qt:

```
select avgSpread: avg .5 * bidprice + askprice from qt date in
-- 2016.04.07 2016.04.08
```

In order to calculate the average, q will first apply a partial sum operation for each date partition and count the number of elements in each date. By running function avg, q recognises that this operation is run over a partitioned table and employs the map-reduce paradigm. This means that the average is calculated in two steps. First, the number of elements and sum of values for each date is obtained and recorded (map). Then, the sum of sums is divided by the sum of counts (reduce) and the average is returned.

Semantically, the above query can be approximated as follows:

```
map: select cnt: sum .5 * bidprice + askprice, avgSpread: sum .5 * bidprice + askprice
by date from qt where in 2016.04.07 2016.04.08
reduce: select avgSpread: sum[avgSpread] % sum cnt from map
```

This optimisation is done automatically and has two benefits:

- Memory: it is more efficient since each on-disk partition directory is reduced to a single number, instead of reading all values for all dates into memory - the latter being memory inefficient.
- Functions have built-in map reduce implemented: count, avg, cor, scor, var, sev, sdev, scov, first, last, max, min, prd, sum, wag, wsum and distinct. It is important to mention that q will only recognise these functions and apply map-reduce on them. Functions outside of this domain will return the result applied individually to each date partition. As an example, observe this oddity:

```
last bidsize sum deltas bidsize from qt where code=`CLM16
```

```
bidsize bidsize1
3 12
```

We expect bidsize and bidsize1 to be the same number, since summing up the differences of a vector should give the last value of vector. However, removing the sum from the query reveals that map-reduce did not work exactly as expected, since (at the time of writing) delta is not a function which is supported:

```
select date, bidsize, dbsize: delta bidsize from qt where code=`CLM16
```
