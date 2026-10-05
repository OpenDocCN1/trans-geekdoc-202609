# A Few Use Cases

Using standard trd trade data, and pretending that this is now the result of today's past updates, stored in cache, we can represent our cache as:

| sym | time | volume price |
|---|---|---|
| CLM6 | 10:20:00.329 | 12:00:00.227 11:00:00.195 4 3 2 38.3 40.61 41.43 |
| E | 12:37:02.106 | 07:57.06.069 07:56:07.585 1 1 1 1240.5 1 |
| GCM16 | 13:00:00.128 | 15:20:00.020 16:00:00.034 3 3 1 38.04 40.78 1257.9 |
| NEW | 14:35:01.241 | 06:31:08.386 06:31:02.386 1 1 1 1241.2 1 |
| VX16 | 12:00:00.153 | 10:18:34.613 28:34:31.631 6 3 1 1239.7 1240 1258.7 |

Assume we want to run our N-tick VWAP calculation in realtime. Further, suppose that we have registered a callback function, which is a function that gets called by our upstream feed every time there is a new update from the market. The input of this function is a table with the newly arrived data:

```
newdata: ([sym:'CLM6','GCM16',time:16:30:00 16:30:01 16:30:02t;volume
  → 5 4 3h;price:1260 42.5 1270);
```

| sym | time | volume price |
|---|---|---|
| VX16 | 16:30:00.000 5 | 1260 |
| CLM6 | 16:30:01.000 4 | 42.5 |
| GCM16 | 16:30:02.000 3 | 1270 |

We shall call this function .quantQ.up.trades, where up stands enables placing this function under this namespace to create other functions in the future for types of updates.

```
.quantQ.up.trades: {[new
// -- the incoming data sent by the upstream feedhandler or
 // tickerplant, in type format
// 1
// aggregate the new data by time, volume and price
// then insert each list to each column for each key (record) of the
// global trades cache
trades: .select time,volume,price by sym from new;
// run a 3-tick vwap using each-both on every record
// : select sym, (~3-volume) wag('~3-price) from trades;
);
```

We run our function and observe the result:

```
.quantQ.up.trades newdata
```

| sym | price |
|---|---|
| CLM6 | 41.63222 |
| E | 41.44167 |
| GCM16 | 741.4629 |
| NEW | 41.4.4 |
| VX16 | 1253.189 |